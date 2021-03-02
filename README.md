# HTTPS-Certbot
#Práctica: HTTPS con Let’s Encrypt y Certbot

En esta práctica vamos a habilitar el protocolo HTTPS en un sitio web WordPress que se estará ejecutando en una instancia EC2 de Amazon Web Services (AWS).
1.1 Conceptos básicos
1.1.1 ¿Qué es HTTPS?

HTTPS (Hyptertext Transfer Protocol Secure) o protocolo seguro de transferencia de hipertexto, es un protocolo de la capa de aplicación basado en el protocolo HTTP, destinado a la transferencia segura de datos de hipertexto. (Fuente: Wikipedia)

Para poder habilitar el protocolo HTTPS en un sitio web es necesario obtener un certificado de seguridad. Este certificado tiene que ser emitido por una autoridad de certificación (AC). En esta práctica vamos a obtener un certificado para un dominio de la Autoriidad de Certificación Let’s Encrypt.
1.1.2 ¿Qué es Let’s Encrypt?

Let’s Encrypt​ es una autoridad de certificación que se puso en marcha el 12 de abril de 2016 y que proporciona certificados X.509 gratuitos para el cifrado de seguridad de nivel de transporte (TLS) a través de un proceso automatizado diseñado para eliminar el complejo proceso actual de creación manual, la validación, firma, instalación y renovación de los certificados de sitios web seguros. (Fuente: Wikipedia)
1.1.3 Cómo funciona Let’s Encrypt

Se recomienda la lectura de la sección Cómo Funciona Let’s Encrypt de la documentación oficial.
1.1.4 ¿Qué es Certbot?

Para poder obtener un certificado de Let’s Encrypt para un dominio de un sitio web es necesario demostrar que se tiene control sobre ese dominio. Para realizar esta tarea es necesario utilizar un cliente del protocolo ACME (Automated Certificate Management Environment). El cliente ACME recomendado para esta tarea es Certbot porque es fácil de usar, tiene soporte para muchos sistemas operativos y dispone de una excelente documentación.
1.3 Tareas a realizar

    Crear una instancia EC2 en Amazon Web Services (AWS). imagen Cuando esté creando la instancia deberá configurar los puertos que estarán abiertos para poder conectarnos por SSH y para poder acceder por HTTP/HTTPS.

    SSH (22/TCP)
    HTTP (80/TCP)
    HTTPS (443/TCP) imagen

    Registrar un nombre de dominio en algún proveedor de nombres de dominio gratuito. Por ejemplo, puede hacer uso de Freenom. imagen

    Obtener la dirección IP pública de su instancia EC2 en AWS. imagen

    Configurar los registros DNS del proveedor de nombres de dominio para que el nombre de dominio de ha registrado pueda resolver hacia la dirección IP pública de su instancia EC2 de AWS. imagen

    A continuación, instala wordpress: imagen

    Instalar y configurar el cliente ACME Certbot en su instacia EC2 de AWS, siguiendo los pasos de la documentación oficial. imagen

Una vez llegado hasta este punto tendríamos nuestro sitio web con HTTPS habilidado y todo configurado para que el certificado se vaya renovando automáticamente.

Con el siguiente comando podemos comprobar que hay un temporizador en el sistema encargado de realizar la renovación de los certificados de manera automática.

systemctl list-timers

    Reemplazamos las direcciones

wp search-replace 'http://la ip publica' 'https://nombre del dominio'

imagen
Este seria el resultado:

imagen
fuente:

https://josejuansanchez.org/iaw/
