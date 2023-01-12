# Actividad-22-cc3s2
Actividad 22 del curso de Desarrollo de Software CC3S2

En esta actividad, veremos qué mejoras podemos hacer al commit pipeline de la actividad anterior
# Cobertura de código
Puede ser que en un proyecto no haya pruebas unitarias. Por lo tanto, el código pasará todas las construcciones, pero esto no quiere decir que el código vaya a funcionar como se esperaba.

La solución para este problema es agregar una herramienta de cobertura de código, la cual verificará qué partes del código se han ejecutado.
Además, podemos crear un informe de las secciones que no se prueban, así como también hacer que falle la construcción cuando haya demasiado código sin probar.

# Agregar JaCoCo a Gradle
- Agregaremos el complemento jacoco al archivo build.gradle.
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-22-cc3s2/main/jacoco-gradle.PNG "")

- Luego, podemos decirle a Gradle que falle en caso haya una baja cobertuda de código, en este caso le diremos que la cobertura de código mínima es un 20%
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-22-cc3s2/main/jacoco-rules.PNG "")

- Podemos ejecutarlo con el sgte comando:
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-22-cc3s2/main/jacoco-test.PNG "")

- También, podemos crear un reporte
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-22-cc3s2/main/jacoco-report.PNG "")

# Agregando una etapa de cobertura de código
- Agregar una etapa de cobertura de código al pipeline es tan simple como las etapas anteriores:
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-22-cc3s2/main/jacoco-stage.PNG "")
- Publicación del informe de cobertura de código
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-22-cc3s2/main/publicar-informe-cobertura.PNG "")

# Análisis de código estático
Este análisis se refeire a un proceso de verificación de código sin ejecutarlo. Es utilizado para definir ciertas reglas en el código fuente y así evitar conflictos al momento de fusionar los cambios que tiene cada desarrollador en la rama en la que trabaja. Por ejemplo, se puede definir que la longitud máxima de una línea es de 120 caracteres, etc.

Para elo utilizaremos CheckStyle:
1. Agregaremos la configuración de Checkstyle
2. Agregamos la etapa Checkstyle
3. Opcionalmente, publicamos el informe Checkstyle en Jenkins

# Triggers y notificaciones
En esta sección, veremos cómo hacer que un pipeline se inicia automáticamente y, cuando se complete, notifique a los miembros del equipo sobre su estado
# Triggers
Es una acción automática que desencadena la construcción de un pipeline. En Jenkins, hay 3 tipos de triggers:
- External
- Source Control Management (SCM)
- Construcciones programadas

# External
Los triggers externos hacen que Jenkins inicie la construcción del pipeline después de que lo llame el notificador (notifier), que puede ser otra consutrcción de un pipeline, Github o cualquier secuencia de comandos remota

- Para ello necesitamos instalar el plugin de Github en Jenkins
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-22-cc3s2/main/github-plugin.PNG "")

# SCM
Esta configuración es más simple, porque Jenkins verifica el código de Github y ya sabe cómo acceder a él. Agregaremos un trigger al pipeline del calculador.

Después de ejecutar el pipeline manualmente por primera vez, se establecerá el trigger automático. Luego, se verifica Github cada minuto y cuando detecta un nuevo commit, comienza una construcción. Le pasamos "* * * * *" como argumento para especificar la frecuencia con la que Jenkins debe verificar si hay nuevos cambios en la fuente y ejecutar una nueva construcción

# Construcciones programadas
El trigger progamado ejecuta la construcción periódicamente, sin importar si hubo commits o pushs en el repositorio

# Notificaciones
Jenkins proporcionar muchas formas de anunciar o notificar el estado de construcción, por ejemplo, podemos notificar al equipo de desarrollo sobre el estado de construcción de un pipeline

Hay varias formas, por ejemplo:

# Correo electrónico
La forma más clásica de notificar a los usuarios sobre el estado de construcción de Jenkins es mediante correos electrónicos

Para configurar esta método de notificaciones, simplemente debemos hacer lo siguiente:
- Tener configurado el servidor SMTP
- Condigurar los detalles en Jenkins
- Utilizar el correo para la instrucción en el pipeline

# Chats grupales
En muchas empresas se suele usar aplicaciones de chat grupal, como Slack, entonces el mandar la notificación a través de Slack vale la pena, ya que, todo el equipo podrá verlo. Para configurarlo se necesita lo sgte:
- Instalar el complemento en Slack o de tu chat grupal de preferencia
- Configurar el complemento (URL del servidor, canal, token, etc)
- Agregar la instrucción de envío al pipeline

