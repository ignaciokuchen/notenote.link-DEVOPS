# Crear una instancia en AWS desde Terraform 

### Primero Instalamos Terraform
[[Codigo como infra - Terraform - Packer]]

## Creamos el main.tf
##### Primero indicamos el proveedor en la web de terraform podemos buscar todos los proveedores soporetedos. Y luego tenemos los recursos (resource). Los parametreos y valores dependen del provider.


		provider "aws" {
			version = "~> 2.7"
			region  = "us-east-2"
			}
		resource "aws\_instance" "web" { 
			ami = "ami-077e31c4939f6a2f3"
			instance\_type = "t2.micro"
			// tags = {
			//   Name = "devops-one"
			// }
			}

		output "public\_ip" {
			value = "${aws\_instance.web.public\_ip}"
		}
		
		// output "private\_ip" {
		//   value = "${aws\_instance.web.private\_ip}"
		// }

#### Ejecutar en la misma carpeta donde se encuentra el main.tf

#### Iniciamos Terraform
	terraform init
	
#### Hacemos el Planing (Esto lee el archivo para saber que se va a realizar (es como un compilado))

	terraform plan
	
#### Aplicamos (Aqui es donde se ejecuta el codigo)
	
	terraform apply
	
#### Verificamos en AWS console, que la instancia esté creada

#### Para destruir  usamos el comando destroy, pero lo que va a destruir es segun el archivo que hayamos usado en el ultimo planing. 

#### Esto quiere decir que si lo que queremos es destruir la ultima/s instancia/s creadas, en el ultimo planing. Dejamos el archivo .tf como esta y apliicamos a continuacion 
	terraform destroy
	
#### Sin embargo si queremos destruir parcialmente la creacion u otra instancia que sea anterior debemos, modificar el archivo .tf. Indicando las instancias a destruir. 

### Luego ejecutamos 
		terraform plan
		
### y por ultimo 
		terraform destroy
		
## Aqui podemos encontrar mas detalles sobre destroy 
**[https://www.terraform.io/docs/cli/commands/destroy.html](https://www.terraform.io/docs/cli/commands/destroy.html)**


</br>
</br>

 # Otro ej de main.tf


		resource "aws\_instance" "web1" {  
    		ami = "${lookup(var.AMI, var.AWS\_REGION)}"  
    		instance\_type = "t2.micro" 
			
			# VPC  
    		subnet\_id = "${aws\_subnet.prod-subnet-public-1.id}" 
			
			# Security Group  
    		vpc\_security\_group\_ids = \["${aws\_security\_group.ssh-allowed.id}"\] 
			
			# the Public SSH key  
    		key\_name = "${aws\_key\_pair.london-region-key-pair.id}" # nginx installation  
   			 provisioner "file" {  
   					source = "nginx.sh"  
        			destination = "/tmp/nginx.sh"  
    		} 
			provisioner "remote-exec" {  
        			inline = [  
             				"chmod +x /tmp/nginx.sh",  
            	 			"sudo /tmp/nginx.sh"  
        				]  
    				} 
			connection {  
        			user = "${var.EC2\_USER}"  
        			private\_key = "${file("${var.PRIVATE\_KEY\_PATH}")}"  
    		}  
	}
	
	// Sends your public key to the instance  
	resource "aws\_key\_pair" "london-region-key-pair" {  
    		key\_name = "london-region-key-pair"  
    		public\_key = "${file(var.PUBLIC\_KEY\_PATH)}"  
	}