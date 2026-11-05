# 3. Operações diárias

## Emissão

Nas redes com emissão periódica, cada membro ativo recebe uma vez por período (por padrão — a cada mês) a sua **parte igual**: por exemplo, 1000 unidades no dia 1.

Particularidades:

- **O desafio de emissão.** Para declarar a emissão, o aplicativo resolve uma tarefa computacional na **sua ranhura do período em curso** (janela de ±48 horas). O momento da ranhura é calculado com antecedência a partir do endereço e do período, e é igual para todos os nós; a ranhura fica dentro do próprio período, por isso a janela **está disponível em cada período** (após a correção do mint — v9.14: antes a janela podia cair num tempo inalcançável, e a carteira, após seis períodos perdidos seguidos, perdia a emissão para sempre). O estado da janela é mostrado pela tela de emissão («aberta — pode emitir» / «fechada — quando abrirá»). O período perdido não se perde: o acúmulo é transferido dentro da **janela de acumulação — 6 períodos**, os fundos não são bloqueados; uma falta consciente além da janela — a emissão se extingue.
- A primeira emissão é possível apenas no período **posterior** à ativação, sem acúmulos retroativos.
- Os fundos recém-emitidos não são transferíveis de imediato (moratória — veja abaixo).

## Transferências

- **A taxa é queimada.** Cada transferência paga uma pequena taxa (`fee`) que é destruída — o destinatário recebe exatamente o valor indicado. A taxa protege a rede contra spam e freia levemente o movimento de valor.
- **A tarifa é adaptativa.** O percentual da taxa é recalculado pela rede no limite de cada época, de forma igual para todos os nós: se a oferta de unidades cresce mais rápido do que o ritmo alvo — a tarifa sobe; caso contrário, desce. Faixa — de 0,5% a 2%, mínimo 0,01 unidade; ninguém pode fixar a tarifa manualmente.
- **Moratória para carteiras recentes:** as transferências estão disponíveis 14 dias após o registro (parâmetro da rede; 14 dias — o valor por padrão). Isso corta o esquema «registrou — esvaziou».
- **O tempo da transação é o momento da assinatura.** As regras da rede (moratória, extinção de cotas, prazos das transferências diferidas, janela de emissão) se aplicam ao momento da assinatura da transação, não ao da sua publicação: uma transferência assinada offline e publicada depois é avaliada da mesma forma por todos os nós. O relógio do telefone não deve divergir da rede mais de ±30 minutos — transações com divergência maior não são aceitas pela rede (repita a publicação após sincronizar a hora).
- **Transferências grandes diferidas.** Uma transferência acima do limite (por padrão **P = 3000 unidades**) é executada somente após **48 horas**. Durante o atraso você pode cancelá-la direto do aplicativo — por exemplo, sob coação ou se mudar de ideia. A regra vale em todas as redes com unidades transferíveis e não pode ser desativada. O limite pode ser alterado dentro do máximo (30000); o aumento entra em vigor após 48 horas, a redução — imediatamente.

### Redes de assinatura (recurring): cotas por período

Nas redes de recurso de assinatura (cenário 8) as unidades são **cotas por período**: cada membro ativo recebe uma cota igual, e a parte não usada **se extingue no limite do período seguinte** — assim a assinatura não se transforma em acúmulo. Transferir ou resgatar uma unidade do período passado após esse limite não se pode: o aplicativo mostrará um erro claro «a unidade expirou». Ninguém «zera» o saldo: o histórico fica visível para todos; simplesmente as cotas antigas já não são transferíveis.

O excedente pode ser transferido a quem não tem cotas suficientes: transferências **membro → membro** e **membro → fornecedor** (modo peer-redeem; a confirmação — um recibo assinado). Nota: o modo é suportado pelo núcleo e pela especificação, mas na interface atual do aplicativo ainda não está implementado.

### Pagamento por Bluetooth

O Bluetooth é usado **somente** para transmitir diretamente a transação assinada ao destinatário, quando não há internet. O destinatário publica a transação na rede quando a conexão aparecer.

**Importante:** enquanto a transação não estiver publicada e confirmada pela rede, ela **não é um pagamento**. O remetente pode entregar a mesma quantia a dois destinatários. Por isso, na interface o estado é «recebido por Bluetooth — aguardando publicação», e o destinatário é obrigado a esperar a confirmação da rede.

## Demurrage (em redes com moeda)

Nos perfis com valor transferível (moeda interna, cofre de ajuda mútua) pode funcionar o **demurrage** — um pequeno «imposto de custódia» mensal acima do mínimo isento. O débito não é feito como transação separada: o saldo efetivo é recalculado de forma determinística na próxima operação.

O sentido: o valor está no fluxo, não no acúmulo. O demurrage e a taxa queimada são parte da proteção contra fazendas, não um modo de tirar unidades de alguém: o demurrage pode ser «contornado» simplesmente não acumulando.

## Avais

- O avalista responde por um membro novo, gastando uma das suas **ranhuras** (3 com tempo de carteira de 3–12 meses, 5 — além disso).
- A ranhura é liberada quando o avalizado completa 3 períodos de emissão sem violações, ou após 90 dias se ele nunca se ativou.
- A recompensa aos avalistas — **10% das primeiras 12 emissões** do avalizado, automaticamente e em partes iguais entre os três.
- Se contra o avalizado é provada uma violação, a recompensa cessa; fundos não são tomados do avalista.

## Violações e a marca flagged

A única violação demonstrável é a **equivocação**: duas transações em conflito assinadas pela mesma carteira (gasto duplo, emissão dupla). A prova é publicada por qualquer nó e verificada por todos da mesma forma. Consequências: marca pública `flagged`, suspensão da emissão por 3 meses (em caso de repetição — para sempre), proibição de avalizar. «Parece uma fazenda» não é uma prova — não há veredictos por suspeita.

## Recuperação do acesso

A chave não é exportável, por isso, em caso de perda do telefone, funciona a **recuperação social** (transação `migrate`):

1. O telefone novo passa pela mesma verificação que no registro.
2. Os guardiões confirmam a migração: **pessoais 2 de 3** ou **públicos 3 de 5** (podem ser combinados).
3. **Atraso de 14 dias**, durante o qual a chave antiga (se estiver viva) pode cancelar a migração.
4. A idade, o histórico, os avais, as emissões **e os fundos (o saldo)** são transferidos para a carteira nova; a digital do telefone antigo vai para a lista negra para sempre.

### Cartão de recuperação — preencha com antecedência

Para iniciar a migração, no telefone novo será preciso digitar **o endereço antigo da carteira** e, depois, o nonce e as assinaturas dos guardiões. Esses dados não se «recuperam do nada»: no telefone perdido eles não ficaram salvos.

**Com antecedência, enquanto o telefone funciona:**

- anote **o endereço da sua carteira** (hex, mostrado no aplicativo) e guarde-o fora do telefone (não na nuvem) — no papel ou como um código QR impresso;
- anote **os endereços dos seus guardiões** e o meio de contatá-los;
- anote **o nome da rede** (no aplicativo ele é mostrado com o rótulo `Eq-<hash8>`) e onde obter o seu APK (cada rede distribui a própria compilação).

O aplicativo mostra todos esses dados na tela **«Cartão de recuperação»** na criação da carteira (e mais tarde — nos ajustes e na tela de migração) com um código QR: exporte-os ou imprima-os.

**Durante a migração:**

- o nonce e as assinaturas dos guardiões são as chaves da recuperação da sua carteira: **não os transmita a ninguém nem os publique**;
- transmita-os **somente diretamente** entre você e o seu guardião — pessoalmente ou por um canal seguro, não por terceiros;
- digite-os apenas no seu próprio aplicativo; após concluir a migração, apague-os das conversas.

Um guardião público (um membro com tempo de carteira ≥ 12 meses) recebe pela migração bem-sucedida do seu tutelado uma recompensa fixa da emissão — não mais de uma vez a cada 12 meses por tutelado.

**Se os guardiões não forem designados**, resta o reinício: um registro novo com uma chave nova e três avais novos. Os fundos da carteira antiga, nesse caso, se perdem — designe guardiões com antecedência.

### Mudança de guardiões

O guardião morreu, sumiu ou saiu da rede — os guardiões podem ser **reeleitos** (transação `update_guardians`):

1. **Consentimento dos novos guardiões.** Cada novo guardião (até 3) assina pessoalmente o hash da mudança — assim como ao confirmar a migração: sem a assinatura dele a mudança é impossível.
2. **Publicação da mudança.** Ajustes → Guardiões → «Reeleger»; a publicação e o cancelamento — somente após digitar o PIN explicitamente.
3. **Janela de 48 horas.** A mudança entra em vigor 48 horas após a publicação; até então ela pode ser cancelada (também somente com PIN).
4. **Limite — 150 mudanças.** Não mais de 150 mudanças efetivas durante a vida da carteira; as canceladas e expiradas não contam. O contador de mudanças restantes fica visível no aplicativo.

Não há taxa pela mudança; cada mudança é publicada no histórico da rede. Os novos guardiões devem estar ativos (`active`) e sem a marca `flagged`. No modo isca, a «mudança de guardiões» é «executada» de modo verossímil, mas a lista real de guardiões não é tocada.

→ A seguir: [Segurança do proprietário](04-security.md)
