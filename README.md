# API Gateway

### APIs
É um conjunto de operações bem definidas com objetivo de oferecer aos seus consumidores um serviço, produto ou uma integração.

Na prática o consumidor de uma API utiliza o serviço sem a necessidade de entender os detalhes de implementação, essa é uma característica que deve ser preservada.

APIs conhecidas
- Twiter
- GCP
- AWS
- Salesforce
- Stripe

![](.github/api-analogy.png)

### API Gateway

#### API Gateway Pattern
Em um modelo que implementa um padrão de arquitetura de microsserviços, como os clientes vão poder identificar o serviço que contém as informações que ele necessita?

Em geral a granularidade das informações do microsserviço é diferente da qual gostaríamos de expor para o cliente.

![](.github/apigateway.jpg)

**API Gateway** é uma ferramenta de gerenciamento, geralmente adicionada entre o cliente e um grupo de sistemas de um determinado contexto, atuando como ponto único de entrada das APIs.

#### Funcionalidades de um API Gateway
Geralmente o API Gateway atua na camada de rede, provendo funcionalidades ortogonais, que necessariamente não são responsabilidade das aplicações.

- Controle de abuso (rate limiting)
- Autenticação / Autorização de maneira padronizada
- Controle de Logs
- Gerenciamento de APIs (touting)
- Metricas padronizadas (ops team)
- Tracing Distribuido

#### Tipos de API Gateway

**Enterprise Gateway**
- Foco deste tipo de solução é na grande maioria das vezes realizar exposição e gerenciamento de deployment de APIs voltadas ao negócio, em geral ele também permite controlar o ciclo de vida de uma API.
- Em geral é uma oferta de algum vendor, com estratégias comerciais suportando a solução. Este também tende a direcionar a aplicação da solução e implicar no segign dos seus serviços.
- Propósito principal: Exposição, composição e gerenciamento de APIs externas/internas
- Manutenção das APIs: Time de APis em geral faz administração via Portal do API Gateway
- Suporta múltiplos ambientes DEV, QA e Prod
- Pode ser utilizado para um modernização de arquitetura aplicando padrões como Façade ou Starngler Application (deve ser o meio, e não o final da solução)
- Disponibilidade vs COnsistência (dependências externas)
- Cuidado com utilização de "policies" da própria ferramenta (vendor lock-in)
- Em geral precisam de dependencias externas, como banco de dados, caches entro outros, **CUIDADO** isso pode aumentar suas chances de ter indisponibilidade
- A "mobilidade" de deployment é bem baixa, enterprise gateways são **EDGE** na maioria dos casos
- Vendor Lock-in

**Micro/Microservices Gateway**
- Tipicamente essa classe de Gateways tem a capacidade de "rotear" tráfego de entrada para APIs ou serviços. Em geral não oferecem suporte ao ciclo de vida das APIs e as equipes tem que fazêlo via processo separado
- Maioria open source
- Geralmente não possuem dependencias externa, e são componentes standalone, o que faz com que a plataforma (k8s) gerencie o estado necessário para a execução da aplicação
- Propósito principal: Exposição, observabilidade e monitoramento de serviços (APIs)
- Manutenção da APIs: Time de API ou time de criação/manutenção do serviço via configuração declarativa fazem atualizações, esta tarefa faz parte do deployment dos serviços
- Suporte a ambientes: A instância controla um único ambiente, possui suporte a roteamento mais dinâmico como por exemplo Canary para facilitar o debugging.
- Reduza o número de instancias para ganhar experiencia na gestão do ambiente para escalar para toda companhia.
- Use a flexibilidade do deploymento para "particionar" suas APIs (use BOunded COntext do DDD)
- Tente ser **Stateless** o máximo possível isso vai aumentar muito a facilidade de escalabilidade/disponibilidade
- Número de instancias pode ser um problema em equipes sem expertise em monitoramento/observabilidade
- Granulidade fina demais, pode complicar a manutenção
- Automação deve ser pensada desde o início da jornada

















