# Construindo sua Primeira Stack com AWS CloudFormation

## Introdução ao CloudFormation

O **AWS CloudFormation** é uma ferramenta poderosa da Amazon Web Services (AWS) que permite a criação e o gerenciamento de recursos em nuvem de forma automatizada. Através de **Infraestrutura como Código (IaC)**, você pode definir toda a sua infraestrutura usando arquivos de configuração em **YAML** ou **JSON**. Isso garante **consistência**, **agilidade** e **escabilidade** na construção de ambientes complexos.

## Benefícios e Funcionalidades

### 1. **Automatização Total**
O CloudFormation automatiza o provisionamento de recursos, eliminando tarefas manuais e minimizando erros. Com ele, você pode configurar instâncias EC2, redes VPC, buckets S3, bancos de dados RDS e muito mais de forma programática.

### 2. **Templates Modulares**
A criação de **templates** reutilizáveis e modulares permite que você defina recursos em várias camadas. Esses templates podem ser facilmente integrados a diferentes projetos, garantindo flexibilidade e padronização.

### 3. **Controle de Custos**
Com o CloudFormation, você paga apenas pelos **recursos provisionados**. Isso oferece controle sobre os custos, já que você pode criar e destruir recursos conforme necessário, sem se preocupar com gastos excessivos.

### 4. **Alta Escalabilidade**
Seja para arquiteturas simples ou ambientes complexos, o CloudFormation é altamente escalável. Ele pode ser usado tanto para configurar pequenas aplicações quanto para gerenciar grandes infraestruturas distribuídas em múltiplas regiões da AWS.

### 5. **Histórico de Alterações**
Cada **alteração em uma stack** é registrada, facilitando o **rastreamento e auditoria** de mudanças. Isso é crucial para fins de segurança, conformidade e manutenção contínua do ambiente.

## O que é uma Stack?

Uma **stack** no CloudFormation é um conjunto de recursos definidos em um template, gerenciados como uma única unidade. Uma stack pode incluir componentes como servidores, redes, bancos de dados, segurança e até integrações com outros serviços da AWS. A vantagem é que você pode tratar essa coleção de recursos como uma unidade, realizando operações de **criação**, **atualização** ou **exclusão** de forma simples.

### Principais Ações com uma Stack:

- **Criar**: Provisiona todos os recursos definidos no template.
- **Atualizar**: Modifica os recursos existentes conforme as necessidades do projeto.
- **Excluir**: Remove todos os recursos de uma stack de forma coordenada.

## Etapas para Criar uma Stack via Console

A seguir, um passo a passo para criar uma stack utilizando o Console AWS:

### 1. **Acesse o Console AWS**
- No Console AWS, vá até **CloudFormation** e clique em **Stacks**.

### 2. **Clique em "Create stack"**
- Clique na opção **Create stack** para iniciar a criação da sua stack.

### 3. **Escolha o Template**
Você pode escolher um template de várias maneiras:
- **Prepare Template**: Se você já tem um arquivo YAML ou JSON pronto, insira-o diretamente.
- **Select a Sample Template**: O AWS oferece templates de amostra para facilitar a criação.

### 4. **Configure os Parâmetros**
Você será solicitado a configurar parâmetros como:
- **Nome da Stack**: Defina um nome único para sua stack.
- **Permissões**: Selecione as permissões necessárias para que os recursos possam ser provisionados corretamente.
- **Opções Avançadas**: Caso necessário, configure opções adicionais de rede e segurança.

### 5. **Revise e Crie**
Revise todas as configurações e clique em **Create**. A partir desse momento, o CloudFormation irá provisionar todos os recursos definidos no template.

---

## Referências

- [Documentação Oficial do AWS CloudFormation](https://docs.aws.amazon.com/cloudformation/)
- [Guia de Introdução Rápida ao AWS CloudFormation](https://docs.aws.amazon.com/cloudformation/latest/userguide/Welcome.html)

