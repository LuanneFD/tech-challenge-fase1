# Tech Challenge - Fase 1: Diagnóstico de Câncer de Mama

Análise exploratória, pré-processamento, redução de dimensionalidade (PCA) e classificação (KNN, Regressão Logística, SVM e Árvore de Decisão) sobre o dataset *Breast Cancer Wisconsin (Diagnostic)*, com interpretação dos modelos via SHAP e discussão crítica sobre o uso em produção.

## Estrutura do repositório

| Arquivo             | Descrição                                                              |
|----------------------|-------------------------------------------------------------------------|
| `fase1.ipynb`        | Notebook principal com todo o desenvolvimento do trabalho.              |
| `data.csv`            | Base de dados utilizada (569 registros, 30 features + diagnóstico).     |
| `requirements.txt`    | Lista de bibliotecas Python necessárias para rodar o notebook.          |

> O arquivo `data.csv` já está incluído no repositório.

## Pré-requisitos

- Python 3.9 ou superior
- Jupyter Notebook ou Jupyter Lab (ou a extensão Jupyter do VS Code)

## Como executar

1. **Clone ou baixe este repositório** e abra um terminal na pasta do projeto.

2. **Prepare o ambiente:**

   ```bash
   python -m venv venv
   ```

3. **Instale as dependências:**

   ```bash
   pip install -r requirements.txt
   ```

4. **Abra o notebook:**

   ```bash
   jupyter notebook fase1.ipynb
   ```

   Ou abra o arquivo `fase1.ipynb` diretamente pelo VS Code / Jupyter Lab.

5. **Execute todas as células em ordem**, um por vez, do início ao fim.

## O que o notebook faz

1. **Exploração e pré-processamento dos dados** remoção de colunas inválidas, tratamento da variável alvo (`diagnosis`), análise de correlação com o diagnóstico.
2. **Padronização das variáveis** com `StandardScaler`.
3. **Redução de dimensionalidade (PCA)** reduz as 30 variáveis originais para 5 componentes principais (PC1 a PC5), explicando ~84,7% da variância dos dados.
4. **Verificação de normalidade** dos componentes via teste de Shapiro-Wilk.
5. **Treinamento de 4 modelos de classificação:** KNN, Regressão Logística, SVM e Árvore de Decisão, avaliados por acurácia, recall e F1-score.
6. **Verificação dos resultados (SHAP)** para os dois modelos de melhor desempenho (Regressão Logística e SVM), identificando quais componentes mais influenciam cada previsão.
7. **Discussão crítica final** sobre a viabilidade do uso do modelo em um contexto clínico real.

## Observações

- O dataset está desbalanceado (357 casos benignos vs. 212 malignos), o que motivou a escolha do **F1-score** e do **recall da classe maligna** como métricas principais de avaliação, em vez da acurácia isolada.
- Não foi feito tratamento de outliers, por decisão consciente: no contexto médico, um registro fora do padrão pode representar um caso raro da doença que não deve ser descartado.
