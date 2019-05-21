# wpwooecommerce
## TFG UJA 19. Contenedores: Docker + WordPress + WooCommerce + Plugins + Themes + Config

Este repositorio ha sido creado como parte de un trabajo de fin de Grado de Informática de la Universidad de Jaén en 2019.

La **idea principal** es conseguir una base para una tienda online, fabricada con contenido gratuito y funcional, apoyado por una gran comunidad de desarrolladores y usuarios que asegure que se siga actualizando y no quede obsoleta en poco tiempo.  

Utilizando el archivo [“docker-compose-ini.yml”](https://github.com/cil00001/wpwooecommerce/blob/data-container-mode/docker-compose-ini.yml) lanzaremos unos contenedores donde trabajar para llegar a esa base. Una vez esté todo configurado, haremos un commit de los contenedores de la base de datos y WordPress para obtener las imágenes que subiremos a DockerHub. Con otro [docker-compose.yml](https://github.com/cil00001/wpwooecommerce/blob/data-container-mode/docker-compose-ini.yml)  asociado a estas imágenes podremos llevar nuestro sitio a otro.

Para llevar a cabo este proyecto pondremos en marcha un servidor con las [imágenes oficiales modificadas](https://github.com/cil00001/wpwooecommerce/tree/data-container-mode/ImagenesPersonalizadas) para quitarles los volúmenes: **[WordPress](https://hub.docker.com/_/wordpress)** , su base de datos  **[MySQL](https://hub.docker.com/_/mysql)**  y para gestionarla **[phpMyAdmin](https://hub.docker.com/r/phpmyadmin/phpmyadmin)** . Instalaremos los **plugins** y **temas** que hallemos más interesantes desde el repositorio oficial, además de **configurar el sitio** siguiendo unas pautas que respeten la accesibilidad, un diseño responsive, el Reglamento General de Protección de Datos y la seguridad del sitio web. 

Cuando tengamos todo, crearemos distintos archivos de **[backup y migración](https://github.com/cil00001/wpwooecommerce/tree/data-container-mode/Backup%26Migration)**, haremos commit de los contenedores MySQL y WordPress para crear unas imágenes que subir a Docker Hub y así poder llevar el sitio a otras plataformas.

### Listado de plugins y themes.

Hemos instalado y configurado estos 15 **plugins**:
- [WooCommerce](https://es.wordpress.org/plugins/woocommerce/)
- [MailChimp](https://es.wordpress.org/plugins/woocommerce-mailchimp/)
- [Jetpack](https://es.wordpress.org/plugins/jetpack/)
- [WP Accessibility](https://es.wordpress.org/plugins/wp-accessibility/)
- [GDPR](https://es.wordpress.org/plugins/gdpr/)
- [iThemes Security](https://es.wordpress.org/plugins/better-wp-security/)
- [UpdraftPlus WordPress Backup Plugin](https://es.wordpress.org/plugins/updraftplus/)
- [Yoast SEO](https://es.wordpress.org/plugins/wordpress-seo/)
- [Smush Image Compression and Optimization](https://es.wordpress.org/plugins/wp-smushit/)
- [Broken LInk Checker](https://es.wordpress.org/plugins/broken-link-checker/)
- [WP Super Cache](https://es.wordpress.org/plugins/wp-super-cache/)
- [Easy Social Icons](https://es.wordpress.org/plugins/easy-social-icons/)
- [Contact Form 7](https://es.wordpress.org/plugins/contact-form-7/)
- [WP Mail SMTP by WPForms](https://es.wordpress.org/plugins/wp-mail-smtp/)
- [All-in-One WP Migration](https://es.wordpress.org/plugins/all-in-one-wp-migration/)
- [Better Search Replace](https://es.wordpress.org/plugins/better-search-replace/)

Y 3 **themes**:
- [Storefront](https://es.wordpress.org/themes/storefront/) (Activo)
- [GeneratePress](https://es.wordpress.org/themes/generatepress/)
- [Shop Isle](https://es.wordpress.org/themes/shop-isle/)

## Instrucciones para desplegar el entorno

Testeado en Windows 10 y Ubuntu 18.04 LTS.

1. Copiamos el archivo [“docker-compose.yml”](https://github.com/cil00001/wpwooecommerce/blob/data-container-mode/docker-compose.yml) en nuestro PC.
2. Abrimos la **consola** y navegamos hasta la ubicación del fichero: `cd ruta_del_yml`
3. Ejecutamos el ".yml" en modo background (-d): `docker-compose up -d`
4. Vamos al **navegador** y escribimos: `localhost:8080`
5. Accedemos con el [usuario](https://github.com/cil00001/wpwooecommerce/blob/data-container-mode/Backup%26Migration/Acceso).
11. Si queremos gestionar la base de datos MySQL, podemos acceder a phpMyAdmin: `127.0.0.1:8084` 
12. ¡Ya tendremos nuestra tienda online lista! 

## ¿Puedo probarlo sin instalar Docker?

¡¡Sí!! hay una web que nos permite jugar con Docker sin tener que instalar nada, solo necesitaremos un usuario en [DockerHub](https://hub.docker.com/).

1. Vamos a la web de [Play with Docker](https://labs.play-with-docker.com/#).
2. Accedemos con nuestro usuario de DockerHub.
3. Le damos a "Start" para crear una nueva sesión, que tendremos durante 4 horas activa.
4. Una vez dentro le damos a la izquierda a "+ADD NEW INSTANCE".
5. Arrastramos el fichero [“docker-compose.yml”](https://github.com/cil00001/wpwooecommerce/blob/data-container-mode/docker-compose.yml) hasta la terminal para subirlo.
6. Lo lanzamos con `docker-compose up -d`
7. Arriba nos saldrán los puertos activos. Nos interesan el **8080** y el **8084**.
8. Como ha sido desarrollado en localhost:8080, tendremos que ir a phpMyAdmin y cambiar la dirección del sitio a la que nos proporcione la web.

## Vídeos de muestra y rendimiento

Aquí podéis ver algunos [vídeos](https://drive.google.com/open?id=10EOfHWG3OKoM1ptfs6G9m8H4DWsCzmpp) del despliegue y rendimiento de este proyecto en Ubuntu 18.04 LTS y Windows 10.

## Problemas conocidos

- Es posible que los enlaces permanentes se desconfiguren al migrar, el plugin da la opción de revisarlos, si no, vamos a "Ajustes/Enlaces Permanentes/" y seleccionamos "Personalizado: %postname%".
- Con ayuda del plugin "Better Search Replace" podremos cambiar la dirección localhost:8080 por la que nos convenga en la base de datos.
