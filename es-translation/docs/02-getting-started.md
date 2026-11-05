# 2. Primeros pasos

> **Estado: versión de prueba.** La aplicación está verificada en una red de prueba cerrada sobre emuladores. La compilación pública y la publicación en las tiendas de aplicaciones — después de los pilotos. Todos los pasos siguientes describen el camino completo de incorporación.

## Qué hará falta

- Un smartphone Android con almacén de claves de hardware seguro (StrongBox / TEE) y una huella digital configurada.
- Un dispositivo sin biometría configurada no se admite al registro: la aplicación propondrá configurar la biometría mediante la pantalla del sistema.
- Conocidos en la red: para activar el monedero se necesitan **3 avales** de miembros activos (véase más abajo).

## Instalación

La aplicación se distribuye como APK (la sección sobre la distribución vía Google Play — en revisión jurídica). Instale el archivo APK de su red: cada instancia de red puede distribuir su propia compilación con los parámetros integrados. La aplicación de la red está firmada con el nombre de la red y la etiqueta `Eq-<hash8>` — compruebe la etiqueta al instalar para no instalar una red ajena. La aplicación y la red deben coincidir en la **versión del protocolo** (la actual — 3): el número queda escrito en cada transacción y en cada checkpoint; una compilación de otra versión no es aceptada por la red.

La interfaz de la aplicación está disponible en cinco idiomas: ruso, inglés, español, portugués, chino.

## Creación del monedero

1. La aplicación crea el par de claves **dentro del almacén seguro del teléfono (Keystore)**. La clave privada no es exportable: no se puede copiar, extraer ni reenviar — nunca.
2. El teléfono pasa la **atestación de hardware**: la red comprueba que es un dispositivo real con arranque intacto y hardware protegido, y que la cadena de atestación fue emitida precisamente para su clave nueva (la vinculación de la clave al certificado — cada nodo de la red la comprueba por sí mismo; no se puede sustituir una cadena ajena). La imagen de la huella no se envía a ninguna parte.
3. Se ejecuta una tarea computacional (proof-of-work) — protección contra el registro masivo automatizado. Toma unos segundos.
4. El monedero recibe el estado **registered** — ya puede recibir transferencias, pero la emisión y el envío todavía no están disponibles.

Una persona ≈ un monedero: el registro repetido desde el mismo dispositivo está **dificultado** — exige un trabajo computacional (PoW) sustancialmente más costoso, y no existe una garantía de hardware estricta «un dispositivo — un monedero».

## Avales: el camino hacia el estado activo

Para un funcionamiento pleno el monedero debe volverse **active**. Para ello se necesitan **K = 3 avales** (`vouch`) de distintos miembros activos.

**Quién puede avalar:**

- un miembro con estado `active` y edad del monedero de 3 meses o más;
- que tenga ranuras de aval libres (son pocas: 3–5 según la antigüedad);
- el aval se puede formalizar en persona mediante un código QR o Bluetooth.

**Qué significa el aval.** El avalador arriesga solo su ranura y su parte de la recompensa; no corre el riesgo de perder unidades. Por un novato honesto el avalador recibe el **10% de las primeras 12 emisiones** del avalado (se paga de la emisión del propio novato, no de la nada). Si se descubre que el novato violó las reglas — el avalador pierde la recompensa.

**Si no tiene conocidos en la red:** use los canales públicos de la comunidad, donde los novatos encuentran avaladores. El avalador responde por su elección con una ranura limitada — «repartir» avales a cualquiera no le conviene.

## Primer acceso y PIN

En la configuración usted elige:

- **PIN** — el medio principal de confirmar las operaciones peligrosas;
- si lo desea — el **PIN de coacción** (véase [Seguridad](04-security.md));
- el acceso a la aplicación — por huella o PIN.

Reglas clave de seguridad:

- **El acceso** a la aplicación — huella o PIN.
- **Las operaciones peligrosas** (transferencia, emisión, inicio de migración) — **solo introduciendo el PIN explícitamente**. La huella nunca se usa para confirmarlas: el dedo se puede poner por la fuerza, el PIN no.
- Si el PIN de coacción está activado, el acceso por huella se desactiva.

Añadir una huella nueva en el sistema **invalida la clave** (más seguro, pero significa perder el acceso) — por eso asigne guardianes de inmediato.

## Guardianes: asígnelos de inmediato

Asigne los guardianes **al crear el monedero**, y no cuando el teléfono ya esté ahogado:

- **guardianes personales** — 2 de 3 personas a su elección;
- o **guardianes públicos** — miembros verificados con antigüedad de 12 meses o más; umbral de 3 de 5 (se pueden combinar).

¿El guardián murió, desapareció o salió de la red? Los guardianes se pueden **reelegir más tarde** — con el consentimiento de los nuevos (ventana de 48 horas, límite de 150 cambios efectivos). Cómo hacerlo — en la sección [«Cambio de guardianes»](03-operations.md#cambio-de-guardianes). No aplace la asignación en sí: sin guardianes la recuperación es imposible.

Con más detalle — en la sección [Recuperación](03-operations.md#recuperación-del-acceso).

Y de inmediato rellene la **tarjeta de recuperación** (véase [Recuperación](03-operations.md#tarjeta-de-recuperación--rellénela-de-antemano)): la dirección de su monedero, las direcciones de los guardianes y el nombre de la red — anótelos y guárdelos fuera del teléfono. Si pierde el teléfono, estos datos ya no habrá de dónde sacarlos. La aplicación los muestra en la pantalla «Tarjeta de recuperación» con un código QR.

## Estados del monedero

| Estado | Cómo se obtiene | Qué se puede |
|--------|-----------------|--------------|
| `registered` | tras el registro (atestación + PoW) | recibir transferencias |
| `active` | 3 avales | emisión, transferencias, avales |
| `expired` | 3 años en registered sin activar | las transferencias hacia la dirección se conservan; para emitir hace falta un registro nuevo |
| la marca `flagged` | violación probada (doble firma) | emisión suspendida, no se puede avalar a otros |

→ Siguiente: [Operaciones diarias](03-operations.md)
