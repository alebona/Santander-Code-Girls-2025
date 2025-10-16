# Gerenciando Instâncias EC2 na AWS

## Objetivo
Este documento visa apresentar a experiência prática de criação, configuração e gerenciamento de instâncias EC2 na AWS. Através deste projeto, buscamos consolidar os conhecimentos adquiridos em infraestrutura na nuvem, segurança de redes e automação de tarefas, aplicando as melhores práticas para otimizar o desempenho e a segurança da aplicação hospedada.

## Arquitetura da Solução

A arquitetura a seguir ilustra o fluxo de comunicação entre os componentes e os recursos utilizados na criação de uma infraestrutura segura e eficiente:

📁 **Diagrama**: O diagrama completo pode ser acessado em `/imagens/diagrama_ec2.jpg`.

---

## Aprendizados

- **Configuração de Redes Virtuais (VPC)**: Compreendemos o processo de criação de uma rede virtual isolada (VPC) e sub-redes (Subnets) públicas e privadas para gerenciar o tráfego de dados de forma controlada.
- **Gerenciamento de Instâncias EC2**: Realizamos o provisionamento de instâncias EC2 para hospedar aplicações, configurando aspectos como tipo de instância, volumes de armazenamento e segurança.
- **Segurança e Acesso**: Aprendemos a aplicar as melhores práticas de segurança na nuvem, incluindo a criação e configuração de **Security Groups** para controlar o tráfego de entrada e saída, além da aplicação de **IAM Roles** para gerenciar permissões de acesso.
- **Escalabilidade e Monitoramento**: Exploramos como configurar autoescalamento e integrar instâncias EC2 com **CloudWatch** para monitoramento e otimização de recursos.

---

## Recursos Adicionais

- [Documentação Oficial EC2 da AWS](https://docs.aws.amazon.com/pt_br/AWSEC2/latest/UserGuide/concepts.html)
- [Guia Completo de Markdown para GitHub](https://guides.github.com/features/mastering-markdown/)
- [Ferramenta de Diagramas Draw.io](https://draw.io)

---

## Visão Geral da Arquitetura

A arquitetura consiste na comunicação entre o **usuário externo** e a aplicação hospedada em uma instância **EC2** na AWS. A instância está localizada em uma **Subnet Pública** dentro de uma **VPC**, com tráfego de dados monitorado e controlado por regras de segurança.

### Fluxo de Comunicação

1. O **Usuário** acessa a aplicação por meio da **Internet**.
2. O tráfego é direcionado para o **Internet Gateway**, permitindo a comunicação entre a **VPC** e a Internet.
3. A comunicação segue para a **Subnet Pública**, onde a **Instância EC2** processa as requisições.
4. O tráfego é controlado por **Security Groups**, que definem regras para entradas e saídas.

---

## Componentes da Arquitetura

| Componente          | Função                                                                 |
|---------------------|------------------------------------------------------------------------|
| **Usuário**          | Realiza as requisições de acesso à aplicação por meio de navegador ou terminal. |
| **Internet**         | Rede pública que conecta o usuário à AWS, permitindo a comunicação com os recursos. |
| **Internet Gateway** | Facilita a comunicação entre a VPC e a Internet, permitindo a troca de dados. |
| **VPC (Virtual Private Cloud)** | Rede privada virtual onde os recursos da aplicação são hospedados de forma isolada e segura. |
| **Subnet Pública**   | Sub-rede com acesso à Internet, onde as instâncias EC2 são lançadas para permitir comunicação externa. |
| **Instância EC2**    | Máquina virtual que executa a aplicação ou serviço, podendo ser escalada conforme a demanda. |
| **Security Group**   | Conjunto de regras de segurança que controlam o tráfego de rede, permitindo ou bloqueando conexões conforme as necessidades. |

---

## Considerações Finais

A configuração de instâncias EC2 na AWS oferece flexibilidade e escalabilidade para diferentes tipos de aplicações. Utilizando boas práticas de segurança e redes, conseguimos garantir que nossa aplicação seja eficiente, segura e resiliente. A AWS oferece ferramentas poderosas como **CloudWatch** para monitoramento e **Auto Scaling** para otimização, o que permite uma gestão proativa da infraestrutura em nuvem.

Com a experiência prática de gerenciamento de instâncias EC2, podemos aplicar esse conhecimento em projetos mais complexos, explorando o potencial da AWS para desenvolver soluções robustas e escaláveis.

