# Análise de Dados e Eficiência Energética (CP1 & Desafios Complementares)

Repositório dedicado ao Checkpoint 1 (CP1) da matéria Soluções em Energias Renováveis e Sustentáveis e às atividades complementares em Python, focadas em manipulação de dados, análise exploratória (EDA), identificação de picos de demanda elétrica, cruzamento de critérios de carga e geração de relatórios técnicos assistidos por IA (Google GenAI / Gemini).

## Integrantes do Grupo
* **Kauan Damasceno de Lima** – RM: 573772
* **Guilherme Figueira Velloso** – RM: 568827
* **Thiago Soalheiro Diamantino** – RM: 569316
* **José Augusto Ribeiro Freire Manfrinato** – RM: 571151
* **Lais da Silva Dias** – RM: 569943
* **João Augusto Poloniato Telles** – RM: 571443

---

## 📂 Sobre a Atividade e Estrutura
O projeto divide-se em etapas de manipulação de datasets reais do setor energético (provenientes da UCI Machine Learning Repository e Kaggle) e a execução dos **Desafios Complementares** no Google Colab, que englobam:
1. **Inspeção e Organização:** Criação de DataFrames, tratamento de valores ausentes, renomeação de colunas e padronização de tipos de dados.
2. **Indicadores Estatísticos:** Cálculo de carga mínima, máxima, média, mediana e amplitude.
3. **Análise de Alta Demanda:** Definição de limiares críticos (ex: 90% ou 75% da carga máxima) e mapeamento do percentual de representatividade dos picos.
4. **Segundo Critério de Análise:** Cruzamento de dados de consumo com variáveis ambientais ou operacionais (como temperatura ou fator de potência).
5. **Visualizações Gráficas:** Construção de gráficos de evolução temporal da carga e distribuições complementares.
6. **Relatório Técnico Assistido por IA:** Integração com a API do Google Gemini (`google-genai`) para síntese de resultados, seguida de uma rigorosa **validação crítica** para evitar vieses ou causalidades falsas.

---

## 📊 Fontes dos Dados Analisados

O projeto explora diferentes bases de dados do setor elétrico:

1. **Dataset 1 (Appliances Energy Prediction - UCI):** [Consumo residencial e microclima] — *Fonte: (https://archive.ics.uci.edu/dataset/374/appliances+energy+prediction)*.
2. **Dataset 2 (Steel Industry Energy Consumption - UCI):** [Indústria siderúrgica, fator de potência e cargas] — *Fonte: (https://archive.ics.uci.edu/dataset/851/steel+industry+energy+consumption)*.
3. **Dataset 3 (Power Consumption of Tetouan City - UCI):** [Zonas de distribuição urbana e clima][cite: 1] — *Fonte: (https://archive.ics.uci.edu/dataset/849/power+consumption+of+tetouan+city)*.
4. **Dataset 4 (Kaggle):** (Solar Power Generation Data) - *Fonte: (https://www.kaggle.com/datasets/anikannal/solar-power-generation-data)*.
5. **Dataset 5 (Kaggle):** (Wind & Solar Energy Production) - *Fonte: (https://www.kaggle.com/datasets/ahmeduzaki/wind-and-solar-energy-production-dataset)*.
6. **Dataset 6 (Individual Household Electric Power Consumption - UCI):** [Monitoramento detalhado de tensão, corrente e submedições] - *Fonte: (https://archive.ics.uci.edu/dataset/235/individual+household+electric+power+consumption)*.

---

## Tecnologias e Ferramentas Utilizadas
* **Python 3.x**
* **Pandas & NumPy** (Manipulação e computação numérica)
* **Matplotlib / Seaborn** (Visualização de dados e gráficos)
* **Google GenAI SDK (`google-genai`)** (Integração com LLM para síntese de relatórios)
* **Google Colab** (Ambiente de desenvolvimento)
* **Git & GitHub** (Controle de versão)

---

## 🚀 Como Executar o Projeto
1. Clone o repositório ou abra o arquivo `.ipynb` diretamente no **Google Colab**.
2. Certifique-se de instalar as dependências necessárias executando:
   ```bash
   pip install -U pandas matplotlib seaborn google-genai
