# Glosario (RU → ES) — mínimo para el usuario

Terminología fija para el espejo `es-translation/` de este repositorio. Los términos siguen la localización de la aplicación (`app/lib/l10n`, `app_es.arb` del repositorio principal) y, cuando la localización no tiene el término, los textos ingleses establecidos de la plataforma (`docs/KNOWLEDGE-ENG-1..5.md`, `README-ENG.md`); no se inventan sinónimos. El glosario completo para desarrolladores está en `equality-programming-docs`; este archivo es el subconjunto reducido y orientado al usuario aplicado en estas traducciones.

Los identificadores de código, nombres de campos y etiquetas (`protocolVersion`, `Eq-<hash8>`, `K = 3`, PIN, QR) nunca se traducen.

| Ruso | Español (establecido) |
|------|----------------------|
| кошелёк | monedero |
| реестр | registro (el registro de la red) |
| генезис | genesis |
| версия протокола | versión del protocolo (`protocolVersion`) |
| манифест | manifiesto |
| посевной круг | círculo semilla |
| поручительство | aval; el verbo: avalar; pl. avales |
| поручитель | avalador |
| поручаемый | avalado |
| слот поручительства | ranura (de aval) |
| челлендж выпуска | desafío de emisión |
| выпуск (эмиссия) | emisión |
| окно накопления | ventana de acumulación |
| эпоха | época |
| чекпоинт | checkpoint |
| финальность | finality |
| мораторий | moratoria |
| демередж | demurrage |
| комиссия (сжигаемая) | comisión (se quema) |
| гардиан | guardián |
| подопечный (у гардиана) | tutelado |
| смена гардианов | cambio de guardianes (reelección) |
| миграция | migración |
| социальное восстановление | recuperación social |
| карточка восстановления | tarjeta de recuperación |
| режим-приманка | modo señuelo |
| тревожный PIN | PIN de coacción |
| Flagged (метка) | la marca flagged |
| BT-платёж | pago por Bluetooth |
| профиль сети | perfil de la red |
| поставщик / получатель пула | proveedor / destinatario del fondo común |
| единица | unidad |
| квота | cuota |
| Eq-хеш (`Eq-<hash8>`) | Eq-hash (`Eq-<hash8>`) |
| recurring (сеть-подписка) | red de suscripción (recurring) |
| peer-redeem | `peer-redeem` |
| сгорание квоты | extinción de la cuota (las cuotas no usadas se extinguen en el límite del periodo) |
| период | periodo |
| ферма (кошельков) | granja (de monederos) |
| аппаратная аттестация | atestación de hardware |
| отложенный перевод | transferencia aplazada |
| порог (P) | umbral (P) |
| задержка (D) | retraso (D) |
| эквивокация | equivocación |

Variante de lengua: español neutro (la localización de la aplicación usa la localidad `es` sin región); trato de «usted», como en la aplicación. Se conservan en inglés, según el uso de la propia aplicación: demurrage, checkpoint, finality, genesis, flagged, peer-redeem, recurring, PoW, sandbox, nonce, hex, full/light (niveles del nodo), foreground, APK, QR, BT/Bluetooth, Argon2id, StrongBox, TEE, Keystore.

Números y formato: coma decimal (0,5%); los números, versiones, tamaños de ventana y umbrales no cambian respecto al original; comillas «»; guion largo —; rangos como «3–12 meses», «48 h» con espacio.
