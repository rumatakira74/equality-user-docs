# 3. Operaciones diarias

## Emisión

En las redes con emisión periódica, cada miembro activo recibe una vez por periodo (por defecto — cada mes) su **parte igual**: por ejemplo, 1000 unidades el día 1.

Particularidades:

- **El desafío de emisión.** Para declarar la emisión, la aplicación resuelve una tarea computacional en **su ranura del periodo en curso** (ventana de ±48 horas). El momento de la ranura se calcula por adelantado a partir de la dirección y del periodo, y es igual para todos los nodos; la ranura queda dentro del propio periodo, por lo que la ventana **está disponible en cada periodo** (tras la corrección del mint — v9.14: antes la ventana podía caer en un tiempo inalcanzable, y el monedero, tras seis periodos perdidos seguidos, perdía la emisión para siempre). El estado de la ventana lo muestra la pantalla de emisión («abierta — se puede emitir» / «cerrada — cuándo se abrirá»). El periodo perdido no se pierde: el devengo se traslada dentro de la **ventana de acumulación — 6 periodos**, los fondos no se bloquean; un salto consciente más allá de la ventana — la emisión se extingue.
- La primera emisión es posible solo en el periodo **posterior** a la activación, sin devengos retroactivos.
- Los fondos recién emitidos no son transferibles de inmediato (moratoria — véase más abajo).

## Transferencias

- **La comisión se quema.** Cada transferencia paga una pequeña comisión (`fee`) que se destruye — el destinatario recibe exactamente el importe indicado. La comisión protege la red contra el spam y frena levemente el movimiento del valor.
- **La tarifa es adaptativa.** El porcentaje de la comisión lo recalcula la red en el límite de cada época, igual para todos los nodos: si la oferta de unidades crece más rápido que el ritmo objetivo — la tarifa sube; si no, baja. Rango — del 0,5% al 2%, mínimo 0,01 unidades; nadie puede fijar la tarifa manualmente.
- **Moratoria para monederos recientes:** las transferencias están disponibles 14 días después del registro (parámetro de la red; 14 días — el valor por defecto). Esto corta el esquema «registró — vació».
- **El tiempo de la transacción es el momento de la firma.** Las reglas de la red (moratoria, extinción de cuotas, plazos de las transferencias aplazadas, ventana de emisión) se aplican al momento de la firma de la transacción, no al de su publicación: una transferencia firmada sin conexión y publicada después la evalúan igual todos los nodos. El reloj del teléfono no debe desviarse de la red más de ±30 minutos — las transacciones con una desviación mayor no son aceptadas por la red (repita la publicación tras sincronizar la hora).
- **Transferencias grandes aplazadas.** Una transferencia por encima del umbral (por defecto **P = 3000 unidades**) se ejecuta solo transcurridas **48 horas**. Durante el retraso usted puede cancelarla directamente desde la aplicación — por ejemplo, bajo coacción o si cambia de opinión. La regla rige en todas las redes con unidades transferibles y no se puede desactivar. El umbral se puede cambiar dentro del máximo (30000); la subida entra en vigor transcurridas 48 horas, la bajada — de inmediato.

### Redes de suscripción (recurring): cuotas por periodo

En las redes de recurso de suscripción (escenario 8) las unidades son **cuotas por periodo**: cada miembro activo recibe una cuota igual, y la parte no usada **se extingue en el límite del periodo siguiente** — así la suscripción no se convierte en acaparamiento. Transferir o canjear una unidad del periodo pasado tras ese límite no se puede: la aplicación mostrará un error claro «la unidad se ha extinguido». Nadie «pone a cero» el saldo: el historial es visible para todos; simplemente las cuotas viejas ya no se transfieren.

El excedente se puede transferir a quienes no les alcanzan las cuotas: transferencias **miembro → miembro** y **miembro → proveedor** (modo peer-redeem; la confirmación — un recibo firmado). Nota: el modo está soportado por el núcleo y la especificación, pero en la interfaz actual de la aplicación todavía no está implementado.

### Pago por Bluetooth

Bluetooth se usa **solo** para transmitir directamente la transacción firmada al destinatario, cuando no hay internet. El destinatario publica la transacción en la red cuando haya conexión.

**Importante:** mientras la transacción no esté publicada y confirmada por la red, **no es un pago**. El remitente puede entregar la misma cantidad a dos destinatarios. Por eso, en la interfaz el estado es «recibido por Bluetooth — pendiente de publicación», y el destinatario está obligado a esperar la confirmación de la red.

## Demurrage (en redes con moneda)

En los perfiles con valor transferible (moneda interna, caja de ayuda mutua) puede funcionar el **demurrage** — un pequeño «impuesto de custodia» mensual por encima del mínimo exento. El cargo no se realiza como transacción aparte: el saldo efectivo se recalcula de forma determinista en la siguiente operación.

El sentido: el valor está en el flujo, no en la acumulación. El demurrage y la comisión quemada son parte de la protección contra granjas, no un modo de quitarle unidades a alguien: el demurrage se puede «eludir» simplemente sin acumular.

## Avales

- El avalador responde por un miembro nuevo, gastando una de sus **ranuras** (3 con una antigüedad de 3–12 meses, 5 — más allá).
- La ranura se libera cuando el avalado completa 3 periodos de emisión sin infracciones, o bien transcurridos 90 días si nunca se activó.
- La recompensa a los avaladores — el **10% de las primeras 12 emisiones** del avalado, automáticamente y por igual entre los tres.
- Si contra el avalado se prueba una infracción, la recompensa se detiene; al avalador no se le quitan fondos.

## Infracciones y la marca flagged

La única infracción demostrable es la **equivocación**: dos transacciones en conflicto firmadas por el mismo monedero (doble gasto, doble emisión). La prueba la publica cualquier nodo y la comprueban todos por igual. Consecuencias: marca pública `flagged`, suspensión de la emisión durante 3 meses (si se repite — para siempre), prohibición de avalar. «Parece una granja» no es una prueba — no hay veredictos por sospechas.

## Recuperación del acceso

La clave no es exportable, por eso, si se pierde el teléfono, funciona la **recuperación social** (transacción `migrate`):

1. El teléfono nuevo pasa la misma verificación que en el registro.
2. Los guardianes confirman la migración: **personales 2 de 3** o **públicos 3 de 5** (se pueden combinar).
3. **Retraso de 14 días**, durante el cual la clave antigua (si sigue viva) puede cancelar la migración.
4. La edad, el historial, los avales, las emisiones **y los fondos (el saldo)** se transfieren al monedero nuevo; la huella del teléfono antiguo queda en la lista negra para siempre.

### Tarjeta de recuperación — rellénela de antemano

Para iniciar la migración, en el teléfono nuevo habrá que introducir **la dirección antigua del monedero**, y después el nonce y las firmas de los guardianes. Estos datos no se «recuperan de la nada»: en el teléfono perdido no quedaron guardados.

**De antemano, mientras el teléfono funciona:**

- anote **la dirección de su monedero** (hex, se muestra en la aplicación) y guárdela fuera del teléfono (no en la nube) — en papel o como un código QR impreso;
- anote **las direcciones de sus guardianes** y el modo de contactarlos;
- anote **el nombre de la red** (en la aplicación se muestra con la etiqueta `Eq-<hash8>`) y dónde obtener su APK (cada red distribuye su propia compilación).

La aplicación muestra todos estos datos en la pantalla **«Tarjeta de recuperación»** al crear el monedero (y más tarde — en los ajustes y en la pantalla de migración) con un código QR: expórtelos o imprímalos.

**Durante la migración:**

- el nonce y las firmas de los guardianes son las llaves de la recuperación de su monedero: **no los transmita a nadie ni los publique**;
- transmítalos **solo directamente** entre usted y su guardián — en persona o por un canal seguro, no por terceros;
- introdúzcalos solo en su propia aplicación; tras completar la migración, bórrelos de las conversaciones.

Un guardián público (un miembro con antigüedad ≥ 12 meses) recibe por la migración exitosa de su tutelado una recompensa fija de la emisión — no más de una vez cada 12 meses por tutelado.

**Si no hay guardianes asignados**, queda el reinicio: un registro nuevo con una clave nueva y tres avales nuevos. Los fondos del monedero antiguo en ese caso se pierden — asigne guardianes de antemano.

### Cambio de guardianes

El guardián murió, desapareció o salió de la red — los guardianes se pueden **reelegir** (transacción `update_guardians`):

1. **Consentimiento de los nuevos guardianes.** Cada nuevo guardián (hasta 3) firma personalmente el hash del cambio — igual que al confirmar la migración: sin su firma el cambio es imposible.
2. **Publicación del cambio.** Ajustes → Guardianes → «Reelegir»; la publicación y la cancelación — solo tras introducir el PIN explícitamente.
3. **Ventana de 48 horas.** El cambio entra en vigor transcurridas 48 horas desde la publicación; hasta entonces se puede cancelar (también solo con PIN).
4. **Límite — 150 cambios.** No más de 150 cambios efectivos durante la vida del monedero; los cancelados y expirados no cuentan. El contador de cambios restantes se ve en la aplicación.

No hay comisión por el cambio; cada cambio se publica en el historial de la red. Los nuevos guardianes deben estar activos (`active`) y sin la marca `flagged`. En el modo señuelo el «cambio de guardianes» se «ejecuta» de manera verosímil, pero la lista real de guardianes no se toca.

→ Siguiente: [Seguridad del propietario](04-security.md)
