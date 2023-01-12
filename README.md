# Actividad-22-cc3s2
Actividad 22 del curso de Desarrollo de Software CC3S2

En esta actividad, veremos qué mejoras podemos hacer al commit pipeline de la actividad anterior
# Cobertura de código
Puede ser que en un proyecto no haya pruebas unitarias. Por lo tanto, el código pasará todas las construcciones, pero esto no quiere decir que el código vaya a funcionar como se esperaba.

La solución para este problema es agregar una herramienta de cobertura de código, la cual verificará qué partes del código se han ejecutado.
Además, podemos crear un informe de las secciones que no se prueban, así como también hacer que falle la construcción cuando haya demasiado código sin probar.

# Agregar JaCoCo a Gradle
- Agregaremos el complemento jacoco al archivo build.gradle.
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/jacoco-gradle.PNG "")

- Luego, podemos decirle a Gradle que falle en caso haya una baja cobertuda de código, en este caso le diremos que la cobertura de código mínima es un 20%
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/jacoco-rules.PNG "")

- Podemos ejecutarlo con el sgte comando:
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/jacoco-test.PNG "")

- También, podemos crear un reporte
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/jacoco-report.PNG "")

# Agregando una etapa de cobertura de código
- Agregar una etapa de cobertura de código al pipeline es tan simple como las etapas anteriores:
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/jacoco-stage.PNG "")
- Publicación del informe de cobertura de código
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/publicar-informe-cobertura.PNG "")

# Análisis de código estático
