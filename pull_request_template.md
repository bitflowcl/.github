<!-- Título: tipo(ámbito): qué cambia para quien usa el sistema [BIT-nnn]
     Convenciones: https://github.com/bitflowcl/.github/blob/main/CONTRIBUTING.md
     Quien llena esto (persona o agente) reemplaza cada comentario.
     Si una sección no aplica, escribe "Ninguna." -->

BIT-nnn <!-- o "Closes #nnn" si el issue es de GitHub -->

## Por qué

<!-- Una frase: qué problema tenía quién. -->

## Qué cambia

<!-- Diagrama: si el PR cambia un flujo (por dónde pasa una acción o un dato,
     qué estados recorre un registro, o cómo se llaman tres o más piezas),
     abre esta sección con un diagrama Mermaid:
     - flowchart para un proceso o una decisión;
     - sequenceDiagram para llamadas entre piezas (controlador, job, API externa);
     - stateDiagram-v2 para los estados de un registro.
     Muestra solo la parte del flujo que toca el PR, hasta ~15 nodos. Marca lo
     nuevo con `:::nuevo` y define `classDef nuevo stroke-width:3px`. Pon entre
     comillas los textos con paréntesis, comas o dos puntos.
     Si el cambio no altera ningún flujo, va sin diagrama.

     Después, en viñetas o en un bloque diff de un árbol: qué cambia, con
     clases, rutas y pantallas nombradas como están en el código. -->

## Decisiones

<!-- Lo que se decidió a propósito y lo que queda fuera de este PR,
     cada uno con su motivo. -->

## Riesgo

**Puerta:** dos vías <!-- o una vía: qué no se puede deshacer y cómo se revierte -->
**Alcance:** <!-- pantallas, roles, jobs o integraciones que toca -->
**Despliegue:** nada <!-- migraciones, variables de entorno, comandos, orden -->

## Evidencia

<!-- Antes → después: el test que fallaba y ahora pasa (nombre y comando),
     una captura de la pantalla, o la salida de un comando. -->
