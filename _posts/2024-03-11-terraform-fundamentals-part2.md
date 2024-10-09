---
title: Terraform Fundamentals (part. 2)
author: grucci
date: 2024-03-11 -0300
img_path: /assets/img/articles/terraform-fundamentals/
categories: [IaC, Terraform, Fundamentals]
tags: [iac, terraform, fundamentals]
---

Part 2:

## Terraform Components (continuação)

### Resource

Resource (recurso) é o elemento mais importante do Terraform, é um bloco de configuração que define um ou mais objetos de infraestrutura que será criado, gerenciado ou destruído. Recursos podem representar uma ampla variedade de componentes, como instâncias de máquinas virtuais, buckets, banco de dados, redes e muito mais. Cada recurso é mapeado para uma API específica do provedor que está sendo utilizado (como AWS, Azure, GCP, etc.). 

Estrutura de um Recurso

Um bloco de recurso no Terraform é definido com o seguinte formato básico:

```main.tf
1 resource "<tipo_do_recurso>" "<nome_lógico>" {
2 # Configurações e parâmetros do recurso
3 }
```

* Tipo do recurso: Especifica o tipo de recurso que está sendo criado. Isso é específico do provedor em uso. Por exemplo, aws_instance para criar uma instância EC2 na AWS ou azurerm_virtual_network para criar uma rede virtual no Azure

* Nome lógico: Um nome que você escolhe para referenciar o recurso dentro do código Terraform. Este nome deve ser único dentro do módulo onde é definido.

* Configurações e parâmetros: Dentro do bloco, você define os atributos específicos do recurso, como tamanho da instância, nome da máquina, configuração de rede, etc.

#### Exemplo de Recurso

Aqui está um exemplo de um recurso que cria uma instância EC2 na AWS:

``` main.tf
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"  # ID da imagem da máquina (AMI)
  instance_type = "t2.micro"               # Tipo da instância

  tags = {
    Name = "MyExampleInstance"             # Tag para nomear a instância
  }
}
```

Neste exemplo:

O tipo do recurso é aws_instance.

O nome lógico do recurso é example.

O bloco define que a instância será criada usando uma imagem específica (AMI) e será do tipo t2.micro.

#### Funcionalidades dos Recursos

* Criação e Destruição: O Terraform cria ou destrói recursos conforme definido na configuração, aplicando as mudanças necessárias para alinhar a infraestrutura ao estado desejado.

``` main.tf
resource "aws_instance" "my_instance" {
  ami           = "ami-0c55b159cbfafe1f0"  # ID da AMI (imagem da máquina)
  instance_type = "t2.micro"               # Tipo da instância
}

# O Terraform cria essa instância com o comando terraform apply.
# Se esse recurso for removido (ou comentado) do código e terraform apply for executado novamente, o Terraform destruirá a instância, já que ela não faz mais parte da configuração.HCL
```

* Referenciamento: Recursos podem ser referenciados em outras partes da configuração do Terraform. Por exemplo, você pode criar um recurso de rede e, em seguida, referenciar essa rede ao criar uma instância de máquina virtual.

``` main.tf
# Definindo um grupo de segurança
resource "aws_security_group" "my_sg" {
  name        = "example-security-group"
  description = "Security group for my instance"

  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]   # Permitir SSH de qualquer IP
  }
}

# Referenciando o security group ao criar a instância EC2
resource "aws_instance" "my_instance" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  # Referenciando o ID do grupo de segurança
  vpc_security_group_ids = [aws_security_group.my_sg.id]
}

# Aqui, o grupo de segurança aws_security_group.my_sg é criado primeiro.
# A instância aws_instance.my_instance usa o ID do grupo de segurança criado no campo vpc_security_group_ids.HCL
```

* Provisionamento e Configuração: Além de criar recursos, você pode usar o Terraform para executar scripts ou comandos de provisionamento após a criação de um recurso, configurando-o conforme necessário.

``` main.tf
resource "aws_instance" "web" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  user_data = <<-EOF
    #!/bin/bash
    sudo apt-get update
    sudo apt-get install -y nginx
  EOF

  tags = {
    Name = "WebServer"
  }
}

# Após a criação da instância, o Terraform provisiona o servidor com o Nginx usando o user_data.HCL
```

#### Recursos Dinâmicos e Módulos

Recursos podem ser criados de forma dinâmica usando loops (count, for_each) ou podem ser organizados em módulos reutilizáveis para manter as configurações DRY (Don't Repeat Yourself). Isso permite que você escale a criação de infraestrutura e mantenha suas configurações bem organizadas.

* Count: Você pode usar o count para criar dinamicamente múltiplos recursos, como várias instâncias EC2

* For_each: O for_each permite criar recursos com base em uma lista ou mapa de valores.

``` Criação Dinâmica de Vários Recursos (usando count)
# Este código cria 3 instâncias EC2, cada uma com um nome único (WebServer-0, WebServer-1, etc.)
resource "aws_instance" "web_servers" {
  count         = 3                            # Criar 3 instâncias
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "WebServer-${count.index}"          # Nome único para cada instância
  }
}
```

``` Criação de Recursos (usando for_each)# O for_each cria uma instância para cada chave no mapa instance_types, usando o valor correspondente para o instance_type.
variable "instance_types" {
  type    = map(string)
  default = {
    "small"  = "t2.micro"
    "medium" = "t2.small"
    "large"  = "t2.medium"
  }
}

resource "aws_instance" "web_servers" {
  for_each      = var.instance_types
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = each.value

  tags = {
    Name = "WebServer-${each.key}"   # Nomeia a instância com base no tipo
  }
}
```

#### Interdependências entre Recursos

O Terraform automaticamente entende as dependências entre os recursos com base nas referências utilizadas. Isso garante que os recursos sejam criados na ordem correta. Por exemplo, se uma instância de máquina virtual depende de uma rede, o Terraform cria primeiro a rede antes de provisionar a instância.

``` main.tf
resource "aws_instance" "my_instance" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

# Esta instância só será criada após o recurso 'aws_security_group.my_sg' ser criado
  depends_on = [aws_security_group.my_sg]
}

# O depends_on garante que a instância só seja criada após o grupo de segurança estar completamente provisionado.HCL
```

- Data Sources
- Variables
- Output
- Dynamic Block
