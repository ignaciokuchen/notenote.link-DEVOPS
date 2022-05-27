
# Terraform 
<u>Terraform</u> Utiliza las API de los provider para conectarse a ellos y realizar las tareas que le indiquemos. 

## Instalamos Terraform
Desde esta pag podemos descargar Terraform
**[https://www.terraform.io/downloads.html](https://www.terraform.io/downloads.html)**

### Linux
	sudo wget https://releases.hashicorp.com/terraform/0.13.0/terraform\_0.13.0\_linux\_amd64.zip
	

	unzip terraform\_0.13.0\_linux\_amd64.zip
	
	sudo cp terraform /usr/local/bin/terraform
	
	cd /usr/local/bin
	
	echo $"exportPATH=\\$PATH:/usr/local/bin" >> ~/.bash\_profilesource~/.bash\_profile

 
	
	
### Windows 
**[https://releases.hashicorp.com/terraform/0.15.3/terraform\_0.15.3\_windows\_amd64.zip](https://releases.hashicorp.com/terraform/0.15.3/terraform_0.15.3_windows_amd64.zip)**

		C:\\Users\\Mi\_user> md terraform
		C:\\Users\\Mi\_user>cd terraform
		

	set path "%path%;{path\_al\_terraform}” 

o abrir una nueva terminal (con “cmd”)

## AWS CLI



[https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-using.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-using.html)

[https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)

[https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html)

  

windows

[https://awscli.amazonaws.com/AWSCLIV2.msi](https://awscli.amazonaws.com/AWSCLIV2.msi)

linux

[https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html)

Mac

[https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-mac.html](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-mac.html)


**[https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html)**

	aws configure
	
	
## Terraform

[https://www.terraform.io/docs/cli/index.html](https://www.terraform.io/docs/cli/index.html)

#### Crear y editar un archivo que se llame main.tf
[[Terraforms - EC2]]
[[Terraforms - VPC]]


# Packer
Packer es una herramienta para construir infraestructura inmutable desarrollada por HashiCorp que nos va a permitir crear imágenes en cualquier proveedor de nube.

## Elementos de Packer

-   `variables`: tal como su nombre lo indica, aquí definimos las variables que vamos a utilizar.
-   `builders`: indicamos de donde vamos a construir nuestra imagen base.
-   `provisioners`: acá personalizamos nuestra imagen, añadir paquetes, crear directorios, definir el estado de la infraestructura, etc.
-   `post-processors`: podemos tener archivos de salida y ejecutar comandos después de haber creado la infraestructura, todo corre de manera local.


Descargar binario 
https://www.packer.io/downloads

Instalar Packer
https://learn.hashicorp.com/tutorials/packer/get-started-install-cli
