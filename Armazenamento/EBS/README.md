# Amazon Elastic Block Store ( Amazon EBS )

## Introdução

É o serviço que oferece volumes de armazenamento em bloco para usar com instâncias do EC2, esses volumes se comportam como dispositivos de blocos brutos não formatados. Os volumes EBS que estão anexados a uma instancia são expostos como volumes de armazenamento que persistem independentemente das instancias EC2 que estão atrelados.

## Quando usar ?

O Amazon EBS é recomendado para dados que devem ser rapidamente acessíveis e requerem persistência no longo prazo. Os volumes do EBS são especialmente adequados ao uso como armazenamento principal para sistemas de arquivos, bancos de dados ou para todas as aplicações que necessitem de atualizações granulares finas e acesso ao armazenamento em nível de bloco bruto e não formatado. O Amazon EBS é ideal para aplicações no estilo de banco de dados que utilizam leituras e gravações aleatórias, bem como para aplicações com alta throughput que executam leituras e gravações longas e contínuas

## Tipos de Volumes
### Uso Geral

São volumes de uso geral baseados em SSD que permitem os clientes oferencerem performance independente da capacidade de armazenamento, são usados em Desktops virtuais, bancos de dados de instância única de tamanho médio, como Microsoft SQL Server e Oracle, aplicações interativas sensíveis à latência, volumes de inicialização e ambientes de desenvolvimento/teste

#### GP2

Volume SSD de uso geral que equilibra a performance de preço para uma ampla variedade de workloads transacionais

#### GP3

Volume SSD de mais baixo custo que equilibra a performance de preço para uma ampla variedade de workloads transacionais

### IOPS (I/O per second) Provisionadas 

Os Volumes IOPS Provisionadas são volumes SSD de maior desempenho para workloads criticas, intensivas em IOPS e em throughput que exigem baixa latência.

#### IO1

#### IO2

#### IO2 Block Express


### Volumes HDD otimizados para throughput

#### ST1
Os volumes de armazenamento otimizados para throughput fornecem amazenamento magnetico (HDD) de baixo custo que define a taxa de transferencia em vez de IOPS. São adequados para workloads de I/O grandes e sequenciais acessados com frequencia, como Amazon EMR, ETL, data warehouses e processamento de log.

### Volumes HDD frios 

#### SC1
Os volumes HDD frios fornecem armazenamento magnético de baixo custo que define a performance em termos de throughput em vez de IOPS. São adequados para grandes workloads sequenciais de dados frios ( pouco acessado ).

### Tabela comparativa

|  |  |  |  |  |  |  |  |
|--|--|--|--|--|--|--|--|
| **Categoria** | Uso geral |  | IOPS Provisionada |  |  | Otimizados para throughput | Cold HDD |
| **Tipo de Volume** | GP2 | GP3 | IO1 | IO2 | IO2 Block Express | ST1 | SC1 |
| **Descrição** | Volume SSD de mais baixo custo que equilibra a performance de preço para uma ampla variedade de workloads transacionais | Volume SSD de mais baixo custo que equilibra a performance de preço para uma ampla variedade de workloads transacionais | Volume SSD de alta performance criado para workloads transacionais sensíveis à latência | Volume SSD de alta performance e durabilidade criado para workloads transacionais que dependem da latência | Volume SSD de maior performance criado para cargas de trabalho transacionais sensíveis à latência essenciais para os negócios | Os volumes HDD otimizados para throughput (st1) fornecem armazenamento magnético de baixo custo que define a performance em termos de taxa de transferência em vez de IOPS. | Os volumes HDD frio (sc1) fornecem armazenamento magnético de baixo custo que define a performance em termos de throughput em vez de IOPS |
| **Durabilidade** | 99,8% ~ 99,9% | 99,8% ~ 99,9% | 99,8% ~ 99,9% | 99,999% | 99,999% | 99,8% a 99,9% (0,1% - 0,2% de taxa de falha anual) | 99,8% a 99,9% (0,1% - 0,2% de taxa de falha anual) |
| **Casos de uso** | Desktops virtuais, bancos de dados de instância única de tamanho médio, como Microsoft SQL Server e Oracle, aplicações interativas sensíveis à latência, volumes de inicialização e ambientes de desenvolvimento/teste | Desktops virtuais, bancos de dados de instância única de tamanho médio, como Microsoft SQL Server e Oracle, aplicações interativas sensíveis à latência, volumes de inicialização e ambientes de desenvolvimento/teste | Bancos de dados NoSQL e relacionais com alto consumo de E/S | Bancos de dados NoSQL e relacionais com alto consumo de E/S | Ideal para implantações de missão crítica maiores e mais intensivas em I/O de NoSQL e bancos de dados relacionais, como Oracle, SAP HANA, Microsoft SQL Server e SAS Analytics | Big data, Data warehouses, Processamento de logs | Armazenamento orientado a throughput para dados acessados com pouca frequência |
| **Nome da API** | gp2 | gp3 | io1 | io2 | io2 | st1 | sc1 |
| **Tamanho do Volume** | 1Gb - 16Tb | 1Gb - 16Tb | 4Gb - 16Tb | 4Gb - 16Tb | 4Gb - 64Tb | 125Gb - 16Tb | 125Gb - 16Tb |
| **Máximo de IOPS/Volume** | 16.000 | 16.000 | 64.000 | 64.000 | 256.000 |  |  |
| **Máximo de throughput/Volume (Mb/s)** | 250 | 1.000 | 1.000 | 1.000 | 4.000 | 500 | 250 |
| **Máximo de IOPS/Instancia** | 260.000 | 260.000 | 350.000 | 160.000** | 350.000 |  |  |
| **Taxa de transferencia maxima/Instancia** | 7.500 MB/s | 10.000 MB/s | 10.000 MB/s | 4.750 MB/s** | 10.000 MB/s | 10.000 MB/s | 7.500 MB/s |
| **Preço** | 0,1 | 0,08 | 0,125 | 0,125 | 0,125 | 0,045 | 0,015 |


## Regras

- Deve estar na mesma zona da instancia EC2.
- São vinculadas a uma instancia, podendo ser atrelasdas a mais de uma instancia com a configuração multi-attach.

## Snapshot

É possível fazer backup dos dados nos volumes do Amazon EBS para o Amazon S3 criando snapshots point-in-time. Snapshots são backups incrementais, o que significa que somente os blocos no dispositivo que tiverem mudado depois do snapshot mais recente serão salvos. Isso minimiza o tempo necessário para criar o snapshot e economiza em custos de armazenamento ao não duplicar os dados.
## Preço 

###  Nivel Gratuito
São oferecidos 30 GB de armazenamento por 12 meses no nivel gratuito

### Calculo de custo

Com o Amazon Elastic Block Store (EBS), você paga somente pelo que provisiona. O armazenamento de volume para todos os tipos de volumes do EBS é cobrado pela quantidade provisionada em GB por mês até a liberação do armazenamento. Os custos aumentam para os volumes EBS compatíveis com mais operações de entrada/saída por segundo (IOPS) e taxa de transferência superior à performance da linha de base.

https://aws.amazon.com/pt/ebs/pricing/?loc=ft


## Fontes

- https://docs.aws.amazon.com/pt_br/AWSEC2/latest/UserGuide/AmazonEBS.html
