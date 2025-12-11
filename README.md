Monitoramento Completo com Docker Compose – API + Prometheus + Grafana + Node Exporter + NGINX

Este projeto implementa um ambiente completo de monitoramento e observabilidade utilizando Prometheus, Grafana, Node Exporter, uma API Python instrumentada com Prometheus, e um proxy reverso NGINX — tudo orquestrado com Docker Compose.

O objetivo é demonstrar, de forma prática, como criar um ambiente profissional de monitoramento em containers, integrando métricas de infraestrutura e métricas de aplicação.

Arquitetura do Projeto
<img width="1364" height="758" alt="aqui1" src="https://github.com/user-attachments/assets/54bed331-d23b-4d40-b44f-629cec2d8a66" />
<img width="808" height="624" alt="arqui2" src="https://github.com/user-attachments/assets/49442693-2483-4764-b81b-e0d5df479dc1" />

Componentes

. API Python
Exposição de métricas customizadas via /metrics.
. Prometheus
Coleta métricas da API e do Node Exporter.
. Grafana
Visualiza e cria dashboards com base nos dados do Prometheus.
. Node Exporter
Exporta métricas do host (CPU, memória, disco).
. NGINX
Proxy reverso para rotear requisições.

Diagrama da Arquitetura

![DIAGRAMA](https://github.com/user-attachments/assets/653ae94c-0ac5-4c90-af92-d4902dc153db)

1. Prints do Ambiente
Docker PS – serviços funcionando
![DOCKER-PS](https://github.com/user-attachments/assets/bdda0a3e-9d09-4f62-a1f2-ee63232e59df)
Prometheus – Target do node-exporter UP
![PROMETHEUS-TARGETS](https://github.com/user-attachments/assets/36f738c5-00c3-4783-8548-1993a1af7632)
Prometheus – Gráfico das métricas
![PROMETHEUS-GRAFICOS](https://github.com/user-attachments/assets/415c0d6b-14ef-4a22-a7b2-6e9ff72525e9)
API /metrics funcionando
![METRICS-API-PYTHON](https://github.com/user-attachments/assets/6e740f1b-9f23-48bc-b5ee-46e22f568fc4)
NGINX – página padrão funcionando
![NGINX](https://github.com/user-attachments/assets/c33cb95d-734f-4458-bf84-874cb42da0fb)
Node Exporter – /metrics
![METRICS-NODE-EXPORTER](https://github.com/user-attachments/assets/e4bb917f-d8ff-46fa-9f47-ce52fd7e4455)
Grafana – painel com métricas
![GRAFANA-DASHBOARD](https://github.com/user-attachments/assets/a53e8f15-d12a-4b72-9c4a-dfd82ec6757a)

3. Como Executar o Projeto
1. Clone o repositório
git clone https://github.com/danielviana2127/compose-avancado
cd compose-avancado

3. Suba os serviços
docker compose up -d

5. Verifique os serviços
docker ps

3. Acessos
| Serviço       | URL                                                            | Porta |
| ------------- | -------------------------------------------------------------- | ----- |
| API           | [http://localhost:8080](http://localhost:8080)                 | 8080  |
| API /metrics  | [http://localhost:8080/metrics](http://localhost:8080/metrics) | 8080  |
| Prometheus    | [http://localhost:9090](http://localhost:9090)                 | 9090  |
| Grafana       | [http://localhost:3000](http://localhost:3000)                 | 3000  |
| Node Exporter | [http://localhost:9100/metrics](http://localhost:9100/metrics) | 9100  |

4. Grafana – Como importar o dashboard

1. Acesse:
http://localhost:3000
2. Vá em:
   Connections → Data sources → Add → Prometheus

3. Configure:
URL = http://prometheus:9090

4. Salve e teste.

5. Vá em:
Dashboards → Import

6. Cole o ID oficial:
1860
   
7. Selecione o Prometheus como data source.

5. Estrutura do Projeto
compose-avancado/
│
├── api/
│   ├── app.py
│   ├── Dockerfile
│   └── requirements.txt
│
├── nginx/
│   └── default.conf
│
├── prometheus/
│   └── prometheus.yml
│
├── docker-compose.yml
└── README.md

6. AUTOR
Projeto desenvolvido por Daniel Viana como parte do estudo avançado em DevOps e Observabilidade.

7. Licença
Este repositório é livre para uso educacional.



