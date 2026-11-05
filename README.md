# Equality Project — документация пользователя

Английская версия документа: [README-ENG.md](README-ENG.md).

**Equality Project** — платформа, на которой сообщество запускает свою **изолированную сеть доверия** на телефонах участников: без серверов, без администратора и без операционных расходов.

**DOI:** [10.5281/zenodo.23558900](https://doi.org/10.5281/zenodo.23558900)

> **Статус: тестовая версия (pre-release).** Приложение полностью проверено в тестовой сети на эмуляторах. Проверка на живых телефонах и первые пилоты — впереди. Документация описывает работу продукта по спецификации v9.16 / protocol_version 3 (включая перевыбор гардианов `update_guardians`: окно 48 ч, лимит 150 вступивших в силу смен; восьмой сценарий — абонентский ресурс: сети-подписки с периодными квотами и сгоранием).

> **Языки.** Документация доступна на русском (оригинал, `docs/`) и в переводах:
> [eng-translation/](eng-translation/) — английский,
> [es-translation/](es-translation/) — испанский,
> [pt-translation/](pt-translation/) — португальский,
> [zh-translation/](zh-translation/) — китайский,
> [fr-translation/](fr-translation/) — французский,
> [de-translation/](de-translation/) — немецкий,
> [it-translation/](it-translation/) — итальянский,
> [ja-translation/](ja-translation/) — японский. Языки интерфейса приложения —
> ru, en, es, pt, zh, fr, de, it, ja (`app/lib/l10n` основного репозитория).

© 2026 Лапчинский Кирилл (Kirill Lapchinsky) · rumatakira74@gmail.com · Telegram [@rumatakira](https://t.me/rumatakira)

## Содержание

1. [О платформе](docs/01-about.md) — что это, кому нужно, восемь сценариев, роли
2. [Начало работы](docs/02-getting-started.md) — установка, создание кошелька, поручительства, вход
3. [Ежедневные операции](docs/03-operations.md) — выпуск, переводы, комиссия, демередж, восстановление
4. [Безопасность владельца](docs/04-security.md) — PIN и биометрия, тревожный PIN, границы защиты
5. [Вопросы и ответы, словарь](docs/05-faq-glossary.md)

## Другие репозитории проекта

- [equality-trust-networks](https://github.com/rumatakira74/equality-trust-networks) — исходный код и спецификация платформы
- [equality-programming-docs](https://github.com/rumatakira74/equality-programming-docs) — документация для программистов
- [equality-anti-farm-simulation](https://github.com/rumatakira74/equality-anti-farm-simulation) — модель экономики ферм (обоснование параметров)

## Отказ от ответственности

Проект в статусе предварительного выпуска; границы гарантий и ответственности описаны в [DISCLAIMER.md](DISCLAIMER.md) (русский и английский).

## Лицензия

Исходный код открыт для **некоммерческого использования**; коммерческое использование и коммерческие производные работы — по платной лицензии (условия — в спецификации, раздел 16).

Текст лицензии: [LICENSE](LICENSE) (русский оригинал, юридически главенствует) · [LICENSE-ENG.md](LICENSE-ENG.md) (неофициальный английский перевод).
