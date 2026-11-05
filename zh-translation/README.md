# Equality Project — 用户文档

**Equality Project** 是一个平台：社区在其中**在自己的成员的手机上**启动属于自己的**孤立信任网络**：没有服务器，没有管理员，没有运营成本。

**DOI:** [10.5281/zenodo.23558900](https://doi.org/10.5281/zenodo.23558900)

> **状态：测试版本（pre-release）。** 应用程序已在测试网络的模拟器上完全验证。在真实手机上的验证和首批试点还在后面。文档按 v9.16 / protocol_version 3 规范描述产品的运作（包括守护人改选 `update_guardians`：48 小时窗口，150 次生效变更的上限；第八个场景——订阅资源：带周期配额与失效机制的订阅网络（recurring））。

> **语言。** 文档提供俄语（原文，`docs/`）与翻译版本：
> [本目录](.)——中文。应用程序的界面语言——
> ru, en, es, pt, zh（主仓库的 `app/lib/l10n`）。

© 2026 Kirill Lapchinsky · rumatakira74@gmail.com · Telegram [@rumatakira](https://t.me/rumatakira)

## 目录

1. [关于平台](docs/01-about.md)——它是什么、面向谁、八个场景、角色
2. [开始使用](docs/02-getting-started.md)——安装、创建钱包、担保、登录
3. [日常操作](docs/03-operations.md)——发行、转账、手续费、损耗费、恢复
4. [所有者的安全](docs/04-security.md)——PIN 与生物识别、胁迫 PIN、保护的边界
5. [常见问题与词汇表](docs/05-faq-glossary.md)

## 项目的其他仓库

- [equality-trust-networks](https://github.com/rumatakira74/equality-trust-networks)——平台的源代码与规范
- [equality-programming-docs](https://github.com/rumatakira74/equality-programming-docs)——面向程序员的文档
- [equality-anti-farm-simulation](https://github.com/rumatakira74/equality-anti-farm-simulation)——农场经济模型（参数的依据）

## 免责声明

项目处于预发布状态；担保与责任的边界在 [DISCLAIMER.md](DISCLAIMER.md)（中文与英文）中描述。

## 许可证

源代码开放用于**非商业用途**；商业使用与商业衍生作品——按付费许可证（条件见规范的第 16 节）。

许可证文本：[LICENSE](../LICENSE)（俄文原文，法律上占优）· [LICENSE-ENG.md](../LICENSE-ENG.md)（非官方英文翻译）。
