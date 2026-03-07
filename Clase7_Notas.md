--- 
# Recuperando datos: MediaCloud y Wikidata

```markdown
---
Fecha: 2026-02-24
Modulo: 2
Sesión: 8
---
```

En esta sesión nos concentramos en dos ejemplos, dos plataformas de datos abiertos: MediaCloud y Wikidata. Antes de entrar a cada una, trabajamos un tema transversal que es el origen de los datos. Destacamos que, antes de usar cualquiera de estas fuentes de datos, hace falta preguntarse: ¿quién los produce, cómo y para qué? Esta pregunta no es accesoria —determina qué podemos observar con esos datos y cómo debemos interpretarlos.

Al ver estas dos plataformas, queda clara nuestra preocupación por las URLs como punto de entrada, claro y explícito, a los datos. Cada búsqueda en MediaCloud o Wikidata genera una URL única. Leer la estructura de un ULR ayuda a entender cómo estamos interactuando con la plataforma, qué le estamos pidiendo y cómo. Esa URL puede guardarse y compartirse, lo que permite reproducir exactamente la misma consulta por diferentes personas en distintos momentos. Esto nos garantiza trazabilidad (es decir, el seguimiento y la posibilidad de identificación de los distintos pasos en un proceso). Por eso es parte de documentar la estrategia de búsqueda y las decisiones que tomamos.

En ese sentido, una buena práctica es llevar "notas" que registren el camino que hacemos (marcando hitos específicos) y las decisiones que tomamos con base a lo que encontramos. En esas anotaciones conviene registrar y comentar las URLs de búsquedas relevantes junto con la fecha en que se realizaron, las primeras interpretaciones y hallazgos, las decisiones sobre cómo avanzar e ideas generales sobre la posible utilización de los datos.

## Proveniencia de los datos: ¿de dónde vienen?

**MediaCloud** archiva artículos de medios de comunicación que publican digitalmente. Funciona capturando feeds RSS, y lo que registra son metadatos (descriptores de los artículos y las fuentes) y URLs. Un punto clave: los medios no "muestran" la realidad, sino que la reflejan a través de prioridades editoriales, sesgos e intereses propios del proceso periodístico. Esto determina qué podemos observar —y qué no— con estos datos.

**Wikidata** es generada colaborativamente por una comunidad de editores. Refleja lo que esa comunidad considera relevante registrar y cómo lo clasifica. Su cobertura es desigual: algunas entidades están muy bien documentadas, otras apenas existen.

## Parte 1: MediaCloud

MediaCloud es una plataforma de investigación desarrollada originalmente por el MIT y otras universidades de Estados Unidos. Permite buscar y analizar cobertura mediática en miles de medios, y es útil para responder preguntas como: ¿cómo se habla de X tema en la prensa? ¿Con qué frecuencia? ¿En qué contextos? ¿Qué actores se mencionan?

Para buscar en MediaCloud, el proceso implica operacionalizar la pregunta de investigación en tres decisiones: seleccionar una **colección de medios** (país, región, tipo de medio), formular una **consulta con palabras clave**, y definir un **rango temporal**. Luego se exploran e interpretan los resultados: volumen de cobertura, medios que publican, términos relacionados.

Algunos consejos que compartimos en clase para la búsqueda fueron: usar términos específicos y también sinónimos o variaciones; comparar distintas colecciones de medios para ver diferencias en cobertura; y atender a los picos y caídas en el tiempo, preguntándose qué los explica.

Trabajamos dos ejemplos en clase. El **primero** fue la búsqueda de ["salario mínimo" OR "salario minimo"](https://search.mediacloud.org/search?qs=%2522salario%2520minimo%2522%2520OR%2520%2522salario%2520m%25C3%25ADnimo%2522%250A&start=01-20-2018&end=02-22-2026&p=onlinenews-mediacloud&ss=&cs=38380322&any=any&name=%22salario%20minimo%22%20OR%20%22salario%20m%C3%ADnimo%22%0A&edit=false) en prensa mexicana, que luego refinamos cruzando con actores institucionales: [("salario minimo" OR "salario mínimo") AND ("COPARMEX" OR "CONASAMI")](https://search.mediacloud.org/search?qs=(%2522salario%2520minimo%2522%2520OR%2520%2522salario%2520m%25C3%25ADnimo%2522)%2520AND%2520(%2522COPARMEX%2522%2520OR%2520%2522CONASAMI%2522)%250A&start=01-20-2018&end=02-22-2026&p=onlinenews-mediacloud&ss=&cs=38380322&any=any&name=(%22salario%20minimo%22%20OR%20%22salario%20m%C3%ADnimo%22)%20AND%20(%22COPARMEX%22AND%22CONSAMI%22)). 

El **segundo** fue el [derrame en la cuenca del río Sonora](https://tinyurl.com/MediaCloudGM), buscando "rio Sonora" AND "Grupo México". Este fue el [mayor desastre ambiental de México](https://es.wikipedia.org/wiki/Desastre_ecol%C3%B3gico_en_los_r%C3%ADos_Bacanuchi_y_Sonora), con 40 mil metros cúbicos vertidos y 254 km de cuenca contaminada, afectando a siete municipios. En ese ejemplo observamos fuentes, top words y actores mencionados (Grupo México, AMLO, SEMARNAT, pobladores afectados) y discutimos para qué puede servir hacer foco en alguno de ellos.

## Parte 2: Wikidata

Wikidata es una base de datos abierta y estructurada, mantenida por la comunidad Wikimedia. Almacena información sobre entidades (personas, organizaciones, lugares, conceptos) en forma de **propiedades y valores** y puede consultarse mediante lenguaje SPARQL o interfaces visuales. Una posibilidad adicional: se puede usar un LLM para traducir lenguaje natural a queries SPARQL.

Para buscar, el proceso es: acceder a [wikidata.org](https://wikidata.org) o al [Wikidata Query Service](https://query.wikidata.org), buscar la entidad de interés, explorar sus propiedades y valores disponibles, y si se quieren consultas más complejas, usar el SPARQL Query Service. En clase, mencionamos que una buena forma de transformar el lenguaje natural (humano) a el lenguaje de las máquinas (SPARQL), puede ser utilizar la ayuda de un LLM (como gemini, ChatGPT, etc.). Sin embargo, esto requiere de que veamos y estudiemos las entidades que componen el servicio de [wikidata.org](https://wikidata.org). Por eso, se incluyen en estas notas enlaces directos a las entidades utilizadas en las búsquedas de ejemplo. 

Vimos tres ejemplos. El **primero** consultó [golpes de Estado en América Latina durante el siglo XX](https://query.wikidata.org/#%23%20Golpes%20de%20estado%20en%20el%20siglo%20XX%0ASELECT%20%3FgolpeLabel%20%3FlugarLabel%20%3Ffecha%20WHERE%20%7B%0A%20%20%3Fgolpe%20wdt%3AP31%20wd%3AQ45382%3B%20%20%20%20%20%23%20instancia%20de%3A%20golpe%20de%20estado%0A%20%20%20%20%20%20%20%20%20wdt%3AP17%20%3Flugar.%0A%20%20OPTIONAL%20%7B%20%3Fgolpe%20wdt%3AP585%20%3Ffecha.%20%7D%0A%20%20FILTER%28%3Ffecha%20%3E%3D%20%221900-01-01%22%5E%5Exsd%3AdateTime%20%26%26%20%3Ffecha%20%3C%20%222000-01-01%22%5E%5Exsd%3AdateTime%29%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22es%22.%20%7D%0A%7D%0AORDER%20BY%20%3Ffecha%0A), combinando la propiedad "instancia de golpe de Estado" (Q45382) con lugar (P17) y fecha. 

El **segundo** buscó [ciudades con sistema de transporte rápido](https://query.wikidata.org/#SELECT%20DISTINCT%20%3FciudadLabel%20%3FpaisLabel%20%3Fpoblacion%20%3Fimagen%0AWHERE%20%7B%0A%20%20%23%20Ciudades%0A%20%20%3Fciudad%20wdt%3AP31%20wd%3AQ515%20.%0A%20%20%0A%20%20%23%20Que%20tengan%20un%20sistema%20de%20transporte%20r%C3%A1pido%0A%20%20%3Fsistema%20wdt%3AP31%20wd%3AQ5503%20.%0A%20%20%3Fsistema%20wdt%3AP131%20%3Fciudad%20.%0A%20%20%0A%20%20%23%20Pa%C3%ADs%0A%20%20%3Fciudad%20wdt%3AP17%20%3Fpais%20.%0A%20%20%0A%20%20%23%20Poblaci%C3%B3n%20de%20la%20ciudad%0A%20%20OPTIONAL%20%7B%20%3Fciudad%20wdt%3AP1082%20%3Fpoblacion%20%7D%0A%20%20%0A%20%20%23%20Imagen%20del%20sistema%20de%20transporte%0A%20%20OPTIONAL%20%7B%20%3Fsistema%20wdt%3AP18%20%3Fimagen%20%7D%0A%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22es%2Cen%22%20%7D%0A%7D%0AORDER%20BY%20DESC%28%3Fpoblacion%29), cruzando la entidad "ciudad" (Q515) con "sistema de transporte rápido" (Q5503), población (P1082) e imágenes (P18). 

El **tercero** consultó [mujeres que son o fueron presidentas](https://w.wiki/HytC) de estados soberanos, filtrando por género femenino (Q6581072), cargo de presidenta (subclase de Q30461) y excluyendo personas fallecidas. En este punto, la búsqueda mostró algunas complicaciones. Esto nos ayudó a ver la importancia que tiene la precisión en el tipo de enunciados (statements) que usamos para solicitar información. En este caso, nuestra búsqueda pedía mujeres que fueran jefas de Estado. Esto requería que Wikidata buscara todas las mujeres y, luego, supiera cuáles son jefas de Estado. Esto requería muchos recursos (poder de cálculo y procesamiento). La alternativa para evitarlo era organizar la búsqueda no como jefes de Estado (incluidos reyes y otras figuras), sino como presidentes. Ahí, luego, era pedirle
