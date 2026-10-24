# CSM-1B en galego

Adaptación de [Sesame CSM-1B](https://github.com/SesameAILabs/csm) al gallego con corpus de voz del [Proxecto Nós](https://nos.gal/), como Trabajo de Fin de Grado. Se estudiarán la pronunciación, la naturalidad y el efecto del contexto previo de texto y audio en la voz generada.

**Estado:** preparación de datos. Fine-tuning y evaluación pendientes.

## Contenido

- [Datasets](docs/datasets.md): corpus disponibles, formatos y criterios de preprocesado.
- [Notebooks](notebooks/): cuadernos de trabajo con marimo.
- [Papers](papers/): artículos de referencia sobre codecs de audio y evaluación de voz.

## Entorno

Python 3.11 y [uv](https://docs.astral.sh/uv/). Para trabajar en CPU:

```bash
uv sync --locked --extra cpu
uv run --locked --extra cpu marimo edit
```

En el servidor con GPU NVIDIA:

```bash
uv sync --locked --extra cuda
```

Los comandos `uv run` deben usar el mismo extra que la instalación: `cpu` o `cuda`.

## Licencia

[Apache-2.0](LICENSE) para el material propio. Los artículos y datasets conservan sus condiciones de uso originales.
