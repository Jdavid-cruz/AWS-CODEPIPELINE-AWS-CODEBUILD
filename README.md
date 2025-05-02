Proyecto de Automatización CI/CD en AWS

Este proyecto consiste en la implementación de un flujo de trabajo CI/CD básico utilizando servicios de AWS como S3, CodePipeline y CodeBuild, integrados con GitHub como sistema de control de versiones.
Tecnologías utilizadas

    AWS S3 para el hosting del sitio web estático.

    AWS CodePipeline para la orquestación del flujo de integración continua y despliegue continuo.

    AWS CodeBuild para la fase de construcción de artefactos.

    GitHub como repositorio de código fuente.

Descripción del flujo de trabajo

Cada vez que realizo un push en la rama principal del repositorio de GitHub:

    CodePipeline detecta automáticamente el cambio mediante un webhook.

    CodeBuild descarga los archivos, los procesa según las instrucciones definidas en buildspec.yml y genera los artefactos.

    CodePipeline despliega los artefactos generados en el bucket de Amazon S3 configurado como hosting web estático.

    La actualización del sitio web es automática y no requiere intervención manual.

Estructura del repositorio

.
├── buildspec.yml    # Archivo de instrucciones para CodeBuild
├── index.html       # Página principal del sitio
├── styles.css       # Archivo de estilos
└── README.md        # Documentación del proyecto

Estado actual del proyecto

    El pipeline funciona correctamente de principio a fin.

    Los cambios realizados en GitHub se ven reflejados automáticamente en el sitio web hospedado en S3.

    La política de permisos IAM se ha ajustado para permitir operaciones de escritura (PutObject) sobre el bucket de destino.

Mejoras posibles

    Configurar un servicio de distribución de contenido (CDN) mediante CloudFront para mejorar la velocidad de carga a nivel global.

    Implementar un certificado SSL con AWS Certificate Manager para habilitar HTTPS.

    Agregar una etapa de pruebas automáticas antes de la fase de despliegue.

Consideraciones

Durante el proceso, se configuraron manualmente políticas específicas en IAM para permitir que CodePipeline y CodeBuild tuvieran acceso adecuado al bucket de S3. Además, se adaptaron los permisos necesarios para la actualización automática de los artefactos en cada despliegue.

Este proyecto representa mi primer flujo completo de CI/CD en AWS, construido desde cero, y refleja mi conocimiento actual sobre integración continua, despliegue automatizado y buenas prácticas en la nube.
