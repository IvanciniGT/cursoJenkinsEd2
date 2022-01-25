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