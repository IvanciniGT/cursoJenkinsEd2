# Qué es Jenkins

Orquestador de tareas: Sirve para automatizar la llamada y controlar trabajos automatizados
Servidor de CI/CD -> Servidor de automatización
Opensource + Freeware -> Free software
    Jenkins tiene versión de pago: CloudBees

Herramientas equivalentes:
    TravisCI
    Jira --> Atlassian -> Bamboo
    JetBrains -> Teamcity
    Microsoft: -> AzureDevops (TFS)
    Gitlab, Github (Tienen modulos de CI/CD)
    Hudson


## Metodologías ágiles: Scrum, Kanban, XtremeProgramming

Metodologías que tienen que ver con el desarrollo y gestión de proyectos de software.
    Se basan en el concepto de iteración (SCRUM: sprint)
        De un proyecto de software vamos a identificar las tareas a realizar (requisitos) -> SACO
        Organizar los proximos 2 semanas-2 meses < 10 tareas
            -> Paso a producción. Entrego una app 100% funcional (a lo mejor con el 5% de la funcionalidad)
            Vamos entregando el producto de forma incremental
                Entrega 1 - 2 semanas: 5% de la funcionalidad total
                    10 pruebas - 5 % funcionalidad
                Entrega 2 - 4 semanas: 15% de la funcionalidad total -> Feedback
                    10 pruebas - 5 % funcionalidad
                    20 pruebas - 10 % funcionalidad
                Entrega 3 - 6 semanas: 25% de la funcionalidad total
        Iteración: 
            - Una fecha*** en la que necesito tener una serie de requisitos (funcionalidades) implementadas
    
Antes usábamos metodologías en cascada (waterfall): V, espiral...
    El proyecto lo dividíamos en fases secuenciales:
        TOMA REQUISITOS *** Es imposible conseguir una toma de requisitos perfecta
            ANALISIS Y PLAN - Diseño pruebas
                DESARROLLO
                    PRUEBAS ejecución
                        DOCUMENTACION
                            IMPLANTACION
    Diagramas de gantt
    HITO: - Una fecha en la que teníamos que tener una serie de requisitos *** (funcionalidades) implementadas
        --> Servían para controlar el avance del proyecto

## Dev--->ops
    Cultura, filosofía: Vamos a automatizar todo lo que podamos en el mundo TI
        Hoy en día devops también se utiliza para un nuevo perfil de trabajador del mundo IT: El que configura y adminsitra JENKINS o equivalentes
    
    ALM: Application Lifecycle Managment
        Planificación -> Desarrollo -> Compilación y empaquetado -> Pruebas -> Distribuirlo -> Instalarlo -> Operarlo -> Monitorizarlo
            Compilar y empaquetar apps: Lo configuran los desarrolladores
                JAVA: Maven, gradle
                C#:   MSBuild
                JS:   nodeJS   <<< npm, yarn, webpack
            Pruebas: Lo configuran los testers, Q&A...... testers 2.0
                Selenium: Automatizar pruebas en un navegador web
                    Página web: Chrome (un monton de versiones)             Windows 11              PC, tablet, telefono android, telefono ios
                                Edge                                        Windows 10
                                Firefox                                     Linux
                                Opera
                                Safari
                Appium: Automatizar pruebas en telefonos moviles.. con apps nativas
                UFT: Automatizar pruebas de una app desktop
                JMeter: Pruebas de carga y estres / LoadRunner
                SonarQube: Pruebas de calidad de código
            Instalaciones: Administradores de sistemas 2.0
                Software
                Entorno hardware: servidores, redes, configuraciones, librerias, dependencias, usuarios...puertos, firewalls
                    Ansible: Automatizar el aprovisionamiento y configuración de entornos  + Puppet, Chef
                    Terraform
                        
    ### Integración Continua CI
        Tengo mi software (su ultima version) continuamente en el entorno de INTEGRACION sometido a pruebas automatizadas
    ### Entrega Continua CD
        Poner en manos de mi cliente automatizadamente la última versión de mi software
    ### Despliegue continuo CD
        Instalar a mi cliente en producción la última versión en automático (solo porque el desarrollador ha dicho, esto está!)

    CI Continuous integration
    CD Continuous Delivery y Continuous Deployment
## Clouds
    ¿Qué es un cloud? Conjunto de servicios IT que una empresa ofrece a través de Internet de forma "automatizada"
        AWS:    Cloud amazon ****
        Azure:  Microsoft
        GPC:    Google

## Contenedores
    Instalaciones de software
    
        Procedimiento tradicional
            
            App 1 (Chrome) | App 2 (Word)               Desventajas / inconvenientes:
            -----------------------------                       - Maquina por máquina hay que hacer la instalación (TIEMPO)
                    SO (Windows)                                - App1 y App2 requieren diferentes configuraciones de SO / Librerias / Herramientas
            -----------------------------                       - Que pasa si App1 tiene un bug? CPU 100% -->> App 1 no responde
                       Hierro                                           ---> el resto de apps se cuajan!
    
        Maquinas virtuales
        
                App1   |     App2                       Desventajas / Inconvenientes:
            -----------------------------                       - Más complejidad en las instalaciones / mantenimiento
                SO     |     SO                                 - Desperdicio de recursos
            -----------------------------                       - Rendimiento
                MV 1   |     MV 2
            -----------------------------
                Hipervisor  (VMWare, Citrix, HyperV, kvm, VirtualBox...)
            -----------------------------
                        SO
            -----------------------------
                       Hierro
    
        Contenedores
    
                App1   |     App2                       
            -----------------------------               
                C 1    |     C 2
            -----------------------------
                Ejecutor de contenedor (docker, podman, crio, containerd)
            -----------------------------
                      SO Linux
            -----------------------------
                       Hierro
    
        Un contenedor solo es un ENTORNO AISLADO donde ejecutar de procesos dentro de un SO Linux
        ENTORNO AISLADO: Cada contenedor va a tener:
            - Limitación de acceso a recursos de HW
            - Su propia configuración de red, con su propia dirección IP
            - Su propio sistema de archivos, independiente del FileSystem del HOST
            - Su propio conjunto de variables de entorno
        
        Los contenedores se generan desde lo que denominamos una IMAGEN DE CONTENEDOR.
            Existen repositorios de imágenes de contenedores: docker hub
            Hoy en día TODO el software (servicios, demonios, scripts, comando) se distribuye mediante imágenes de contenedor.
            Una IMAGEN DE CONTENEDOR no es sino un fichero ZIP que contiene un software YA INSTALADO Y PRECONFIGURADO. Listo para su ejecución.
        
        Voy a instalar office en mi windows de casa. Qué hago?
            1º Descargarme el instalador de office
            Al instalar (se crean variables de entorno, registros en windows....)
            2º Ejecutarlo -> Instalación: c:\archivos de programa\office -> ZIP -> email -> descomprimis 
        
    En un entorno de producción:
        - Alta disponibilidad: Intentar cumplir con un nivel de servicio al que me habré comprometido
                90% RUINA... 10 dias 1 puede esta off... 36 dias al año...                  |   €
                99% 100 dias 1 off... 3.5 dias al año off ... PELUQUERIA DEL BARRIO         |   €€€
                99,9% 1000 dias 1 off. 8 horas al año.        RAZONABLE                     |   €€€€€€
                99,99%. Minutos al año                                                      V   €€€€€€€€€€€
        - Escalabilidad: Capacidad de ajustar mi infraestructura a las necesidades de cada momento
    
        Para conseguir esto utilizamos: Clusters: (Grupo)
        Clusters de máquinas / procesos que ofrecen simultaneamente la misma funcionalidad
            - Instalación 1: Servidor email en una maquina 1    \  balanceador de carga  < Usuarios
            - Instalación 2: Servidor email en una maquina 2    /
            - Instalación 3: Servidor email en una maquina 3   /
        
        En entornos de producción usamos herramientas que permiten gestionar granjas de ejecutores de contenedores instalados en multiples máquinas 
            KUBERNETES > Openshift
    
## Otros

Jenkins
    JAVA    .java (Cientos) -> Compilarlos, juntarlos con otras librerias, empaquetarlos
                                                                                .jar
                                                                                .war
                                                                                .ear
                                                                                
## Aplicación de software:
    
    Aplicación A - Infraestructura... Calculo y dimensiono, compro
        Dia 1:     1000 usuarios
        Dia 100:   1010 usuarios
        Dia 300:    980 usuarios
        Dia 1000:  1500 usuarios
        
    Aplicación B Lo mismo... pero será cambiante en el tiempo... de vez en cuando tengo que recalcular
        Dia 1:      100 usuarios
        Dia 100:   1000 usuarios
        Dia 300:   5000 usuarios
        Dia 1000: 15000 usuarios
        
    Aplicación C:  *** Este el mundo de hoy en dia. INTERNET. Va cambiando por minutos
        Dia n:         0 usuarios
        Dia n+1:       0 usuarios   
        Dia n+2: 2000000 usuarios               ALQUILAR HARDWARE bajo demanda
        Dia n+3:       0 usuarios   
    
    Empresa grande 10000 empleados: Gestión de nóminas
        dia 15 del mes?    0
        dia 30, 31, 1 .... todo el mundo
        
## Tipos de software:
    servicios   |
    demonios    |  Disponibles como imágenes de contenedores
    scripts     |   Es el procedimiento recomendado para hacer instalaciones por los fabricantes de software
    comando     |
-------
    aplicación
    so
    driver
    

------
#   git es un SCM < Kernel de Sistema de control de versión
     ^
    svn (subversion)
     ^
    cvs

git = Linus Torvalds + Linux
                            Google + sus librerias = Android
                            GNU => GNU/Linux    >   Redhat
                                                    Debian / Ubuntu
                                                    Suse
    git para su uso requiere de repositorios remotos. Estos son ofrecidos por apps tipo:
        - Github : Más usado a nivel mundial para software opensource + Microsoft (Funciona en el cloud)
        - Gitlab        \
        - Bitbucket     - Se utilizan mucho en el mundo empresarial. Permiten su instalación on premisses



JENKINS que sabe hacer? Mandar . Nada MAS !
    
    Si quiero que Jenkins compile un proyecto JAVA con MAVEN... que voy a necesitar?
        1º JAVA? 1.5   "1.8"  1.11          < Desarrollo
        2º MAVEN versiones de maven ... tropetantas
        3º Necesitaré instalar en Jenkins el plugin de Maven
    
    Quiero compilar una app Python: 
        1º Python 2 y 3
        2º Plugin en Jenkins ara hablar con python
    
    Alquilar unas máquinas en AWS:
        1º Terraform
                Cliente de amazon
        2º Plugin de jenkins para terraform
    
    Configurar unas maquina desde jenkins:
        1º Ansible
        2º Plugin de ansible en Jenkins


QUEREIS PROSPERAR EN EL MUNDO DEVOPS / JENKINS:
    Contenedores: DOCKER / Kubernetes (openshift) ***
    Programación BASH
    GIT o equivalente                             ***
    + Otros

