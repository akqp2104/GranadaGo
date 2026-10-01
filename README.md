# RoyaleDeck

## Descripción del problema

Modificar un mazo de Clash Royale exige considerar cómo afecta cada cambio al conjunto. Una sustitución puede cubrir una carencia y, al mismo tiempo, aumentar demasiado el coste de elixir o eliminar una capacidad que se quería conservar.

El problema consiste en determinar qué cambios permiten cubrir las necesidades del jugador utilizando las cartas disponibles, respetando las que desea mantener y su límite de coste medio de elixir. Se busca alterar lo menos posible el mazo original e identificar qué condiciones habría que reconsiderar cuando no puedan cumplirse todas.

Este problema parte de mi experiencia como jugadora. La ficha del cliente recoge el contexto y las dificultades que motivan el proyecto.

## Alcance

Las necesidades consideradas deberán expresarse mediante características comprobables de las cartas: coste de elixir, tipo y objetivos a los que pueden atacar.

La cobertura de un objetivo significa que el mazo contiene cartas capaces de atacarlo, pero no garantiza que puedan derrotar cualquier amenaza de ese tipo. El proyecto tampoco pretende predecir victorias ni identificar un mazo universalmente superior.

Los niveles de las cartas no se utilizarán para estimar resultados de combate. El jugador podrá indicar qué cartas quiere conservar por tenerlas mejoradas y cuáles acepta considerar como sustitutas.

El alcance inicial se limitará a las cartas cuyos atributos necesarios estén verificados en la versión del catálogo utilizada. No se asumirá que ese catálogo refleja todas las modificaciones posteriores del juego.

## Procedencia de los datos

### Catálogo de cartas

Se utilizará el conjunto [Clash Royale Cards Data, de Nitesh Kakkar](https://www.kaggle.com/datasets/niteshkakkar/clash-royal-cards-data). La versión consultada fue actualizada el 30 de octubre de 2025 y contiene los archivos `clash_royale_cards_1.json` y `clash_royale_cards.xlsx`.

El JSON incluye 120 registros dentro de una lista denominada `items`. Los campos relevantes son:

| Campo | Información |
|---|---|
| `id` | Identificador de la carta |
| `name` | Nombre |
| `elixirCost` | Coste de elixir |
| `type` | Tipo de carta |
| `targets` | Objetivos a los que puede atacar |

Por ejemplo, el registro de Knight contiene el identificador `26000000`, un coste de elixir de `3`, el tipo `troop` y el objetivo `ground`.

Los atributos ausentes o ambiguos no se completarán con valores inventados. Los registros que no permitan comprobar las condiciones del problema quedarán fuera del alcance hasta que puedan verificarse.

El conjunto declara licencia CC BY-NC-SA 4.0. Se conservarán la atribución al autor, la referencia a la licencia y la indicación de las modificaciones realizadas, respetando sus condiciones de uso no comercial y de distribución de adaptaciones. No se incorporarán las imágenes enlazadas desde el catálogo.

La copia utilizada se incluirá en el repositorio junto con su procedencia y versión.

### Información aportada por el jugador

Para describir su caso, el jugador indicará:

- Las ocho cartas de su mazo actual.
- Las cartas que quiere conservar.
- Las cartas disponibles que acepta considerar como sustitutas.
- Las condiciones que necesita cumplir, como el límite de coste medio de elixir y la cobertura de objetivos.

No será necesario introducir estadísticas, historiales de partidas ni toda la colección. Las alternativas se limitarán a las cartas indicadas por el jugador.

Los datos de referencia necesarios estarán dentro del repositorio. El funcionamiento no dependerá de consultas a APIs ni de bases de datos externas.

## Justificación del despliegue en la nube

El problema afecta a jugadores con diferentes colecciones y restricciones, pero que utilizan un mismo catálogo de referencia.

El despliegue en la nube resulta adecuado para ofrecer el análisis de combinaciones desde sus dispositivos, manteniendo una versión común de los datos y evitando que cada jugador tenga que instalar y mantener un entorno de ejecución.

La dificultad requiere valorar conjuntamente las restricciones y los efectos de varias sustituciones. Por ello, el servicio previsto tendría una responsabilidad de procesamiento que va más allá de almacenar y consultar cartas.

## Imágenes relacionadas con las fichas del problema y la configuración de git

- [Fotografía de la ficha del cliente](media/cliente.jpg).
- [Configuración del repositorio](config/configuracion.md).