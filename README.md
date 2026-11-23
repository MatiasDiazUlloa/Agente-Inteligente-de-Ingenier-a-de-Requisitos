# Agente Inteligente para Ingeniería de Requisitos

Este proyecto implementa un asistente conversacional que transforma ideas vagas o incompletas de software en especificaciones de requisitos. El agente funciona como puente entre un cliente no técnico y un equipo de desarrollo.

> Estado: prototipo educativo ejecutado principalmente en Google Colaboratory.

## Qué hace

1. Recibe una idea general de una aplicación o sistema.
2. Analiza la solicitud y detecta información ambigua o faltante.
3. Formula entre dos y tres preguntas de negocio.
4. Recupera reglas de arquitectura relevantes desde una base de conocimientos.
5. Genera casos de uso, historias de usuario y requisitos no funcionales medibles.
6. Presenta alternativas arquitectónicas y entrega la respuesta también por voz.

## Métodos utilizados

| Componente | Implementación |
|---|---|
| Modelo generativo | Gemini de Google para conversación y generación de especificaciones |
| Prompt de rol | Consultor senior especializado en elicitación y arquitectura de software |
| Chunking | Documentos divididos por párrafos con solapamiento de 50 tokens |
| Embeddings | Representación vectorial de los fragmentos de conocimiento |
| Base vectorial | ChromaDB en memoria |
| Recuperación | Búsqueda semántica por similitud coseno, Top-K igual a 3 |
| RAG | Se envían al modelo únicamente las reglas recuperadas y la solicitud actual |
| Voz | Conversión de la respuesta a audio con gTTS |

## Tecnologías

- Python
- Google Colaboratory
- Google Gemini
- ChromaDB
- Embeddings de Google
- gTTS
- Google Drive

## Estructura

```text
.
├── README.md
└── Agente_inteligente_(_IA).ipynb
```

## Uso

1. Abrir el cuaderno `.ipynb` en Google Colab.
2. Configurar `GEMINI_API_KEY` en los secretos de Colab.
3. Montar Google Drive.
4. Crear en Drive el archivo:
   `Colab Notebooks/Documentos_AgenteIA/reglas_arquitectura.txt`
5. Ejecutar las celdas en orden.
6. Escribir una idea del sistema cuando el agente solicite el requerimiento.
7. Escribir `salir` para finalizar la conversación.

## Dependencias del cuaderno

```text
google-generativeai
gTTS
chromadb
```

El cuaderno instala estas dependencias automáticamente al inicio.

## Consideraciones

- El prototipo necesita acceso a Google Drive y una clave válida de Gemini.
- ChromaDB se crea en memoria, por lo que el índice se reconstruye al reiniciar Colab.
- El documento `reglas_arquitectura.txt` no está incluido en este repositorio y debe existir en Drive.
- El agente evita inventar información crítica y solicita aclaraciones antes de producir casos de uso.
