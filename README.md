# CloudAWS
Trabalho de conclusão do curso re/Start da Escola da Nuvem.
O objetivo do projeto é melhorar a infraestrutura cloud do cliente, observando o limite de orçamento inicial de $10.000,00, além de $300,00 para atender a gastos extras recorrentes.

Diagrama da infraestrutura do cliente:
![image](https://github.com/Saraiana/CloudAWS/assets/102194276/2dc7c661-3dec-4887-8855-9a05788fa748)

Diagrama da arquitetura proposta:

![ArquiteturaProposta](https://github.com/Saraiana/CloudAWS/assets/102194276/bc214c33-c4d5-4f8f-a84a-85b3793f43c1)

Considerações sobre o diagrama da infraestrutura proposta quanto aos serviços utilizados: 

**Amazon Virtual Private Cloud (Amazon VPC)**

Permite criar uma rede virtual personalizada na AWS. Foi criada com duas sub-redes públicas e duas sub-redes privadas distribuídas em 2 zonas de disponibilidade diferentes. 

**NAT Gateway**

Serviço de tradução de endereços de rede. Foram adicionadas duas NAT Gateway, uma em cada sub-rede pública, para que as instâncias das sub-redes privadas possam se conectar a internet. 

**Amazon EC2**

Capacidade de computação escalável sob demanda na nuvem AWS. Foram propostas 2 instâncias compartilhadas com 2vCPU e 4GiB de memória. A infraestrutura poderá escalar horizontalmente em caso de aumento de demanda, com auxílio do Auto Scaling Group. 

**Amazon RDS for MariaDB**

O RDS é um serviço que simplifica a gestão do banco de dados na nuvem e é compatível com várias versões do MariaDB Server. A implementação do RDS foi multi-AZ (mais de uma zona de disponibilidade), onde ele cria automaticamente uma instância de banco de dados primária e replica de forma síncrona os dados para uma instância em uma AZ diferente. A configuração do MariaDB foi feita com 8vCPU e 32 GiB de memória.  

**Amazon CloudWatch**

O CloudWatch coleta e visualiza logs, métricas e dados de eventos em tempo real em painéis automatizados. Na arquitetura proposta, estão sendo usadas 10 métricas personalizadas com 1 milhão de solicitações de API, 3 painéis personalizados com até 50 métricas e 5 GB de dados em logs, que são oferecidos gratuitamente, mais três painéis de alarmes com 3 métricas de alarme de resolução padrão de 60 segundos. 

**Amazon CloudTrail**

Monitora e registra atividades da conta por toda infraestrutura da AWS. Registra eventos de gerenciamento nos serviços da AWS por padrão e está disponível sem custo, com 90 dias de histórico de atividades da conta. 

**Elastic Load Balancing**

Distribui automaticamente o tráfego de entrada entre vários destinos em uma ou mais zonas de disponibilidade. Monitora a integridade dos destinos e roteia o tráfego apenas para os destinos íntegros. Trabalha junto com o Auto Scaling Group.

**Auto Scaling Group**

Realiza o gerenciamento da escalabilidade de forma automática e ajusta as instância para atender a capacidade desejada. Propomos o uso mínimo de 2 instâncias e o máximo de 4, para que o auto scaling ajuste de forma automátima em relação à demanda. 

**AWS Shild**

Serviço de proteção contra ataques DDoS (Distributed Denial of Service) oferecido pela AWS de forma gratuita na versão básica. Ajuda a proteger aplicativos conta ataques DDoS comuns, garantindo a disponibilidade e a integridade dos serviços hospedados na AWS.

**AWS Web Application Firewall (WAF)**

Serviço de segurança da AWS que protege aplicativos web contra explorações comuns da Web e bots que podem afetar a disponibilidade, comprometer a segurança e consumir recursos excessivos.

**AWS Identity and Access Management (IAM)**

Simplifica a gestão de permissões, padroniza o acesso, facilita a escalabilidade, reforça a segurança e permite um controle mais eficiente do acesso aos recursos na nuvem AWS.

**Custo da Infraestrutura Apresentada**
![image](https://github.com/Saraiana/CloudAWS/assets/102194276/b827b798-3cfd-445d-a9b1-674ff1d45f88)
https://calculator.aws/#/estimate?id=11b421ff1920ead09dbea53c351588021f0ecdb3


A solução proposta apresenta uma arquitetura com maior segurança, alta disponibilidade, estratégia de recuperação de desastres e componentes independentes para cada carga de trabalho.
