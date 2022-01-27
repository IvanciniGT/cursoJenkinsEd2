SonarQube < Jenkins (Hoy vamos a hacer esto TIRANDO POR LA CALLE DE EN MEDIO...)
    Contenedores
Pipeline

# Contenedores

Procedimiento para distribuir e instalar/ejecutar software. 
No todo tipo de software:
    * Servicios. (Servidor web, servidor de BBDD, Servidor de email,)
    * Demonios.  (Programa que indea los archivos del HDD, Desfragmenta en segundo plano, Actualizador de apps)
    * Script.    (Programa que hace sus cosillas y acaba)
    * Librerías. (Conjuntos de funciones, metodos que pueden usarse por otros software)
    * Comandos.  (Programas que con una conf inicial hacen un trabajo)
    ---
    - Aplicación (Word, Chrome, Juego)
    - Driver
    - SO
Contenedor: Entorno aislado dentro de un SO Linux donde ejecutar procesos (1 o muchos)
Entorno aislado:
    - Tienen limitación de acceso al hardware
    - Tienen su propia configuración de red > IP
    - Tienen su propio sistema de archivos
    - Tienen sus propias variables de entorno

Los contenedores se crean desde IMAGENES DE CONTENEDOR
IMAGENES DE CONTENEDOR: ZIP con un programa o varios YA INSTALADOS y PRECONFIGURADOS por alguien.

Los contenedores son la forma estándar a día de hoy para distribuir e instalar software.
Entre los programas para gestionar contenedores:
    DOCKER, podman, crio, containerD
Y ... en entornos de producción:
    KUBERNETES < K8S, Vanila, Openshift

docker run -d --name misonarqube -p 8081:9000 sonarqube:8.9.6-community

MAVEN se integra automaticamente con SONARQUBE

mvn sonar:sonar -Dsonar.projectKey=proyectoMaven -Dsonar.host.url=http://172.31.7.239:8081 -Dsonar.login=6b674b3412bf8d985f3d3c0536c8ae05fa256efe


JAVA : Definir la variable "numero de empleados".  CAMEL CASE: variables, metodos
    numeroDeEmpleado
    numEmp
    numEmpleado
    
    Constantes: NUMERO_DE_EMPLEADO
    Clase Gestor de emepleados: GestorDeEmpleados

PYTHON. SNAKE_CASE
    numero_de_empleados
    
COBOL
    NUM-EMPLEADOS
    
    
Metricas de SonarQube:
    Deuda Técnica: Tiempo que me tardaría en arreglar los pufos (smell codes) (malas practicas) en mi codigo
    Orden de Complejidad de un algoritmo: Como se comporta el algoritmo según necesita hacer una operación 
                                          para conjuntos más grandes de datos.
    Complejidad ciclomática:              Cuantos caminos diferentes puede tomar la ejecución del código 
                                            IF, CASE -> IMPORTANTE?
                                                Número mínimo de pruebas que tengo que diseñar
    Complejidad cognitiva:                Dificultar de una persona para enter mi código

    
    
    
    IF condicion1 ENTONCES:  
        algo
    ELSE IF condicion2: ENTONCES:
        IF subcondicion1 ENTONCES: 
            algo
        ELSE IF subcondicion2 ENTONCES: 
            otro
        END
    ELSE
        IF subcondicion3 ENTONCES: 
            algo
        ELSE IF subcondicion4 ENTONCES: 
            otro
        END
    END IF
    
    Ciclomatica de este codigo: 7
    
    CASE variable   
        WHEN condicion1: algo
        WHEN condicion2: algo
        WHEN condicion3: algo
        WHEN condicion4: algo
        WHEN condicion5: algo
        WHEN condicion6: algo
        WHEN condicion7: algo
        ELSE: algo
        
        
    

    int numeroDeEmpleados=0;
    
DESARROLLO
PRUEBAS
DESARROLLO
PRUEBAS
--- Cuando todo esta OK: 
REFACTORIZACION DEL CODIGO
PRUEBAS




PROYECTO -> MAVEN -> SONARQUBE
 V
 git
 V
CI/Jenkins > MAVEN (compile, pruebe, sonaquberice, empaquete)

Esto está guay SOLO SI MI PROYECTO ES JAVA y USA MAVEN


Flujo de tareas que voy a ejecutar un monton de veces: Script
    .bat
    .sh
En Jenkins lo que hacemos es definir PROGRAMAS
Si lo que estoy haciendo es un programa.... 
    tendré que aplicar conceptos y buenas prácticas de DESARROLLO DE SOFTWARE
PRIMERA REGLA DE ORO INOLVIDABLE en el mundo del desarrollo de software, BAJO PENA CAPITAL DE INCUMPLIMIENTO?
    Donde tiene que estar el código? En un SCM


Ahora el codigo está ...npi... lo tiene jenkins por dentro... en algún sitio...
    Sin control de versión de ningún tipo.
    
Entorno de Jenkins de preproducción / desarrollo
Como paso los flujos de pre a pro? 

Jenkins permite trabajar con lo denominado JENKINSFILES < Defino un pipeline (Job, flujo de tareas)
Un fichero "Jenkinsfile" están escritos en un lenguaje de programación basado en Groovy > JAVA



Etapa 1: Compilación √
Etapa 2: Pruebas Básicas √
    Etapa 2.1 Pruebas unitarias √
    Etapa 2.2 SonarQube √
Etapa 3: Empaquetamiento del proyecto
Etapa 4: Instalación en entorno de integración
    Etapa 4.1 Crear un entorno en Amazon AWS (terraform)
    Etapa 4.2 Aprovisionar y configurar el nuevo entorno
        Pasos... Ansible
    Etapa 4.3 Depliegue de mi app
Epata 5 Resto de pruebas
    Etapa 5.3 Pruebas UI
        Etapa 5.3.1 Chrome
        Etapa 5.3.1 Otros navegadores ? Opcional solo se ejecuta en determinados casos
    Etapa 5.4 Pruebas de rendimiento : JMETER
Etapa 6 Borrar todo ENTORNO DE AMAZON √
Etapa 7: ACOPIO DE RESULTADOS de todas la pruebas √
Etapa 8: Mandar comunicaciones
