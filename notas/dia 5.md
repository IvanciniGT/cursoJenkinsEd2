# Ficheros Jenkinsfile

## Sintaxis
Basada en Groovy
- Declarativa ***
- Scripting

# Marcas teníamos en los Jenkinsfile

pipeline:
    - agent:            Entorno donde se ejecuta el proyecto (pipeline): Maquina física, maquina virtual, contenedor, pod
    - parameters
    - triggers
    - stages:
        - stage("Nombre"):
            - steps:
                ........ Plugins (Tareas en ultima instancia que ejecutamos) < Snippet generator
              stages    Define trabajos secuenciales
              parallel  Define trabajos paralelos
            - post  
            - when
            - agent
    - post:             Permite dar un trámites especial según el estado en que que acabe un stage o el pipeline completo
        - always
        - success
        - failure
        
        
1. Sonar proyectos no JAVA
2. Contenedores DOCKER PASADA... guay ! SUPERFACIL
3. Kubernetes y como funciona JENKINS en un entorno REAL
4. 


KUBERNETES !
    Permite gestionar una granja de maquinas que tengan instalado docker o una herramienta equivalente
    
    
    
    
Maven JAVA
Web App

Compilacion: Contenedor necesito? maven+java

Test: 15 contenedores
    Contenedor necesito? maven+java Contenedor
        Unit testing JUNIT
                        Servidor de Aplciaciones JAVA donde instalar mi app recien empaquetada
                            JBoss, Websphere, Weblogic, Tomcat Contenedor
                        Servidor de Base de datos Contenedor
        Probar interfaz gráfica de mi app
                        Selenium Contenedor
                        Navegadores
                            6 < Contenedor
        Pruebas de rendimiento
                        JMeter Contenedor