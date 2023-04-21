```yaml
resource "aws_instance" "example" {
	ami = "abc123"
	network_interface {
		# ...
	}
}

```


## Multiple proveedores diferentes

```yaml
provider "aws" {
	region = "us-east-1"
}

resource "random_integer" "rand" {
	min = 10000
	max = 99999
}

resource "aws_s3_bucket" "bucket" {
	name = "unique-name-${random_integer.rand.result}"
	...
}
```

>In this configuration, we’ve already used two separate providers to create a single S3 bucket. The `random` provider gives us a random integer for naming the bucket, and the `aws` provider gives us the S3 bucket resource


### Múltiples Instancias de un Provider

```yaml
...
resource "aws_ec2_instance" "example-west" {
	name = "instance2"
	provider = aws.west
...

}
```


### Modulo que contiene Provider

```yaml
module "vpc" {
	source = "terraform-aws-modules/vpc/aws"
	providers = {
	aws = aws.west
	}
}
```

### Agregar Providers

```yaml
terraform {
	required_providers {
		aws = {
			source = "hashicorp/aws"
			version = "~> 3.0"
		}
	}
}
```

### Agregar Provisioner 

```yaml
resource "aws_instance" "web" {

# ...
provisioner "local-exec" {
	command = "echo The server's IP address is ${self.private_ip}"
	}
}

```

### Provisioner `local-exec `
```yaml
resource "aws_instance" "web" {
# ...

provisioner "local-exec" {
	command = "echo ${self.private_ip} >> private_ips.txt"
	} 
}
```


### Provisioner `remote-exec`

```yaml
resource "aws_instance" "web" {
# ...
provisioner "remote-exec" {
inline = [
			"puppet apply",
			"consul join ${aws_instance.web.private_ip}",
		]
	}
}
```