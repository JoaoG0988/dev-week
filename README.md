# Santander Dev Week 2023 - Projeto de ETL Bancário

Este projeto foi desenvolvido como parte de um desafio prático para consolidar conhecimentos em **Engenharia de Dados (ETL)**, **IA Generativa** e **Desenvolvimento Backend com Java**. O objetivo é processar dados de clientes e criar mensagens de marketing personalizadas focadas em investimentos.

## 🚨 Solução Resiliente (API Offline)

Como a API original de demonstração (`sdw-2023-prd.up.railway.app`) foi descontinuada, este repositório implementa um fluxo de **ETL alternativo** que garante o funcionamento do projeto de forma totalmente independente e local:

* **Extração (Extract)**: Realizada a partir do ficheiro `SDW2023.csv` na raiz do projeto, contendo dados simulados de clientes como Nome, Conta e Limites.
* **Transformação (Transform)**: O script Python processa estes dados e gera mensagens personalizadas, simulando o comportamento de um especialista em marketing bancário via IA.
* **Carregamento (Load)**: Os dados enriquecidos são persistidos num ficheiro `transformed_users.json`, permitindo a visualização dos resultados finais sem dependência de serviços externos.

## 🏗️ Arquitetura do Sistema

A solução integra duas frentes principais:

### 1. Backend (Java/Spring Boot)
Uma API RESTful que define o domínio bancário robusto:
* **Modelo de Dados**: Entidades como `User`, `Account`, `Card` e `News` mapeadas com JPA.
* **Serviços**: Lógica de negócio para criação e consulta de utilizadores com validações de integridade.
* **Documentação**: API documentada com Swagger/OpenAPI para facilitar a integração.

### 2. Pipeline de Dados (Python)
Script responsável pelo processamento de dados em lote:
* **Manipulação**: Uso da biblioteca Pandas para leitura e estruturação dos dados.
* **Personalização**: Geração de mensagens dinâmicas baseadas no perfil financeiro extraído do CSV.

## 🛠️ Tecnologias Utilizadas

* **Java 17 & Spring Boot 3**
* **Spring Data JPA** para persistência de dados
* **H2 Database** (Ambiente de Desenvolvimento)
* **PostgreSQL** (Ambiente de Produção)
* **Python 3.x** com Pandas
* **OpenAPI (Swagger)** para documentação

## 🚀 Como Executar

### Pré-requisitos
* Java 17 ou superior.
* Python 3.x e gestor de pacotes `pip`.

### Passo 1: Executar o Backend (Opcional)
Para rodar a API Java localmente:
```bash
./gradlew bootRun
```

### Passo 2: Executar o ETL (Python)

#### Recomendado: criar e ativar ambiente virtual
```bash
python -m venv venv
source venv/bin/activate  # Windows: .\venv\Scripts\Activate.ps1
```

#### Instalar dependências e rodar
```bash
pip install pandas
python etl_pipeline.py
```
