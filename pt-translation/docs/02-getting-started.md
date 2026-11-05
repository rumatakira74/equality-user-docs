# 2. Primeiros passos

> **Estado: versão de teste.** O aplicativo está verificado em uma rede de teste fechada em emuladores. A compilação pública e a publicação nas lojas de aplicativos — depois dos pilotos. Todos os passos abaixo descrevem o caminho completo de integração.

## O que será necessário

- Um smartphone Android com armazenamento de chaves de hardware seguro (StrongBox / TEE) e uma digital configurada.
- Um dispositivo sem biometria configurada não é admitido ao registro: o aplicativo proporá configurar a biometria pela tela do sistema.
- Conhecidos na rede: para ativar a carteira são necessários **3 avais** de membros ativos (veja abaixo).

## Instalação

O aplicativo é distribuído como APK (a seção sobre distribuição via Google Play — em análise jurídica). Instale o arquivo APK da sua rede: cada instância de rede pode distribuir a própria compilação com os parâmetros embutidos. O aplicativo da rede está assinado com o nome da rede e o rótulo `Eq-<hash8>` — verifique o rótulo ao instalar para não instalar uma rede alheia. O aplicativo e a rede devem coincidir na **versão do protocolo** (a atual — 3): o número fica registrado em cada transação e em cada checkpoint; uma compilação de outra versão não é aceita pela rede.

A interface do aplicativo está disponível em cinco idiomas: russo, inglês, espanhol, português, chinês.

## Criação da carteira

1. O aplicativo cria o par de chaves **dentro do armazenamento seguro do telefone (Keystore)**. A chave privada não é exportável: não se pode copiá-la, extraí-la nem reenviá-la — nunca.
2. O telefone passa pela **atestação de hardware**: a rede verifica que é um dispositivo real com boot intacto e hardware protegido, e que a cadeia de atestação foi emitida justamente para a sua chave nova (a vinculação da chave ao certificado — cada nó da rede a verifica por si mesmo; não se pode substituir uma cadeia alheia). A imagem da digital não é enviada a lugar algum.
3. Executa-se uma tarefa computacional (proof-of-work) — proteção contra registro massivo automatizado. Leva segundos.
4. A carteira recebe o estado **registered** — ela já pode receber transferências, mas a emissão e o envio ainda não estão disponíveis.

Uma pessoa ≈ uma carteira: o registro repetido a partir do mesmo dispositivo está **dificultado** — ele exige um trabalho computacional (PoW) substancialmente mais caro, e não existe garantia de hardware estrita de «um dispositivo — uma carteira».

## Avais: o caminho para o estado ativo

Para o funcionamento pleno a carteira deve se tornar **active**. Para isso são necessários **K = 3 avais** (`vouch`) de membros ativos diferentes.

**Quem pode avalizar:**

- um membro com estado `active` e idade da carteira a partir de 3 meses;
- que tenha ranhuras de aval livres (são poucas: 3–5 conforme o tempo de carteira);
- o aval pode ser formalizado pessoalmente por meio de um código QR ou Bluetooth.

**O que significa o aval.** O avalista arrisca apenas a sua ranhura e a sua parte da recompensa; a perda de unidades não ameaça ele. Por um novato honesto o avalista recebe **10% das primeiras 12 emissões** do avalizado (pago da emissão do próprio novato, não do nada). Se se descobre que o novato violou as regras — o avalista perde a recompensa.

**Se você não tem conhecidos na rede:** use os canais públicos da comunidade, onde os novatos encontram avalistas. O avalista responde pela escolha com uma ranhura limitada — «distribuir» avais a qualquer um não lhe convém.

## Primeiro acesso e PIN

Na configuração você escolhe:

- **PIN** — o meio principal de confirmar operações perigosas;
- se quiser — o **PIN de coação** (veja [Segurança](04-security.md));
- o acesso ao aplicativo — pela digital ou pelo PIN.

Regras principais de segurança:

- **O acesso** ao aplicativo — digital ou PIN.
- **As operações perigosas** (transferência, emissão, início de migração) — **somente digitando o PIN explicitamente**. A digital nunca é usada para confirmá-las: o dedo pode ser posto à força, o PIN não.
- Se o PIN de coação estiver ativado, o acesso pela digital é desativado.

Adicionar uma digital nova no sistema **invalida a chave** (mais seguro, mas significa perder o acesso) — por isso designe guardiões imediatamente.

## Guardiões: designe-os de imediato

Designar os guardiões **na criação da carteira**, e não quando o telefone já estiver afogado:

- **guardiões pessoais** — 2 de 3 pessoas à sua escolha;
- ou **guardiões públicos** — membros verificados com tempo de carteira a partir de 12 meses; limite de 3 de 5 (podem ser combinados).

O guardião morreu, sumiu ou saiu da rede? Os guardiões podem ser **reeleitos mais tarde** — com o consentimento dos novos (janela de 48 horas, limite de 150 mudanças efetivas). Como — na seção [«Mudança de guardiões»](03-operations.md#mudança-de-guardiões). Não adiante a designação em si: sem guardiões a recuperação é impossível.

Com mais detalhes — na seção [Recuperação](03-operations.md#recuperação-do-acesso).

E de imediato preencha o **cartão de recuperação** (veja [Recuperação](03-operations.md#cartão-de-recuperação--preencha-com-antecedência)): o endereço da sua carteira, os endereços dos guardiões e o nome da rede — anote e guarde fora do telefone. Se perder o telefone, esses dados já não haverá de onde tirar. O aplicativo os mostra na tela «Cartão de recuperação» com um código QR.

## Estados da carteira

| Estado | Como se obtém | O que se pode |
|--------|---------------|---------------|
| `registered` | após o registro (atestação + PoW) | receber transferências |
| `active` | 3 avais | emissão, transferências, avais |
| `expired` | 3 anos em registered sem ativar | as transferências para o endereço se conservam; para emitir é preciso um registro novo |
| o rótulo `flagged` | violação provada (dupla assinatura) | emissão suspensa, não se pode avalizar outros |

→ A seguir: [Operações diárias](03-operations.md)
