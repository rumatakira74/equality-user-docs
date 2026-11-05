# Equality Project — documentación de usuario

**Equality Project** es una plataforma en la que una comunidad lanza su **propia red de confianza aislada** en los teléfonos de sus miembros: sin servidores, sin administrador y sin costos de operación.

**DOI:** [10.5281/zenodo.23558900](https://doi.org/10.5281/zenodo.23558900)

> **Estado: versión de prueba (pre-release).** La aplicación está completamente verificada en la red de prueba sobre emuladores. La verificación en teléfonos reales y los primeros pilotos están por venir. La documentación describe el funcionamiento del producto según la especificación v9.16 / protocol_version 3 (incluida la reelección de guardianes `update_guardians`: ventana de 48 h, límite de 150 cambios efectivos; el octavo escenario — un recurso de suscripción: redes de suscripción (recurring) con cuotas por periodo y extinción).

> **Idiomas.** La documentación está disponible en ruso (el original, `docs/`) y en traducciones:
> [este directorio](.) — español. Los idiomas de la interfaz de la aplicación —
> ru, en, es, pt, zh (`app/lib/l10n` del repositorio principal).

© 2026 Kirill Lapchinsky · rumatakira74@gmail.com · Telegram [@rumatakira](https://t.me/rumatakira)

## Contenido

1. [Acerca de la plataforma](docs/01-about.md) — qué es, para quién es, los ocho escenarios, los roles
2. [Primeros pasos](docs/02-getting-started.md) — instalación, creación del monedero, avales, acceso
3. [Operaciones diarias](docs/03-operations.md) — emisión, transferencias, comisión, demurrage, recuperación
4. [Seguridad del propietario](docs/04-security.md) — PIN y biometría, PIN de coacción, límites de la protección
5. [Preguntas y respuestas, glosario](docs/05-faq-glossary.md)

## Otros repositorios del proyecto

- [equality-trust-networks](https://github.com/rumatakira74/equality-trust-networks) — el código fuente y la especificación de la plataforma
- [equality-programming-docs](https://github.com/rumatakira74/equality-programming-docs) — la documentación para programadores
- [equality-anti-farm-simulation](https://github.com/rumatakira74/equality-anti-farm-simulation) — el modelo de la economía de granjas (la justificación de los parámetros)

## Aviso legal

El proyecto está en estado de versión preliminar; los límites de las garantías y de la responsabilidad se describen en [DISCLAIMER.md](DISCLAIMER.md) (español e inglés).

## Licencia

El código fuente está abierto para el **uso no comercial**; el uso comercial y las obras derivadas comerciales — bajo una licencia de pago (las condiciones — en la especificación, sección 16).

El texto de la licencia: [LICENSE](../LICENSE) (el original en ruso, jurídicamente prevalente) · [LICENSE-ENG.md](../LICENSE-ENG.md) (una traducción inglesa no oficial).
