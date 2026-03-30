# Mastering Python 2026

Repositório de estudo e portfólio técnico — CPython moderno, dados em alta performance, agentes de IA e interfaces.

**Autor:** [Saulo Souza da Cunha Prado](https://github.com/sauloprado)

## Mapa de pastas (roteiro)

| Pasta | Foco |
|--------|------|
| `01-cpython-internals/` | PEPs recentes, free-threading, múltiplos interpretadores, t-strings |
| `02-high-performance-data/` | Pandas 3.x, Polars (lazy), RAPIDS cuDF onde fizer sentido |
| `03-ai-agents-and-workflows/` | Agentes, ingestão de documentos, workflows resilientes |
| `04-modern-gui-saas/` | NiceGUI, Streamlit, PySide6 / QML |
| `flashcards/` | Cartões para memorização (Markdown + TSV para Anki) |

## Como usar os flashcards

- Estudo direto: abra `flashcards/python-especialista-2026.md`.
- Anki: importe `flashcards/anki-import.tsv` (separador: tabulação), tipo “Básico”.

## Referências oficiais úteis

- [PEP 703](https://peps.python.org/pep-0703/) — GIL opcional / free-threading (base conceitual)
- [PEP 779](https://peps.python.org/pep-0779/) — critérios de suporte ao build free-threaded
- [PEP 734](https://peps.python.org/pep-0734/) — múltiplos interpretadores → `concurrent.interpreters`
- [PEP 750](https://peps.python.org/pep-0750/) — template strings (`t"..."`)

---

*Estrutura inicial gerada para evolução incremental: cada pasta pode ganhar `notebooks/`, `src/` e `README` próprio conforme você for implementando.*
