---
title: Terraform Fundamentals (part. 3)
author: grucci
date: 2024-03-11 -0300
img_path: /assets/img/articles/terraform-fundamentals/
categories: [IaC, Terraform, Fundamentals]
tags: [iac, terraform, fundamentals]
---

Part 3:

## Terraform Components (continuação)

### Variables

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
- Variables
- Output
- Dynamic Block
