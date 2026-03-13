# 🛒 Projeto Olist - Análise de E-commerce e Data App

**Autor:** José Guilherme Lima de Carvalho
**Mês/Ano:** 03/2026

## 📌 Sobre o Projeto
Este projeto foi desenvolvido como parte de um case técnico para demonstrar habilidades ponta a ponta em Engenharia de Dados, Análise de Dados (BI) e desenvolvimento de Aplicativos de Dados. Utilizamos a base de dados pública do e-commerce brasileiro **Olist**.

## 📋 Planeamento e Agilidade (Item 0)
Para garantir a entrega contínua de valor e o alinhamento com os objetivos de negócio, o projeto foi estruturado utilizando metodologias ágeis (Kanban). Abaixo está o fluxo de trabalho seguido:

| 📝 Backlog / To Do | ⚙️ In Progress | ✅ Done (Concluído) |
| :--- | :--- | :--- |
| [Item 5] Integrar API de LLM para análise de sentimentos | [Item 4] Criar testes de Data Quality | [Item 1] Seleção da Base de Dados (Olist) |
| [Item bônus] Gerador de imagens de produtos com IA | [Item 6] Desenhar Diagrama de Modelagem (Star Schema) | [Item 2] Ingestão de Dados na Dadosfera / Snowflake |
| [Item 10] Gravação do Pitch (Especialista Dadosfera) | | [Item 3] Catalogação e Dicionário de Dados |
| | | [Item 7] Desenvolvimento de Queries SQL |
| | | [Item 7] Construção do Dashboard Executivo (Metabase) |
| | | [Item 9] Deploy do Data App (Streamlit) |

## 🛠️ Tecnologias Utilizadas
* **Dadosfera:** Ingestão de dados e catalogação.
* **Snowflake:** Armazenamento em nuvem e consultas SQL.
* **Metabase:** Criação de consultas nativas e visualização de dados (Dashboard).
* **Python:** Processamento de dados (Pandas) e visualização (Plotly).
* **Streamlit:** Desenvolvimento e deploy do aplicativo web interativo.

---


**Diagrama da Arquitetura (Star Schema):**

```mermaid
erDiagram
    FATO_PEDIDOS {
        string order_id PK
        string customer_id FK
        string product_id FK
        date purchase_timestamp
        float payment_value
        string order_status
    }
    DIM_CLIENTES {
        string customer_id PK
        string customer_city
        string customer_state
    }
    DIM_PRODUTOS {
        string product_id PK
        string product_category_name
        float product_weight_g
    }
    DIM_TEMPO {
        date data_completa PK
        int ano
        int mes
        string dia_semana
    }

    FATO_PEDIDOS }|--|| DIM_CLIENTES : "realizado por"
    FATO_PEDIDOS }|--|| DIM_PRODUTOS : "contém"
    FATO_PEDIDOS }|--|| DIM_TEMPO : "ocorre em"



## 📁 Fase 1: Ingestão e Catálogo de Dados

Os dados brutos em `.csv` foram importados para a plataforma Dadosfera, onde as tabelas físicas foram geradas no Snowflake.

* **Link para o Catálogo na Dadosfera:** [https://app.dadosfera.ai/pt-BR/catalog/data-assets?tags=&asset_types=&owner=guilherme.lima85&page=1&sort=az]

**Evidência do Catálogo:**
![Catálogo de Dados](catálogo.jpeg)

---

## 📊 Fase 2: Análise Exploratória e Dashboard Executivo

A partir das tabelas físicas, foram construídas consultas SQL complexas para responder a perguntas de negócio e montar um painel gerencial completo.

**Métricas desenvolvidas (Overdelivery):**
1. Faturamento Total (R$)
2. Ticket Médio por Pedido
3. Tempo Médio de Entrega (Dias)
4. Nota Média de Satisfação dos Clientes
5. Evolução Mensal de Pedidos (Série Temporal)
6. Top 10 Categorias Mais Vendidas
7. Top 10 Cidades Compradoras

* **Link para o Dashboard na Dadosfera:** [https://metabase-treinamentos.dadosfera.ai/dashboard/287-visao-executiva-e-commerce-olist]

**Evidência do Dashboard:**
![Dashboard Executivo Olist](dashboard.jpeg)

---

## 💻 Fase 3: Aplicativo de Dados Interativo (Data App)

Foi desenvolvido um aplicativo interativo utilizando **Python e Streamlit** para permitir que os usuários finais explorem os dados de forma dinâmica, com filtros iterativos e análises detalhadas como proporção de status e dias da semana com maior volume de compras.

**Evidência do Aplicativo:**
![App Streamlit](tela.jpeg)

### Como rodar o aplicativo localmente:
1. Clone este repositório.
2. Certifique-se de ter o Python instalado.
3. Instale as dependências: `pip install streamlit pandas plotly`
4. Execute o comando no terminal: `streamlit run app.py`

---
*Projeto construído com foco em resolução de problemas, governança de dados e entrega de valor para o negócio.*
