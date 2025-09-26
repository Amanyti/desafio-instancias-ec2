# Desafio Instâncias EC2

Repositório criado para o Desafio Instâncias EC2.  
Contém imagens do projeto desenvolvido no **draw.io**, exemplos de arquitetura de sistemas na AWS e as anotações pessoais do meu entendimento sobre os módulos do curso feitos até agora.


## Módulo 1 – Introdução e Conceitos básicos

- AWS significa **Amazon Web Services**.  
- O nome "Amazon" foi inspirado no rio Amazonas, o maior do mundo, para transmitir a ideia de grandeza e escalabilidade.  
- Foi uma das pioneiras em computação em nuvem e hoje é líder mundial no setor.  
- Faz parte da empresa Amazon, fundada por **Jeff Bezos**.  


## Módulo 2 – Computação na nuvem com EC2

### Instâncias EC2
- São máquinas virtuais na nuvem, configuráveis em sistema operacional, memória e processamento.  
- Eliminam a necessidade de servidores físicos locais.  

### Tipos de Instâncias
- **General Purpose**: uso equilibrado, indicado para aplicações comuns.  
- **Compute Optimized**: voltado a cargas de trabalho que exigem alto processamento.  
- **Memory Optimized**: indicado para bancos de dados e aplicações que exigem muita RAM.  
- **Storage Optimized**: eficiente em operações intensivas de leitura e escrita em disco.  
- **Accelerated Computing**: voltado para IA, machine learning e processamento gráfico.  

### Otimização de Recursos
- Escolher o tipo adequado de instância ajuda a reduzir custos.  
- Escalabilidade permite ajustar recursos de acordo com a demanda.  
- Serviços como **Auto Scaling** e **Load Balancer** otimizam desempenho e disponibilidade.  

### Amazon EBS (Elastic Block Store)
- Serviço de armazenamento em blocos que funciona como HD/SSD para instâncias EC2.  
- Permanece disponível mesmo após desligar a instância.  
- Permite redimensionamento, criação de snapshots e restauração de dados.  

### Amazon S3 (Simple Storage Service)
- Serviço de armazenamento de objetos altamente escalável.  
- Utilizado para guardar arquivos de qualquer tipo, como documentos, imagens, vídeos e backups.  
- Organizado em **buckets** (semelhante a pastas).  
- É durável, seguro e de baixo custo.  

### AWS Lambda
- Serviço de computação **serverless** (sem precisar gerenciar servidores).  
- Permite executar código em resposta a eventos, como uploads no S3 ou requisições HTTP.  
- Ideal para automações, processamento de dados e aplicações que não rodam 24h.  
- Escala automaticamente e cobra apenas pelo tempo de execução.  

### Amazon DynamoDB
- Banco de dados NoSQL totalmente gerenciado pela AWS.  
- Armazena dados em tabelas de chave-valor e documentos.  
- É altamente escalável, rápido e com baixa latência.  
- Indicado para aplicações que precisam lidar com grandes volumes de dados em tempo real, como jogos, IoT e apps web/móveis.  


## Exemplos de Arquitetura na AWS
Nesta seção serão adicionadas imagens mostrando exemplos de arquiteturas de sistemas utilizando serviços da AWS.  
- Esquemas do Desafio:
<img width="300"  alt="Instancias_EBS_EC2 drawio" src="https://github.com/user-attachments/assets/7fa4d3b6-f51d-48b7-8bda-dac3770c78de" />
<img width="300"  alt="Instancias_S3_Lambda_Dynamo drawio" src="https://github.com/user-attachments/assets/2217e197-ebda-4afb-9fee-6e3fefc69980" />


- Esquemas mais Complexos:
<img width="200"  alt="Captura de tela 2025-09-13 180650" src="https://github.com/user-attachments/assets/abf433ef-d4b9-41bf-a4aa-ceec6b4f6efb" />
<img width="200"  alt="Captura de tela 2025-09-13 180715" src="https://github.com/user-attachments/assets/f86e2792-3083-4c86-9587-75ba3821b650" />


## Módulo 4 – Redes na AWS

### Amazon VPC (Virtual Private Cloud)
- Permite criar uma **rede privada virtual** dentro da AWS.  
- Dá controle sobre IPs, roteamento, firewalls e segurança da rede.  
- Serve para isolar recursos, organizar ambientes e controlar o tráfego entre serviços.
  
### Serviços Públicos e Privados
- Públicos: serviços que não estejam implantados em um VPC.
- Privados: serviços que requerem configuração VPC para funcionar.
- Serviços como lambda podem ser os dois.
  
### Subnet
- Subdivisão de uma VPC em **segmentos menores de rede**.  
- Pode ser **pública** (acesso à internet) ou **privada** (sem acesso direto à internet).  
- Facilita organizar servidores e serviços de acordo com funções e regras de segurança.
- <img  height="250" alt="Captura de tela 2025-09-19 163947" src="https://github.com/user-attachments/assets/4b158914-bea6-49c5-ae92-fcb002f9b68b" /> <img height="200" alt="Captura de tela 2025-09-19 163757" src="https://github.com/user-attachments/assets/d28cf23c-c546-4d77-8ff4-0597eb46752e" />

### Security Group
- Funciona como um **firewall virtual** para instâncias dentro da VPC.  
- Permite controlar o **tráfego de entrada e saída** por IP, porta e protocolo.  
- Associado a instâncias EC2, Lambda ou outros serviços, garantindo segurança e isolamento de rede.  
- Diferente de uma subnet, o Security Group atua no nível **da instância**, não da rede inteira.  
- Taxado ao nivel da placa de rede.

### Amazon Route 53
- Serviço de **DNS (Domain Name Service) gerenciado** da AWS.  
- Traduz nomes de domínio (ex: www.exemplo.com) em endereços IP para direcionar o tráfego corretamente.  
- Permite registrar domínios, criar zonas hospedadas e gerenciar roteamento de tráfego global.  
- Suporta **failover**, balanceamento de carga e integração com outros serviços da AWS.  

### Amazon CloudFront
- Serviço de **Content Delivery Network (CDN)** da AWS.  
- Distribui conteúdo (imagens, vídeos, APIs, sites) globalmente através de **edge locations**, reduzindo latência.  
- Funciona integrado com S3, EC2 e outros serviços da AWS.  
- Oferece segurança com suporte a HTTPS, proteção DDoS e integração com AWS WAF.

### Elastic Load Balancer (ELB)
- Serviço que **distribui automaticamente o tráfego** entre múltiplas instâncias ou serviços.  
- Garante **alta disponibilidade e tolerância a falhas** em aplicações.  
- Suporta diferentes tipos de balanceamento: **Application Load Balancer** (camada HTTP/HTTPS), **Network Load Balancer** (camada TCP/UDP), **Gateway Load Balancer** (segurança de rede) e **Classic Load Balancer** (HTTP/HTTPs e TCP entre EC2) .  
- Funciona integrado com VPC, Auto Scaling e Security Groups.  


## Módulo 5 – Banco de Dados na AWS

### Amazon RDS (Relational Database Service)
- Serviço PASS gerenciado de **banco de dados relacional** na AWS.  
- Suporta motores como **MySQL, PostgreSQL, MariaDB, Oracle, SQL Server e Aurora**.  
- Cuida de tarefas administrativas como **backup, patching, replicação e escalabilidade**.  
- Permite configurar alta disponibilidade com **Multi-AZ** e replicação para leitura.  
- Ideal para aplicações que precisam de **banco de dados estruturado e gerenciado**, sem se preocupar com infraestrutura.

### Amazon DynamoDB
- Banco de dados **NoSQL** para dados estruturados e não estruturados totalmente gerenciado pela AWS.  
- Trabalha com modelos de **chave-valor** e **documentos**.  
- Escalável automaticamente para lidar com grandes volumes de dados em tempo real.  
- Oferece **baixa latência**, mesmo em milhões de requisições por segundo.  
- Indicado para aplicações de **alta performance**, como jogos, IoT, sistemas de e-commerce e apps web/móveis.

### Estratégias de Backup e Recuperação de Dados
- Backups garantem a **disponibilidade e integridade** das informações mais importantes e cruciais em caso de falhas, exclusões acidentais ou desastres.  
- Na AWS, serviços como **RDS** e **DynamoDB** oferecem backup automático e snapshots manuais.  
- É importante definir uma **política de backup** com frequência adequada (diária, semanal, incremental).  
- **Recuperação de desastres (Disaster Recovery – DR)** envolve ter dados replicados em múltiplas zonas de disponibilidade (Multi-AZ) ou até em diferentes regiões.  
- Estratégias comuns incluem:
  - **Avaliação e Planejamento**: RPO (margem que pode ser perdida entre os ciclos de backups) e RTO (limite de tempo que o sistema pode ficar parado antes de voltar ao funcionamento)
  - **Backup and Restore**: restaurar dados a partir de snapshots.  
  - **Pilot Light**: manter uma versão mínima do ambiente pronta para ser escalada.  
  - ** Recuperação de Dados**: .  
  - **Segurança e Conformidade**: criptografia, controles de acesso, .
  - **Custo e Otimização**: .

 
## Módulo 6 - Serviçoes de Armazenamento e CDN

### Amazon S3 Glacier
- Serviço de armazenamento da AWS voltado para **arquivamento de longo prazo** e backup.  
- Oferece custo muito baixo para armazenar grandes volumes de dados que não precisam ser acessados com frequência, com duração mínima de 90 dias.  
- Possui diferentes classes de recuperação:  
  - **Expedited**: minutos.  
  - **Standard**: horas.  
  - **Bulk**: até 12 horas (mais econômico).  
- Os dados ficam criptografados e podem ser recuperados sob demanda.  
- Indicado para conformidade, arquivamento histórico, registros e backups que raramente são acessados.

### Família AWS Snow
- Conjunto de dispositivos físicos fornecidos pela AWS para **transferência e migração de grandes volumes de dados**.  
- Usado quando a rede não é suficiente para mover dados para a nuvem em tempo hábil.  
- Principais opções:  
  - **AWS Snowball Edge**: transporte em grande velocidades por meio de operadoras regionais.  
  - **AWS Snowball**: maior capacidade, usado para dezenas ou centenas de terabytes.  
  - **AWS Snowmobile**: caminhão equipado para transportar até 100 petabytes de dados.  
- Suporta casos de uso como: migração de data centers, coleta de dados em campo e cenários de baixa conectividade.

### Amazon CloudFront
- Serviço de **Content Delivery Network (CDN)** da AWS.  
- Distribui conteúdo (sites, vídeos, APIs e outros arquivos) com **baixa latência** e **alta velocidade de transferência**.  
- Usa uma rede global de **edge locations** (pontos de presença - POP) para entregar conteúdo mais próximo do usuário final.  
- Integra-se com outros serviços da AWS, como **S3, EC2, Elastic Load Balancer e Route 53**.  
- Benefícios principais:  
  - Redução de latência e aumento de performance.  
  - Escalabilidade automática para lidar com picos de tráfego.  
  - Segurança integrada com **AWS Shield** e **AWS WAF**.  


 ## Módulo 7 - Seviços Intermediários e Avançados

### AWS Lambda
- Serviço de **computação serverless** da AWS.  
- Permite executar código sem necessidade de provisionar ou gerenciar servidores.  
- Funciona baseado em **eventos**: o código é acionado quando ocorre um gatilho (ex.: upload no S3, alteração no DynamoDB, requisições via API Gateway, etc.).  
- Suporta várias linguagens (Python, Node.js, Java, Go, entre outras).  
- Escala automaticamente de acordo com a demanda.  
- Modelo de cobrança: **pay-per-use**, ou seja, paga-se apenas pelo tempo de execução do código.
- Intenção de receber informação e passar pra frente.
- Usado em:  
  - Processamento de dados em tempo real.  
  - Automação de tarefas.  
  - Criação de backends de aplicações leves.  

### Amazon ECS e EKS
- **ECS (Elastic Container Service):** serviço de orquestração de containers da AWS, podendo ser monolítico ou de microserviços.  
  - Gerencia containers Docker de forma simplese é ideial para execução maiores de 15 minutos e fora das regios AWS.  
  - Permite rodar aplicações em containers sem precisar gerenciar servidores diretamente com facil integração com outros sistemas.
  - ECR é um serviço de registro de contêiner gerenciado para gerenciar imagens no docker.
  - <img height="200" alt="Captura de tela 2025-09-26 115208" src="https://github.com/user-attachments/assets/12f053e5-aaba-4d5a-8f8a-4ca18c3829c2" />
  
- **EKS (Elastic Kubernetes Service):** serviço gerenciado de **Kubernetes**, faz praticamente a mesma coisa que o ECS só que com kubernetes.  
  - Ideal para quem já utiliza Kubernetes e quer mais flexibilidade.  
  - Escala aplicações em containers com alta disponibilidade.
  - <img height="250" alt="Captura de tela 2025-09-26 120826" src="https://github.com/user-attachments/assets/38502459-1ff0-467a-af49-31d6b71d33ec" />

### Amazon SNS e SQS
- **SNS (Simple Notification Service): melhor parr usuários**  
  - Serviço assíncrono de **pub/sub** para envio de mensagens FIFO.  
  - Permite notificar múltiplos sistemas ou usuários ao mesmo tempo.  
  - Usado para notificações push, SMS, emails e integrações com outros sistemas AWS.  
- **SQS (Simple Queue Service): melhor para sistemas mais complexos**  
  - Serviço de **fila de mensagens** totalmente gerenciado. As filas podem ser de diferentes tipos, como padrão e FIFO.  
  - Garante a entrega assíncrona entre serviços desacoplados.  
  - Usado para processar tarefas em segundo plano e gerenciar picos de requisições.  
- **Tipo Padrão: não importa a ordem**.

### AWS Step Functions
- Serviço para **orquestração de fluxos de trabalho** (workflows).  
- Permite coordenar múltiplos serviços da AWS em etapas definidas.  
- Usa uma abordagem **visual e baseada em estados** para controlar a execução.  
- Ideal para:  
  - Automatizar processos complexos.  
  - Integrar Lambda, ECS, SQS, DynamoDB e outros serviços.  
  - Monitorar e depurar fluxos de execução.  

 
