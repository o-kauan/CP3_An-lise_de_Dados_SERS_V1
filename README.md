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

# RELATÓRIO TÉCNICO DE ANÁLISE DE CARGA ELÉTRICA
 
### 1. Objetivo e Fonte dos Dados
O objetivo deste relatório técnico é apresentar a avaliação quantitativa do comportamento da carga elétrica verificada na região de São Paulo (SP) durante o período de 01/08/2025 00:30 a 08/08/2025 00:00. Os dados utilizados foram obtidos por meio da API pública de Carga Verificada do Operador Nacional do Sistema Elétrico (ONS), totalizando 336 registros temporais analisados.
 
---
 
### 2. Principais Indicadores
A análise estatística descritiva do conjunto de 336 registros apresenta os seguintes valores expressos em megawatts médios (MWmed):
 
*   **Quantidade de registros:** 336
*   **Carga Mínima:** 12.139,25 MWmed
*   **Carga Máxima:** 23.185,31 MWmed
*   **Carga Média:** 17.870,83 MWmed
*   **Mediana:** 18.199,13 MWmed
 
**Comparação Média vs. Mediana:**  
A mediana (18.199,13 MWmed) posiciona-se 328,30 MWmed acima da carga média (17.870,83 MWmed). Essa diferença indica uma assimetria à esquerda na distribuição dos dados, demonstrando que mais de 50% dos registros estão concentrados em patamares superiores à média aritmética global do período.
 
---
 
### 3. Pico e Alta Demanda
*   **Momento do Pico:** O valor máximo absoluto de carga do período ocorreu no dia **01/08/2025 às 19:00**, atingindo **23.185,31 MWmed**.
*   **Limiar de Alta Demanda (Percentil 90):** Definido em **21.278,37 MWmed**.
*   **Registros acima do limiar:** Foram contabilizados **34 registros** situados no decil superior de carga, o que representa **10,12%** do total de 336 registros analisados.
 
---
 
### 4. Comparação entre os Dois Critérios
 
*   **Critério 1 (Limiar de Alta Demanda / Percentil 90):**  
    *   *O que mede:* Mede a ocorrência de cargas extremas localizadas na cauda superior da distribuição (valores que superam 90% de todo o histórico do período).  
    *   *Volume selecionado:* 34 registros (10,12% do total).  
    *   *Limiar exigido:* Carga superior a 21.278,37 MWmed.
 
*   **Critério 2 (Carga acima da média no intervalo 18h-21h):**  
    *   *O que mede:* Mede a frequência e a intensidade com que a carga excede a média global do período (17.870,83 MWmed) especificamente dentro da janela horária das 18h às 21h.  
    *   *Volume selecionado:* 41 registros (12,20% do total).  
    *   *Carga média observada nesse grupo:* 21.658,22 MWmed.
 
*   **Análise comparativa e restritividade:**  
    O **Critério 1 é mais restritivo** em relação ao patamar mínimo de carga exigido (21.278,37 MWmed contra 17.870,83 MWmed do Critério 2), resultando em menor quantidade de registros selecionados (34 contra 41). A diferença entre os critérios evidencia que a janela horária das 18h às 21h concentra de forma recorrente patamares elevados de carga (41 ocorrências acima da média global), cuja média própria (21.658,22 MWmed) chega a superar o próprio limiar de percentil 90 da curva geral (21.278,37 MWmed).
 
---
 
### 5. Observações Consolidadas
*   A amplitude total entre a demanda máxima (23.185,31 MWmed) e a mínima (12.139,25 MWmed) no período foi de 11.046,06 MWmed.
*   O ponto de carga máxima registrada (23.185,31 MWmed em 01/08/2025 às 19:00) situa-se dentro da janela horária contemplada pelo Critério 2 (18h às 21h).
*   Os registros pertencentes ao Critério 2 mantiveram um valor médio de 21.658,22 MWmed, superior à mediana global do sistema (18.199,13 MWmed).
*   Exatamente 34 registros (10,12%) situam-se no patamar de cauda superior (acima de 21.278,37 MWmed).
 
---
 
### 6. Hipóteses a Verificar
 
*   **Hipótese a verificar 1:** O valor máximo de carga verificado em 01/08/2025 às 19:00 (23.185,31 MWmed) esteve associado a temperaturas extremas na região.  
    *   *Dado adicional necessário para teste:* Série temporal de variáveis meteorológicas (temperatura e umidade relativa do ar) na região SP coincidentes com o período e horários analisados.
 
*   **Hipótese a verificar 2:** A concentração de 41 registros acima da média global entre 18h e 21h decorre da sobreposição de consumo do setor residencial e comercial ao final da jornada de trabalho.  
    *   *Dado adicional necessário para teste:* Dados de medição desagregados por classe de consumo (residencial, comercial, industrial e outros) em intervalos semi-horários ou horários.
 
---
 
### 7. Limitações da Análise
*   **Ausência de Causalidade:** Com base exclusivamente nas medições de carga fornecidas, não é possível atribuir causas climáticas, comportamentais, econômicas ou associadas a feriados/dias úteis para os padrões observados.
*   **Restrição Temporal:** O conjunto de dados limita-se a 336 registros (7 dias completos de amostragem), impossibilitando inferências sobre sazonalidade anual ou tendências de longo prazo.
*   **Falta de Informação Operacional:** A base não contempla dados sobre indisponibilidade de equipamentos de rede, geração distribuída instalada ou eventos sistêmicos atípicos no período.
 
---
 
### 8. Conclusão
A análise da carga verificada na região SP entre 01/08/2025 e 08/08/2025 identificou uma demanda média de 17.870,83 MWmed e um valor de pico de 23.185,31 MWmed (01/08/2025 às 19:00). A distribuição apresenta mediana (18.199,13 MWmed) superior à média, refletindo predomínio de registros em patamares elevados. O limiar de alta demanda de 21.278,37 MWmed (percentil 90) capturou 34 registros (10,12%), mostrando-se mais seletivo do que o filtro de carga acima da média na janela das 18h às 21h, o qual capturou 41 registros (12,20%) com carga média de 21.658,22 MWmed.

---

## 🚀 Como Executar o Projeto
1. Clone o repositório ou abra o arquivo `.ipynb` diretamente no **Google Colab**.
2. Certifique-se de instalar as dependências necessárias executando:
   ```bash
   
   pip install -U pandas matplotlib seaborn google-genai
