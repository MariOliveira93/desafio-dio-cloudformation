# desafio-dio-cloudformation

Este projeto contém templates AWS CloudFormation para criar instâncias EC2, servidores Apache, grupos de segurança, buckets S3 e usuários/grupos IAM.

## Estrutura de Pastas

- `templates/`: Contém todos os templates YAML do CloudFormation.
- `.gitignore`: Ignora arquivos de configuração do IDE.

## Pré-requisitos

- Conta AWS
- AWS CLI instalado e configurado
- Par de chaves EC2 existente (para acesso SSH)

## Como Utilizar

1. **Escolha o template**
   - Acesse a pasta `templates/`.
   - Escolha o template desejado (ex: `EC2.yaml`).

2. **Crie uma stack**
   - Execute o comando abaixo, substituindo `<nome-da-stack>`, `<arquivo-template>` e `<nome-da-chave>` conforme necessário:

     ```bash
     aws cloudformation create-stack \
       --stack-name <nome-da-stack> \
       --template-body file://<arquivo-template> \
       --parameters ParameterKey=KeyName,ParameterValue=<nome-da-chave>
     ```
   - Para templates com mais parâmetros, adicione-os em `--parameters`.

3. **Verifique o status da stack**
   ```bash
   aws cloudformation describe-stacks --stack-name <nome-da-stack>
   ```

4. **Exclua a stack**
   ```bash
   aws cloudformation delete-stack --stack-name <nome-da-stack>
   ```

## Templates Disponíveis

- `EC2.yaml`: Instância EC2 simples.
- `Apache.yaml`: Instância EC2 com Apache instalado.
- `Firewall.yaml`: EC2 com grupo de segurança HTTP.
- `EC2_S3_UserGroup.yaml`: EC2, bucket S3, usuário e grupo IAM.

## Licença

MIT
