# github_actions_demo

![CI](https://github.com/R4C3RS3TH/github_actions_demo/actions/workflows/devops.yml/badge.svg)
![Release](https://img.shields.io/github/v/release/R4C3RS3TH/github_actions_demo)

Laboratorio de CI/CD con GitHub Actions y Python — UTEC.

🌐 **Página desplegada:** https://r4c3rs3th.github.io/github_actions_demo/

## Pipeline

| Workflow | Disparador | Jobs |
|---|---|---|
| `devops.yml` | push a `main` y pull requests | `test` → `package` → `docs` / `deploy` |
| `release.yml` | tags `v*` | `release` |

- **test**: pytest con gate de cobertura ≥ 80%, reporte JUnit y job summary.
- **package**: empaqueta `hello.py` en un ZIP con el build tag.
- **docs**: imprime información del runner.
- **deploy**: publica `site/index.html` en GitHub Pages (requiere aprobación manual).

## Ejecutar en local

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
PYTHONPATH=. pytest -q --cov=hello --cov-report=term-missing
```

## Publicar una versión

```bash
git tag -a v1.0.0 -m "Primera versión estable"
git push origin v1.0.0
```
