Proyecto JAVA
    Colección de ficheros con extensión: .java
    Esos ficheros se compilan:           .class (bytecode)
    Un proyecto tiene muchos archivos...
        Y para distribuirlo esos archivos los empaqueto:
            .jar    librerias y scripts
            .war    aplicaciones web
            .ear    aplicaciones web... algo más complejas
                                                                                Kotlin Scala
Una herramienta (no la única) que nos ayuda al desarrollo, compilación y empaquetado de proyectos Java: MAVEN
    Otras (gradle, sbt)

Maven...
    1º Requería una configuración: pom.xml
    2º Requiere una determinada estructura de carpetas (personalizable... nadie la personaliza)
        Código de la app:                           src/main
        Código de las pruebas automatizadas         src/test
        Clases compiladas                           target/classes          NOS DA IGUAL
        Clases compiladas de las pruebas            target/test-classes     NOS LA IGUAL
        Al hacer las pruebas se generan informes    target/surefire-reports/*.xml       IMPORTANTE PARA NOSOTROS
                                                    target/test-reports/*.xml
        Al empaquetar un proyecto                   target (.jar, .war, .ear) > Distribuir

Para trabajar con maven: GOALS (tareas que podiamos solicitar a maven):
    compile
        test-compile
            test
                package
    clean   (básicamente borra la carpeta target)

---
Pruebas de software
    Estaticas - No requieren ejecutar el código: Analizar la calidad de mi programa
                                                 Ayudarme a encontrar bugs, vulnerabilidades
        Sonarqube Cobertura de codigo... % del codigo está siendo probado por pruebas unitarias 70-80%
    Dinamicas - Requieren ejecutar código
        Funcionales
            Unitarias       Prueban una función del código.     FRAMEWORKS DE PRUEBAS UNITARIAS:
                                                                    Junit -> Definió cómo deben ser los informes de ejecución de pruebas
                                                                    TestNG
                                                                    MSTest
                                                                    PyTest
                                                                    TestUnit
            Integración     Prueba la comunicación de esas funciones entre si, comunicación con otros sistemas
            Sistema         Casos de uso completos
            Aceptación      Las del cliente... importantes
        No Funcionales
            Rendimiento     Jmeter / LoadRunner -> Las pantallas de la app tardan en ejecuatrse 100ms < 110ms (ESTABLECIDO COMO MINIMO)
            Estres          Jmeter / LoadRunner
            HA              
            UI              Selenium (web) Appium (phone) UFT (desktop) -> cuando accedes a una pantalla de la app y rellenas un formulario se obtienen tropetantos datos > 0 Todo guay
            ...
            
# SCM o Sistemas de Control de Versión

Qué es esto? Para que sirve?
- Herramienta que nos ayuda a gestionar los cambios que vamos haciendo de un software... y sus versiones.
- Auditoria / Revertir cambios
- A trabajar en equipo en un proyecto

Conceptos básicos en los Sistemas de control de versión:
- Commit:   Foto del estado del proyecto en un momento dado. Copia. Backup completo del proyecto
- Rama:     Una linea de tiempo paralela de evolución de mi proyecto
- Tag:      Una etiqueta que pongo a un commit en una rama. Me permite identificar commits (backups, fotos) rápidamente 
                Los usamos para identificar versiones del software
Ramas:
    Principal: master < main, trunk      NO SE TOCA.. al que hace aquí un commit , despedido fulminante!
                Se entiende que lo que hay en esta rama está listo para producción.
    Desarrollo: development, develop, dev. Aqui es donde los desarrolladores trabajan la mayor parte del tiempo
        Crear sus propias ramas donde van haciendo su código, sus pruebas... y cuando todo está listo lo mandan a "desarrollo"
    Cuando en dasarrollo creo que tengo un codigo guay, listo para producción-> release, test -> master/main

cvs > svn > git
    Sistema de control de versión distribuido
    
    Desarrollador 1                     Desarrollador 2                 Tester 1            Sysadmin 1
        Repo propio con el proyecto           Repo                        Repo                Repo        SON DIFERENTES !!!!
            ------> Desarrollo                  ^
                            V                   ^ (desarrollo)
                            Servidor accesible por red (repo remoto)
                                    Repo
    commit -> Esa operación genera una foto de mi proyeco (backup, sellado) se hace en el repo local
    Ese commit lo hemos de mandar a un repo remoto para compartirlo: Push
    La gente que quiera sincronizarse con un repo remoto:            Fetch  Pull(Fetch+Merge)
    
    Los repos remotos suelen ser creados y ofrecidos por productos de 
        software especializados en ese trabajo: Albergar repos remotos de git:
            - Github: Internet, como servicio
            - Gitlab        Permiten también instalarse en mi empresa ****
            - Bitbucket     Permiten también instalarse en mi empresa   
                            (va ganando terreno, en especial por la integración con el resto de herramientas de esa empresa)
                            Atlassian: JIRA, CONFLUENCE
                            
                            
                            