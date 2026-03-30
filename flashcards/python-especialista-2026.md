# Flashcards — Python especialista (3.14+) e stack de dados

Formato: **Frente** → **Verso**. Use cobertura ativa (tente responder antes de virar o cartão).

---

## CPython, concorrência e interpretadores

**Frente:** O que a [PEP 703](https://peps.python.org/pep-0703/) propõe em relação ao GIL no CPython?

**Verso:** Tornar o Global Interpreter Lock *opcional* em builds de CPython, permitindo execução **free-threaded** (paralelismo real em threads para código puro Python em cenários suportados), com trade-offs de compatibilidade e extensões nativas.

---

**Frente:** O que é a [PEP 779](https://peps.python.org/pep-0779/) em uma frase?

**Verso:** Define **critérios** para o Python free-threaded sair de fase experimental e ser considerado **suportado oficialmente** (estabilidade, manutenção, desempenho, ecossistema de wheels/ABI onde aplicável).

---

**Frente:** O que a [PEP 734](https://peps.python.org/pep-0734/) adiciona ao ecossistema padrão?

**Verso:** API em stdlib para **múltiplos interpretadores** no mesmo processo (`concurrent.interpreters`), com filas e executor — isolamento de estado entre interpretadores; complementar (não idêntico) ao modelo “só free-threading”.

---

**Frente:** Quando **subinterpretadores** (PEP 734) podem ajudar em tarefas CPU-bound?

**Verso:** Ao isolar execuções pesadas em interpretadores separados, reduzindo contenção do modelo de threading clássico **com GIL**; útil como ferramenta de **isolamento + paralelismo limitado pelo modelo**, não como substituto automático de todo multiprocessing.

---

**Frente:** Diferença prática entre `threading` com GIL clássico e build **free-threaded** para CPU-bound?

**Verso:** Com GIL, threads costumam **não paralelizar** código Python CPU-intensivo; free-threaded remove essa barreira **no build adequado**, mas exige **dependências compatíveis** (extensões C/wheels) e validação de desempenho.

---

## Template strings (t-strings)

**Frente:** O que é uma **t-string** ([PEP 750](https://peps.python.org/pep-0750/))?

**Verso:** Literal `t"..."` que produz um objeto **`Template`** (não `str` direto), expondo partes interpoladas para **processamento customizado** antes da renderização final — útil para sanitização, i18n, DSLs e templates seguros.

---

**Frente:** Diferença essencial entre **f-string** e **t-string**?

**Verso:** **f-string** interpola e já forma `str`; **t-string** preserva estrutura (`Template`) para o código **decidir** como combinar/validar trechos (hook de processamento).

---

## Dados: Pandas, Polars, cuDF

**Frente:** O que é **Copy-on-Write (CoW)** no contexto do Pandas moderno?

**Verso:** Estratégia em que cópias de DataFrame/Series são **adiadas**: compartilha dados até haver escrita, evitando cópias desnecessárias e ajudando desempenho e semântica mais previsível em encadeamentos.

---

**Frente:** Por que o Polars costuma ser rápido em pipelines analíticos?

**Verso:** Núcleo em **Rust**, execução **multithread** onde cabe, API **lazy** (`lazyframes`) que **otimiza o plano de query** antes de executar — bom para filtros/agregações em volume.

---

**Frente:** “Polars é sempre 10× Pandas” — isso é regra?

**Verso:** **Não.** Ganho depende de **workload**, tamanho, operações (join, groupby, I/O), e se o plano lazy foi usado. Benchmark **seu caso** antes de afirmar fator fixo.

---

**Frente:** Para que serve **RAPIDS cuDF**?

**Verso:** DataFrame **GPU-accelerated** (ecossistema NVIDIA), útil quando o gargalo é compute massivo em GPU disponível; exige **hardware/drivers** e mentalidade diferente de pandas puro.

---

**Frente:** Quando escolher **Pandas** vs **Polars** vs **cuDF**?

**Verso:** **Pandas** — ecossistema máximo, exemplos legados, integrações. **Polars** — performance/previsibilidade em ETL analítico médio/grande. **cuDF** — dados grandes **e** GPU + stack RAPIDS viável.

---

## IA, agentes e workflows

**Frente:** Papel típico de **Smolagents** (Hugging Face) em um projeto?

**Verso:** Biblioteca leve para **agentes** que orquestram ferramentas e **geração de código** em passos — bom para protótipos e fluxos com modelo + tools.

---

**Frente:** Para que **MarkItDown** (Microsoft) em pipelines de LLM?

**Verso:** Converter **PDF, Office, HTML**, etc. para **Markdown** limpo, facilitando chunking/RAG e alimentação de modelos com texto estruturado.

---

**Frente:** O que **Temporal** resolve que filas simples não resolvem sozinhas?

**Verso:** **Orquestração durável**: estado de workflow sobrevive a falhas/restarts, retries com política, timers e saga-like patterns — ideal para processos longos (backoffice, pagamentos, pipelines).

---

**Frente:** O que é **Jupyter AI** no dia a dia?

**Verso:** Extensão/ecossistema para **assistência generativa dentro do Jupyter** (explicação, geração de código, magics) — produtividade, não substituto de design de ML sério.

---

## GUI e SaaS rápido

**Frente:** NiceGUI vs Streamlit — ideia geral de posicionamento?

**Verso:** **Streamlit** — apps dados-first ultra rápidos, modelo re-run. **NiceGUI** — UI reativa com **Vue/Quasar** por baixo, bom para painéis e protótipos web Python-first com mais controle de componentes.

---

**Frente:** Por que **PySide6 + QML** para desktop?

**Verso:** UI **declarativa** (QML) + lógica Python, performance nativa Qt, indicado para **aplicações desktop profissionais** (offline, integração SO) frente a apps web embutidos.

---

## Meta (estudo)

**Frente:** Por que versionar laboratórios junto de um README honesto sobre limitações?

**Verso:** Portfólio sênior valoriza **reproducibilidade**, escopo claro e **o que você validou** — evita “demo bonita” sem evidência; recrutadores técnicos notam.

---

**Frente:** Checklist mínimo antes de publicar um benchmark no GitHub?

**Verso:** Versões fixas (`python -V`, `pip freeze`), tamanho do dataset, hardware, warm-up, número de repetições, mediana/pctil — e código para reproduzir.
