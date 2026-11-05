# 5. Perguntas e respostas · Glossário

## FAQ

**Precisa de internet?**
Para as operações normais — sim, uma conexão ao menos periódica. O Bluetooth permite transmitir a transação assinada diretamente ao destinatário, mas o pagamento só se efetiva após a publicação e a confirmação pela rede.

**Não tenho conhecidos na rede. Como me ativar?**
Pelos canais públicos da comunidade: ali os novatos encontram avalistas. O avalista responde com uma ranhura limitada e com a recompensa; distribuir avais a qualquer um não lhe convém. O aval pode ser formalizado pessoalmente por meio de QR ou Bluetooth.

**Perdi o telefone. E as unidades?**
A chave não é exportável, mas funciona a recuperação social: os guardiões (pessoais 2 de 3 ou públicos 3 de 5) confirmam a migração para o telefone novo; após 14 dias a idade, o histórico, os avais e os fundos são transferidos. Sem guardiões designados — resta apenas um registro novo, e os fundos da carteira antiga se perdem.

**Posso trocar os guardiões?**
Sim. Se o guardião sumiu, morreu ou saiu da rede, reeleja-o: os novos guardiões assinam pessoalmente o hash da mudança, a mudança é publicada com digitação explícita do PIN e entra em vigor após 48 horas (até então ela pode ser cancelada). Limite — 150 mudanças efetivas durante a vida da carteira. Com mais detalhes — [«Mudança de guardiões»](03-operations.md#mudança-de-guardiões).

**Esqueci os dois PIN.**
A carteira fica inacessível: a chave não pode ser extraída e o PIN não pode ser «redefinido por e-mail» — esses canais não existem em um sistema sem servidores. O único caminho — a migração por meio dos guardiões.

**Alguém pode falsificar a minha carteira?**
A chave está no armazenamento seguro do telefone; só ela pode assinar uma operação. A falsificação é impossível sem acesso físico ao dispositivo desbloqueado.

**E se alguém criar centenas de carteiras (uma fazenda)?**
As barreiras: 3 avais por carteira (as ranhuras são limitadas), a atestação de hardware (emuladores e dispositivos com root não passam, a cadeia de atestação está vinculada à chave registrada), o desafio computacional na ranhura do período em curso, a moratória de transferências, a taxa e o demurrage. O modelo da economia de fazendas: com uma avaliação canônica de $120 por dispositivo, uma fazenda fica no positivo não antes de ~3,5 anos (com $200 — em ~4,5 anos) e somente com um alto valor externo da unidade; várias carteiras no mesmo dispositivo barateiam a fazenda — a estabilidade da conclusão foi verificada com uma grade de sensibilidade (custo do dispositivo × número de carteiras por dispositivo). O horizonte de verificação da métrica de segurança — não menos de 5 anos. A garantia «uma pessoa — uma carteira» ninguém dá: a proteção é econômica.

**Por que o saldo diminuiu sozinho?**
Nas redes com moeda funciona o demurrage — um pequeno percentual mensal acima do mínimo isento. Ele é refletido na próxima operação; não há uma transação de débito separada.

**A transferência «travou» por 48 horas. Isso é um ataque?**
Não, é uma transferência diferida: uma quantia acima do limite (por padrão 3000) sempre é executada após 48 horas, e ela pode ser cancelada antes da execução.

**Pode-se votar em segredo dentro da rede?**
Na v1 — não: o identificador para um aplicativo de terceiros está vinculado publicamente ao endereço. Votações secretas serão possíveis apenas em versões futuras.

**O aplicativo escreve «a unidade expirou». O que é isso?**
Você está em uma rede de assinatura (recurring): a cota está vinculada ao período e, após o limite do período seguinte, transferi-la já não se pode. Não é uma punição nem uma perda de saldo — a cota nova chega no período novo; o excedente é melhor entregar via peer-redeem a quem precisa do recurso.

**Quanto custa participar?**
A rede não cobra nada pela participação. A plataforma não tem custos de operação de forma alguma — os servidores não existem. A taxa da transferência é queimada, não fica para ninguém.

## Glossário

| Termo | Significado |
|-------|-------------|
| **Carteira** | A conta do membro: endereço + cadeia de entradas assinadas + saldo. Uma por dispositivo. |
| **Registro** | O registro público de todas as transações da rede; cada nó o guarda e o verifica. |
| **Genesis** | O pacote de lançamento da rede: parâmetros, manifesto, círculo semente. |
| **Versão do protocolo (`protocolVersion`)** | O número da versão das regras da rede (a atual — 3). Fica registrado em cada transação e em cada checkpoint; o aplicativo e a rede devem coincidir na versão do protocolo — uma compilação de outra versão não é aceita pela rede. |
| **Manifesto** | A descrição pública das regras da rede; o hash é fixado no genesis. |
| **Círculo semente** | Os primeiros membros do genesis com direitos especiais temporários; os direitos se autoliquidam (seed_sunset: 100 carteiras ativas ou 24 épocas). |
| **Aval (`vouch`)** | A assinatura de garantia de um membro ativo por um novato. Três avais ativam a carteira. |
| **Ranhura de aval** | O lugar limitado do avalista; é liberada após 3 períodos de emissão do avalizado ou 90 dias. |
| **Desafio de emissão** | A tarefa computacional (PoW) na ranhura do período em curso, calculável com antecedência; a janela de ±48 h está disponível em cada período, o seu estado é mostrado pela tela de emissão; a falta é compensada dentro da janela de acumulação (6 períodos). |
| **Época** | O intervalo do tempo de rede (por padrão 24 horas); nos limites das épocas são colocados checkpoints. |
| **Checkpoint** | A foto do estado da rede assinada por um limite de membros; dá finality e proteção aos nós light. |
| **Finality** | O momento a partir do qual é impossível reverter uma transação. |
| **Moratória** | O período após o registro (por padrão 14 dias) em que as transferências de saída não estão disponíveis. |
| **Demurrage** | O percentual mensal de custódia acima do mínimo; o que é debitado é queimado. |
| **Isca** | O modo aberto pelo PIN de coação: uma interface verossímil com um pequeno saldo, sem operações reais. |
| **Guardião** | O membro designado para confirmar a migração em caso de perda do telefone. |
| **Migração** | A transferência da carteira para um dispositivo novo por meio dos guardiões; atraso de 14 dias. |
| **Mudança de guardiões** | A reeleição dos guardiões pessoais (até 3) com o consentimento deles; janela de 48 h, limite de 150 mudanças efetivas durante a vida da carteira. |
| **Flagged** | A marca pública de uma violação provada (equivocação). |
| **Pagamento BT** | A transmissão da transação assinada por Bluetooth; torna-se pagamento somente após a confirmação pela rede. |
| **Perfil da rede** | O conjunto de parâmetros: a unidade, a emissão, a transferência, o dreno, a entrada etc. |
| **Eq-hash (`Eq-<hash8>`)** | O rótulo curto da rede (os primeiros 8 caracteres do seu identificador); fica visível no nome do aplicativo e na integração — por ele se verifica que está instalada a rede correta. |
| **Recurring (rede de assinatura)** | A rede de recurso de assinatura: uma cota igual por período, o não usado se extingue no limite do período. |
| **Peer-redeem** | A transferência membro → membro ou membro → fornecedor nas redes recurring: o excedente de cotas flui para quem precisa do recurso (na interface atual do aplicativo ainda não está implementado). |
| **Extinção da cota** | A unidade do período passado deixa de ser transferível após o limite do período seguinte; o saldo e o histórico se conservam. |

---

[← Sobre a plataforma](01-about.md) · [Sumário](../README.md)
