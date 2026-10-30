# QA Mainframe Testing Lab

## Descripción del proyecto

QA Mainframe Testing Lab es un proyecto personal orientado al diseño, desarrollo y documentación de un laboratorio de Quality Assurance (QA) para entornos Mainframe.

El objetivo es construir un entorno práctico de aprendizaje que permita diseñar, implementar y documentar diferentes tipos de pruebas sobre componentes y procesos Mainframe, utilizando datos completamente ficticios.

El laboratorio contempla tecnologías como COBOL Batch, CICS, JCL y DB2, incorporando progresivamente técnicas de testing manual, automatización con Python y Pytest, y herramientas de Inteligencia Artificial aplicadas al proceso de QA.

## Objetivos del proyecto

Los principales objetivos de QA Mainframe Testing Lab son:

- Diseñar y documentar casos de prueba para aplicaciones y procesos Mainframe.
- Aplicar técnicas de testing unitario, validación, funcional, integración y regresión.
- Desarrollar escenarios de prueba para componentes COBOL Batch, CICS, JCL y DB2.
- Incorporar progresivamente Python y Pytest para automatizar pruebas y validaciones.
- Construir herramientas de apoyo para la ejecución, análisis y generación de evidencias de testing.
- Explorar el uso de Inteligencia Artificial para asistir en el diseño de pruebas, análisis de defectos y documentación técnica.
- Aplicar buenas prácticas de desarrollo, control de versiones y documentación mediante Git y GitHub.

## Alcance del laboratorio

El laboratorio estará orientado al diseño, desarrollo y documentación de escenarios de prueba sobre los siguientes componentes del entorno Mainframe:

### Tecnologías Mainframe

- COBOL Batch: validación de procesos batch, reglas de negocio, procesamiento de archivos secuenciales y controles de registros.
- CICS: diseño de escenarios funcionales para transacciones, validación de entradas y respuestas de aplicaciones online.
- JCL: validación de jobs, parámetros de ejecución, datasets, condiciones de procesamiento y manejo de errores.
- DB2: validación de consultas SQL, integridad de datos, operaciones CRUD y consistencia de información.

### Tipos de testing

- Testing unitario: verificación de unidades individuales de procesamiento y reglas de negocio.
- Testing de validación: comprobación de formatos, campos obligatorios, rangos y condiciones de entrada.
- Testing funcional: verificación del comportamiento esperado de los procesos y aplicaciones.
- Testing de integración: validación de la interacción entre programas, archivos, jobs y bases de datos.
- Testing de regresión: comprobación de que los cambios no afecten funcionalidades previamente verificadas.

## Arquitectura del repositorio

El proyecto utiliza una estructura modular para separar los componentes Mainframe, los casos de prueba, las herramientas de automatización y las funcionalidades de asistencia basadas en Inteligencia Artificial.

```text
qa-mainframe-testing-lab/
│
├── documentation/
│  └── Documentación general del proyecto
│
├── mainframe/
│  ├── cobol/
│  ├── cics/
│  ├── jcl/
│  └── db2/
│
├── test-cases/
│  ├── unit/
│  ├── validation/
│  ├── functional/
│  ├── integration/
│  └── regression/
│
├── automation/
│  ├── python/
│  ├── pytest/
│  ├── test-data/
│  └── reports/
│
├── ai-qa-assistant/
│  ├── prompts/
│  ├── tutorials/
│  ├── examples/
│  └── guidelines/
│
├── ai-qa-application/
│  ├── app/
│  ├── services/
│  └── tests/
│
└── .github/
  └── workflows/
```

### Responsabilidad de los directorios

- `documentation`: documentación funcional y técnica del laboratorio.
- `mainframe`: ejemplos y componentes relacionados con las tecnologías Mainframe.
- `test-cases`: diseño y documentación de los diferentes tipos de pruebas.
- `automation`: scripts, pruebas automatizadas, datos ficticios e informes.
- `ai-qa-assistant`: biblioteca de prompts, tutoriales y guías para utilizar IA en actividades de QA.
- `ai-qa-application`: futura aplicación propia de asistencia de QA basada en IA.
- `.github/workflows`: futuras automatizaciones de integración y ejecución mediante GitHub Actions.

## Tecnologías y herramientas

El laboratorio incorporará progresivamente las siguientes tecnologías y herramientas:

### Entorno Mainframe

- COBOL: lenguaje utilizado para desarrollar y analizar programas Mainframe.
- CICS: entorno de procesamiento de transacciones online.
- JCL: lenguaje de control de trabajos batch.
- DB2: sistema de gestión de bases de datos relacionales.

### Testing y automatización

- Python: desarrollo de scripts y herramientas de automatización.
- Pytest: framework para implementar y ejecutar pruebas automatizadas.
- CSV, JSON y YAML: formatos para organizar datos y configuraciones de prueba.

### Control de versiones y CI/CD

- Git: control de versiones del proyecto.
- GitHub: alojamiento y gestión del repositorio.
- GitHub Actions: automatización futura de validaciones y pruebas mediante workflows.

### Inteligencia Artificial

- OpenAI API: integración futura de capacidades de IA para asistir en actividades de QA.
- Streamlit o FastAPI: alternativas previstas para desarrollar una aplicación propia de asistencia de testing.

## Asistente de QA basado en Inteligencia Artificial

El proyecto contempla la incorporación progresiva de herramientas de Inteligencia Artificial para asistir en diferentes actividades del proceso de Quality Assurance.

La solución estará organizada en dos componentes:

### AI QA Assistant

Biblioteca de prompts, ejemplos y guías orientadas a utilizar Inteligencia Artificial como apoyo para:

- Generar y mejorar casos de prueba.
- Diseñar escenarios positivos, negativos y de valores límite.
- Aprender Python y Pytest aplicados a testing.
- Generar y explicar scripts de automatización.
- Analizar defectos y posibles causas.
- Comparar resultados esperados y obtenidos.
- Proponer escenarios de regresión.
- Generar documentación e informes de testing.

### AI QA Application

Desarrollo futuro de una aplicación propia conectada a OpenAI API, destinada a centralizar funcionalidades de asistencia para actividades de QA.

La aplicación podrá incorporar progresivamente:

- Generación asistida de casos de prueba.
- Análisis de resultados de ejecución.
- Asistencia en la identificación y documentación de defectos.
- Generación de scripts de automatización.
- Elaboración de informes de testing.
- Sugerencias de pruebas de regresión.

### Uso responsable de Inteligencia Artificial

Las respuestas y los scripts generados mediante IA serán considerados propuestas que deberán ser revisadas por una persona antes de utilizarse.

La Inteligencia Artificial no reemplazará la ejecución real de las pruebas ni la validación de sus resultados.

Todas las simulaciones deberán identificarse claramente y no se presentarán como ejecuciones reales.

## Metodología de trabajo y testing

El laboratorio seguirá una metodología progresiva de diseño, ejecución, análisis y documentación de pruebas.

### Diseño de casos de prueba

Cada caso de prueba deberá incluir:

- ID del caso de prueba.
- Objetivo.
- Precondiciones.
- Datos de entrada.
- Pasos de ejecución.
- Resultado esperado.
- Resultado obtenido.
- Estado de ejecución.
- Evidencias.

### Diseño de escenarios

Se contemplarán diferentes tipos de escenarios:

- Positivos: validación del comportamiento esperado con datos correctos.
- Negativos: comprobación del comportamiento ante datos inválidos o condiciones de error.
- Límites: validación de valores mínimos, máximos y condiciones especiales.
- Errores: análisis del comportamiento ante fallos de procesamiento o inconsistencias.
- Regresión: verificación de funcionalidades previamente probadas después de realizar cambios.

### Registro de resultados

Los resultados de las pruebas se clasificarán de la siguiente manera:

- Diseñado: caso de prueba documentado, pendiente de ejecución.
- Simulado: escenario o resultado representado mediante una simulación.
- Ejecutado: prueba realizada realmente y respaldada por evidencias.

Los defectos identificados se documentarán indicando su descripción, pasos para reproducirlos, resultado esperado, resultado obtenido, severidad, prioridad y evidencias disponibles.

## Roadmap del proyecto

El desarrollo del laboratorio se realizará de manera progresiva, incorporando nuevas funcionalidades y tecnologías en diferentes etapas.

| Etapa | Descripción | Estado |
|---|---|---|
| 0 | Preparación del entorno y estructura del repositorio | En progreso |
| 1 | Fundamentos de Mainframe QA y diseño de casos de prueba | Pendiente |
| 2 | Introducción a Python y Pytest para testing | Pendiente |
| 3 | Desarrollo de pruebas automatizadas para el laboratorio | Pendiente |
| 4 | Construcción del asistente de QA mediante prompts y documentación | Pendiente |
| 5 | Desarrollo de la aplicación de QA integrada con OpenAI API | Pendiente |
| 6 | Integración continua y automatización mediante GitHub Actions | Pendiente |

Las etapas se desarrollarán progresivamente, documentando los avances y verificando cada funcionalidad antes de considerarla completada.

## Estado actual del proyecto

El proyecto se encuentra en su etapa inicial de preparación y organización.

### Actividades completadas

- Creación del repositorio público en GitHub.
- Configuración del entorno local de desarrollo.
- Creación de la estructura inicial de directorios.
- Elaboración de la primera versión del README principal.

### Actividades pendientes

- Revisar y aprobar la primera versión del README principal.
- Incorporar archivos de configuración iniciales.
- Diseñar los primeros casos de prueba Mainframe.
- Desarrollar ejemplos y escenarios con datos ficticios.
- Implementar progresivamente pruebas automatizadas con Python y Pytest.
- Incorporar las funcionalidades de asistencia basadas en Inteligencia Artificial.

El estado de las actividades se actualizará a medida que se desarrollen, documenten y verifiquen nuevas funcionalidades.

## Seguridad y uso de datos

Este proyecto utiliza exclusivamente información, programas y escenarios ficticios creados con fines educativos y de demostración.

Se aplicarán las siguientes buenas prácticas:

- No utilizar código fuente, datos, archivos o documentación confidencial pertenecientes a empleadores o terceros.
- No publicar información sensible, credenciales, contraseñas, tokens ni claves de API.
- Utilizar variables de entorno para gestionar credenciales y configuraciones privadas.
- No incorporar datos reales de clientes, usuarios o sistemas productivos.
- Revisar manualmente los scripts y contenidos generados mediante Inteligencia Artificial antes de utilizarlos.
- Identificar claramente las pruebas simuladas y diferenciarlas de las ejecuciones reales.

El objetivo es mantener un entorno de aprendizaje seguro, reproducible y adecuado para su publicación como portfolio técnico en GitHub.