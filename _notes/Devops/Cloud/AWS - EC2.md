# AWS EC2
Armado de Red para EC2 [[AWS - Networking]]

## Conectarnos a una instamcia EC2 desde windows.
Usamos "mobaxterm" para conectarnos usando la SSH creada, en el caso de la instancia creada para el curso la guarde en google drive. 
El usuario que utilizamos (es el que se crea por defecto en todas las maquinas que sean basadas en imagenes Amazon), es ec2-user .

## Conectarse desde un OS basados en unix
Nos conectamos desde la terminal eje cutando la siguiente linea de comando:
### ssh -i <nombre de la llave sin mayor-menor-que que es .pem> ec2.user@00.00.00.00
	00.00.00.00 => es la ip publica de la instancia (en AWS), que se debe verificar y suplantar en cada inicio de sesion ya que es dinamica y puede haber cambiado. 
	
### Si tienes problema para conectarte puede deberse a alguno de estos inconvenientes: 
	
	
1.  Mover la clave a la carpeta ssh de su home

		mv ~/Downloads/platzi-prueba-llave.pem ~/.ssh/.


2.  Cambiar los permisos de la clave


		chmod 600 ~/.ssh/platzi-prueba-llave.pem


3.  Conectar a la instancia EC2

		ssh -i ~/.ssh/platzi-prueba-llave.pem ec2-user@[IP_PUBLICA]



