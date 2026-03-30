# Alta performance com dados — Pandas, Polars, cuDF

Roteiro prático para a pasta `02-high-performance-data/`. Cada tópico pode virar um notebook em `notebooks/` quando você avançar.

## 1. Pandas (3.x / 2.2+)

- **CoW:** entender quando cópias acontecem; habilitar/assumir comportamento da sua versão ao ler o [changelog](https://pandas.pydata.org/docs/whatsnew/).
- **Dtypes:** migrar strings de `object` para **`string[pyarrow]`** quando fizer sentido.
- **Evitar:** `apply(axis=1)` em datasets grandes; preferir vetorização ou outra ferramenta.
- **Docs:** [pandas.pydata.org](https://pandas.pydata.org/docs/)

## 2. Polars

- **Mental model:** colunar Arrow + **expressões** (`pl.col`) + **lazy** (`scan_*`, `collect`).
- **Fluxo típico:** `pl.scan_parquet("*.parquet")` → `.filter` / `.select` / `.group_by` → `.collect()`.
- **Debug:** usar `.fetch(n)` / `.head()` antes de `collect()` completo em dados enormes.
- **Docs:** [docs.pola.rs](https://docs.pola.rs/)

## 3. cuDF (RAPIDS)

- **Quando:** GPU NVIDIA disponível, dados cabendo na VRAM, pipeline compatível com API RAPIDS.
- **Sem GPU:** foque em Polars (CPU) ou out-of-core (DuckDB, Spark, etc.).
- **Docs:** [docs.rapids.ai](https://docs.rapids.ai/)

## Tabela rápida de decisão

| Critério | Tendência |
|----------|-----------|
| Integração sklearn / código legado | Pandas |
| ETL in-process, joins/agregações pesadas | Polars |
| GPU NVIDIA + volume compatível com VRAM | cuDF |
| Dados >> RAM ou governança SQL | Warehouse / DuckDB / Spark |

## Flashcards

- Markdown: [`../flashcards/pandas-polars-cudf.md`](../flashcards/pandas-polars-cudf.md)
- Anki: [`../flashcards/anki-pandas-polars.tsv`](../flashcards/anki-pandas-polars.tsv)

## Próximos artefatos sugeridos (portfólio)

1. `notebooks/01_pandas_cow_strings.ipynb` — mesmo pipeline com/sem CoW e com `string[pyarrow]`.
2. `notebooks/02_polars_lazy_vs_eager.ipynb` — mesmo query plan: scan+collect vs read eager.
3. `notebooks/03_pandas_polars_same_task.ipynb` — tempo + memória (com `%%time` / `memory_profiler` ou mensagens simples).

Manter em cada notebook: versões (`import pandas as pd; pd.__version__`, `polars.__version__`) e tamanho do dataset.
