![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-002.png?fit=1107%2C803&ssl=1)

# Conexion a instancia de Amazon EC2 con MobaXterm

noviembre 7, 2018 por [Gorka Izquierdo](https://aprendiendoavirtualizar.com/author/gorka/ "Ver todas las entradas de Gorka Izquierdo")

Existen muchos clientes SSH para Windows, pero yo desde hace bastante tiempo utilizo [MobaXterm](https://mobaxterm.mobatek.net/) para mi portatil y PC fijo porque me resulta cómodo la vista, tiene muchas opciones, se puede personalizar bastante y los colores de la consola ayudan mucho, donde los directorios, ficheros, ips te los pone de diferentes colores etc etc. Si lo hago desde otro pc o servidor utilizo [putty](https://www.putty.org/) que solo pesa unos kb

Existen 2 versiones:

-   la versión Home, portable o instalable
-   la versión professional, donde viene con menos tonterías, soporte y es bastante mas personalizable, en esta versión tienes que pasar por caja.

Para conectarnos a una instancia EC2 de AWS, entramos a la consola y vamos a Key Pairs.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-001.png?resize=825%2C432&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-001.png?ssl=1)

Le damos a **Create Key Pair** y le ponemos un nombre, le damos a **Create**.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-002.png?resize=825%2C598&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-002.png?ssl=1)

Al darle a **Create**, nos generará el fichero de la clave privada con la extensión **.pem** y nos dirá donde queremos guardarlo.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-003.png?resize=825%2C464&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-003.png?ssl=1)

En la pestaña **Key Pairs** nos aparecerá la **Key** recién creada.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-004.png?resize=825%2C671&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-004.png?ssl=1)

Ahora necesitaremos crear una clave privada, los clientes SSH para Windows no admiten de forma nativa el formato de clave privada (.pem) generado por Amazon EC2.

**NOTA:** MobaXterm ahora si permite conectarte desde un cliente Windows usando el fichero **.pem**, si utilizas por ejemplo putty, tendrás que seguir las indicaciones de este articulo y crear el fichero **.ppk**.

MobaXterm tiene una herramienta llamada **MobaKeyGen**, que puede convertir claves al formato requerido (.ppk). Se debe convertir la clave privada a este formato (.ppk) antes de intentar conectarse a la instancia mediante MobaXterm u otro cliente SSH .la podemos crear desde el mismo **MobaXterm en Tools — MobaKeyGen (SSH key generator)**

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-005.png?resize=825%2C429&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-005.png?ssl=1)

Nos abrirá la herramienta y le daremos a Load para cargar el fichero **.pem** descargado anteriormente.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-006.png?resize=770%2C689&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-006.png?ssl=1)

Lo buscamos seleccionando All Files en el desplegable, ya que si no no lo veremos.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-007.png?resize=825%2C503&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-007.png?ssl=1)

Le damos a **Save private key** y nos preguntara si queremos guardarlo sin una contraseña.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-008.png?resize=479%2C619&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-008.png?ssl=1)

Nos guardara con el fichero con extensión **.ppk.**

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-009.png?resize=825%2C499&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-009.png?ssl=1)



Apuntamos el Public DNS para crear la conexión. Vamos al MobaXterm y le damos a **New Session**[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-010.png?resize=825%2C474&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-010.png?ssl=1)

Ponemos el **Public Dns** en el campo Remote Host.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-017.png?resize=825%2C600&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-017.png?ssl=1)

En la pestaña **Advanced SSH settings**, marcamos la opción de **Use private key** y añadimos la clave privada.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-018.png?resize=825%2C599&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-018.png?ssl=1)

Personalizamos la conexión con nombres, icono y descripción.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-019.png?resize=825%2C602&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-019.png?ssl=1)

Nos pedirá el usuario

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-020.png?resize=825%2C436&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-020.png?ssl=1)

Si no lo sabemos y damos a enter o metemos uno equivocado, nos mostrará un mensaje diciendo que usuario es. Normalmente es **root** o **ec2-user**, dependiendo de la AMI que tengamos.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-021.png?resize=825%2C422&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-021.png?ssl=1)

Metemos el usuario y accederemos automáticamente al autenticarnos con la clave publica.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-022.png?resize=825%2C410&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-022.png?ssl=1)

Una vez dentro, a trabajar.

[![](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-023.png?resize=825%2C483&ssl=1)](https://i0.wp.com/aprendiendoavirtualizar.com/wp-content/uploads/2018/11/Image-023.png?ssl=1)

[[ZSH + complemento Oh-My-Zsh]]