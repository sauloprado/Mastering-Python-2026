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

## Publicar no GitHub (2 passos)

1. **Criar o repositório vazio** em [github.com/new](https://github.com/new) com o nome `Mastering-Python-2026` (sem README/licença gerados pelo site, para evitar conflito).
2. **Enviar este diretório** (já com `git init` e commit local):

```powershell
cd "c:\Users\saulo\OneDrive\Documentos\01 - Pessoal\03 Estudo e Carreira\Cursos\DIO\Gen IA e Dados\Mastering-Python-2026"
git branch -M main
git remote add origin https://github.com/sauloprado/Mastering-Python-2026.git
git push -u origin main
```

*(Se o GitHub CLI [`gh`](https://cli.github.com/) estiver instalado e autenticado, você pode usar `gh repo create` no lugar do passo 1.)*

Identidade Git **deste repo** já está em `user.name` / `user.email` local (formato `users.noreply.github.com`). Ajuste com `git config user.name` / `user.email` se quiser outro e-mail.

## Como usar os flashcards

- Geral: `flashcards/python-especialista-2026.md` + `flashcards/anki-import.tsv`
- **Pandas / Polars / cuDF:** `flashcards/pandas-polars-cudf.md` + `flashcards/anki-pandas-polars.tsv`
- Anki: importar TSV com separador **tabulação**, tipo de nota “Básico” (frente / verso).
- Roteiro de estudo dados: `02-high-performance-data/README.md`

## Referências oficiais úteis

- [PEP 703](https://peps.python.org/pep-0703/) — GIL opcional / free-threading (base conceitual)
- [PEP 779](https://peps.python.org/pep-0779/) — critérios de suporte ao build free-threaded
- [PEP 734](https://peps.python.org/pep-0734/) — múltiplos interpretadores → `concurrent.interpreters`
- [PEP 750](https://peps.python.org/pep-0750/) — template strings (`t"..."`)

---

*Estrutura inicial gerada para evolução incremental: cada pasta pode ganhar `notebooks/`, `src/` e `README` próprio conforme você for implementando.*
