<p align="center">
<img src="assets/capa.png" alt="Mastering Python 2026" width="100%">
</p>

<h1 align="center">Mastering Python 2026</h1>
<p align="center"><i>Estudo e portfólio técnico: CPython moderno, dados em alta performance, agentes de IA e interfaces</i></p>

<p align="center">
<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
<img src="https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white" alt="Pandas">
<img src="https://img.shields.io/badge/Polars-CD792C?style=flat-square&logo=polars&logoColor=white" alt="Polars">
<img src="https://img.shields.io/badge/Anki-235390?style=flat-square" alt="Anki">
<img src="https://img.shields.io/badge/status-em%20andamento-F59E0B?style=flat-square" alt="status: em andamento">
</p>

## Sumário

- [Sobre](#sobre)
- [Roteiro](#roteiro)
- [Flashcards](#flashcards)
- [Referências](#referências)
- [Estrutura do repositório](#estrutura-do-repositório)
- [Autor](#autor)

## Sobre

Roteiro de estudos para dominar o **Python de 2026**: o que mudou no interpretador, como trabalhar com dados em alta performance, como construir agentes de IA e como entregar interfaces modernas. Cada módulo evolui de forma incremental, com anotações, notebooks e código.

## Roteiro

```mermaid
flowchart LR
    A[01 · CPython internals] --> B[02 · Dados em alta performance]
    B --> C[03 · Agentes de IA e workflows]
    C --> D[04 · GUI e SaaS modernos]
```

| Módulo | Foco | Status |
| --- | --- | --- |
| [`01-cpython-internals/`](01-cpython-internals/) | PEPs recentes, free-threading, múltiplos interpretadores, t-strings | 🔜 planejado |
| [`02-high-performance-data/`](02-high-performance-data/) | Pandas 3.x, Polars (lazy) e RAPIDS cuDF — [roteiro](02-high-performance-data/README.md) | 🔄 em andamento |
| [`03-ai-agents-and-workflows/`](03-ai-agents-and-workflows/) | Agentes, ingestão de documentos e workflows resilientes | 🔜 planejado |
| [`04-modern-gui-saas/`](04-modern-gui-saas/) | NiceGUI, Streamlit, PySide6 / QML | 🔜 planejado |

## Flashcards

Cartões para memorização em Markdown e prontos para importar no **Anki**:

| Tema | Leitura | Importação no Anki |
| --- | --- | --- |
| Python especialista 2026 | [python-especialista-2026.md](flashcards/python-especialista-2026.md) | `flashcards/anki-import.tsv` |
| Pandas, Polars e cuDF | [pandas-polars-cudf.md](flashcards/pandas-polars-cudf.md) | `flashcards/anki-pandas-polars.tsv` |

> No Anki: importar o `.tsv` com separador **tabulação** e tipo de nota **Básico** (frente / verso).

## Referências

- [PEP 703](https://peps.python.org/pep-0703/) — GIL opcional / free-threading
- [PEP 779](https://peps.python.org/pep-0779/) — critérios de suporte ao build free-threaded
- [PEP 734](https://peps.python.org/pep-0734/) — múltiplos interpretadores (`concurrent.interpreters`)
- [PEP 750](https://peps.python.org/pep-0750/) — template strings (`t"..."`)

## Estrutura do repositório

```text
Mastering-Python-2026/
├── 01-cpython-internals/
├── 02-high-performance-data/
│   └── README.md
├── 03-ai-agents-and-workflows/
├── 04-modern-gui-saas/
├── flashcards/
│   ├── python-especialista-2026.md
│   ├── pandas-polars-cudf.md
│   ├── anki-import.tsv
│   └── anki-pandas-polars.tsv
└── assets/capa.png
```

## Autor

**Saulo Prado** · Analista de Sistemas · Gestão de Ativos de TI, orçamento, automação e dashboards

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Saulo%20Prado-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/saulo-prado-ab4a0b96/)
[![GitHub](https://img.shields.io/badge/GitHub-sauloprado-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/sauloprado)
