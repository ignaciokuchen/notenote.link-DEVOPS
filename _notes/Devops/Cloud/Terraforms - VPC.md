---
title: Terraform - VPC
season: summer
tags: Devops Terraform VPC Cloud
toc: true
comments: true
---
# Crear una VPC desde terraform

## Primero hay que tener instalado Terraform 
[[Codigo como infra - Terraform - Packer]]

##  Create <u> vars.tf</u> -- Creamos un archivo para las variables

	variable "AWS_REGION" { 
		default = "eu-west-2"
	}

##  Create <u>provider.tf</u>
### Toda la infraestructura estará en AWS. Si desea utilizar otro proveedor de nube como GCP o Azure debe cambiar esto.
Usaremos variables en esta demostración. Más tarde, verá el archivo vars.tf y las variables que contiene. Ahora, var.AWS_REGION = eu-west-2 es suficiente.

		provider "aws" {  
			region = "${var.AWS_REGION}"  
		}



#### Incializamos Terraform
		terraform init
	
</br></br></br>
## Create vpc.tf   -- Generamos e archivo para la networking

</br>


### <u>Creamos la VPC</u>

##### <em>cidr_block: 10.0.0.0/16 le permite usar la dirección IP que comienza con "10.0.X.X". Hay 65.536 direcciones IP listas para usar.</em>

#### instance_tenancy si es verdadero, su ec2 será la única instancia en un hardware físico de AWS. Suena bien, pero es caro.

	resource “aws_vpc” “prod-vpc” { 
		cidr_block = “10.0.0.0/16”
		enable_dns_support = “true” #gives you an internal domain name
		enable_dns_hostnames = “true” #gives you an internal host name
		enable_classiclink = “false”  
		instance_tenancy = “default” 
		tags {  
			Name = “prod-vpc”  
		}
	}

## Create Public Subnet
#### Seguimos en vpc.tf

vpc_id: Esta  sera una subnet de la vpc recien creada. Y le pasamos el nombre de la VPC. 

cidr_block: 10.0.1.0/24. Tendremos 254 direciones IP deiponibles, en esta Subnet

map_public_ip_on_launch:  esta linea es importante ya que es la que diferencia una red publica de una privada. Si colocamos true sera una subnet publica, de lo contrario sera privada. 

		resource “aws_subnet” “prod-subnet-public-1” {  
    		vpc_id = “${aws_vpc.prod-vpc.id}”  
    		cidr_block = “10.0.1.0/24”  
    		map_public_ip_on_launch = “true” //it makes this a public subnet  
    		availability_zone = “eu-west-2a” 
			
			tags {  
        		Name = “prod-subnet-public-1”  
    		}  
		}
		
		


##  Create Internet Gateway "IGW"
### Creamos <u>network.tf</u>

Esto nos permitira conectar nuestra VPC a internet
		
		resource "aws_internet_gateway" "prod-igw" {  
			vpc_id = "${aws_vpc.prod-vpc.id}"  
			tags {  
				Name = "prod-igw"  
			}  
			}
			
## Create Custom Route Table "CRT"
### Seguimos en network.tf

Crearemos una tabla de enrutamiento (route table) para la subnet publica. Esta subnet podra usar este para llegar a internet. 

		resource "aws_route_table" "prod-public-crt" {  
    		vpc_id = "${aws_vpc.main-vpc.id}"  
      
    		route {  
       			 //associated subnet can reach everywhere  
       			 cidr_block = "0.0.0.0/0" 
				 
				 //CRT uses this IGW to reach internet  
        			gateway_id = "${aws_internet_gateway.prod-igw.id}" 
   				 	}  
     			tags {  
        			Name = "prod-public-crt"  
    				}  
				}
				
	
	
## Asociamos el CRT y la subnet
### Seguimos con <u>network.tf</u>

	resource "aws_route_table_association" "prod-crta-public-subnet-1"{  
		subnet_id = "${aws_subnet.prod-subnet-public-1.id}"  
		route_table_id = "${aws_route_table.prod-public-crt.id}"  
	}
	


## Create a Security Group
### Seguimos con <u>network.tf</u>

Usaremos este grupo de seguridad para nuestra EC2.

Si queremos acceder al EC2 mediante SSH, podemos abrir el puerto 22 para todo internet. Leer los comentarios que estan sobre cidr_blocks.
Ademas podremos llegar a NGINX, ya que podemos abrie el puerto 80. 

		resource "aws_security_group" "ssh-allowed" {  
    		vpc_id = "${aws_vpc.prod-vpc.id}"  
      
    		egress {  
        		from_port = 0  
        		to_port = 0  
        		protocol = -1  
        		cidr_blocks = ["0.0.0.0/0"]  
   			} 
			ingress {  
       			from_port = 22  
        		to_port = 22  
        		protocol = "tcp" // This means, all ip address are allowed to ssh !   
        		// Do not do it in the production.   
        		// Put your office or home address in it!  
        		cidr_blocks = ["0.0.0.0/0"]  
    		} 
			
	//If you do not add this rule, you can not reach the NGIX    
    		ingress {  
        		from_port = 80  
        		to_port = 80  
       	 		protocol = "tcp"  
        		cidr_blocks = ["0.0.0.0/0"]  
    		} 
			
			tags {  
        		Name = "ssh-allowed"  
    		}  
	}
