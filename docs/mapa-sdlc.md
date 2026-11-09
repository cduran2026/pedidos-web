# Mapa de uso de IA en el SDLC · Pedidos Web

**Autor:** [Carlos Duran]  
**Fecha:** 09-11-2026  
**Proyecto:** Pedidos Web — Unidad 1,  
**Entorno:** Visual Studio Code, Claude Code, .NET 10, C# y xUnit.

## Objetivo

Identificar qué actividades del ciclo de desarrollo de software pueden apoyarse con Claude Code, qué evidencia debe conservarse en Git y qué decisiones requieren revisión humana. Como ejercicio se utiliza la función `FormatearFolio()`, que debe mantener la compatibilidad de los folios de pedidos con el sistema legado.

## Mapa por etapa

| Etapa | Se delega a Claude | Artefacto versionado | Revisa una persona | Riesgo | Evento Scrum |
|---|---|---|---|---|---|
| **Requisitos** | Analizar las reglas R1–R5 de `FormatearFolio()` y proponer una historia de usuario, criterios de aceptación y casos límite, sin inventar reglas. | `docs/requisitos-folios.md` (propuesto). | Product Owner o referente funcional confirma que la numeración y los códigos de sucursal sean compatibles con el sistema legado. | Omitir excepciones o suponer reglas de negocio inexistentes. | **Sprint Planning**, con requisitos preparados previamente. |
| **Diseño** | Proponer una implementación simple en C#, orden de validaciones y estructura de pruebas antes de escribir código. | `docs/diseno-folios.md` (propuesto). | Desarrollador responsable aprueba la solución y verifica que respete `AGENTS.md`. | Sobrediseñar una función sencilla o cambiar el comportamiento heredado. | **Sprint Planning**. |
| **Código** | Implementar `FormatearFolio()` en el archivo indicado, luego de presentar un plan y recibir aprobación. | `src/PedidosWeb.Core/Folios/FolioFormatter.cs`. | Desarrollador lee el diff, comprueba la validación prioritaria de `numero` y autoriza los cambios. | Código convincente pero incorrecto; incumplir R3 o R5. | **Durante el Sprint**, con seguimiento en el **Daily Scrum**. |
| **Pruebas** | Proponer y escribir pruebas xUnit para casos correctos, extremos, sucursales inválidas y prioridad de excepciones; ejecutar `dotnet test`. | `tests/PedidosWeb.Core.Tests/Folios/FolioFormatterTests.cs`. | Desarrollador comprueba que cada regla R1–R5 tenga cobertura y que las pruebas realmente verifiquen el resultado esperado. | Tests que no cubran todos los casos o que validen una interpretación incorrecta. | **Durante el Sprint**, con seguimiento en el **Daily Scrum**. |
| **Revisión y despliegue** | Revisar el diff, resumir resultados de compilación y pruebas, y preparar una lista de verificación. No ejecutar commit, push, merge ni despliegue. | `docs/checklist-liberacion.md` (propuesto) y cambios aprobados en Git. | Responsable técnico revisa código, evidencias y riesgos; una persona decide y ejecuta el versionamiento y la liberación. | Regresiones, despliegues sin aprobación o validaciones omitidas. | **Sprint Review** para mostrar el incremento y recoger comentarios; la aprobación de despliegue es un control técnico separado. |
| **Mejora continua** | Comparar tiempo, errores y correcciones de la ronda manual frente a la asistida; proponer ajustes al uso de IA. | `docs/mapa-sdlc.md` y, si se acuerda, `docs/mejoras-sdlc.md`. | Equipo analiza la evidencia y acuerda mejoras concretas para el próximo Sprint. | Confundir rapidez con calidad o generar dependencia de la IA sin revisar sus resultados. | **Sprint Retrospective**. |

> **Criterio de control:** Claude propone y ejecuta tareas acotadas; una persona valida los requisitos, aprueba los cambios, revisa el diff y realiza el commit y push. Los documentos marcados como «propuesto» no existen necesariamente en el repositorio actual.

## Evidencia del paso 3

| Evidencia | Sin IA (ronda A) | Con Claude Code (ronda B) |
|---|---|---|
| **Tiempo (min)** | Pendiente de medir. | Pendiente de medir. |
| **Errores encontrados** | Pendiente de registrar durante la implementación y las pruebas. | Pendiente de registrar durante la implementación y las pruebas. |
| **Qué tuve que corregir** | Pendiente de registrar. | Pendiente de registrar, incluidas las sugerencias de Claude que requirieron ajustes. |

**Estado inicial del ejercicio:** `dotnet build` compila y los tres tests base de `FolioFormatterTests` fallan con `NotImplementedException`, porque `FormatearFolio()` está sin implementar. Este resultado es esperado y **no** corresponde a una comparación de las rondas A y B.

## Reflexión preliminar

El uso de Claude Code puede acelerar tareas de análisis, implementación, documentación y pruebas, pero no reemplaza el conocimiento del negocio ni la revisión técnica. En este proyecto, la compatibilidad con el sistema legado, la cobertura de las reglas R1–R5 y la aprobación humana son esenciales. La comparación de ambas rondas permitirá evaluar la ayuda de la IA con evidencia, no solo con percepciones.
