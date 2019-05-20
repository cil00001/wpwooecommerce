# wpwooecommerce
## TFG UJA 19. Contenedores: Docker + WordPress + WooCommerce + Plugins + Themes + Config

Este repositorio ha sido creado como parte de un trabajo de fin de Grado de Informática de la Universidad de Jaén en 2019.

La **idea principal** es conseguir una base para una tienda online, fabricada con contenido gratuito y funcional, apoyado por una gran comunidad de desarrolladores y usuarios que asegure que se siga actualizando y no quede obsoleta en poco tiempo.  

Utilizando el archivo [“docker-compose.yml”](https://github.com/cil00001/wpwooecommerce/blob/master/docker-compose.yml) lanzaremos unos contenedores donde trabajar para llegar a esa base. Una vez esté todo configurado, obtendremos un archivo con ayuda de un plugin que nos permitirá **migrar** nuestro sitio a otro donde despleguemos el fichero “.yml”.

Para llevar a cabo este proyecto pondremos en marcha un servidor con **WordPress** , su base de datos  **MySQL**  y para gestionarla **phpMyAdmin** , e instalaremos los **plugins** y **temas** que hallemos más interesantes, además de **configurar el sitio** siguiendo unas pautas que respeten la accesibilidad, un diseño responsive, el Reglamento General de Protección de Datos y la seguridad del sitio web. Cuando tengamos todo, crearemos distintos archivos de **backup y migración** para poder llevarlo a otras plataformas y probarlo con Docker.

### Listado de plugins y themes.

Hemos instalado y configurado estos 15 **plugins**:
- WooCommerce.
- MailChimp.
- Jetpack.
- WP Accessibility.
- GDPR.
- iThemes Security.
- UpdraftPlus WordPress Backup Plugin.
- Yoast SEO.
- Smush Image Compression and Optimization.
- Broken LInk Checker.
- WP Super Cache.
- Easy Social Icons.
- Contact Form 7.
- WP Mail SMTP by WPForms.
- All-in-One WP Migration.

Y 3 **themes**:
- Storefront (Activo).
- GeneratePress.
- Shop Isle.

## Instrucciones para desplegar el entorno

Testeado en Windows 10 y Ubuntu 18.04 LTS.

1. Copiamos el archivo [“docker-compose.yml”](https://github.com/cil00001/wpwooecommerce/blob/master/docker-compose.yml) en nuestro PC.
2. Abrimos la **consola** y navegamos hasta la ubicación del fichero: `cd ruta_del_yml`
3. Ejecutamos el ".yml" en modo background (-d): `docker-compose up -d`
4. Vamos al **navegador** y escribimos: `127.0.0.1:8080`
5. Instalamos **WordPress** con unos datos de acceso provisionales ya que al migrar tendremos los datos del entorno de desarrollo.
6. Instalamos y activamos el plugin **All-in-One WP Migration**.
7. Volvemos a la **terminal** y entramos en el contenedor con: `docker container exec -it wp bash`
8. Una vez **dentro del contenedor** escribimos: `(echo php_value upload_max_filesize 250M; echo php_value post_max_size 250M; echo php_value memory_limit 512M; echo php_value max_execution_time 400; echo php_value max_input_time 400) >> .htaccess`
9. Ahora podemos **importar** con el plugin previamente instalado el entorno configurado, hay que descomprimir el [".wpress"](https://github.com/cil00001/wpwooecommerce/tree/master/Backup%26Migration/MigrationFile_All-in-One%20WP%20Migration).
10. Una vez importado, **recargamos** la página y tendremos que acceder con el [usuario](https://github.com/cil00001/wpwooecommerce/blob/master/Backup%26Migration/Acceso) del entorno de desarrollo, nos olvidamos del temporal.
11. Si queremos gestionar la base de datos MySQL, podemos acceder a phpMyAdmin: `127.0.0.1:8084` 
12. ¡Ya tendremos nuestra tienda online lista! 

## Vídeos de funcionamiento

Aquí podéis ver algunos [vídeos](https://drive.google.com/open?id=10EOfHWG3OKoM1ptfs6G9m8H4DWsCzmpp) del despliegue y rendimiento de este proyecto en Ubuntu 18.04 LTS y Windows 10.

## Bugs

- Es posible que los enlaces permanentes se desconfiguren al migrar, el plugin da la opción de revisarlos, si no, vamos a "Ajustes/Enlaces Permanentes/" y seleccionamos "Personalizado: %postname%".

## ¿Puedo probarlo sin instalar Docker?

¡¡Sí!! hay una web que nos permite jugar con Docker sin tener que instalar nada, solo necesitaremos un usuario en [DockerHub](https://hub.docker.com/).

1. Vamos a la web de [Play with Docker](https://labs.play-with-docker.com/#).
2. Accedemos con nuestro usuario de DockerHub.
3. Le damos a "Start" para crear una nueva sesión, que tendremos durante 4 horas activa.
4. Una vez dentro le damos a la izquierda a "+ADD NEW INSTANCE".
5. Arrastramos el fichero [“docker-compose.yml”](https://github.com/cil00001/wpwooecommerce/blob/master/docker-compose.yml) hasta la terminal para subirlo.
6. Lo lanzamos con `docker-compose up -d`
7. Arriba nos saldrán los puertos activos. Nos interesan el **8080** y el **8084**, si pulsamos el primero vamos a la instalación de WordPress y desde ahí podemos seguir los pasos 5-11 antes citados  en el despliegue. También podemos ir a phpMyAdmin con el 8084.
