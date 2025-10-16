# Implementando Infraestrutura Automatizada com AWS CloudFormation

## Descrição do Projeto

Este repositório contém as anotações e práticas realizadas durante o desafio de **Implementação de Infraestrutura Automatizada com AWS CloudFormation**. O objetivo deste projeto é aplicar os conceitos de **Infraestrutura como Código (IaC)** utilizando o serviço **AWS CloudFormation** para criar, configurar e gerenciar recursos de forma automatizada e segura, proporcionando um processo eficiente e escalável para a construção de ambientes na AWS.

## O que é o AWS CloudFormation?

O **AWS CloudFormation** é um serviço que permite criar e provisionar infraestrutura na AWS através de arquivos de template escritos em **JSON** ou **YAML**. Esses templates descrevem todos os recursos desejados (como **instâncias EC2**, **buckets S3**, **roles IAM**, entre outros) e possibilitam sua criação de maneira repetível, versionável e auditável, garantindo consistência no ambiente de desenvolvimento.

## Benefícios Principais

- **Automação:** Elimina a necessidade de configurações manuais e reduz o tempo gasto na criação de recursos.
- **Consistência:** Garante que os ambientes sejam criados de forma padronizada e sem variações indesejadas.
- **Escalabilidade:** Facilita a replicação de ambientes em diferentes regiões ou contas AWS.
- **Segurança:** Aplica configurações seguras e controladas via código, garantindo conformidade com as políticas de segurança.
- **Auditoria:** Permite versionamento e rastreamento de alterações na infraestrutura, facilitando auditorias e acompanhamento de modificações.

## Estrutura Básica do CloudFormation

| Componente  | Descrição                                                                            |
|-------------|--------------------------------------------------------------------------------------|
| **Template** | Arquivo JSON ou YAML que define os recursos e configurações da infraestrutura.     |
| **Stack**    | Conjunto de recursos criados a partir de um template.                              |
| **Resources**| Elementos da AWS que serão provisionados (ex: EC2, S3, RDS).                       |
| **Parameters**| Valores dinâmicos que podem ser passados ao template para personalizar a stack.    |
| **Outputs**  | Informações retornadas após a criação da stack (ex: IP da instância EC2).          |
| **Mappings** | Tabelas estáticas usadas para configurar valores com base em condições.            |
| **Conditions**| Permite criar recursos dependendo de critérios específicos (ex: se X, crie Y).    |

## Fluxo Prático de Uso

1. **Acesse o console da AWS** e selecione o serviço **CloudFormation**.
2. **Clique em "Create Stack"** para iniciar o processo de criação da stack.
3. **Escolha entre subir um template pronto** ou utilizar o **Designer** para criar visualmente o fluxo.
4. **Defina os parâmetros necessários** (como tipo de instância EC2, nome do bucket S3, etc.).
5. **Revise as configurações** e clique em **Create** para confirmar a criação da stack.
6. **Acompanhe o progresso e status da criação** dos recursos no console.
7. Utilize o recurso de **Rollback** em caso de falhas durante a criação dos recursos.

## CloudFormation vs Terraform

| Ferramenta         | Características                                                                       |
|--------------------|----------------------------------------------------------------------------------------|
| **AWS CloudFormation** | Serviço nativo da AWS, altamente integrado com a plataforma, ideal para ambientes exclusivamente AWS. |
| **Terraform**      | Ferramenta de IaC **multi-cloud**, com maior flexibilidade e suporte a diversos provedores de nuvem. |

## Insights Adquiridos Durante o Projeto

- **Templates em YAML** são mais legíveis e fáceis de entender, mas o **JSON** também é uma opção suportada.
- O uso de **Stacks** facilita a organização e o gerenciamento de recursos relacionados em um único conjunto.
- **CloudFormation** é ideal para ambientes **AWS-only**, aproveitando sua integração nativa e suporte oficial da AWS.
- A **reutilização de templates** reduz erros humanos, acelera o provisionamento e assegura que os ambientes sejam criados de forma consistente.
- O **versionamento de templates** com ferramentas como **Git** facilita a manutenção e implementação de **boas práticas de DevOps**.
- O **Designer** da AWS é uma ferramenta útil para iniciantes, mas a criação manual de templates oferece **mais controle e flexibilidade**.

## Fontes de Estudo

- [Documentação Oficial do AWS CloudFormation](https://docs.aws.amazon.com/cloudformation/)
- [Getting Started com CloudFormation](https://docs.aws.amazon.com/cloudformation/latest/userguide/Welcome.html)
- [Vídeos da AWS Brasil no YouTube](https://www.youtube.com/c/AWSBrasil)
- **Aulas práticas do bootcamp DIO**

