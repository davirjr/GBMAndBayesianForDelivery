# Previsão de Desempenho de Entregas com Modelos de Machine Learning

Este projeto tem como objetivo prever o desempenho das entregas ao longo do mês, estimando a proporção de entregas realizadas em menos de 30 minutos. Utiliza uma combinação de modelo Bayesiano dinâmico e Gradient Boosting Machines (GBM) para previsões contínuas e ações corretivas proativas. Este modelo é útil para dados onde o tempo de entrega se comporta de forma não paramétrica e tem alta influência de caudas longas (outliers).

O modelo Bayesiano é particularmente eficaz quando combinado com métodos que permitem determinar a importância de cada variável para o resultado. Nesse caso, ele é ideal para um processo de entrega que segue um comportamento semelhante ao log-normal, com efeito de cauda longa e a presença de cerca de 5% de outliers.

## Objetivo
- **Meta de Desempenho**: 75% ou mais das entregas realizadas em menos de 30 minutos. #Pode ser ajustado conforme a necessidade do seu processo. 
- O modelo Bayesiano faz previsões contínuas da proporção de entregas dentro do prazo, atualizadas diariamente com novos dados (certifique-se de que a distribuição seja razoavelmente similar à log-normal - caso não seja, ajuste o modelo). 
- Quando a previsão indicar risco de não atingir a meta, o **GBM** é acionado para identificar as principais causas dos atrasos e permitir ações corretivas.

## Funcionalidade
- **Modelo Bayesiano Dinâmico**: Calcula a probabilidade mensal de que a porcentagem de entregas abaixo de 30 minutos seja inferior a 75%. As previsões são ajustadas diariamente.
- **Gradient Boosting Machines (GBM)**: Quando necessário, é utilizado para identificar fatores influentes nos atrasos, como setor de prescrição, horário de geração da entrega e outros.

## Como Funciona
1. **Previsão Diária**: O modelo Bayesiano gera previsões contínuas com base nas entregas do dia.
2. **Análise de Atrasos**: Se a previsão indicar que a meta pode não ser atingida, o modelo GBM analisa as causas dos atrasos.
3. **Ação Corretiva**: A equipe pode tomar ações específicas para melhorar o desempenho antes que a meta de 75% seja comprometida.

## Tecnologias Utilizadas
- Python
- Bibliotecas: `numpy`, `pandas`, `scikit-learn`, `xgboost`, `pyMC3` (ou qualquer biblioteca Bayesiana similar)
- Jupyter Notebook

## Como Usar
1. Clone este repositório para sua máquina local:
   ```bash
   git clone https://github.com/SEU_USUARIO/NOME_DO_REPOSITORIO.git
