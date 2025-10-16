# V Desafio de Projeto - Executando Tarefas Automatizadas com AWS Lambda e S3

## Descrição do Projeto

Este repositório contém anotações, exemplos e aprendizados adquiridos durante o projeto **Executando Tarefas Automatizadas com AWS Lambda e S3**. O objetivo do projeto é explorar a integração entre **AWS Lambda** e o serviço de **armazenamento Amazon S3**, permitindo a automação de tarefas como processamento de arquivos, geração de logs, notificações e muito mais, tudo sem a necessidade de gerenciar servidores, aproveitando a escalabilidade e flexibilidade do ambiente **serverless**.

## O que é o AWS Lambda?

O **AWS Lambda** é um serviço de computação **serverless** (sem servidor) que permite executar código automaticamente em resposta a eventos, como **uploads em buckets S3**, alterações em **bancos de dados**, chamadas **HTTP via API Gateway**, entre outros. Ao usar o Lambda, você escreve a função, define o gatilho e o Lambda cuida da execução, escalabilidade e gerenciamento de recursos, permitindo focar apenas no código e na lógica de negócios.

### Principais Características do AWS Lambda:
- **Serverless**: Não é necessário provisionar nem gerenciar servidores.
- **Escalabilidade Automática**: O Lambda escala automaticamente em resposta à carga.
- **Execução sob Demanda**: O código é executado em resposta a eventos sem a necessidade de uma instância dedicada.

## O que é o Amazon S3?

O **Amazon S3** (Simple Storage Service) é um serviço de **armazenamento de objetos** altamente escalável e seguro. Ele é ideal para armazenar arquivos, imagens, logs, backups, dados estáticos e muito mais. O S3 oferece **alta durabilidade**, **escalabilidade** e **segurança**, permitindo gerenciar grandes volumes de dados de forma eficiente.

O S3 pode ser integrado com o AWS Lambda para **automatizar ações** sempre que arquivos são carregados, modificados ou excluídos de um bucket.

### Casos de uso comuns:
- **Armazenamento de backups e logs**
- **Processamento de imagens, vídeos e outros arquivos**
- **Armazenamento de dados estáticos como sites e aplicativos**

## Integração Lambda + S3

A integração entre **Lambda** e **S3** permite que uma função Lambda seja disparada automaticamente sempre que um evento ocorrer em um **bucket S3**. Isso é útil para automatizar processos que envolvem arquivos, como:

- **Processar imagens** após upload (ex: redimensionar, converter, etc.).
- **Validar ou transformar arquivos CSV** antes de armazenar em banco de dados.
- **Gerar notificações** ou logs quando arquivos são adicionados ou modificados.
- **Criar thumbnails** de vídeos ou imagens.
- **Indexar documentos** para facilitar a busca e a organização.

## Estrutura do Projeto

| Componente      | Descrição                                                       |
|-----------------|-----------------------------------------------------------------|
| **Bucket S3**   | Armazena os arquivos que disparam eventos.                     |
| **Função Lambda** | Código que será executado automaticamente em resposta ao evento. |
| **Trigger/Event** | Configuração que conecta o evento do S3 à função Lambda.        |
| **IAM Role**    | Permissões que permitem à função Lambda acessar o S3 e outros recursos. |

## Fluxo de Implementação

1. **Criar um bucket no Amazon S3**: Armazene os arquivos que irão disparar os eventos.
2. **Criar uma função Lambda**: Escolha a linguagem desejada (por exemplo, Python ou Node.js) e escreva a função para processar os dados.
3. **Definir o gatilho (Trigger)**: Configure um evento de **PUT** (upload) no bucket S3 para acionar a função Lambda.
4. **Criar uma Role IAM**: Defina permissões de leitura/escrita no bucket S3 para a função Lambda.
5. **Testar o fluxo**: Envie um arquivo para o S3 e verifique a execução da função Lambda.
6. **Monitorar logs**: Utilize o **Amazon CloudWatch** para monitorar a execução e os logs da função Lambda.

## Exemplo de Código (Python)

Este exemplo mostra como usar o **AWS Lambda** para copiar automaticamente arquivos de um bucket S3 para outro quando um arquivo é carregado.

```python
import json
import boto3
import logging

# Configurar o cliente do S3
s3 = boto3.client('s3')

# Configurar o logger
logger = logging.getLogger()
logger.setLevel(logging.INFO)

def lambda_handler(event, context):
    # Extrair informações do evento do S3
    bucket = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']
    
    # Gerar log com informações sobre o arquivo carregado
    logger.info(f"Arquivo {key} foi carregado no bucket {bucket}")
    
    # Recuperar os metadados do arquivo
    metadata = s3.head_object(Bucket=bucket, Key=key)
    
    # Logar os metadados (exemplo de tamanho do arquivo)
    file_size = metadata['ContentLength']
    logger.info(f"Tamanho do arquivo: {file_size} bytes")
    
    # Criar um log em formato JSON com os dados do evento
    log_entry = {
        'event': 'Arquivo carregado',
        'bucket': bucket,
        'key': key,
        'file_size': file_size
    }
    
    # Enviar o log para um bucket S3 (poderia ser um log de aplicação ou um arquivo de auditoria)
    log_bucket = 'bucket-para-logs'
    log_key = f"logs/{key}_log.json"
    s3.put_object(Bucket=log_bucket, Key=log_key, Body=json.dumps(log_entry))
    
    return {
        'statusCode': 200,
        'body': json.dumps(f'Log do arquivo {key} gerado com sucesso!')
    }

