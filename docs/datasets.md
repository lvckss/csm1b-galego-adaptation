# Corpus de voz del Proxecto Nós

Última revisión de las fuentes: **24 de octubre de 2026**.

Inventario de datos candidatos para adaptar CSM-1B al gallego. Las duraciones y características proceden de las fichas enlazadas; las horas utilizables se calcularán durante el preprocesado. Las propuestas de uso describen experimentos pendientes, no resultados de entrenamiento.

## Inventario

| Corpus | Horas publicadas | Dominio | Transcripción / alineamiento |
| --- | ---: | --- | --- |
| [Nos_Parlaspeech-GL](https://huggingface.co/datasets/proxectonos/Nos_Parlaspeech-GL) | 1.674,63 | Parlamento | Transcripciones oficiales y alineamiento automático |
| [Nos_Telexornais-GL](https://huggingface.co/datasets/proxectonos/Nos_Telexornais-GL) | 1.172,10 | Informativos | Automáticos, con filtrado y revisión parcial |
| [Nos_RG-Podcast-GL](https://huggingface.co/datasets/proxectonos/Nos_RG-Podcast-GL) | 328 declaradas; 288,156 en la tabla de particiones | Radio y podcasts | Automáticos; test revisado manualmente |
| [Nos_Transcrispeech-GL](https://huggingface.co/datasets/proxectonos/Nos_Transcrispeech-GL) | 49,952 en Hugging Face | Entrevistas, debates, conferencias y discursos | Manuales |
| [Nos_Celtia-GL](https://zenodo.org/records/7716958) | ≈25 | Habla leída, voz femenina | Texto de lectura; grabación en estudio |
| [Nos_Brais-GL](https://zenodo.org/records/14265241) | ≈18 | Habla leída, voz masculina | Texto de lectura; grabación en estudio |
| [Nos_ImosNavegando-GL](https://huggingface.co/datasets/proxectonos/Nos_ImosNavegando-GL) | ≈14 | Entretenimiento televisivo | Texto y alineamiento revisados manualmente |
| [CRPIH_UVigo-GL-Voices](https://zenodo.org/records/8027725) | ≈21 h 1 min originales | Habla leída, cuatro voces | Transcripciones y alineamiento fonético |

Las colecciones oficiales de [ASR](https://huggingface.co/collections/proxectonos/asr-datasets) y [TTS](https://huggingface.co/collections/proxectonos/tts-datasets) permiten consultar sus distribuciones en Hugging Face. Los identificadores de Parlaspeech y Transcrispeech se escriben aquí como aparecen en sus repositorios.

### Cómo interpretar las horas

Los seis primeros corpus suman **3.267,682 h** usando las 328 h nominales de RG-Podcast. Es una suma de cifras publicadas, que incluye evaluación y requiere resolver la discrepancia de ese corpus. ImosNavegando y CRPIH amplían ese inventario.

El recuento final debe distinguir audio publicado, audio descargado, audio único, audio aceptado tras filtrado y horas de cada partición. Las versiones de un mismo corpus, las distintas frecuencias de muestreo y las variantes de edición no se contabilizarán como grabaciones nuevas.

## Distribuciones y frecuencia de muestreo

CSM-1B espera audio a **24 kHz**, según su [documentación de entrada](https://huggingface.co/docs/transformers/model_doc/csm#with-conversational-context). La tabla distingue las distribuciones de cada corpus: que Zenodo contenga originales de mayor frecuencia no implica que Hugging Face los conserve, ni que todos los corpus de Zenodo superen los 16 kHz.

Las frecuencias se han contrastado con las fichas oficiales y los metadatos disponibles, sin descargar corpus completos. Salvo indicación expresa, son valores documentados por el proveedor, no el resultado de auditar todas las cabeceras de audio. **No verificado** indica que no se ha podido establecer el dato; no significa que el recurso no exista.

| Corpus | Hugging Face: distribución y frecuencia | Zenodo: distribución y frecuencia | Observaciones |
| --- | --- | --- | --- |
| Nos_Parlaspeech-GL | [HF](https://huggingface.co/datasets/proxectonos/Nos_Parlaspeech-GL): **No verificado** | [Zenodo 7913218](https://zenodo.org/records/7913218): **16 kHz**, WAV de 16 bits | Zenodo declara 16 kHz para los archivos distribuidos; no documenta aquí la frecuencia de las grabaciones fuente del Parlamento. La ficha HF no especifica la frecuencia: no trasladar automáticamente el dato de Zenodo. |
| Nos_Telexornais-GL | [HF](https://huggingface.co/datasets/proxectonos/Nos_Telexornais-GL): **No verificado** | **No verificado**: publicación anunciada como «Proximamente» en el catálogo oficial | No se ha confirmado un registro de Zenodo del mismo corpus. Tampoco se ha verificado la frecuencia original de CRTVG ni la de los archivos HF. |
| Nos_RG-Podcast-GL | [HF](https://huggingface.co/datasets/proxectonos/Nos_RG-Podcast-GL): **No verificado** | **No verificado**: publicación anunciada como «Proximamente» en el catálogo oficial | No se ha confirmado un registro de Zenodo del mismo corpus. No asumir una frecuencia uniforme entre programas sin inspeccionar archivos o manifiestos. |
| Nos_Transcrispeech-GL | [HF](https://huggingface.co/datasets/proxectonos/Nos_Transcrispeech-GL): **16 kHz declarados en los metadatos**; frecuencia de los archivos: **No verificado** | [Zenodo 7717140](https://zenodo.org/records/7717140): **44,1 kHz**, WAV de 16 bits | Zenodo conserva audio sin segmentar y anotaciones lingüísticas; HF ofrece segmentos para ASR. La configuración de decodificación HF se distingue de la frecuencia de los bytes almacenados; véase la comprobación de metadatos debajo. |
| Nos_Celtia-GL | [HF](https://huggingface.co/datasets/proxectonos/Nos_Celtia-GL): **16 kHz**, WAV de 16 bits | [Zenodo 7716958](https://zenodo.org/records/7716958): **48 kHz**, WAV de 16 bits | Zenodo declara el formato de grabación original y audio `raw`; HF distribuye audio con volumen normalizado (`norm`) a menor frecuencia. Para preparar 24 kHz, priorizar Zenodo. |
| Nos_Brais-GL | [HF](https://huggingface.co/datasets/proxectonos/Nos_Brais-GL): **16 kHz**, WAV de 16 bits | [Zenodo 14265241](https://zenodo.org/records/14265241): **48 kHz**, WAV de 24 bits | Zenodo declara el formato de grabación original y variantes `raw`, `edit` y `norm`; HF publica la variante normalizada a menor frecuencia y profundidad de bits. |
| Nos_ImosNavegando-GL | [HF](https://huggingface.co/datasets/proxectonos/Nos_ImosNavegando-GL): **No verificado** | **No verificado**: sin registro oficial confirmado | La ficha HF no especifica la frecuencia de los archivos ni la de las grabaciones fuente. No se ha encontrado una segunda distribución confirmada del mismo corpus. |
| CRPIH_UVigo-GL-Voices | [HF, versión extendida](https://huggingface.co/datasets/proxectonos/CRPIH_UVigo-GL-Voices_extended): **16 kHz**, PCM de 16 bits | [Zenodo 8027725](https://zenodo.org/records/8027725): **16 / 44 / 48 / 96 kHz**, según voz y variante | La ficha de Zenodo declara varias frecuencias; se detallan por voz más abajo. «44 kHz» es el valor publicado para Sabela: su valor exacto en cabecera es **No verificado**. HF incluye una extensión con audio sintético, no una copia idéntica del original. |

### Alcance de la verificación

- **Transcrispeech en HF:** el [README de la revisión `cc5f53eb4cfc691237cccd71ff53b668a243c80e`](https://huggingface.co/datasets/proxectonos/Nos_Transcrispeech-GL/blob/cc5f53eb4cfc691237cccd71ff53b668a243c80e/README.md), consultado en la copia local de la caché de Hugging Face, declara `dataset_info.features.audio.dtype.audio.sampling_rate: 16000` (**16 kHz**). Esto verifica la configuración declarada. La [documentación de Datasets](https://huggingface.co/docs/datasets/audio_process#cast) explica que `Audio(sampling_rate=...)` puede remuestrear al decodificar: el dato del esquema no demuestra por sí solo la frecuencia de los archivos almacenados. Para verificarla, leer la cabecera de los bytes o rutas obtenidos con `decode(False)`, sin remuestrear, y registrar revisión, partición y archivo inspeccionado.
- **Zenodo pendiente:** el [catálogo oficial de corpus de Nós](https://github.com/proxectonos/corpora#reco%C3%B1ecemento-da-fala-asr) anuncia Telexornais y RG-Podcast como «Proximamente». Las búsquedas por los nombres del corpus y la revisión de sus fichas HF no han permitido confirmar registros adicionales para esos dos corpus ni para ImosNavegando. No se enlazan resultados que solo mencionan el corpus, como artículos o presentaciones.
- **Variantes confirmadas:** las fichas enlazadas identifican las parejas HF/Zenodo de Parlaspeech, Transcrispeech, Celtia y Brais. La ficha HF de CRPIH remite al original de Zenodo y documenta su extensión. No se ha confirmado otra distribución oficial del original de CRPIH en HF ni otros registros de Zenodo de los corpus revisados. Las variantes de edición y frecuencia ya documentadas no son nuevos corpus.

### Elección de fuente para CSM-1B

- **Fuentes documentadas con al menos 24 kHz:** Transcrispeech en Zenodo (**44,1 kHz**), Celtia y Brais en Zenodo (**48 kHz**) y las variantes de mayor frecuencia de Iago, Icía y Sabela en CRPIH/Zenodo (**48, 96 y 44 kHz**, respectivamente; pendiente precisar Sabela mediante cabecera). Se remuestrearán a **24 kHz**. La frecuencia publicada no demuestra por sí sola que no haya habido remuestreo previo; Celtia y Brais sí identifican explícitamente su formato original de grabación.
- **Fuentes documentadas a 16 kHz:** Parlaspeech en Zenodo, Celtia y Brais en HF, CRPIH extendido en HF y las variantes de 16 kHz de todas las voces de CRPIH en Zenodo, incluida la única documentada para Paulo. Requieren remuestreo a **24 kHz**, sin recuperar el contenido perdido al reducir la frecuencia. Para Celtia, Brais y las voces con alternativa de CRPIH, se dispone de una distribución de mayor frecuencia.
- **Pendientes:** archivos HF de Parlaspeech, Telexornais, RG-Podcast e ImosNavegando; cabeceras de los archivos HF de Transcrispeech, aunque su configuración declara **16 kHz**; frecuencia exacta de la variante alta de Sabela. Los posibles originales de mayor frecuencia de Parlaspeech, Telexornais, RG-Podcast e ImosNavegando siguen siendo **No verificado**.

## Fichas de los corpus

### Nos_Parlaspeech-GL

Fuentes: [Hugging Face](https://huggingface.co/datasets/proxectonos/Nos_Parlaspeech-GL) · [Zenodo](https://zenodo.org/records/7913218).

- **Contenido:** sesiones parlamentarias de 2015–2022; `clean` suma 1.196,92 h y `other`, 477,71 h.
- **Metadatos:** la distribución HF documenta `path`, `sentence` y `speaker_id`, además de información del hablante. Sus particiones separan hablantes; `clean-test` recibió revisión manual dentro de ALIA 2026.
- **Formato:** [Zenodo](https://zenodo.org/records/7913218) y el [catálogo de Nós](https://github.com/proxectonos/corpora#nos_parlaspeech-gl) describen WAV a 16 kHz y 16 bits, y anotaciones STM/JSON. Ese dato corresponde a la distribución de Zenodo; la frecuencia de la distribución HF y la de las grabaciones fuente del Parlamento son **No verificado**.
- **Uso propuesto:** estudiar adaptación con volumen y múltiples hablantes, empezando por `clean`. Comprobar correspondencia texto/audio e identificación de hablantes; la propia ficha señala posibles errores heredados de las transcripciones originales.

### Nos_Telexornais-GL

Fuente: [Hugging Face](https://huggingface.co/datasets/proxectonos/Nos_Telexornais-GL).

- **Contenido:** informativos de la CRTVG de 2019–2022; 662,17 h en `clean` y 509,93 h en `other`.
- **Texto:** generado con Chirp2. El filtrado compara sus transcripciones con Whisper-large-v3-gl; el umbral entre modelos no constituye una medición contra transcripción humana.
- **Metadatos:** `filename`, `audio` y `sentence`. Comprobar si existe información adicional de hablantes y grabaciones originales antes de construir contexto.
- **Uso propuesto:** ampliar cobertura lingüística y voces. Revisar duración, música, cambios de locutor y correspondencia textual. La ficha advierte de segmentos muy largos y muy cortos en `other`. Frecuencia y canales de los archivos descargados: pendientes de inspección.

### Nos_RG-Podcast-GL

Fuente: [Hugging Face](https://huggingface.co/datasets/proxectonos/Nos_RG-Podcast-GL).

- **Contenido:** 33 series de radio/podcasts de distintos géneros, con transcripción y alineamiento automáticos.
- **Discrepancia de duración:** la descripción declara 328 h; la tabla publica `train=259,078`, `dev=14,541` y `test=14,537` h, cuya suma es **288,156 h**. Falta contrastar ambas cifras con el manifiesto y los audios.
- **Evaluación:** la ficha documenta revisión manual del test en ALIA 2026.
- **Uso propuesto:** estudiar registros y estilos variados. Verificar hablantes, cronología y relación entre segmentos antes de tratarlos como conversaciones. Frecuencia y canales: pendientes de inspección.

### Nos_Transcrispeech-GL

Fuentes: [Hugging Face](https://huggingface.co/datasets/proxectonos/Nos_Transcrispeech-GL) · [original en Zenodo](https://zenodo.org/records/7717140).

- **HF:** 40,680 h de entrenamiento, 4,771 h de desarrollo y 4,501 h de test; total de 49,952 h. Ofrece segmentos WAV y metadatos TSV, con particiones separadas por hablante. El test recibió revisión adicional en ALIA 2026.
- **Frecuencia HF:** 16 kHz declarados en los metadatos de la revisión indicada en la tabla; frecuencia de los archivos almacenados: **No verificado**. No confundir el remuestreo durante la decodificación con el formato de distribución.
- **Zenodo:** describe 53 h de audio sin segmentar, WAV a 44,1 kHz y 16 bits, transcripciones STM/TRS y metadatos de hablantes. Conserva anotaciones de turnos, risas, pausas, solapamientos e interrupciones que se omiten en la distribución HF preparada para ASR.
- **Uso propuesto:** inspeccionar los originales y sus anotaciones para reconstruir contexto conversacional. Las dos distribuciones comparten material: no sumar 53 y 49,952 h. La diferencia de duración no tiene una explicación verificada en este inventario.

### Nos_Celtia-GL

Fuentes: [Zenodo](https://zenodo.org/records/7716958) · [Hugging Face](https://huggingface.co/datasets/proxectonos/Nos_Celtia-GL).

- **Contenido:** unas 25 h y 20.000 frases leídas por una locutora profesional en estudio.
- **Originales:** WAV a 48 kHz y 16 bits, sin edición ni normalización. `metadata.csv` utiliza `|` como separador y relaciona archivo y texto UTF-8 sin normalizar.
- **HF:** su ficha declara WAV a 16 kHz y 16 bits, con volumen normalizado. Esta distribución tiene menor frecuencia que el original de Zenodo; no son formatos intercambiables al elegir la fuente para preparar audio a 24 kHz.
- **Uso propuesto:** validar un primer pipeline y un experimento controlado de voz y pronunciación. El habla leída limita las conclusiones sobre interacción conversacional. Parte del material textual se comparte con otros corpus TTS; controlar el solapamiento entre particiones también por texto.

### Nos_Brais-GL

Fuentes: [Zenodo](https://zenodo.org/records/14265241) · [Hugging Face](https://huggingface.co/datasets/proxectonos/Nos_Brais-GL).

- **Contenido:** unas 18 h y 16.121 frases, grabadas por un locutor profesional en estudio.
- **Originales:** WAV a 48 kHz y 24 bits, con variantes `raw`, `edit` y `norm`. Sus CSV, separados por `|`, relacionan audio y texto normalizado UTF-8. Son variantes de las mismas grabaciones.
- **HF:** su ficha declara únicamente audio normalizado, WAV a 16 kHz y 16 bits. Para conservar la frecuencia y profundidad de bits del original, utilizar la distribución de Zenodo.
- **Uso propuesto:** incorporar una segunda voz o repetir el piloto monolocutor. Hay textos compartidos con Celtia; mantenerlos juntos al asignar particiones si se quiere evaluar con frases nuevas.

### Nos_ImosNavegando-GL

Fuente: [Hugging Face](https://huggingface.co/datasets/proxectonos/Nos_ImosNavegando-GL).

- **Contenido:** unas 14 h de entretenimiento televisivo, con habla espontánea o semiespontánea y cambios de hablante. La ficha cita el recurso como publicación de 2026.
- **Revisión:** lingüistas revisaron texto y alineamiento en ELAN; el material de partida combinaba 10 h con subtítulos humanos y 4 h con transcripción automática.
- **Uso propuesto:** estudiar contexto y variación prosódica. Inspeccionar música, ruido y edición televisiva, y confirmar que los metadatos permiten recuperar hablantes y continuidad. La ficha describe utilidad para ASR, no una validación para entrenar CSM. Frecuencia y canales: pendientes de inspección.

### CRPIH_UVigo-GL-Voices

Fuentes: [original en Zenodo](https://zenodo.org/records/8027725) · [extensión en Hugging Face](https://huggingface.co/datasets/proxectonos/CRPIH_UVigo-GL-Voices_extended).

| Voz original | Duración aproximada | Frecuencias publicadas en Zenodo |
| --- | ---: | --- |
| Iago | 1 h 13 min | 16 / 48 kHz |
| Icía | 4 h 5 min | 16 / 96 kHz |
| Paulo | 1 h 15 min | 16 kHz |
| Sabela | 14 h 28 min | 16 / 44 kHz, según la ficha; valor exacto de la variante alta en cabecera: **No verificado** |

Los originales incluyen textos ISO-8859-1 y alineamiento fonético. La distribución HF describe audio a 16 kHz y 16 bits. Su extensión incorpora audio **sintetizado** para añadir o modificar frases de Iago y Paulo; identificarlo y contabilizarlo por separado. Las versiones original y extendida comparten grabaciones.

La [ficha de Zenodo](https://zenodo.org/records/8027725) organiza el audio en carpetas `wav_[bit depth]bits_[sampling rate]kHz`. Para Iago e Icía existen alternativas de mayor frecuencia a los 16 kHz; para Paulo solo se documentan 16 kHz. No sustituir los 44 kHz publicados para Sabela por 44,1 kHz sin comprobar el archivo, ni sumar las variantes de frecuencia como horas adicionales.

**Uso propuesto:** ampliar hablantes de habla leída. Evitar duplicar el mismo audio por frecuencia o versión y revisar solapamientos textuales con Celtia/Brais.

## Criterios de preparación para CSM

Propuesta de trabajo, pendiente de validar con los archivos y la implementación elegida:

1. Registrar fuente, revisión o versión, variante, partición y checksum; conservar los originales.
2. Inventariar duración, frecuencia, canales, corrupción, clipping y correspondencia entre audio y texto.
3. Priorizar las distribuciones verificadas de al menos **24 kHz** y generar una copia mono a **24 kHz**, conforme a la [entrada documentada de CSM](https://huggingface.co/docs/transformers/model_doc/csm). Remuestrear desde 16 kHz permite cumplir el formato, pero no recupera contenido perdido. Comprobar la frecuencia del archivo antes de cualquier transformación; la frecuencia configurada en un decodificador no sustituye esa comprobación.
4. Conservar texto original y texto transformado, documentando reglas lingüísticas y etiquetas de oralidad. Una normalización preparada para ASR puede eliminar puntuación útil para síntesis.
5. Respetar las particiones de evaluación y comprobar duplicados por texto, audio y grabación de origen. Construir cada contexto íntegramente dentro de una misma partición.
6. Mantener identificador de grabación, hablante y tiempos cuando estén disponibles. La proximidad entre filas de un dataset no demuestra continuidad conversacional.
7. Calcular horas aceptadas y descartadas por corpus, variante, hablante y partición antes de elegir la mezcla de entrenamiento.

Los corpus ASR son candidatos si el audio, el texto y la segmentación resultan adecuados. `clean` indica el filtrado descrito por cada autor; su calidad para síntesis debe comprobarse. Los pilotos con TTS de estudio y las pruebas con contexto conversacional responden a preguntas distintas.

## Acceso y reutilización

Las fuentes enlazadas contienen las condiciones aplicables a cada distribución. Celtia, Brais y varias distribuciones ASR requieren aceptar condiciones o solicitar acceso. Las fichas de Telexornais, RG-Podcast e ImosNavegando restringen la difusión pública de las grabaciones. RG-Podcast identifica su licencia como `other`; varias de las demás fichas muestran CC BY 4.0 junto con condiciones específicas de acceso.

La licencia del código de este repositorio no sustituye las condiciones de los corpus. El inventario documenta fuentes y transformaciones; la publicación de audio se regirá por las condiciones de su distribución.
