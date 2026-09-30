# GranadaGo
Comparación de transporte público en el área metropolitana de Granada

## Procedencia del problema

Vivo en Maracena y me desplazo con frecuencia dentro de la zona metropolitana de Granada para ir a la universidad, quedar con amigos o cuando tenía que ir a trabajar presencialmente. Aunque tengo carné y puedo utilizar el coche, prefiero utilizar el transporte público ya que encontrar aparcamiento en el centro es bastante complicado y dejarlo en el parking me sale muy caro. Sin embargo, tampoco siempre tengo claro qué transporte público encaja mejor con mis planes.

El metro puede resultar conveniente por su frecuencia, mientras que un autobús puede dejarme más cerca del destino. Sin embargo, además del tiempo de desplazamiento también influyen la espera, los posibles transbordos y las opciones disponibles para regresar.

Las diferencias entre días laborables, fines de semana, festivos y temporadas complican estas comprobaciones. Un horario que sirve un día puede no estar disponible en otro. Asimismo, retrasar unos minutos la salida puede suponer tener que esperar al próximo servicio disponible y aumentar considerablemente el tiempo de espera.

El coste también influye en mi decisión. Las tarifas dependen del medio de transporte, del título utilizado y, cuando corresponde, de las zonas y condiciones de transbordo. Por ello, comparar únicamente el precio de un primer trayecto puede no reflejar el importe del desplazamiento completo.

Consultar todo esto manualmente conlleva mucho tiempo, además del riesgo de pasar por alto alguna incompatibilidad.

El proyecto parte de esta experiencia y se centra en los desplazamientos en transporte público entre Maracena, Albolote o Armilla y destinos concretos de Granada capital.

## Delimitación del problema

El ámbito inicial comprende desplazamientos entre paradas seleccionadas de Maracena, Albolote y Armilla y paradas de Granada capital, utilizando metro y autobuses metropolitanos o urbanos.

La comparación se basa en los horarios programados. Estos permiten estudiar las alternativas previstas, pero no garantizan la puntualidad ni anticipan incidencias.

Los recorridos a pie desde el origen o hasta el destino final solo se tendrán en cuenta cuando se disponga de duraciones conocidas y documentadas. En los demás casos, la comparación se realizará entre paradas.

La duración del viaje en coche y la disponibilidad de aparcamiento quedan fuera del ámbito inicial, ya que no se dispone de datos suficientes para compararlas de forma fundamentada.

## Fuentes de datos

### Autobuses metropolitanos

El [Portal de Datos Abiertos de la Red de Consorcios de Transporte de Andalucía](https://api.ctan.es/) ofrece una [descarga del conjunto GTFS](https://api.ctan.es/v1/datos/UNIFICADO/gtfs.zip).

El archivo contiene información sobre líneas, paradas, expediciones, horas de llegada y salida y calendarios de servicio. Se ha comprobado que incluye líneas del área de Granada que dan servicio a Maracena, Albolote y Armilla.

Las [condiciones de reutilización](https://api.ctan.es/avisolegal.html) permiten utilizar la información para fines comerciales y no comerciales, respetando sus condiciones y citando la fuente.

### Autobuses urbanos de Granada

La [página municipal del planificador de transporte público](http://www.movilidadgranada.com/bus_planificador.php) ofrece un [archivo GTFS descargable](http://www.movilidadgranada.com/gtfs/gtfs.zip).

Se ha comprobado que contiene líneas, paradas, expediciones, tiempos programados y calendarios. Se utilizarán estos archivos como fuente de datos, sin delegar los cálculos en el planificador externo de la página.

### Metro de Granada

El Metropolitano publica sus [horarios y frecuencias](https://metropolitanogranada.es/index.php/horarios).

También se ha inspeccionado una [copia del conjunto GTFS del Metro de Granada](https://files.mobilitydatabase.org/mdb-2784/mdb-2784-202607180029/mdb-2784-202607180029.zip), conservada por MobilityDatabase y procedente del Punto de Acceso Nacional de Transporte. Incluye tiempos por parada y calendarios, con servicios cuya vigencia alcanza diciembre de 2026.

Antes de incorporar este conjunto al repositorio se comprobarán las condiciones de reutilización aplicables y se documentarán su procedencia, fecha de obtención y periodo de vigencia.

### Tarifas

El Consorcio publica la [matriz de saltos y zonas](https://siu.ctagr.es/es/tarifas_saltos.php) y las [tarifas y condiciones de transbordo](https://siu.ctagr.es/es/tarifa.php).

Estas referencias permiten identificar las reglas económicas del desplazamiento. Se conservará la fecha de vigencia de las tarifas utilizadas. Su incorporación no dependerá de consultas automáticas ni de scraping de estas páginas.

### Tratamiento de las fuentes

El procesamiento se realizará sobre archivos previamente descargados. La extracción de los campos necesarios y su interpretación se desarrollarán con código propio, sin bibliotecas externas que resuelvan la extracción ni servicios externos que calculen las alternativas.

Se documentarán la procedencia y vigencia de cada conjunto para evitar mezclar horarios o tarifas correspondientes a periodos incompatibles.

## Imágenes relacionadas con las fichas del problema y la configuración de git
![Ficha de cliente](/media/cliente.jpg)
![Configuración del repositorio](/config/configuracion.md)