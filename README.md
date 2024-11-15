
# 🚀 CrewAI - Stock Agents

CrewAI_StockAgents é um projeto de agentes inteligentes focados em análise e previsão de ações no mercado financeiro. Utilizando a combinação de APIs e modelos de aprendizado de máquina, CrewAI_StockAgents oferece uma maneira automatizada de pesquisar dados financeiros, analisar o desempenho das ações e gerar relatórios detalhados.

![Gif](gif.gif)


## Funcionalidades ✨

- **Pesquisa de Dados**: Coleta de dados históricos de ações usando a API do **Yahoo Finance**.
- **Análise de Desempenho**: Análise do desempenho das ações comparando com a média dos últimos 5 dias.
- **Geração de Relatórios**: Geração de relatórios detalhados com emojis personalizados, fornecendo uma análise completa.

## Modelos e APIs Utilizadas 🔧

### 1. **API do Yahoo Finance (yfinance) 📉**
O **yfinance** é uma biblioteca Python que permite acessar dados financeiros diretamente da plataforma **Yahoo Finance**. Ela é usada para coletar os dados históricos de ações, como preços de fechamento e médias móveis.

- **Objetivo**: Pesquisar os dados financeiros de ações e obter os históricos de preços de ações (últimos 5 dias).
- **Exemplo de Uso**: Coleta de dados históricos para um símbolo de ação (ex: `TSLA`, `AAPL`).

### 2. **Llama 3.2 1B 💡**
**Llama 3.2 1B** é um modelo de linguagem avançado, desenvolvido para entender e gerar respostas precisas em contextos financeiros. Com 1 bilhão de parâmetros, o modelo é altamente capaz de fazer previsões e gerar análises de dados financeiros de ações.

- **Objetivo**: Usado para analisar dados financeiros e fornecer recomendações detalhadas.
- **Modelo de aprendizado de máquina**: Utiliza redes neurais profundas para processar dados históricos e comparar tendências.

### 3. **API do Hugging Face 🔑**
O projeto **CrewAI_StockAgents** utiliza a API do **Hugging Face** para carregar modelos pré-treinados, como o **Llama 3.2 1B**. A plataforma Hugging Face fornece uma ampla gama de modelos de aprendizado de máquina, permitindo o uso de modelos avançados para diversas tarefas.

- **Objetivo**: Fornecer o modelo Llama 3.2 1B via Hugging Face para análise e previsão de ações.
- **Exemplo de Uso**: Carregar e usar modelos de linguagem para análise de dados financeiros.

## Como Funciona a CrewAI? 🤖

A CrewAI_StockAgents utiliza três **agentes inteligentes** para realizar a pesquisa, análise e geração de relatórios de ações. Cada agente é responsável por uma parte específica do fluxo de trabalho, e eles interagem entre si para fornecer os resultados finais.

### Agentes da CrewAI

1. **Agente Pesquisador de Ações** 🔍
   - **Função**: O Agente Pesquisador de Ações é responsável por pesquisar dados financeiros históricos das ações. Ele utiliza a API do **Yahoo Finance** para coletar os dados dos últimos 5 dias de cada ação.
   - **Exemplo de uso**: Pesquisa dos dados históricos de uma ação, como `TSLA`, `AAPL` ou `AMZN`.
   
   **Código**:
   ```python
   class StockSearchTool:
       def __init__(self):
           pass

       def search(self, stock_symbol):
           # Chama a função para pesquisar dados históricos da ação
           return search_stock_data(stock_symbol)
   ```

2. **Agente Analista de Ações** 📊
   - **Função**: O Agente Analista de Ações recebe os dados históricos de uma ação e realiza uma análise do seu desempenho. Ele compara o preço atual de fechamento com a média dos últimos 5 dias para determinar se a ação está em alta ou baixa.
   - **Exemplo de uso**: Analisar o desempenho de `TSLA` com base nos dados históricos coletados.

   **Código**:
   ```python
   class StockAnalysisTool:
       def __init__(self):
           pass

       def analyze(self, stock_data):
           # Chama a função para analisar o desempenho da ação
           return analyze_stock_performance(stock_data)
   ```

3. **Agente Gerador de Relatórios** 📑
   - **Função**: O Agente Gerador de Relatórios utiliza os dados coletados e os resultados da análise para gerar um relatório detalhado sobre o desempenho da ação. Os relatórios incluem uma recomendação baseada no desempenho da ação, com emojis personalizados.
   - **Exemplo de uso**: Gerar um relatório detalhado para `TSLA` após análise dos dados.

   **Código**:
   ```python
   class ReportGenerationTool:
       def __init__(self):
           pass

       def generate(self, stock_symbol, stock_data, analysis_result):
           # Chama a função para gerar o relatório da ação
           return generate_report(stock_symbol, stock_data, analysis_result)
   ```

## Fluxo de Trabalho 🛠️

O fluxo de trabalho da CrewAI segue o processo abaixo:

1. **Pesquisa de Dados**: O Agente Pesquisador de Ações coleta os dados históricos da ação usando a API `yfinance`.
2. **Análise de Desempenho**: O Agente Analista de Ações avalia o desempenho da ação, comparando o preço atual com a média dos últimos 5 dias.
3. **Geração de Relatórios**: O Agente Gerador de Relatórios gera um relatório detalhado, incluindo uma recomendação personalizada com emojis.

Cada relatório é salvo automaticamente em um arquivo `.txt`, com o nome da ação (ex: `TSLA_report.txt`), na pasta `/content`.

### Exemplo de Uso 🧑‍💻

1. **Passo 1: Pesquisa de Dados**
   Ação `TSLA`:
   ```python
   stock_data = agent_search.tools[0].search("TSLA")
   ```

2. **Passo 2: Análise de Desempenho**
   ```python
   analysis_result = agent_analysis.tools[0].analyze(stock_data)
   ```

3. **Passo 3: Geração de Relatório**
   ```python
   report = agent_report.tools[0].generate("TSLA", stock_data, analysis_result)
   ```

4. **Salvar Relatório em .txt**
   O relatório gerado será automaticamente salvo como `TSLA_report.txt` na pasta `/content`.

## Integração com o Telegram 📲

Os relatórios gerados podem ser enviados automaticamente para um canal do **Telegram** utilizando a API do **Telegram**. O bot pode enviar os arquivos `.txt` gerados para o canal, permitindo que os resultados sejam facilmente compartilhados.

- **Passo para Enviar Relatórios**:
   Após gerar o relatório, basta usar o método de envio para o Telegram.

```python
await send_all_reports_to_telegram(bot_token, '@IDCANAL')
```

**Espaço para o print**:
_(Aqui, você pode inserir um print do relatório ou do processo em execução no Telegram, conforme necessário)_

---

## Contribuições 🤝

Se você quiser contribuir para o projeto **CrewAI_StockAgents**, fique à vontade para fazer um fork do repositório, criar um branch e enviar pull requests. Estamos abertos a sugestões e melhorias! 🚀

---
