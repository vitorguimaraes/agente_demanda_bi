# Assistente de Demanda de Soluções de Dados — Núcleo de Inteligência de Dados (NID)

> Um agente do Microsoft Copilot que atua como **Líder Técnico de Soluções de Dados**: entrevista analistas que trazem uma necessidade, **diagnostica** o problema real e **recomenda a solução certa** — que nem sempre é um painel de BI. O resultado é uma **Ficha de Demanda** clara e curada, pronta para o time de dados avaliar, sem longas reuniões de levantamento.

---

## 📌 Sobre o projeto

No dia a dia de um núcleo de dados, muitos pedidos chegam já embrulhados numa solução assumida: "preciso de um dashboard", "quero um painel". Mas o painel raramente é a necessidade — é uma **hipótese**. Às vezes a melhor resposta para "quero acompanhar os prazos" não é um dashboard que alguém precisa lembrar de abrir, e sim uma **automação** que avisa sozinha quando algo está prestes a estourar.

Este projeto desloca o **diagnóstico da necessidade** para um agente de IA que conduz uma entrevista estruturada, critica respostas vagas e — o mais importante — **não assume a solução no início**. Ele investiga a dor, a decisão e a natureza do problema antes de recomendar o formato do produto.

> **Princípio central:** o painel não é o produto — é uma hipótese de solução. O produto certo é o que melhor apoia a decisão do usuário com o menor esforço.

### O que o agente faz (e não faz)

- ✅ Diagnostica a necessidade de forma agnóstica à solução.
- ✅ Recomenda o tipo de solução mais adequado (painel, automação, agente de IA, micro-app, pipeline, análise pontual ou encaminhamento).
- ✅ Gera uma Ficha de Demanda de Solução curada, com o escopo explícito.
- ❌ **Não** constrói a solução nem entra em detalhes técnicos (código, DAX, modelagem, visuais) — isso permanece com o NID, na fase seguinte.

---

## 🏛️ A arquitetura em duas camadas

O agente separa **diagnóstico** de **execução**. A inteligência mora na Camada 1; a Camada 2 apenas aprofunda no tipo já identificado.

```
┌───────────────────────────────────────────────────┐
│  CAMADA 1 — DIAGNÓSTICO (agnóstica à solução)     │
│  1. Identificação                                 │
│  2. Problema (a dor)                              │
│  3. Decisão esperada                              │
│  4. Ação vs. visão                                │
|  5. Recorrência / interatividade                  │
|  6. Realidade dos dados                           │ 
|  7. Esforço vs. valor                             │
│                     ↓                             │
│  HIPÓTESE DE SOLUÇÃO → validada com o solicitante │
└───────────────────────────────────────────────────┘
                     ↓ (roteamento por sinais)
┌─────────────────────────────────────────────────────────────┐
│  CAMADA 2 — APROFUNDAMENTO (só o bloco da solução escolhida)│
│  A. Painel de BI   B. Automação    C. Agente de IA          │
│  D. Micro-app      E. Pipeline/ETL F. Análise pontual       │
│  G. Encaminhamento (fora do escopo → não aprofunda)         │
└─────────────────────────────────────────────────────────────┘
                     ↓
        FICHA DE DEMANDA DE SOLUÇÃO (com recomendação e escopo)
```

### O filtro de qualidade

A cada resposta, o agente aplica um filtro. Se falhar em qualquer item, ele **não avança** — devolve o problema e pede refinamento:

- **Específica?** Evita termos genéricos como "melhorar", "acompanhar", "ter visão".
- **Acionável?** Leva a uma decisão ou ação concreta.
- **Mensurável?** É possível saber quando o objetivo foi atingido.
- **Delimitada?** Deixa claro o que está dentro e o que está fora.

---

## 🧭 O quadro de decisão (sintoma → solução)

O roteamento da Camada 1 para a Camada 2 segue esta lógica:

| Sinais predominantes no diagnóstico | Solução recomendada | Escopo |
|-------------------------------------|---------------------|--------|
| Enxergar + recorrente + explorar/filtrar | Painel de BI | 🟢 Núcleo |
| Enxergar + recorrente + receber pronto | Relatório agendado | 🟢 Núcleo |
| Agir + gatilho condicional | Automação | 🟡 Adjacente |
| Linguagem / triagem / perguntas repetidas | Agente de IA | 🟡 Adjacente |
| Dado não existe / precisa capturar | Micro-app | 🟡 Adjacente |
| Bases desconectadas ou sujas | Pipeline / ETL | 🟢 Núcleo |
| Pergunta única, não recorrente | Análise pontual | 🟢 Núcleo |
| Não é problema de dados | Encaminhamento | 🔴 Fora |

> **Combinações são normais.** Ex.: um painel que depende de um pipeline para existir, ou um dashboard com uma automação de alerta acoplada. O agente registra a solução principal e as complementares.

### Os três anéis de escopo do NID

Ampliar os **caminhos de diagnóstico** não amplia o escopo de **execução**:

- 🟢 **Núcleo** — transformar dados em decisão (painel, relatório, análise, modelagem, pipeline). O NID executa.
- 🟡 **Adjacente** — soluções que produzem ou consomem dados (automação, agente de IA, micro-app, preditivo). O NID executa se houver capacidade.
- 🔴 **Fora** — engenharia de software completa, infraestrutura, redesenho de processo. O NID diagnostica e **encaminha**, não constrói.

**Régua de decisão:** *"esta solução existe para apoiar uma decisão baseada em dados?"* Se sim, é candidata. Se é sobre operação, infra ou processo puro, o NID orienta mas não assume.

---

## 🎯 O fluxo de uso

```
1. Analista traz uma necessidade ao Núcleo de Inteligência de Dados
2. O Núcleo direciona o analista para o agente
3. O agente diagnostica a necessidade (Camada 1) e recomenda a solução (Camada 2)
4. O agente gera a Ficha de Demanda de Solução curada
5. O analista encaminha a ficha ao Núcleo — sem reunião de levantamento
```

---

## 📁 Estrutura do repositório

```
.
├── README.md                                   # Este arquivo
├── instrucoes/
│   └── Instrucoes-Agente-Solucoes-de-Dados.md  # Instruções do agente (campo "Instructions")
├── conhecimento/
│   ├── Template-Solucoes-de-Dados.md           # Roteiro completo das 2 camadas (knowledge source)
│   └── Exemplo-Preenchido-Solucoes-de-Dados.md # Entrevista de exemplo + ficha (knowledge source)
├── referencia/
│   ├── Quadro-de-Decisao-Solucoes-de-Dados.md  # Lógica sintoma → solução
│   └── Arquitetura-Duas-Camadas-Agente-NID.md  # Documento de arquitetura
└── docs/
    └── (opcional) versões .pdf / .docx para upload
```

| Arquivo | Papel |
|---------|-------|
| **Instruções** | Vai colado no campo **Instructions** do agente. Define persona, comportamento, contador de etapa, filtro de qualidade, roteamento e regra de geração da ficha. Condensado para caber no limite de ~8.000 caracteres. |
| **Template de Soluções de Dados** | Entra como **knowledge source**. Detalha as 7 etapas do diagnóstico e os 7 blocos de aprofundamento (A a G). |
| **Exemplo Preenchido** | Entra como **knowledge source**. Uma entrevista simulada de ponta a ponta que ensina o roteamento (caso que começa como "painel" e vira automação) e fixa o formato da ficha. |
| **Quadro de Decisão** e **Arquitetura** | Documentos de referência para o time. Não precisam ir para o agente. |

---

## 🚀 Como publicar o agente no Copilot

Recomendado o **Agent Builder** do Microsoft 365 Copilot (no-code), ideal para agentes que entrevistam e geram documentos.

### Pré-requisitos
- Licença **Microsoft 365 Copilot** com o Agent Builder habilitado pelo administrador.
- Acesso ao app do Microsoft 365 Copilot (web, Teams ou Edge).

### Passo a passo

1. **Abra o criador** — No app do M365 Copilot, vá em **Agents → New Agent** e escolha a aba **Configure**.
2. **Cole as instruções** — Copie o conteúdo de `instrucoes/Instrucoes-Agente-Solucoes-de-Dados.md` no campo **Instructions**.
3. **Defina nome e descrição:**
   - **Nome:** `Assistente de Demanda de Soluções de Dados — NID`
   - **Descrição:** *Assistente do Núcleo de Inteligência de Dados que atua como Líder Técnico de Soluções de Dados. Diagnostica a necessidade do solicitante e recomenda a solução certa — painel, automação, agente de IA, micro-app, pipeline ou análise — gerando uma Ficha de Demanda clara e curada, sem reuniões de levantamento.*
4. **Adicione os knowledge sources** — Envie os dois arquivos de `conhecimento/` (um de cada vez). Dê uma descrição a cada um.
5. **Configure os starter prompts:**
   - "Tenho uma necessidade, mas não sei qual solução resolve."
   - "Quero acompanhar os atendimentos das unidades."
   - "Preciso ser avisado quando algo sair do esperado."
6. **Teste na aba "Try it"** — Simule um analista que chega pedindo "um painel" e verifique se o agente **diagnostica antes de assumir** e roteia para a solução certa.
7. **Publique e compartilhe** com a organização ou com o grupo de analistas.

> 💡 **Formatos de arquivo:** o Agent Builder pode recusar `.md` no upload. Se acontecer, use os arquivos em **`.pdf`** ou **`.docx`** (nomes sem acentos ou caracteres especiais como `—`).

> 💡 **Hospedagem no SharePoint (opcional):** mantenha os knowledge sources numa biblioteca do SharePoint e aponte o agente para ela — assim, ao atualizar, o agente acompanha. Mantenha os arquivos na raiz da biblioteca.

---

## 🔧 Manutenção e evolução

- **A fonte da verdade é o Markdown deste repositório.** Edite os `.md` aqui, versione com Git e só então gere os `.pdf`/`.docx` e reenvie ao agente.
- **O limite de instruções é ~8.000 caracteres.** A Camada 2 tem muitos blocos; mantenha nas instruções apenas o roteamento e um resumo de cada bloco, e detalhe os blocos completos no template (knowledge source).
- **O modelo do Copilot evolui.** Revalide o comportamento periodicamente, pois mudanças de versão do modelo podem afetar a interpretação das instruções.

---

## 🗺️ Roadmap (ideias futuras)

- [ ] Migrar para **Copilot Studio** para gravar a Ficha de Demanda automaticamente em uma lista do SharePoint via Power Automate.
- [ ] Guia de triagem para o NID priorizar as fichas recebidas.
- [ ] Roteiro de testes com cenários-armadilha (analista que insiste no painel, que pula etapas, que pede detalhe técnico).
- [ ] Blocos de aprofundamento adicionais na Camada 2 conforme novos tipos de solução surgirem.

---

## 🤝 Contribuindo

1. Faça um fork e crie uma branch por mudança.
2. Edite os arquivos `.md` (nunca só os binários gerados).
3. Abra um pull request descrevendo o ajuste de comportamento pretendido.

---

## ✍️ Créditos

Desenvolvido pelo **Núcleo de Inteligência de Dados** para padronizar e qualificar a entrada de demandas — recomendando a solução de dados certa para cada necessidade.
