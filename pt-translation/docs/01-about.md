# 1. Sobre a plataforma

## O que é

Equality Project é uma plataforma na qual uma comunidade (uma escola, uma cooperativa, um grupo de voluntários, uma diáspora, um fundo, o organizador de um evento) lança **a sua própria rede isolada** nos telefones dos membros:

- **sem servidores** — a rede vive nos próprios telefones;
- **sem administrador** — não há ninguém que possa «desligar» a rede ou mudar as suas regras;
- **sem custos de operação** — não é preciso pagar por hospedagem nem manutenção.

Cada rede dá aos membros três coisas:

1. **Uma pessoa ≈ uma carteira.** A entrada é somente por avais de membros ativos, mais a verificação de hardware do telefone. É a barreira principal contra contas falsas.
2. **Direito periódico e igual.** A «unidade» da rede (horas, cota, pontos) é emitida para todos os membros ativos **em partes iguais**, segundo um calendário.
3. **Histórico público e verificável.** A reputação do membro — a idade da carteira, quem avalizou quem, a contribuição — é visível para todos os membros da rede.

O que se considera «unidade» e o que se pode fazer com ela define o **perfil da rede**: uma moeda interna, um banco de tempo, cotas sobre um recurso comum, o registro do aporte voluntário etc.

A rede é montada a partir de um **modelo pronto** para um dos oito cenários: o organizador escolhe o modelo, define os parâmetros — e obtém a sua rede com o seu próprio aplicativo (APK).

## Isto não é criptomoeda

- A plataforma **não emite nem vende tokens**, não cria um mercado de troca e não recompensa a mineração no sentido habitual.
- As unidades existem apenas dentro de uma rede concreta e, em alguns perfis, nem sequer são transferidas.
- O valor está no uso (veja os cenários abaixo), não na cotação da unidade.
- As palavras «carteira», «emissão», «checkpoint» — são o vocabulário técnico do registro de entradas assinadas, não o sinal de um instrumento financeiro.

## Oito cenários de uso

| N.º | Cenário | Unidade |
|-----|---------|---------|
| 1 | Educação e laboratório de instituições (incluindo simulações) | pontos ou moeda de jogo |
| 2 | Prova de humanidade como serviço para outros aplicativos | «pulso» de atividade não transferível |
| 3 | Cotas iguais sobre um recurso comum (água, internet, depósito) | cota por período, não se acumula |
| 4 | Programas voluntários e de rua (alimentação, ajuda) | vales do programa |
| 5 | Moeda interna ou banco de tempo da comunidade | horas ou moeda, emissão igual |
| 6 | Registro do aporte voluntário | pontos por aporte verificado |
| 7 | Cofre de ajuda mútua | moeda, demurrage contra o acúmulo |
| 8 | Recurso de assinatura — assinatura de um recurso recorrente (comercial) | cota por período, o não usado se extingue |

## As redes são isoladas, e essa é a propriedade principal

- Não uma única rede grande, mas **muitas redes separadas**. Cada uma tem a sua composição, as suas regras (perfil), as suas unidades.
- Entre as redes não há troca. O saldo de uma rede não significa nada em outra.
- As regras da rede ficam escritas no **manifesto** na criação e, por padrão, são imutáveis; o hash do manifesto é fixado no genesis. Se as regras deixam de servir à comunidade — lança-se uma rede nova (é grátis) e os membros migram voluntariamente.
- O nível de garantias da rede **é calculado a partir do manifesto**, não é declarado: os parceiros veem de qual rede e com quais garantias chega a «pessoa».
- Cada rede é montada com o **seu próprio aplicativo**: o rótulo `Eq-<hash8>` (hash curto do identificador da rede) no nome do aplicativo mostra que está instalada justamente a sua rede; no aplicativo a rede está assinada com o nome e o rótulo — por exemplo, «cirrus · Eq-e5796f9c».
- Nas redes de assinatura (cenário 8) as cotas não se acumulam: a parte não usada se extingue no limite do período, e o excedente pode ser transferido a quem precisa do recurso (mais detalhes em [Operações diárias](03-operations.md)).

## Papéis do membro

Cada papel é uma carteira normal; ninguém tem «permissões» especiais:

- **Membro** — uma carteira registrada; após a ativação recebe a emissão e transfere unidades.
- **Avalista** — um membro ativo com tempo de carteira de 3 meses ou mais, que responde por uma pessoa nova com uma das suas ranhuras de aval limitadas.
- **Guardião** — uma pessoa designada com antecedência para recuperar o acesso em caso de perda do telefone (guardiões pessoais — 2 de 3; ou públicos — 3 de 5).
- **Fornecedor / destinatário do fundo comum** — uma carteira indicada nos parâmetros da rede (por exemplo, um ponto parceiro que aceita os vales). Ele não pode administrar a rede.

## Com honestidade sobre os limites

- **Sem smartphone adequado não há participação.** O protocolo exige um telefone Android com armazenamento de chaves de hardware seguro. Não há esquemas alternativos (curadores, recibos de papel).
- **O anonimato não é o objetivo.** O registro da rede é público dentro da rede: os membros veem os endereços, os estados e o histórico uns dos outros; o saldo é dedutível do estado público da rede.
- **A proteção contra fazendas é econômica, não absoluta.** Criar uma carteira extra deve custar mais do que ela rende; uma garantia plena de «uma pessoa — uma carteira» sem uma âncora externa é tecnicamente impossível.

→ A seguir: [
Primeiros passos](02-getting-started.md)
