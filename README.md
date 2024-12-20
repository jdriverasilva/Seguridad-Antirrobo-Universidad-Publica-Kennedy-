# Seguridad-Antirrobo-Universidades-Bogota.
## Descripción General:

La seguridad en los entornos escolares enfrenta desafíos significativos como el microtráfico, la violencia, el robo de dispositivos móviles y el pandillismo, generando un clima de inseguridad que afecta el bienestar de estudiantes y docentes. En localidades como Suba, Kennedy y Engativá, el hurto ha alcanzado cifras alarmantes, con hasta 745 incidentes al año, impactando negativamente la estabilidad emocional, el desempeño académico y, en algunos casos, la continuidad educativa de los jóvenes.

Para abordar esta problemática, se propone una aplicación móvil que conecte a los estudiantes con las autoridades mediante alertas instantáneas activadas con un solo botón. Con geolocalización integrada, esta solución garantiza respuestas rápidas, previniendo delitos y promoviendo la confianza de las familias. Además, su accesibilidad y adaptabilidad a diversos dispositivos buscan fortalecer la seguridad y el desarrollo integral de la comunidad educativa.

## Objetivo Principal 

Desarrollar una base de datos para una aplicación móvil que, basada en la situación y ubicación del usuario, envíe alertas en tiempo real a las autoridades competentes, específicamente a la Policía Nacional.

## Objetivos Especificos

1. Diseñar una base de datos relacional que almacene información de los usuarios, incluyendo detalles como identificación, ubicación en tiempo real y contacto de emergencia.

2. Implementar un sistema de registro y seguimiento de incidentes que guarde los datos de cada alerta enviada, como fecha, hora, ubicación y tipo de emergencia.

3. Optimizar las consultas y procesos en la base de datos para garantizar la rápida recuperación de información relevante y el envío eficiente de alertas a las autoridades.

4. Asegurar la integridad y protección de los datos almacenados en la base de datos mediante mecanismos de encriptación y gestión de accesos para mantener la privacidad de los usuarios.

## Justificacion

La seguridad de los estudiantes en las universidades de Bogotá se ha convertido en una preocupación creciente debido al aumento de robos y situaciones de riesgo en las inmediaciones de estas instituciones. Los estudiantes, que suelen llevar dispositivos móviles y otros objetos de valor, enfrentan amenazas constantes que afectan no solo su bienestar, sino también su tranquilidad al desplazarse por la ciudad.

Por eso, esta propuesta busca dar una respuesta práctica y accesible a este problema mediante una aplicación móvil que, con un simple comando usando las teclas de volumen, pueda enviar alertas inmediatas al Centro de Atención Inmediata (CAI) más cercano. La idea es que en un momento de peligro o emergencia, los estudiantes puedan pedir ayuda de manera rápida y discreta, facilitando que las autoridades lleguen lo antes posible.

Al final, lo que se busca con esta propuesta es más que un sistema tecnológico: es brindar a los estudiantes una herramienta que les devuelva la confianza de moverse seguros, sabiendo que en caso de cualquier eventualidad, la ayuda estará a solo un clic de distancia. Porque la seguridad no debe ser un lujo, sino un derecho para todos. 


## Diseño y Modelado. 


Breve paso a paso de la realizacion de la normalizacion y apoyo de imagenes, las cuales muestra la manera que realizamos la primera, segunda, tercera forma normal. Para mayor informacion pueden dar consultar acá [Normalizacion](./Normalizacion.md) 

Adjunto encontraras un documento excel en el cual se encuentra las tablar normalizas de acuerdo a lo establecido a los requerimientos dados. para mayor informacion descargar tabla dandole click en el enlace [Tabla Normalizada](./tabla_normalizacion_seguridad_antirrobo.xlsx)

Adjunto encontraras la carpeta que contienen todos los codigos de las importaciones de las tablas en MySQL Workbench.para descargar los codigos dirigirse a la carpeta. [Codigos SQL](./SQL)

## Diagrama EER

![EER](https://github.com/user-attachments/assets/9119ba63-f514-44a8-8573-9e5a21e70853)

## Diagrama ER

![Diagrama en blanco (1)](https://github.com/user-attachments/assets/c5afcaa4-91d0-460b-881f-042babe6ae6b)

## Conclusiones

integración de tecnologías en la seguridad escolar: El proyecto demuestra un enfoque práctico para abordar problemas de inseguridad en entornos educativos mediante el uso de herramientas tecnológicas. La integración de funcionalidades como el uso de geolocalización y notificaciones instantáneas refuerza la capacidad de respuesta ante incidentes de robo o violencia.

Enfoque comunitario y accesibilidad: La solución está diseñada pensando en la accesibilidad y el beneficio colectivo, ofreciendo una herramienta gratuita y compatible con diferentes dispositivos. Esto promueve la inclusión tecnológica y fomenta la participación activa de estudiantes, docentes y familias en la mejora de la seguridad escolar.

Potencial para la expansión y mejora continua: Aunque el proyecto cubre necesidades específicas, su estructura permite futuras ampliaciones, como agregar análisis de datos de incidentes o funcionalidades adicionales para la comunicación con las autoridades. Esto lo convierte en una solución escalable que puede adaptarse a otros contextos o instituciones educativas.

## Referencias
1.https://claude.ai/new

2.https://chatgpt.com/

3.https://www.infobae.com/colombia/2024/05/08/estas-son-las-zonas-en-las-que-mas-roban-cerca-a-colegios-en-bogota-en-2023-se-registraron-13128-casos/
