# Flashcards — Pandas × Polars × cuDF

**Frente** → **Verso**. Baralho complementar a `python-especialista-2026.md`.

---

**Frente:** Modelo de dados: Pandas 2.x costuma repousar em que base colunar?

**Verso:** **NumPy** e, cada vez mais, tipos **PyArrow-backed** (`string[pyarrow]`, etc.) para strings e extensões — dependendo da versão e configuração.

---

**Frente:** Modelo de dados nativo do Polars?

**Verso:** **Apache Arrow** em colunas; execução pensada para **vetorização** e **query planner** (especialmente no modo lazy).

---

**Frente:** API típica do Polars para adiar execução e otimizar o plano?

**Verso:** `scan_csv` / `scan_parquet` → **`LazyFrame`** → encadear `.filter`, `.select`, `.group_by` → **`.collect()`** (ou `sink_*` para streaming em cenários avançados).

---

**Frente:** No Pandas, o que **Copy-on-Write (CoW)** ajuda a evitar?

**Verso:** Cópias defensivas **desnecessárias** ao encadear operações; compartilha buffers até haver **escrita** real — menos RAM e surpresas em certos padrões de slicing.

---

**Frente:** Por que `df.apply(axis=1)` no Pandas é frequentemente lento?

**Verso:** Itera em Python puro por linha, **fora** do núcleo vetorizado; preferir operações **vetoriais**, `transform`, merge/join, ou Polars **expressions**.

---

**Frente:** No Polars, o que são **expressions** (`pl.col("a")`)?

**Verso:** Descrições **declarativas** de transformações que o engine otimiza e paraleliza — alternativa moderna a `apply` row-wise.

---

**Frente:** Diferença entre **`null`** no Polars e **`NaN`** no ecossistema NumPy/Pandas?

**Verso:** Polars distingue **ausência de valor** (`null`) de **float NaN** com semântica mais explícita em muitas operações; no Pandas historicamente **NaN** misturou “missing” e resultado inválido em floats.

---

**Frente:** Quando Pandas ainda é a escolha mais pragmática?

**Verso:** Integração com **scikit-learn**, exemplos/cursos legados, libs que **esperam** `DataFrame`/`Series` pandas, pipelines já escritos, e time que só conhece pandas.

---

**Frente:** Quando Polars tende a brilhar?

**Verso:** **ETL** e análise em **DataFrames grandes**, muitos **filtros/agregações/joins**, necessidade de **lazy** + paralelismo sem reescrever tudo em SQL.

---

**Frente:** Polars substitui SQL?

**Verso:** **Não** automaticamente; para **bilhões** de linhas e políticas enterprise, **warehouse + SQL** ou **Spark/DuckDB** podem ser melhores. Polars é excelente **in-process** até limites de RAM (com streaming parcial).

---

**Frente:** O que é **cuDF** no ecossistema RAPIDS?

**Verso:** API **estilo pandas** executada em **GPU NVIDIA** (CUDA), acelerando joins, groupby, etc., quando dados cabem na **VRAM** e o pipeline é compatível.

---

**Frente:** Principal pré-requisito operacional para cuDF?

**Verso:** **GPU NVIDIA** adequada, drivers, e ambiente conda/pip **alinhado** à versão CUDA suportada; sem GPU, use Polars/Pandas.

---

**Frente:** Armadilha comum ao comparar Pandas vs Polars em benchmark?

**Verso:** Medir Pandas **eager** cheio de cópias vs Polars **lazy otimizado**; ou **um** sem warm-up/I/O em disco. **Isolar** a operação pura ou documentar pipeline inteiro.

---

**Frente:** Como ler **Parquet** de forma eficiente nos dois?

**Verso:** Pandas: `pd.read_parquet` com engine pyarrow; Polars: `pl.scan_parquet` (lazy) ou `read_parquet` (eager) — preferir **scan** em pipelines grandes.

---

**Frente:** Join: diferença de estilo mental Pandas vs Polars?

**Verso:** Pandas: `merge` com `how=`; Polars: `.join` no **LazyFrame/DataFrame** com argumentos `how` — ambos exigem atenção a **chaves duplicadas** e **tipos** alinhados.

---

**Frente:** Strings longas: tendência no Pandas 2+?

**Verso:** Migrar para dtype **`string[pyarrow]`** ou equivalente quando possível — melhor memória/desempenho que `object` para texto.

---

**Frente:** Polars em Jupyter: por que `.collect()` pode “travar” a célula?

**Verso:** Porque **aí** o plano lazy **executa de verdade**; antes era só construção do grafo. Use amostras (`head`, `fetch`) para depuração.

---

**Frente:** Estratégia híbrida Pandas + Polars em produção?

**Verso:** **Ingestão/transformação** em Polars → `.to_pandas()` só na **borda** onde a lib downstream exige pandas — minimiza conversões duplas.

---

**Frente:** O que documentar num README de benchmark entre os três?

**Verso:** Versões (`pandas`, `polars`, `cudf`), **hardware** (CPU/GPU/VRAM), **tamanho** do dataset, **operação** isolada, repetições e **mediana** — e link para o script.
