# Assistente de Demanda de Painéis — Núcleo de Inteligência de Dados (NID)

> Um agente do Microsoft Copilot que atua como **Líder Técnico de BI**: entrevista analistas que solicitam painéis de Power BI e transforma pedidos vagos em uma **Ficha de Demanda** clara, curada e pronta para o time de dados avaliar — sem longas reuniões de levantamento.

---

## 📌 Sobre o projeto

No dia a dia de um núcleo de dados, muitos pedidos de painel chegam sem critério: "preciso de um dashboard de atendimento", "quero acompanhar as vendas". Falta clareza sobre **o problema real**, **a decisão que o painel apoia** e **o estado das bases de dados** — o que gera idas e vindas e reuniões intermináveis.

Este projeto resolve isso deslocando o **levantamento qualitativo da necessidade** para um agente de IA. O agente conduz uma **entrevista estruturada de 12 seções**, critica respostas genéricas e força decisões claras. O resultado é uma demanda tão bem definida que o núcleo consegue avaliá-la sem reunião de requisitos.

> ⚠️ **Escopo consciente:** o agente **não** desenha o painel nem trata de aspectos técnicos (DAX, modelagem, visuais). Ele para no **levantamento da necessidade** — a construção do painel permanece com o time de dados, na fase seguinte.

### Por que parar no levantamento?

A construção do painel exige acesso às bases reais, à capacidade de processamento e à governança da organização — coisas que o agente não tem. O maior gargalo (e o maior valor) está justamente em **entender a necessidade com qualidade**. É aí que este agente atua.

---

## 🎯 O fluxo de uso

```
1. Analista solicita um painel ao Núcleo de Inteligência de Dados
2. O Núcleo direciona o analista para o agente
3. O analista conversa com o agente, que o entrevista seção por seção
4. O agente gera a Ficha de Demanda curada
5. O analista encaminha a ficha ao Núcleo — sem reunião de levantamento
```

---

## 🧩 As 12 seções da entrevista

| # | Seção | O que captura |
|---|-------|---------------|
| 1 | Identificação | Quem pede, área, público-alvo, prazo |
| 2 | Problema real (a dor) | O incômodo concreto que motivou o pedido |
| 3 | Decisão apoiada | Que decisão o painel habilita (o coração da entrevista) |
| 4 | Perguntas de negócio | 3 a 8 perguntas objetivas que o painel responde |
| 5 | Público e uso | Quem consome, nível, contexto e frequência |
| 6 | Indicadores | Métricas em linguagem de negócio, metas e direção do "bom" |
| 7 | Dimensões de análise | Recortes (unidade, período, etc.) e janela de tempo |
| 8 | Realidade dos dados | Onde vivem, dono, estado e conexões (com honestidade) |
| 9 | Frequência de atualização | Tempo real / diária / semanal / mensal, justificada |
| 10 | Critérios de sucesso | Pelo menos 2 critérios verificáveis |
| 11 | Fora de escopo | O que o painel **não** fará nesta versão |
| 12 | Prioridade e prazo | Crítico / importante / desejável e data-limite |

### O filtro de qualidade

A cada resposta, o agente aplica um filtro. Se a resposta falhar em qualquer item, ele **não avança** — devolve o problema e pede refinamento:

- **Específica?** Evita termos genéricos como "melhorar", "acompanhar", "ter visão".
- **Acionável?** Leva a uma decisão ou ação concreta.
- **Mensurável?** É possível saber quando o objetivo foi atingido.
- **Delimitada?** Deixa claro o que está dentro e o que está fora.

---

## 📁 Estrutura do repositório

```
.
├── README.md                                   # Este arquivo
├── Instrucoes-Agente-Copilot.md            # Instruções do agente (campo "Instructions")
├── Template-Levantamento-Painel-BI.md      # Roteiro completo (knowledge source)
└── Exemplo-Preenchido-Levantamento.md      # Entrevista de exemplo + ficha (knowledge source)
```

| Arquivo | Papel no agente |
|---------|-----------------|
| **Instruções** | Vai colado no campo **Instructions** do agente. Define persona, comportamento, contador de etapa, filtro de qualidade e regra de geração da ficha. Condensado para caber no limite de ~8.000 caracteres. |
| **Template de Levantamento** | Entra como **knowledge source**. Detalha o propósito, as perguntas-guia e o padrão de qualidade de cada uma das 12 seções. |
| **Exemplo Preenchido** | Entra como **knowledge source**. Uma entrevista simulada de ponta a ponta que ensina o estilo e fixa o formato exato da Ficha de Demanda. |

---

## 🚀 Como publicar o agente no Copilot

Recomendado o **Agent Builder** do Microsoft 365 Copilot (no-code), ideal para agentes que entrevistam e geram documentos.

### Pré-requisitos
- Licença **Microsoft 365 Copilot** com o Agent Builder habilitado pelo administrador.
- Acesso ao app do Microsoft 365 Copilot (web, Teams ou Edge).

### Passo a passo

1. **Abra o criador** — No app do M365 Copilot, vá em **Agents → New Agent** e escolha a aba **Configure**.
2. **Cole as instruções** — Copie o conteúdo de `Instrucoes-Agente-Copilot.md` no campo **Instructions**.
3. **Defina nome e descrição:**
   - **Nome:** `Assistente de Demanda de Painéis — NID`
   - **Descrição:** *Assistente do Núcleo de Inteligência de Dados que atua como Líder Técnico de BI. Entrevista o analista solicitante, questiona respostas vagas e gera uma Ficha de Demanda de Painel clara e curada — eliminando idas e vindas e reuniões de levantamento.*
4. **Adicione os knowledge sources** — No botão **+ / Add knowledge**, envie os dois arquivos de conhecimento (um de cada vez). Dê uma descrição a cada um.
5. **Configure os starter prompts:**
   - "Preciso de um painel, por onde começo?"
   - "Me ajude a montar a demanda para o Núcleo de Dados."
   - "Quero acompanhar os atendimentos."
6. **Teste na aba "Try it"** — Simule um analista com respostas vagas ("quero acompanhar o atendimento") e verifique se o agente **critica e não avança**.
7. **Publique e compartilhe** com a organização ou com o grupo de analistas.

> 💡 **Dica sobre formatos de arquivo:** o Agent Builder pode recusar `.md` no upload. Se isso acontecer, use os arquivos em **`.pdf`** ou **`.docx`** (mantenha nomes sem acentos ou caracteres especiais como `—`).

> 💡 **Hospedagem opcional no SharePoint:** você pode manter os arquivos de conhecimento numa biblioteca do SharePoint e apontar o agente para ela — assim, ao atualizar o template, o agente acompanha. Mantenha os arquivos na raiz da biblioteca (evite subpastas profundas).

---

## 🔧 Manutenção e evolução

- **A fonte da verdade é o Markdown deste repositório.** Edite os `.md` aqui, versione com Git e só então gere os `.pdf`/`.docx` e reenvie ao agente.
- **O limite de instruções é ~8.000 caracteres.** Ao adicionar comportamento, prefira detalhar nos knowledge sources em vez de inflar as instruções.
- **O modelo do Copilot evolui.** Revalide o comportamento do agente periodicamente, pois mudanças de versão do modelo podem afetar a interpretação das instruções.

---

## 🗺️ Roadmap (ideias futuras)

- [ ] Migrar para **Copilot Studio** para gravar a Ficha de Demanda automaticamente em uma lista do SharePoint via Power Automate.
- [ ] Guia de triagem para o Núcleo decidir se a ficha vira projeto.
- [ ] Roteiro de testes com cenários-armadilha (analista vago, que pula etapas, que pede DAX).

---

## 🤝 Contribuindo

1. Faça um fork e crie uma branch por mudança.
2. Edite os arquivos `.md` (nunca só os binários gerados).
3. Abra um pull request descrevendo o ajuste de comportamento pretendido.

---

## ✍️ Créditos

Desenvolvido pelo **Núcleo de Inteligência de Dados** para padronizar e qualificar a entrada de demandas de BI.
