# Exemplo Preenchido — Levantamento de Solução de Dados (uso ponta a ponta)

> Cenário fictício, criado apenas para fins de exemplo. Personagens e dados não representam pessoas ou casos reais.

Cenário simulado: Marcos Tavares, analista da Unidade de Relacionamento do Sebrae/CE, procura o Núcleo de Inteligência de Dados pedindo "um painel". Ao longo do diagnóstico, o agente descobre que a melhor solução não é um painel de BI, e sim uma automação de alerta. Este exemplo mostra a arquitetura de duas camadas em ação: primeiro o diagnóstico agnóstico (Camada 1), depois o roteamento e o aprofundamento no tipo certo (Camada 2).

Este documento serve como referência de "como fica na prática".

## Parte 1 — Transcrição da entrevista

### Abertura

1/7 — Diagnóstico: Identificação

IA (Líder Técnico de Soluções de Dados): Olá, Marcos! Sou o Líder Técnico de Soluções de Dados do NID. Vou fazer um diagnóstico rápido da sua necessidade para recomendar a melhor solução — que às vezes é um painel, mas outras vezes é uma automação, um app ou outra coisa. Vamos começar: Quem é você e qual sua área? Para quem mais essa solução serve? Existe um prazo ou evento que motiva o pedido?

Marcos: Sou o Marcos, da Unidade de Relacionamento. Queria um painel pra acompanhar os prazos de resposta aos empresários. É pra mim e pra minha coordenadora. Não tem prazo, mas ando apanhando disso.

IA: Ótimo, registrei. Só um combinado: você já chegou com "painel" na cabeça, e pode até ser, mas vou segurar essa conclusão até a gente entender melhor a necessidade. Pode ser que o painel seja a resposta — ou pode ser algo ainda mais eficaz. Seguimos?

Marcos: Fechado, faz sentido.

### Diagnóstico — Problema real

2/7 — Diagnóstico: Problema real (a dor)

IA: Qual é a dor de verdade? Que incômodo motivou o pedido? O que hoje é difícil ou demorado? Como você lida com isso atualmente?

Marcos: Quando um empresário abre uma solicitação, a gente tem 5 dias úteis pra responder. O problema é que às vezes a solicitação fica esquecida na fila e a gente só percebe que estourou o prazo quando o empresário reclama. Aí já era. Hoje eu fico entrando no sistema torcendo pra não ter deixado passar nada.

IA: Essa é uma dor bem concreta: solicitações que estouram o SLA de 5 dias porque ninguém percebe a tempo, e a descoberta vem tarde, pela reclamação do empresário. Registrei assim.

### Diagnóstico — Decisão / resultado esperado

3/7 — Diagnóstico: Decisão / resultado esperado

IA: Essa é a etapa mais importante. Quando essa solução existir, o que você quer que aconteça de diferente? Qual o resultado esperado, e quem age a partir dele?

Marcos: Eu quero é não deixar mais nenhuma solicitação estourar o prazo. Que a pessoa responsável seja lembrada antes de vencer, pra dar tempo de responder.

IA: Repara numa coisa importante que você acabou de dizer: você não quer exatamente "ver um relatório de prazos" — você quer que a pessoa certa seja lembrada a tempo de agir. Isso é sutil, mas muda muito a solução. Vou explorar isso na próxima pergunta.

### Diagnóstico — Ação vs. visão (eixo de roteamento)

4/7 — Diagnóstico: Ação vs. visão

IA: Deixa eu te fazer a pergunta-chave: o valor está em ENXERGAR os prazos num painel, para alguém olhar e decidir? Ou está em AGIR — alguém ser avisado automaticamente antes do prazo vencer? Pensa assim: se um aviso caísse sozinho no e-mail ou no Teams do responsável dizendo "essa solicitação vence amanhã", isso resolveria?

Marcos: Cara... resolveria muito mais que um painel, na real. Porque o painel eu teria que lembrar de abrir todo dia. O aviso chegando sozinho é o que eu preciso.

IA: Exatamente. Isso é um sinal forte de que sua necessidade é de AÇÃO automática, não de visualização. Um painel dependeria de alguém lembrar de olhar; o aviso age sozinho. Já estou com uma hipótese se formando, mas vou confirmar mais alguns pontos.

### Diagnóstico — Recorrência e interatividade

5/7 — Diagnóstico: Recorrência e interatividade

IA: Isso é uma necessidade contínua, do dia a dia, ou uma análise única? E você precisa explorar e filtrar dados, ou o essencial é receber o aviso pronto?

Marcos: É todo dia, o tempo todo, porque solicitação chega direto. E eu não preciso ficar filtrando nada, só preciso que o aviso chegue certo, pra pessoa certa.

IA: Contínuo e sem necessidade de exploração — mais um sinal para automação, e não para dashboard.

### Diagnóstico — Realidade dos dados

6/7 — Diagnóstico: Realidade dos dados

IA: Agora os dados, com honestidade. Onde vive a informação das solicitações? Você tem acesso? Ela tem a data de abertura e o responsável? O dado já existe ou precisaria ser criado?

Marcos: Vive no sistema de atendimento, o mesmo que a gente usa pra tudo. Tem a data de abertura, o responsável e o status. Eu tenho acesso de consulta. O dado existe, sim, só não tem ninguém vigiando ele.

IA: Perfeito — e essa é uma ótima notícia para automação: o dado existe, é estruturado e tem os campos que importam (data de abertura, responsável, status). Não precisamos capturar nada novo nem limpar bases. Só falta alguém "vigiando" e disparando o aviso — que é justamente o papel de uma automação.

Marcos: Isso!

### Diagnóstico — Esforço vs. valor

7/7 — Diagnóstico: Esforço vs. valor

IA: Por último, pra dimensionar: quantas pessoas essa dor afeta e qual o tamanho do estrago quando um prazo estoura?

Marcos: Afeta minha equipe toda, umas 8 pessoas. E quando estoura, além da reclamação do empresário, a gente leva bronca da coordenação e mancha o indicador de SLA da unidade. Acontece umas 3 ou 4 vezes por mês, e cada uma dá muita dor de cabeça.

IA: Entendi — dor recorrente (3-4 vezes/mês), com impacto reputacional e no indicador de SLA da unidade. Valor claro em resolver.

### Roteamento — Hipótese de solução

Hipótese de solução

IA: Fechei o diagnóstico. Deixa eu te devolver o que entendi: o valor está em AGIR (avisar antes do vencimento), a necessidade é CONTÍNUA, você não precisa explorar dados, e o dado JÁ EXISTE e é estruturado no sistema de atendimento. Isso me indica que a melhor solução não é um painel de BI — é uma AUTOMAÇÃO que monitora as solicitações e dispara um alerta ao responsável antes do prazo estourar. 

Um painel ainda poderia existir como complemento, para a coordenadora ver o retrato geral do SLA no fim do mês, mas o que resolve a sua dor central é a automação. Faz sentido para você seguirmos por esse caminho?

Marcos: Faz total sentido. Eu vim pedindo painel, mas o que eu quero mesmo é isso: parar de deixar passar.

IA: Ótimo. Então vou aprofundar no bloco de Automação. Se você quiser, no fim eu registro o painel de SLA como solução complementar, para a coordenação.

Marcos: Pode registrar, seria bom pra ela.

### Aprofundamento — Automação

Aprofundamento — Automação

IA: Vamos detalhar a automação. Primeiro o gatilho: o que deve disparar o aviso? Um prazo se aproximando? Com quanta antecedência?

Marcos: Quando faltar 1 dia útil pro prazo de 5 dias vencer. Ou seja, no 4º dia sem resposta, dispara o aviso.

IA: E a ação: o que exatamente deve acontecer quando dispara? Um e-mail? Uma mensagem no Teams? Para quem?

Marcos: Uma mensagem no Teams pro responsável pela solicitação, e com cópia pra mim. Dizendo qual solicitação é e que vence amanhã.

IA: Quais sistemas e informações estão envolvidos? Você mencionou o sistema de atendimento com data de abertura, responsável e status.

Marcos: Isso. Precisa olhar a data de abertura, calcular os dias úteis, ver se ainda está sem resposta e quem é o responsável.

IA: E as exceções — em que situações o aviso NÃO deve disparar?

Marcos: Se a solicitação já foi respondida, óbvio, não avisa. E se for fim de semana ou feriado, tem que contar só dia útil, senão vai avisar errado.

IA: Perfeito. Registrei: cálculo em dias úteis (ignorando fim de semana e feriado) e nenhum aviso para solicitações já respondidas. Cobrimos tudo. Vou gerar a Ficha de Demanda de Solução.

## Parte 2 — Ficha de Demanda de Solução gerada

**Ficha de Demanda de Solução — Alerta de SLA de Solicitações**

Resumo executivo: A Unidade de Relacionamento perde prazos de resposta a empresários (SLA de 5 dias úteis) porque solicitações ficam esquecidas na fila e o estouro só é percebido pela reclamação do cliente. O solicitante pediu um painel, mas o diagnóstico revelou que a necessidade é de ação automática, não de visualização. Solução recomendada: uma automação que avisa o responsável 1 dia útil antes do vencimento. Afeta uma equipe de 8 pessoas; o estouro ocorre 3-4 vezes/mês com impacto no indicador de SLA da unidade.

Diagnóstico (Camada 1):

1. Solicitante — Nome / Área: Marcos Tavares — Unidade de Relacionamento; Público-alvo: equipe de relacionamento (8 pessoas) e coordenadora; Prazo: sem prazo definido.
2. Problema real — Solicitações estouram o SLA de 5 dias úteis por ficarem esquecidas na fila; o estouro é percebido tarde, pela reclamação do empresário.
3. Decisão / resultado esperado — Nenhuma solicitação deve estourar o prazo; o responsável deve ser lembrado a tempo de agir.
4. Natureza — Ação (avisar automaticamente), não visão.
5. Recorrência — Contínua; sem necessidade de explorar/filtrar dados.
6. Realidade dos dados:

| Informação | Onde vive | Dono | Estado | Conecta? |
|---|---|---|---|---|
| Solicitações (data de abertura, responsável, status) | Sistema de atendimento | Unidade de Relacionamento / Marcos tem consulta | Estruturado, campos necessários existem | Fonte única; não precisa integrar |

7. Esforço vs. valor — Dor recorrente (3-4 estouros/mês), com impacto reputacional e no indicador de SLA. Alto valor em resolver; dado já disponível reduz o esforço.

Recomendação de solução:
- Solução principal: Automação (monitorar solicitações e alertar o responsável antes do vencimento). Justificativa: o valor está em agir automaticamente, a necessidade é contínua e o dado já existe estruturado — um painel dependeria de alguém lembrar de olhar.
- Soluções complementares: Painel de SLA (visão mensal para a coordenação acompanhar o retrato geral).
- Anel de escopo: 🟡 Adjacente (automação orientada a dados) para a solução principal; 🟢 Núcleo para o painel complementar.
- Encaminhamento sugerido: não aplicável (dentro do escopo do NID).

Especificação da solução (Camada 2 — Automação):
- Gatilho: quando faltar 1 dia útil para o prazo de 5 dias úteis vencer (ou seja, no 4º dia útil sem resposta).
- Ação: mensagem no Teams ao responsável pela solicitação, com cópia para o Marcos, identificando a solicitação e informando que vence no dia seguinte.
- Sistemas / dados envolvidos: sistema de atendimento — data de abertura, responsável, status; cálculo de dias úteis.
- Exceções: não disparar para solicitações já respondidas; contar apenas dias úteis (ignorar fins de semana e feriados).

Critérios de sucesso:
- Zerar (ou reduzir drasticamente) os estouros de SLA por esquecimento.
- O responsável recebe o aviso a tempo de responder, sem precisar abrir nenhum painel.

Fora de escopo:
- Responder as solicitações automaticamente (o aviso lembra; a resposta continua humana).
- Solicitações de outras unidades além da Relacionamento.

Prioridade e prazo: Prioridade Importante; sem data-limite definida.

Pontos em aberto (a resolver com o NID):
- Confirmar a fonte oficial de feriados a considerar no cálculo de dias úteis (municipal/estadual/nacional).
- Verificar se o sistema de atendimento permite integração/leitura automática (API, conector) ou se exige outra abordagem de coleta.
- Definir com a coordenação se o painel de SLA complementar entra nesta demanda ou vira uma demanda separada.

*Ficha gerada via Assistente de Demanda de Soluções de Dados — NID. Data de geração: 06/08/2026.*

## Observações sobre este exemplo (para quem for treinar analistas)

Repare onde o agente agiu como líder técnico de soluções, e não como executor de painéis:

- Não aceitou a solução pronta: o Marcos veio pedindo "painel", e o agente segurou a conclusão até diagnosticar a necessidade.
- A pergunta de roteamento foi decisiva: "enxergar ou agir?" revelou que a dor era de ação automática — o coração do diagnóstico.
- Usou os eixos certos: ação vs. visão (etapa 4), recorrência (etapa 5) e realidade dos dados (etapa 6) convergiram para automação.
- Validou a hipótese antes de aprofundar: propôs a automação e confirmou com o solicitante, em vez de impor.
- Registrou combinação de soluções: automação como principal e painel como complementar, cada um com seu anel de escopo.
- Foi honesto sobre incertezas: feriados, integração do sistema e o painel complementar viraram pontos em aberto, sem invenção.

O resultado é uma demanda que o NID consegue avaliar sem reunião de levantamento — e que evita construir um painel que não resolveria a dor real.
