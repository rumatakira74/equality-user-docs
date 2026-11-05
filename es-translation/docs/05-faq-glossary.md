# 5. Preguntas y respuestas · Glosario

## FAQ

**¿Necesita internet?**
Para las operaciones normales — sí, una conexión al menos periódica. Bluetooth permite transmitir la transacción firmada directamente al destinatario, pero el pago solo se consuma tras la publicación y la confirmación por la red.

**No tengo conocidos en la red. ¿Cómo me activo?**
Mediante los canales públicos de la comunidad: allí los novatos encuentran avaladores. El avalador responde con una ranura limitada y con su recompensa; repartir avales a cualquiera no le conviene. El aval se puede formalizar en persona mediante un QR o Bluetooth.

**Perdí el teléfono. ¿Qué pasa con las unidades?**
La clave no es exportable, pero funciona la recuperación social: los guardianes (personales 2 de 3 o públicos 3 de 5) confirman la migración al teléfono nuevo; transcurridos 14 días, la edad, el historial, los avales y los fondos se transfieren. Sin guardianes asignados — solo queda un registro nuevo, y los fondos del monedero antiguo se pierden.

**¿Se pueden cambiar los guardianes?**
Sí. Si el guardián desapareció, murió o salió de la red, reelíjalo: los nuevos guardianes firman personalmente el hash del cambio, el cambio se publica con introducción explícita del PIN y entra en vigor transcurridas 48 horas (hasta entonces se puede cancelar). Límite — 150 cambios efectivos durante la vida del monedero. Con más detalle — [«Cambio de guardianes»](03-operations.md#cambio-de-guardianes).

**Olvidé ambos PIN.**
El monedero queda inaccesible: la clave no se puede extraer y el PIN no se puede «restablecer por correo» — esos canales no existen en un sistema sin servidores. El único camino — la migración mediante los guardianes.

**¿Puede alguien falsificar mi monedero?**
La clave está en el almacén seguro del teléfono; solo ella puede firmar una operación. La falsificación es imposible sin acceso físico al dispositivo desbloqueado.

**¿Y si alguien crea cientos de monederos (una granja)?**
Las barreras: 3 avales por monedero (las ranuras son limitadas), la atestación de hardware (los emuladores y los dispositivos rooteados no la pasan, la cadena de atestación está vinculada a la clave registrada), el desafío computacional en la ranura del periodo en curso, la moratoria de transferencias, la comisión y el demurrage. El modelo de la economía de granjas: con una valoración canónica de $120 por dispositivo, una granja sale en positivo no antes de ~3,5 años (con $200 — a los ~4,5 años) y solo con un alto valor externo de la unidad; varios monederos en un mismo dispositivo abaratan la granja — la estabilidad de la conclusión fue verificada con una rejilla de sensibilidad (costo del dispositivo × número de monederos por dispositivo). El horizonte de verificación de la métrica de seguridad — no menos de 5 años. La garantía «una persona — un monedero» no la da nadie: la protección es económica.

**¿Por qué el saldo disminuyó solo?**
En las redes con moneda funciona el demurrage — un pequeño porcentaje mensual por encima del mínimo exento. Se refleja en la siguiente operación; no hay una transacción de cargo aparte.

**La transferencia «se atascó» durante 48 horas. ¿Es un ataque?**
No, es una transferencia aplazada: una cantidad por encima del umbral (por defecto 3000) siempre se ejecuta transcurridas 48 horas, y se puede cancelar antes de la ejecución.

**¿Se puede votar en secreto dentro de la red?**
En la v1 — no: el identificador para una aplicación de terceros está vinculado públicamente a la dirección. Las votaciones secretas serán posibles solo en versiones futuras.

**La aplicación escribe «la unidad se ha extinguido». ¿Qué es?**
Está en una red de suscripción (recurring): la cuota está vinculada al periodo y, tras el límite del periodo siguiente, ya no se puede transferir. No es una sanción ni una pérdida de saldo — la cuota nueva llega en el periodo nuevo; el excedente es mejor entregarlo mediante peer-redeem a quienes necesitan el recurso.

**¿Cuánto cuesta participar?**
La red no cobra nada por participar. La plataforma no tiene costos de operación en absoluto — los servidores no existen. La comisión de la transferencia se quema, no se la lleva nadie.

## Glosario

| Término | Significado |
|---------|-------------|
| **Monedero** | La cuenta del miembro: dirección + cadena de entradas firmadas + saldo. Uno por dispositivo. |
| **Registro** | El registro público de todas las transacciones de la red; lo guarda y lo comprueba cada nodo. |
| **Genesis** | El paquete de arranque de la red: parámetros, manifiesto, círculo semilla. |
| **Versión del protocolo (`protocolVersion`)** | El número de versión de las reglas de la red (la actual — 3). Queda escrito en cada transacción y en cada checkpoint; la aplicación y la red deben coincidir en la versión del protocolo — una compilación de otra versión no es aceptada por la red. |
| **Manifiesto** | La descripción pública de las reglas de la red; su hash queda fijado en el genesis. |
| **Círculo semilla** | Los primeros miembros del genesis con derechos especiales temporales; los derechos se autoliquidan (seed_sunset: 100 monederos activos o 24 épocas). |
| **Aval (`vouch`)** | La firma de respaldo de un miembro activo por un novato. Tres avales activan el monedero. |
| **Ranura de aval** | El lugar limitado del avalador; se libera tras 3 periodos de emisión del avalado o 90 días. |
| **Desafío de emisión** | La tarea computacional (PoW) en la ranura del periodo en curso, calculable por adelantado; la ventana de ±48 h está disponible en cada periodo, su estado lo muestra la pantalla de emisión; el salto se compensa dentro de la ventana de acumulación (6 periodos). |
| **Época** | El intervalo del tiempo de red (por defecto 24 horas); en los límites de las épocas se ponen checkpoints. |
| **Checkpoint** | La instantánea del estado de la red firmada por un umbral de miembros; da finality y protección a los nodos light. |
| **Finality** | El momento a partir del cual es imposible revertir una transacción. |
| **Moratoria** | El periodo tras el registro (por defecto 14 días) en el que las transferencias salientes no están disponibles. |
| **Demurrage** | El porcentaje mensual por custodia por encima del mínimo; lo cobrado se quema. |
| **Señuelo** | El modo que abre el PIN de coacción: una interfaz verosímil con un pequeño saldo, sin operaciones reales. |
| **Guardián** | El miembro designado para confirmar la migración si se pierde el teléfono. |
| **Migración** | El traslado del monedero a un dispositivo nuevo mediante los guardianes; retraso de 14 días. |
| **Cambio de guardianes** | La reelección de los guardianes personales (hasta 3) con su consentimiento; ventana de 48 h, límite de 150 cambios efectivos durante la vida del monedero. |
| **Flagged** | La marca pública de una infracción probada (equivocación). |
| **Pago BT** | La transmisión de la transacción firmada por Bluetooth; se convierte en pago solo tras la confirmación por la red. |
| **Perfil de la red** | El conjunto de parámetros: la unidad, la emisión, la transferencia, el drenaje, la entrada, etc. |
| **Eq-hash (`Eq-<hash8>`)** | La etiqueta corta de la red (los primeros 8 caracteres de su identificador); se ve en el nombre de la aplicación y en la incorporación — con ella se comprueba que está instalada la red correcta. |
| **Recurring (red de suscripción)** | La red de recurso de suscripción: una cuota igual por periodo, lo no usado se extingue en el límite del periodo. |
| **Peer-redeem** | La transferencia miembro → miembro o miembro → proveedor en las redes recurring: el excedente de cuotas fluye hacia quienes necesitan el recurso (en la interfaz actual de la aplicación todavía no está implementado). |
| **Extinción de la cuota** | La unidad del periodo pasado deja de ser transferible tras el límite del periodo siguiente; el saldo y el historial se conservan. |

---

[← Acerca de la plataforma](01-about.md) · [Contenido](../README.md)
