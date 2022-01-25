# JENKINS es un sistema distribuido

¿Qué significa esto?
    cluster?
        M1  Inst1 Jk \
        M2  Inst2 Jk  - Balanceador de carga < Usuario
        M3  Inst3 Jk /
    
Un sistema distribuido implica que tendremos varias partes de jenkins en varias ubicaciones (maquinas)
realizando tareas diferentes
        M1  Maestro Jenkins << Usuarios
         \ \-  M2  Agente de compilación de apps Java
          \-- M3  Agente de compilación de apps JS
          
# JOB DE JENKINS
- Configuración
- Origen del código SCM
- Disparadores (eventos que desencadenan la ejecución del proyecto)
- Steps-Secuencia de tareas que deben ejecutarse

Cada ejecución de un JOB dará lugar a un BUILD (ejecución, trabajo, compilación)

Para jenkins, una tarea, es un proceso que se lanza a nivel de SO. PUNTO PELOTA !!!!
    Jenkins mira el codigo de salida de cada proceso:
        - 0:    GUAY
        - No 0: RUINA GRANDE !!!!

Jenkins crea un directorio donde trabajar para cada proyecto.
Ese directorio se mantiene entre ejecuciones.... SI NO LE DIGO LO CONTRARIO
Eso es bueno o malo?
    Yo que se... dependerá de lo que esté haciendo
    
Jenkins separa el flujo de trabajo en 2 bloques:
    Tareas. Si hay un error en las tareas... las posttareas se ejecutan igualmente
                                         ... por contra, se detiene la ejecución de nuevos pasos(tareas)
    Post Tareas

¿Que os parece este comportamiento? POBRE !!!!

A priori, las tareas y las post tareas, son de DIFERENTE NATURALEZA

## PRUEBAS DE SOFTWARE

Estáticas: No requieren poner el software en ejecución para hacer la pruebas.¿?
    LEER CODIGO (por alguien que sepa mucho... un senior): CALIDAD.
        Un experto llamado SONARQUBE
            Codigo muerto.. que no hace nada
            Variables no inicializadas
            Codigo duplicado
            Malas prácticas
            Poca documentación

Dinámicas: Implica poner el software en ejecución para hacer la pruebas
    Funcionales
        Unitarias
        Integración
        Sistema
        Aceptación
    No funcionales
        Estres
        Carga
        H/A
        UI
        UX

# Lenguajes de programación
- Lenguajes Compilados -> Traducción de mi carta a CHINO (traductor) -> Carta traducida en chino -> mando al chino
                          Traducción de mi carta a ALEMAN (traductor) -> Carta traducida en aleman -> mando al aleman
        C, cobol, C++
- Lenguajes Interpretados (Mensaje a mi amigo: Jodete y buscate la vida)
                            Le mando a mi amigo chino la carta en español  < Él contrata a un interprete < En tiempo real 
                                                                             el interprete lee la carte en español y la promuncia en Chino
                            Le mando a mi amigo aleman la carta en español < Él contrata a un interprete < En tiempo real 
                                                                             el interprete lee la carte en español y la promuncia en Aleman
        Python, JS, sh, basic

JAVA es un lenguaje MUY RARITO!!!
    Java es compilado + interpretado

# Proyectos JAVA
    
    Partimos de ficheros: *.java   (no se entienden por el SO, igual que otros lenguajes: *.c     *.py)
    Los vamos a compilar: *.class  (byte-code) [javac]
    Son interpetados en el destino (allá donde instale la app) por un interprete (Máquina virtual de Java: JVM)
    
    Un proyecto Java contiene de decenas a miles de archivos .java
        Esos archivos los compilo > cientos o miles de archivos .class
    
    Todos esos archivos .class se meten en un ZIP, al que se le cambia la extensión:
        .jar    Librerias, scripts  [jar]   |   
        .war    App web                     |   Resultado de empaquetar un proyecto java
        .ear    App web... más compleja     |
    
    Maven ayuda a automatizar las tareas de compilación, gestión de dependencias y empaquetado de un proyecto JAVA
    Maven hay que configurarlo para cada proyecto > pom.xml < ESTO LO ESCRIBEN LOS DESARROLLADORES
    
    En maven existen lo que denominamos GOALS: Basicamente las tareas que puedo pedir a maven que haga sobre mi proyecto:
    - compile
        V
    - test-compile
        V
    - test
        V
    - package 
    
    Maven además impone una serie de carpetas donde trabajar.
        El código JAVA lo tendremos dentro de una carpeta llamada       src/main
        Las pruebas automatizadas las tendremos en una carpeta llamada  src/test
        Cuando maven compile un proyecto, el resultado lo guardará en   target/classes (me da igual)
        Cuando a maven le pido que ejecute las pruebas de un proyecto.  target/surefire-reports/*.xml   IMPORTANTE PARA NOSOTROS
        El resultado de empaquetar el proyecto se depositará en         target                          MUY IMPORTANTE