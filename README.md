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
<img  height="250" alt="Captura de tela 2025-09-19 163947" src="https://github.com/user-attachments/assets/4b158914-bea6-49c5-ae92-fcb002f9b68b" />
<img height="200" alt="Captura de tela 2025-09-19 163757" src="https://github.com/user-attachments/assets/d28cf23c-c546-4d77-8ff4-0597eb46752e" />

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

 
