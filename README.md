# 📊 Projeto de Segmentação de Clientes usando Machine Learning

## 📌 Introdução

Este projeto utiliza técnicas de *Machine Learning* para agrupar clientes com base em características como **idade, renda anual e pontuação de gastos**. A segmentação de clientes ajuda as empresas a personalizarem estratégias de marketing e oferecerem serviços específicos para grupos de clientes semelhantes.

---

## 🔍 Metodologia

O projeto segue estas etapas:

1. **📥 Carregamento dos Dados**
   - Os dados dos clientes são importados de um arquivo CSV usando Python.
   
   ```python
   import pandas as pd
   from sklearn.cluster import KMeans
   from sklearn.preprocessing import StandardScaler
   df = pd.read_csv('/content/dados_clientes.csv')
   df.head()
   ```

2. **📊 Análise Exploratória**
   - São exibidas as primeiras linhas dos dados e estatísticas simples das variáveis principais.

   ```python
   df[['idade', 'renda_anual', 'pontuacao_gastos']].describe()
   ```

3. **⚙️ Pré-Processamento dos Dados**
   - Os dados são ajustados para terem a mesma escala, garantindo uma análise mais precisa.

   ```python
   from sklearn.preprocessing import StandardScaler
   padronizador = StandardScaler()
   dados_padronizados = padronizador.fit_transform(df[['idade', 'renda_anual', 'pontuacao_gastos']])
   ```

4. **🤖 Construção do Modelo de Machine Learning (K-Means)**
   - Utiliza-se o algoritmo **K-Means** para agrupar os clientes. Neste caso, escolhemos **3 grupos**.

   ```python
   from sklearn.cluster import KMeans
   k = 3
   kmeans = KMeans(n_clusters=k)
   kmeans.fit(dados_padronizados)
   df['cluster'] = kmeans.labels_
   ```

5. **🏷️ Atribuição de Rótulos e Salvamento**
   - Os grupos são atribuídos aos clientes e o resultado é salvo em um novo arquivo CSV.

   ```python
   df.to_csv('dados_segmentos.csv', index=False)
   ```

6. **📊 Geração de Relatório no Power BI**
   - Um relatório interativo é criado usando **Python e Power BI** para uma análise mais visual dos grupos de clientes.

   ```python
   # Instala o pacote
   !pip install -q powerbiclient
   
   # Carrega as funções usadas para autenticar e gerar relatórios
   from powerbiclient import QuickVisualize, get_dataset_config, Report
   from powerbiclient.authentication import DeviceCodeLoginAuthentication
   
   # Define a autenticação no Power BI service
   device_auth = DeviceCodeLoginAuthentication()
   
   # Cria Relatório no Power BI
   relatorio_PBI = QuickVisualize(get_dataset_config(df), auth=device_auth)
   ```

---

## 🛠️ Ferramentas Utilizadas

- **Linguagem de programação**: Python 🐍
- **Bibliotecas principais**: Pandas, Scikit-learn, Powerbiclient 📚
- **Ferramentas adicionais**: Google Colab (para execução do código), Power BI (para geração de relatórios interativos) 📊

---

## ✅ Conclusão

A **segmentação de clientes** ajuda a entender o comportamento dos consumidores, facilitando estratégias de marketing mais eficazes. Este projeto utiliza *Machine Learning* para agrupar clientes e cria um **relatório visual no Power BI** para análise fácil e decisões de negócios informadas. 📈

---



