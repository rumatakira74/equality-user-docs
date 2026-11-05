# 4. Seguridad del propietario

## PIN y biometría: para qué sirve cada uno

| Acción | Con qué se confirma |
|--------|---------------------|
| Acceso a la aplicación | huella **o** PIN |
| Transferencia, emisión, inicio de migración | **solo introduciendo el PIN explícitamente** |
| Cambio de guardianes (publicación, cancelación) | **solo introduciendo el PIN explícitamente** |
| Desbloqueo de la clave dentro de la operación | biometría después del PIN — solo «desbloqueo» |

Por qué es así: la huella **se puede coaccionar físicamente** — poner el dedo de otra persona sobre el sensor es posible por la fuerza. El PIN no. Por eso cada operación capaz de causar un daño exige precisamente el PIN, y cada pantalla de introducción del PIN es también el punto de entrada al modo señuelo (más abajo).

El acceso por huella — es solo una comodidad para desbloquear la interfaz; con el PIN de coacción activado se desactiva por completo.

## El PIN de coacción y el modo señuelo

La amenaza: lo obligan a abrir la aplicación o a enviar unidades.

En la configuración usted define dos PIN: **normal** y **de coacción**. El PIN de coacción abre el **modo señuelo**:

- la interfaz se ve exactamente igual, pero muestra un **pequeño saldo verosímil** y un historial (mostrar cero no se puede: en un monedero activo la emisión llega con regularidad, y un saldo nulo sería sospechoso);
- las «transferencias» desde el señuelo terminan con un verosímil «en espera de confirmación» o con un error de red — las transacciones reales no se publican;
- el monedero real sigue funcionando en segundo plano;
- las notificaciones no contienen importes: en la aplicación no hay notificaciones de operaciones; la única notificación del sistema es el servicio en primer plano (foreground) del nodo («El nodo de la red de confianza funciona»), sin importes ni direcciones;
- el «cambio de guardianes» en el señuelo se «ejecuta» de manera verosímil, pero la lista real de guardianes no se toca.

Ambos PIN son **indistinguibles**: el mismo tiempo de apertura, la misma interfaz, el mismo límite de intentos. El PIN de coacción se aplica en **cualquier** pantalla de introducción del PIN — transferencia, emisión, cambio de ajustes.

**Ocultar se puede, anular no:** el saldo — es el estado público de la red, la clave no se elimina. La base local se puede eliminar con los medios normales del sistema — se restaurará al conciliarse con la red.

## Transferencias grandes aplazadas — la segunda capa

Una transferencia por encima del umbral (por defecto 3000 unidades) se ejecuta transcurridas **48 horas**; en cualquier momento antes de la ejecución se puede cancelar. Quien coacciona recibe «transferencia enviada», no unidades; usted la cancela en cuanto está a salvo. El retraso es fijo y no se puede desactivar.

## De qué no protege (léalo con honestidad)

- **El registro es público.** Cualquiera a quien usted pagó o de quien recibió conoce su dirección; el historial es público, el saldo se deduce del estado de la red (el registro de la aplicación muestra la dirección, el estado y la edad; el saldo — en el monedero y mediante la prueba Merkle del checkpoint). El señuelo se comprueba: su dirección no coincidirá con la real por la red.
- **Contra un atacante preparado el señuelo no está garantizado.** Funciona contra la coacción rápida y el atraco.
- **Contra el robo del teléfono desbloqueado** protege la firma «en cada operación»: gastar unidades con solo tener el teléfono en las manos no se puede.
- **Contra la pérdida del teléfono** — los guardianes y la migración (sección [Recuperación](03-operations.md#recuperación-del-acceso)). Sin guardianes los fondos se pierden.
- **Un ladrón que conozca su PIN puede cancelar la migración** dentro de la ventana de 14 días — una limitación conocida de la v1: el derecho de cancelación pertenece a la clave antigua. Atenuaciones — guardianes públicos y un nuevo inicio de la migración.

## Lista de verificación de una configuración segura

1. Defina el PIN y el PIN de coacción en el primer arranque.
2. Asigne los guardianes (2 de 3 personales o 3 de 5 públicos) — de inmediato, al crear el monedero.
3. Rellene la tarjeta de recuperación ([sección «Recuperación»](03-operations.md#tarjeta-de-recuperación--rellénela-de-antemano)): la dirección del monedero, las direcciones de los guardianes, el nombre de la red — anótelo y guárdelo fuera del teléfono. Los datos de migración (el nonce, las firmas de los guardianes) no los transmita a nadie ni los publique.
4. No comunique su PIN a nadie; el de coacción — con mayor razón (nadie debe saber de su existencia).
5. Recuerde: añadir una huella nueva en el sistema invalida la clave — es protección contra la sustitución, pero también su riesgo de perder el acceso.
6. No guarde sumas grandes «por si acaso» — el demurrage en las redes con moneda castiga precisamente el almacenamiento.

→ Siguiente: [Preguntas y respuestas, glosario](05-faq-glossary.md)
