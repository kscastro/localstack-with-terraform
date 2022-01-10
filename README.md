# Terraform com Localstack exemplo com lambda

## Antes de começar você vai precisar ter instalado os projetos listados abaixo:

[Docker](https://www.docker.com/) <br />
[Terraform](https://www.terraform.io/) <br />
[Localstack](https://github.com/localstack/localstack)<br />
[Aws cli](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

## Rodando o projeto

### Parte Localstack

Uma vez que tenha todos os aplicativos instalados abra o terminal e rode o comando abaixo:

```docker
docker-compose up
```

Este comando vai subir o localstack em um docker

### Parte Terraform

Em outro terminal rode os comandos abaixo:

```terraform

terraform init
terraform plan

```

Depois desses passos no mesmo terminal cole os export abaixo :

```
export AWS_SECRET_ACCESS_KEY=secret_key
export AWS_ACCESS_KEY_ID=access_key
export AWS_DEFAULT_REGION=us-west-2
```

Agora rode o comando de apply

```
terraform apply
```

Apos rodar esse comando digite `yes` para confirmar a subida da infra.

Rode o comando abaixo para invocar o lambda

```
aws --endpoint-url=http://localhost:4566 lambda invoke --function=test_lambda --payload fileb://example.json outputfile.txt
```
