# 4. Segurança do proprietário

## PIN e biometria: para que serve cada um

| Ação | Com o que se confirma |
|------|-----------------------|
| Acesso ao aplicativo | digital **ou** PIN |
| Transferência, emissão, início de migração | **somente digitando o PIN explicitamente** |
| Mudança de guardiões (publicação, cancelamento) | **somente digitando o PIN explicitamente** |
| Desbloqueio da chave dentro da operação | biometria após o PIN — apenas «desbloqueio» |

Por que é assim: a digital **pode ser coagida fisicamente** — pôr o dedo de outra pessoa no sensor é possível à força. O PIN não. Por isso cada operação capaz de causar dano exige justamente o PIN, e cada tela de digitação do PIN é também o ponto de entrada ao modo isca (abaixo).

O acesso pela digital — é apenas uma conveniência para desbloquear a interface; com o PIN de coação ativado ele é desativado por completo.

## O PIN de coação e o modo isca

A ameaça: eles o forçam a abrir o aplicativo ou a enviar unidades.

Na configuração você define dois PIN: **normal** e **de coação**. O PIN de coação abre o **modo isca**:

- a interface parece exatamente a mesma, mas mostra um **pequeno saldo verossímil** e um histórico (mostrar zero não se pode: numa carteira ativa a emissão chega com regularidade, e um saldo nulo seria suspeito);
- as «transferências» da isca terminam com um verossímil «aguardando confirmação» ou com um erro de rede — as transações reais não são publicadas;
- a carteira real continua funcionando em segundo plano;
- as notificações não contêm valores: no aplicativo não há notificações de operações; a única notificação do sistema é o serviço em primeiro plano (foreground) do nó («O nó da rede de confiança está funcionando»), sem valores nem endereços;
- a «mudança de guardiões» na isca é «executada» de modo verossímil, mas a lista real de guardiões não é tocada.

Ambos os PIN são **indistinguíveis**: o mesmo tempo de abertura, a mesma interface, o mesmo limite de tentativas. O PIN de coação é aplicado em **qualquer** tela de digitação do PIN — transferência, emissão, mudança de ajustes.

**Ocultar se pode, zerar não:** o saldo — é o estado público da rede, a chave não é excluída. A base local pode ser excluída pelos meios normais do sistema — ela se restaurará ao conciliar com a rede.

## Transferências grandes diferidas — a segunda camada

Uma transferência acima do limite (por padrão 3000 unidades) é executada após **48 horas**; a qualquer momento antes da execução ela pode ser cancelada. Quem coage recebe «transferência enviada», não unidades; você a cancela assim que estiver em segurança. O atraso é fixo e não pode ser desativado.

## De que a proteção não protege (leia com honestidade)

- **O registro é público.** Qualquer pessoa a quem você pagou ou de quem recebeu conhece o seu endereço; o histórico é público, o saldo é dedutível do estado da rede (o registro do aplicativo mostra o endereço, o estado e a idade; o saldo — na carteira e pela prova Merkle do checkpoint). A isca é verificável: o endereço dela não coincidirá com o real pela rede.
- **Contra um atacante preparado a isca não é garantida.** Ela funciona contra a coação rápida e o assalto.
- **Contra o roubo do telefone desbloqueado** protege a assinatura «em cada operação»: gastar unidades apenas tendo o telefone nas mãos não se pode.
- **Contra a perda do telefone** — os guardiões e a migração (seção [Recuperação](03-operations.md#recuperação-do-acesso)). Sem guardiões os fundos se perdem.
- **Um ladrão que conheça o seu PIN pode cancelar a migração** dentro da janela de 14 dias — uma limitação conhecida da v1: o direito de cancelamento pertence à chave antiga. Atenuações — guardiões públicos e um novo início da migração.

## Lista de verificação de uma configuração segura

1. Defina o PIN e o PIN de coação na primeira execução.
2. Designe os guardiões (2 de 3 pessoais ou 3 de 5 públicos) — de imediato, na criação da carteira.
3. Preencha o cartão de recuperação ([seção «Recuperação»](03-operations.md#cartão-de-recuperação--preencha-com-antecedência)): o endereço da carteira, os endereços dos guardiões, o nome da rede — anote e guarde fora do telefone. Os dados de migração (o nonce, as assinaturas dos guardiões) não os transmita a ninguém nem os publique.
4. Não informe o seu PIN a ninguém; o de coação — com mais razão (ninguém deve saber da sua existência).
5. Lembre: adicionar uma digital nova no sistema invalida a chave — é proteção contra substituição, mas também o seu risco de perder o acesso.
6. Não guarde valores grandes «caso venha a precisar» — o demurrage nas redes com moeda pune justamente o armazenamento.

→ A seguir: [Perguntas e respostas, glossário](05-faq-glossary.md)
