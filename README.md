# csm1b-galego-adaptation

Trabajo de Fin de Grado sobre la adaptación de **Sesame CSM-1B al gallego** con datos de voz del **Proxecto Nós**.

El objetivo es evaluar si un modelo de generación de voz condicionado por texto y audio puede adaptarse al gallego mediante fine-tuning eficiente, y estudiar su pronunciación, naturalidad y uso del contexto acústico.

[CSM-1B](https://github.com/SesameAILabs/csm) genera códigos de audio que se reconstruyen mediante el codec Mimi. Permite proporcionar texto y audio de intervenciones previas como contexto para la generación.

## Líneas de trabajo

- Analizar la arquitectura de CSM-1B y la representación de audio de Mimi.
- Preparar corpus gallegos de audio y transcripciones para el entrenamiento.
- Explorar LoRA y comparar el modelo adaptado con el original.
- Evaluar inteligibilidad, pronunciación, naturalidad y efecto del contexto.

## Datos

Los corpus candidatos incluyen [Nos_Celtia-GL](https://huggingface.co/datasets/proxectonos/Nos_Celtia-GL) y [Nos_Brais-GL](https://huggingface.co/datasets/proxectonos/Nos_Brais-GL). La selección y el preprocesado tendrán en cuenta la calidad del audio, la cobertura lingüística y la separación entre entrenamiento y evaluación.

Más información: [corpus del Proxecto Nós](https://github.com/proxectonos/corpora).

## Estado

Proyecto en fase inicial, centrado en la revisión de la arquitectura y la selección de datos. El repositorio se irá completando con scripts de preprocesado, experimentos y resultados.

## Bibliografía

Los artículos de referencia están en [`papers/`](papers/):

- **SoundStream**: codecs neuronales y cuantización vectorial residual (RVQ).
- **EnCodec**: compresión neuronal de audio de alta fidelidad.
- **Moshi**: codec Mimi y generación de voz para diálogo en tiempo real.
- **A review on subjective and objective evaluation of synthetic speech**: evaluación de voz sintética.

## Licencia

El material propio del proyecto se publica bajo [Apache-2.0](LICENSE). Los artículos y otros materiales de terceros conservan sus licencias originales.
