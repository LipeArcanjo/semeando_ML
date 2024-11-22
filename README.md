# Predição de Dificuldades por Tipo de Pergunta

Este projeto utiliza **machine learning** para prever a dificuldade de usuários em responder perguntas de diferentes temas. Ele foi desenvolvido como um notebook Jupyter projetado para execução no Google Colaboratory. O modelo é treinado com dados simulados e ajustado para realizar previsões com base em características como taxa de acertos, tempo de resposta e mudanças realizadas pelo usuário.

---

## Requisitos

### Pré-requisitos para execução:
- Conta no Google Colaboratory.
- Navegador com suporte para Jupyter Notebooks.

### Bibliotecas Utilizadas:
As bibliotecas necessárias para executar o notebook são instaladas automaticamente ao rodar as células correspondentes.

---

## Passos para Execução

### 1. Abrir o Notebook no Google Colaboratory
Faça upload do arquivo `Semeando_ML.ipynb` no Google Colab ou abra-o diretamente a partir do seu Google Drive.

### 2. Configurar o Ambiente
Execute a célula que instala as bibliotecas necessárias (já incluída no notebook):

### 3. Executar o Notebook
Execute cada célula sequencialmente para:
- Simular os dados.
- Treinar o modelo.
- Realizar previsões.

---

## Descrição do Projeto

### Objetivos:
- Simular um conjunto de dados representando perguntas, opções e respostas de usuários.
- Treinar um modelo de machine learning utilizando **Random Forest Classifier**.
- Realizar previsões de dificuldade para diferentes temas.

### Dados:
- **Tabela de Perguntas (`tb_Pergunta`)**: Contém os tipos de perguntas.
- **Tabela de Opções (`tb_Opcao`)**: Contém as opções de resposta e se são corretas.
- **Tabela de Respostas (`tb_Resposta`)**: Contém as respostas dos usuários, tempos de resposta e mudanças realizadas.

### Predições:
O modelo prevê se a dificuldade para um tipo de pergunta será **alta** ou **baixa** para um exemplo de usuário.

---

## Estrutura do Notebook

### Simulação de Dados:
As tabelas são geradas com os seguintes campos:

- **`tb_Pergunta`:**
  - `id_pergunta`: Identificador único da pergunta.
  - `tipo_pergunta`: Tipo da pergunta (e.g., Fontes de Energia Renovável, Impacto Ambiental, etc.).

- **`tb_Opcao`:**
  - `id_opcao`: Identificador único da opção.
  - `id_pergunta`: Pergunta associada.
  - `op_correta`: Define se a opção é correta (`S`) ou incorreta (`N`).

- **`tb_Resposta`:**
  - `id_usuario`: Usuário que respondeu.
  - `id_pergunta`: Pergunta associada.
  - `op_escolhida`: Opção escolhida.
  - `tempo_resposta`: Tempo em segundos para responder.
  - `mudanca_resposta`: Indica se houve mudança de resposta (`0` ou `1`).

### Treinamento do Modelo:
- Os dados são processados para calcular variáveis auxiliares:
  - Taxa de acertos, erros e desvio no tempo de resposta.
- As classes são balanceadas com **SMOTE**.
- O modelo é treinado utilizando **Random Forest Classifier**.

### Visualização:
O notebook inclui gráficos mostrando a importância das variáveis no modelo.

---

## Exemplo de Saída

### Relatório de Classificação

```plaintext
Relatório de Classificação:
              precision    recall  f1-score   support

           0       0.91      0.89      0.90        35
           1       0.88      0.90      0.89        30

    accuracy                           0.90        65
   macro avg       0.90      0.90      0.90        65
weighted avg       0.90      0.90      0.90        65

Acurácia do modelo: 0.90
```
### Importância das Variáveis
O notebook inclui um gráfico que destaca a importância de cada variável no desempenho do modelo. Esse gráfico é gerado automaticamente após o treinamento, indicando quais características tiveram maior impacto nas previsões.

### Previsões para um Usuário

#### Exemplo de Dados de um Usuário para Previsão:
```plaintext
                        tipo_pergunta              total_respostas  tempo_medio  tempo_desvio  mudancas_resposta  proporcao_acertos  porcentagem_erros
0     Fontes de Energia Renovável                     50             12            2                 1                  85                15
1     Transporte Sustentável                          45             15            3                 2                  75                25
2     Impacto Ambiental                               40             10            4                 3                  65                35
3     Mudanças Climáticas                             60             20            6                 1                  80                20
4     Redução de Consumo Doméstico                   55             18            5                 0                  90                10
```

### Previsões:

Com base nos dados fornecidos, o modelo realiza as seguintes previsões sobre a dificuldade:

- **Fontes de Energia Renovável**: Baixa dificuldade
- **Transporte Sustentável**: Alta dificuldade
- **Impacto Ambiental**: Alta dificuldade
- **Mudanças Climáticas**: Baixa dificuldade
- **Redução de Consumo Doméstico**: Baixa dificuldade

