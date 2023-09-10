# Amazon Elastic Compute Cloud (Amazon EC2)

## Imagens das maquinas da Amazon ( AMIs )

Uma AMI inclui o seguinte:

* Um ou mais snapshots do [Amazon Elastic Block Store (Amazon EBS)](/Armazenamento/EBS/README.md) ou, para AMIs com suporte de armazenamento de instâncias, um modelo para o volume raiz da instância (por exemplo, um sistema operacional, um servidor da aplicação e aplicações).

* Permissões de execução que controlam quais contas da AWS podem usar a AMI para executar instâncias.

* Um mapeamento de dispositivos de blocos que especifica os volumes a serem anexados à instância quando ela for executada.

## Load balancers

Balanceadores de carga

### Tipos de Balanceamento
- ALB ( aplication load balancer ) Layer 7 OSI Layers
    - Routing Path Based
    - Host based
    - Consegue apontar para :
        - Instancias
        - IP Adreess
        - Lambda Functions
        - Containers
        - Targets
    - Roteamento mais detalhado e inteligente
- NLB ( Network load balance ) 
    - Layer 4 OSI Layers
    - Routing Ip based ( TCP/UDP )
    - Roteamento mais rapido ( Higth performance + low latancy)

