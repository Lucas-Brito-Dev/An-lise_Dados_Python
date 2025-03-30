# 📊 Projeto 03 - Análise de Vendas

Este projeto tem como objetivo analisar e visualizar dados de vendas utilizando bibliotecas do Python.

🚀 Tecnologias Utilizadas

🐍 pandas: Manipulação e análise de dados.

📂 openpyxl: Leitura e escrita de arquivos Excel.

📊 plotly: Criação de gráficos interativos.

📝 nbformat: Estruturação de notebooks Jupyter.

🛠️ Como Usar

1️⃣ Instalação das Bibliotecas

Caso ainda não tenha as bibliotecas instaladas, execute o seguinte comando:

pip install pandas openpyxl plotly nbformat

2️⃣ Carregar os Dados

O código lê um arquivo vendas.xlsx. Certifique-se de ter esse arquivo na mesma pasta do script.

import pandas as pd
import openpyxl
import plotly.express as px
import nbformat

dados = pd.read_excel("vendas.xlsx")

3️⃣ Análises Exploratórias 🔍

O código permite visualizar informações básicas sobre os dados, como:

📌 Primeiras e últimas linhas (head() e tail())

🏗️ Estrutura dos dados (shape e info())

📊 Estatísticas descritivas (describe())

🏬 Contagem de vendas por loja, cidade e forma de pagamento (value_counts())

4️⃣ Agrupamento de Dados 📂

Para analisar o faturamento:

dados.groupby("loja")["preco"].sum().to_frame()
dados.groupby("forma_pagamento")["preco"].sum().to_frame()

Os resultados são salvos em um arquivo Excel Faturamento.xlsx.

5️⃣ Visualização de Dados 📈

Gráficos interativos são gerados para facilitar a análise do faturamento:

grafico = px.histogram(dados, x="loja", y="preco", text_auto=True, title="Faturamento", color="forma_pagamento")
grafico.show()
grafico.write_html("Faturamento.html")

Gráficos são gerados para diferentes colunas e salvos em arquivos HTML.

6️⃣ Laço de Repetição (for) 🔄

O código também utiliza um loop for para gerar gráficos para várias colunas:

lista_colunas = ["loja", "cidade", "estado", "tamanho", "local_consumo"]
for coluna in lista_colunas:
    grafico = px.histogram(dados, x=coluna, y="preco", text_auto=True, title="Faturamento", color="forma_pagamento")
    grafico.show()
    grafico.write_html(f"Faturamento - {coluna}.html")

Isso permite automatizar a geração de gráficos para diferentes variáveis.
