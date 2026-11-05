# 1. Acerca de la plataforma

## Qué es

Equality Project es una plataforma en la que una comunidad (una escuela, una cooperativa, un grupo de voluntarios, una diáspora, un fondo, el organizador de un evento) lanza **su propia red aislada** en los teléfonos de sus miembros:

- **sin servidores** — la red vive en los propios teléfonos;
- **sin administrador** — no hay nadie que pueda «apagar» la red o cambiar sus reglas;
- **sin costos de operación** — no hace falta pagar por alojamiento ni mantenimiento.

Cada red da a sus miembros tres cosas:

1. **Una persona ≈ un monedero.** El acceso es solo mediante avales de miembros activos, más la verificación de hardware del teléfono. Es la barrera principal contra las cuentas falsas.
2. **Derecho periódico e igual.** La «unidad» de la red (horas, cuota, puntos) se emite a todos los miembros activos **por igual**, según un calendario.
3. **Historial público y verificable.** La reputación de un miembro — la edad del monedero, quién avaló a quién, la contribución — es visible para todos los miembros de la red.

Qué se considera «unidad» y qué se puede hacer con ella lo define el **perfil de la red**: una moneda interna, un banco de tiempo, cuotas sobre un recurso común, el registro del aporte voluntario, etc.

La red se monta a partir de una **plantilla lista** para uno de los ocho escenarios: el organizador elige la plantilla, define los parámetros — y obtiene su red con su propia aplicación (APK).

## Esto no es una criptomoneda

- La plataforma **no emite ni vende tokens**, no crea un mercado de intercambio y no recompensa la minería en el sentido habitual.
- Las unidades existen solo dentro de una red concreta y en algunos perfiles ni siquiera se transfieren.
- El valor está en el uso (véase los escenarios más abajo), no en la cotización de la unidad.
- Las palabras «monedero», «emisión», «checkpoint» — son el vocabulario técnico del registro de entradas firmadas, no el signo de un instrumento financiero.

## Ocho escenarios de uso

| N.º | Escenario | Unidad |
|-----|-----------|--------|
| 1 | Educación y laboratorio de instituciones (incluidas simulaciones) | puntos o moneda de juego |
| 2 | Prueba de humanidad como servicio para otras aplicaciones | «pulso» de actividad no transferible |
| 3 | Cuotas iguales sobre un recurso común (agua, internet, almacén) | cuota por periodo, no se acumula |
| 4 | Programas voluntarios y callejeros (alimentación, ayuda) | vales del programa |
| 5 | Moneda interna o banco de tiempo de la comunidad | horas o moneda, emisión igual |
| 6 | Registro del aporte voluntario | puntos por aporte verificado |
| 7 | Caja de ayuda mutua | moneda, demurrage contra el acaparamiento |
| 8 | Recurso de suscripción — suscripción a un recurso recurrente (comercial) | cuota por periodo, lo no usado se extingue |

## Las redes están aisladas, y esa es su propiedad principal

- No una sola gran red, sino **muchas redes separadas**. Cada una tiene su composición, sus reglas (perfil), sus unidades.
- Entre las redes no hay intercambio. El saldo de una red no significa nada en otra.
- Las reglas de la red quedan escritas en el **manifiesto** al crearla y por defecto son inmutables; el hash del manifiesto queda fijado en el genesis. Si a la comunidad ya no le convienen las reglas — se lanza una red nueva (es gratis) y los miembros pasan voluntariamente.
- El nivel de garantías de la red **se calcula del manifiesto**, no se declara: los socios ven de qué red y con qué garantías llega la «persona».
- Cada red se monta con **su propia aplicación**: la etiqueta `Eq-<hash8>` (hash corto del identificador de la red) en el nombre de la aplicación muestra que está instalada precisamente su red; en la aplicación la red está firmada con el nombre y la etiqueta — por ejemplo, «cirrus · Eq-e5796f9c».
- En las redes de suscripción (escenario 8) las cuotas no se acumulan: la parte no usada se extingue en el límite del periodo, y el excedente se puede transferir a quienes necesitan el recurso (más detalles en [Operaciones diarias](03-operations.md)).

## Roles del miembro

Cada rol es un monedero normal; nadie tiene «permisos» especiales:

- **Miembro** — un monedero registrado; tras la activación recibe la emisión y transfiere unidades.
- **Avalador** — un miembro activo con una antigüedad de 3 meses o más, que responde por una persona nueva con una de sus ranuras de aval limitadas.
- **Guardián** — una persona designada de antemano para recuperar el acceso si se pierde el teléfono (guardianes personales — 2 de 3; o públicos — 3 de 5).
- **Proveedor / destinatario del fondo común** — un monedero indicado en los parámetros de la red (por ejemplo, un punto asociado que acepta los vales). No puede administrar la red.

## Con honestidad sobre los límites

- **Sin smartphone adecuado no hay participación.** El protocolo exige un teléfono Android con almacén de claves de hardware seguro. No hay esquemas alternativos (curadores, recibos de papel).
- **El anonimato no es el objetivo.** El registro de la red es público dentro de la red: los miembros ven las direcciones, los estados y el historial de los demás; el saldo se deduce del estado público de la red.
- **La protección contra granjas es económica, no absoluta.** Crear un monedero extra debe costar más de lo que rinde; una garantía plena de «una persona — un monedero» sin un ancla externa es técnicamente imposible.

→ Siguiente: [
Primeros pasos](02-getting-started.md)
