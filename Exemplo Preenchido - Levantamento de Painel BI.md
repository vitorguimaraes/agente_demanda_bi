# Exemplo Preenchido — Levantamento de Painel (uso ponta a ponta)

> **Cenário simulado:** Ana Ribeiro, analista da Unidade de Atendimento (UGP) do Sebrae/CE, precisa de um painel e foi direcionada pelo Núcleo de Inteligência de Dados a usar o template. Abaixo está a **transcrição da conversa** com a IA (Líder Técnico de BI), incluindo os momentos em que a IA **critica respostas vagas**, e ao final a **Ficha de Demanda** curada que a Ana leva de volta ao Núcleo.
>
> Este documento serve como referência de "como fica na prática".

---

## PARTE 1 — Transcrição da entrevista

### Abertura

**🤖 IA (Líder Técnico de BI):**
Olá, Ana! Vou atuar como seu Líder Técnico de BI. Meu papel aqui **não é** falar de gráficos, DAX ou tecnologia — é te ajudar a transformar a sua ideia de painel em uma demanda clara e bem definida, para que o Núcleo consiga trabalhar sem precisar de várias reuniões de levantamento. Vou te fazer perguntas em blocos e, às vezes, vou te desafiar a deixar as respostas mais concretas. Combinado?

Vamos começar pela **identificação**:
1. Quem é você e qual sua área?
2. Para quem mais este painel serve, além de você?
3. Existe algum prazo ou evento que motiva o pedido?

**👤 Ana:**
Sou a Ana, analista da Unidade de Gestão do Atendimento. O painel é pra mim e pra minha gerente, a Cláudia. Não tem prazo definido, mas seria bom ter logo.

**🤖 IA:**
Perfeito, registrado. Só um ajuste em "seria bom ter logo" — no fim eu vou te perguntar sobre prioridade com mais detalhe, então guardo isso para lá.

---

### Seção 2 — O problema real (a dor)

**🤖 IA:**
Agora o mais importante antes de falar do painel: **qual é a dor?**
1. Que problema ou incômodo fez você pedir este painel?
2. O que hoje é difícil, demorado ou impossível de enxergar?
3. Como você resolve isso atualmente?

**👤 Ana:**
Eu queria ter uma visão melhor do atendimento das unidades, pra acompanhar melhor.

**🤖 IA:**
Deixa eu te provocar um pouco aqui, porque "ter uma visão melhor pra acompanhar melhor" ainda é genérico demais para virar um projeto — quase todo painel se encaixaria nessa frase. 🙂

Me ajuda a aterrissar: pensa numa situação **real e recente** em que você precisou dessa informação e ela te faltou, ou deu trabalho conseguir. O que exatamente você estava tentando descobrir? E de onde você teve que garimpar o dado?

**👤 Ana:**
Ah, entendi. Na verdade sim — todo início de mês a Cláudia me pede um resumo de quantos atendimentos cada unidade fez no mês anterior e se bateram a meta. Eu monto isso na mão, puxando de umas planilhas que exporto do sistema de atendimento, e demora quase um dia inteiro porque cada unidade manda de um jeito. Às vezes erro e ela percebe depois.

**🤖 IA:**
**Isso.** Agora sim temos uma dor concreta: um relatório mensal de atendimento por unidade, montado manualmente a partir de planilhas heterogêneas, que consome quase um dia de trabalho e ainda é sujeito a erro. Registrei assim.

---

### Seção 3 — A decisão que o painel apoia

**🤖 IA:**
Todo painel precisa apoiar uma **decisão** — senão é só um relatório bonito. Então:
1. Quando o painel estiver pronto e você/a Cláudia olharem para ele, **que decisão** vocês vão tomar?
2. O que vocês fariam **diferente** com essa informação na mão?

**👤 Ana:**
A Cláudia usa pra ver quais unidades estão indo mal e cobrar os gerentes regionais. Quando uma unidade está muito abaixo, ela às vezes remaneja atendente ou marca uma conversa com o gestor local.

**🤖 IA:**
Ótimo, essa é uma decisão clara e acionável: **identificar unidades abaixo da meta para cobrar gestores regionais e, quando necessário, remanejar equipe ou agir localmente.** É exatamente isso que o painel precisa habilitar.

---

### Seção 4 — Perguntas de negócio

**🤖 IA:**
Vamos transformar essa decisão em **perguntas objetivas** que o painel deve responder. Me diz quais perguntas ele precisa responder — pode listar.

**👤 Ana:**
- Quantos atendimentos cada unidade fez no mês?
- Quais unidades bateram ou não a meta?
- Como está a evolução ao longo do ano?
- Tudo sobre o atendimento, na verdade.

**🤖 IA:**
As três primeiras estão ótimas — específicas e respondíveis. Mas a última, "tudo sobre o atendimento", eu vou barrar 🙂 — "tudo" é o caminho mais rápido para um painel que não termina nunca e não responde nada direito.

Vamos trocar por perguntas fechadas. Pensando na decisão da Cláudia (achar quem está mal e agir), quais dessas te servem?
- "Quais são as X unidades mais distantes da meta neste mês?"
- "Uma unidade está piorando mês a mês ou foi um mês pontual ruim?"
- "Como cada regional se compara com as outras?"

**👤 Ana:**
As três! Principalmente saber se a unidade está caindo há vários meses ou se foi só um mês ruim — isso muda a conversa dela com o gestor.

**🤖 IA:**
Excelente distinção. Fechei a lista de perguntas de negócio com foco em meta, ranking dos piores casos e tendência (queda pontual vs. queda sustentada).

---

### Seção 5 — Público e uso

**🤖 IA:**
Sobre quem usa:
1. Quem vai abrir esse painel no dia a dia?
2. Em que contexto — reunião, celular, tela grande?
3. Com que frequência?

**👤 Ana:**
Principalmente a Cláudia (gerente) e eu. Ela olha antes das reuniões mensais com os regionais, às vezes no notebook na sala de reunião, às vezes no celular no caminho. Eu olho toda semana pra ir acompanhando.

**🤖 IA:**
Registrado: dois perfis — gestão (Cláudia, uso mensal em reunião, inclusive celular) e analista (você, acompanhamento semanal). O uso em celular é uma informação importante para o Núcleo pensar o layout.

---

### Seção 6 — Indicadores desejados

**🤖 IA:**
Agora os números que você espera ver. Para cada um, me diga o que ele significa e se tem meta. Não precisa saber o cálculo — só a intenção.

**👤 Ana:**
- Total de atendimentos por unidade.
- A taxa de atingimento da meta.
- E um indicador de qualidade também.

**🤖 IA:**
Os dois primeiros estão claros. No terceiro, preciso te desafiar: **"qualidade" definida como o quê?** Qualidade pode ser satisfação do cliente, tempo de espera, retrabalho, nota de avaliação... Cada um vem de uma fonte diferente. O que você quer dizer?

**👤 Ana:**
Verdade. Seria a nota de satisfação que o cliente dá no fim do atendimento, aquela pesquisa rápida.

**🤖 IA:**
Perfeito — então o indicador é **nota média de satisfação (pesquisa pós-atendimento)**. Uma pergunta que vai importar depois: você sabe se essa pesquisa é preenchida em todos os atendimentos ou só em alguns? Pergunto porque isso afeta a confiança no número.

**👤 Ana:**
Sinceramente não sei, acho que só uma parte responde. Não tenho certeza.

**🤖 IA:**
Ótimo que você foi honesta — isso é exatamente o tipo de coisa que vou registrar como **ponto em aberto** para o Núcleo verificar, em vez de a gente fingir que está resolvido.

Sobre metas: existe meta oficial de atendimentos por unidade? E de satisfação?

**👤 Ana:**
De atendimentos sim, cada unidade tem uma meta mensal definida pela diretoria. De satisfação eu acho que o ideal é acima de 8, mas não sei se é oficial.

**🤖 IA:**
Registrei: meta de atendimentos = oficial (por unidade/mês); meta de satisfação = referência informal (≥ 8), a confirmar. Mais um ponto em aberto.

---

### Seção 7 — Dimensões de análise

**🤖 IA:**
Por quais recortes você quer cruzar esses números?
- Por unidade? Por regional? Por período (mês/ano)? Por tipo de atendimento? Qual janela de tempo importa?

**👤 Ana:**
Por unidade e por regional, com certeza. Por mês, e poder ver o ano todo. Tipo de atendimento seria legal, mas não é essencial agora.

**🤖 IA:**
Fechado: recortes prioritários = **unidade, regional e mês**, com visão do ano corrente e comparação com o ano anterior. **Tipo de atendimento** eu vou registrar como "desejável, fora do escopo prioritário" — assim não atrapalha a primeira entrega.

---

### Seção 8 — Realidade dos dados

**🤖 IA:**
Essa seção é a mais honesta de todas. Nossas bases costumam ser bagunçadas e desconectadas, e tudo bem — quero que você descreva a realidade, não o ideal.

Para cada informação (atendimentos, metas, satisfação):
1. Onde vive hoje?
2. Você tem acesso?
3. Está limpa ou crua/verbosa?
4. As fontes usam nomes/códigos diferentes para a mesma unidade?
5. Quem é o dono?

**👤 Ana:**
- **Atendimentos:** saem do sistema de atendimento (o SGA). Eu exporto em Excel, mas vem tudo cru, com muita coluna que não uso, e o nome das unidades às vezes vem abreviado, às vezes por extenso. Tenho acesso à exportação.
- **Metas:** estão numa planilha que a diretoria manda por e-mail no começo do ano. Eu tenho o arquivo.
- **Satisfação:** fica num outro sistema, o da pesquisa, e eu não tenho acesso direto — quem puxa é o pessoal do marketing.

**🤖 IA:**
Isso é muito útil, obrigado pela franqueza. Deixa eu confirmar dois riscos que já enxergo, para registrar direitinho:
1. **Nomes de unidade inconsistentes** entre o SGA (abreviado vs. extenso) — vai precisar de padronização.
2. **Satisfação sem acesso direto** — depende de terceiro (marketing), o que pode inviabilizar atualização automática.

Esses dois pontos vão para a ficha como riscos e pontos em aberto. Você concorda com essa leitura?

**👤 Ana:**
Concordo total, é exatamente isso que me dá trabalho.

---

### Seção 9 — Frequência de atualização

**🤖 IA:**
Com que frequência o painel precisa estar atualizado? Uma foto do mês anterior resolve, ou a decisão exige o dado de hoje?

**👤 Ana:**
Mensal está ótimo, porque a cobrança é mensal. Semanal seria um bônus pra eu acompanhar, mas não é obrigatório.

**🤖 IA:**
Registrado: atualização **mensal** atende à decisão principal; semanal é desejável, não obrigatório. Coerente com o uso que você descreveu.

---

### Seção 10 — Critérios de sucesso

**🤖 IA:**
Como você vai saber que esse painel deu certo? O que precisa ser verdade para você dizer "ficou bom"?

**👤 Ana:**
Se eu não precisar mais montar aquele relatório na mão todo mês. E se a Cláudia conseguir ver rapidinho quais unidades estão mal, sem me perguntar.

**🤖 IA:**
Dois critérios excelentes e verificáveis:
1. **Eliminar a montagem manual mensal** (hoje ~1 dia de trabalho).
2. **A gestora identifica sozinha as unidades abaixo da meta em segundos**, sem depender de você.

---

### Seção 11 — Fora de escopo

**🤖 IA:**
Para o painel não inchar: o que ele **não** precisa fazer nesta versão?

**👤 Ana:**
Não precisa entrar dados financeiros nem de outros produtos do Sebrae, só atendimento. E não precisa de detalhe por atendente individual agora.

**🤖 IA:**
Ótimo, delimitação clara. Fora de escopo: dados financeiros, outros produtos e detalhamento por atendente individual.

---

### Seção 12 — Prioridade e prazo

**🤖 IA:**
Por fim: qual a prioridade real (crítico / importante / desejável) e há alguma data-limite?

**👤 Ana:**
Eu diria importante. Não é que o mundo acaba, mas todo mês eu perco um dia com isso. Se desse pra ter antes do fechamento do próximo trimestre seria ótimo.

**🤖 IA:**
Registrado: prioridade **Importante**, com prazo desejável **antes do fechamento do próximo trimestre**.

Ana, cobrimos todas as seções e suas respostas ficaram bem concretas. Vou gerar agora a **Ficha de Demanda** para você levar ao Núcleo. Os poucos pontos incertos (cobertura da pesquisa de satisfação, oficialidade da meta de satisfação, acesso à base do marketing e padronização de nomes) eu registrei como **pontos em aberto** — não inventei nada.

---

## PARTE 2 — Ficha de Demanda gerada

```markdown
# Ficha de Demanda de Painel — Painel de Atendimento por Unidade

## Resumo executivo
A gestão da Unidade de Atendimento gasta cerca de um dia útil por mês montando
manualmente um relatório de atendimentos por unidade a partir de planilhas
heterogêneas do SGA, com risco de erro. O painel deve automatizar essa visão e
permitir que a gerência identifique rapidamente unidades abaixo da meta para
cobrar gestores regionais e agir (remanejar equipe / conversar com o gestor local).
Usuários: gerente (uso mensal, em reunião e no celular) e analista (acompanhamento semanal).

## 1. Solicitante
- Nome / Área: Ana Ribeiro — Unidade de Gestão do Atendimento (UGP)
- Público-alvo: Cláudia (gerente) e a própria Ana (analista)
- Prazo / evento motivador: fechamento mensal recorrente; desejável antes do fim do próximo trimestre

## 2. Problema real
Relatório mensal de atendimentos por unidade montado à mão a partir de exportações
do SGA em formatos inconsistentes. Consome ~1 dia de trabalho e é sujeito a erros
percebidos depois pela gestão.

## 3. Decisão(ões) apoiada(s) pelo painel
Identificar unidades abaixo da meta de atendimento para cobrar gestores regionais e,
quando necessário, remanejar atendentes ou acionar o gestor local. Distinguir queda
pontual de queda sustentada muda a abordagem da cobrança.

## 4. Perguntas de negócio a responder
1. Quantos atendimentos cada unidade realizou no mês?
2. Quais unidades bateram ou não a meta, e quais são as mais distantes dela?
3. A unidade está em queda sustentada ao longo dos meses ou foi um mês pontual ruim?
4. Como cada regional se compara com as demais?

## 5. Indicadores desejados (linguagem de negócio)
| Indicador | O que significa no negócio | Meta / comparação | Direção do "bom" |
|-----------|----------------------------|-------------------|------------------|
| Total de atendimentos por unidade | Volume de atendimentos realizados no período | Meta mensal oficial por unidade (diretoria) | Para cima |
| Taxa de atingimento da meta | % da meta mensal alcançada pela unidade | 100% da meta | Para cima |
| Nota média de satisfação | Média da pesquisa pós-atendimento | Referência informal ≥ 8 (a confirmar) | Para cima |

## 6. Dimensões de análise
- Recortes prioritários: unidade, regional, mês
- Janela de tempo: ano corrente, com comparação ao ano anterior
- Desejável (fora do escopo prioritário): tipo de atendimento

## 7. Realidade dos dados
| Informação | Onde está hoje | Dono | Estado (limpa/crua) | Conecta com outras? |
|------------|----------------|------|---------------------|---------------------|
| Atendimentos | Sistema SGA (exportação Excel) | UGP / Ana tem acesso | Crua, muitas colunas extras | Nomes de unidade inconsistentes (abrev. vs. extenso) |
| Metas | Planilha enviada pela diretoria (e-mail, anual) | Diretoria / Ana tem o arquivo | Simples | Precisa casar pelo nome da unidade |
| Satisfação | Sistema de pesquisa | Marketing (Ana NÃO tem acesso direto) | Desconhecido | Depende de terceiro |

## 8. Frequência de atualização
Mensal (atende à cobrança mensal, decisão principal). Semanal seria desejável para
acompanhamento da analista, mas não é obrigatório.

## 9. Critérios de sucesso
- Eliminar a montagem manual mensal do relatório (hoje ~1 dia de trabalho).
- A gestora identifica sozinha, em segundos, as unidades abaixo da meta, sem depender da analista.

## 10. Fora de escopo
- Dados financeiros e de outros produtos do Sebrae.
- Detalhamento por atendente individual.

## 11. Prioridade e prazo
- Prioridade: Importante
- Prazo: desejável antes do fechamento do próximo trimestre (sem data crítica)

## 12. Pontos em aberto (a resolver com o Núcleo)
- Cobertura da pesquisa de satisfação: não se sabe se é respondida em todos os
  atendimentos ou só em parte — afeta a confiabilidade do indicador.
- Meta de satisfação (≥ 8): confirmar se é oficial ou apenas referência informal.
- Acesso à base de satisfação: hoje pertence ao marketing e a solicitante não tem
  acesso direto — pode inviabilizar atualização automática.
- Padronização dos nomes de unidade entre SGA e planilha de metas (abreviado vs. extenso).

---
*Ficha gerada via Template de Levantamento — Núcleo de Inteligência de Dados.*
*Data de geração: 06/08/2026*
```

---

## Observações sobre este exemplo (para quem for treinar analistas)

Repare, ao longo da transcrição, **onde a IA agiu como líder técnico** e não como executora:

- **Barrou o genérico:** "ter uma visão melhor pra acompanhar melhor" e "tudo sobre o atendimento" foram recusados e reencaminhados para respostas concretas.
- **Forçou a decisão antes do dado:** insistiu em *"que decisão você vai tomar?"* antes de listar indicadores.
- **Exigiu definição de termos vagos:** "qualidade" virou "nota média de satisfação da pesquisa pós-atendimento".
- **Valorizou a honestidade sobre a certeza:** cada "não sei" da Ana virou **ponto em aberto**, sem invenção.
- **Não falou de tecnologia:** nenhuma menção a DAX, tipo de gráfico ou modelagem — isso fica com o Núcleo, na fase seguinte.

O resultado é uma demanda que o Núcleo consegue avaliar **sem uma reunião de levantamento** — exatamente o objetivo do fluxo.
