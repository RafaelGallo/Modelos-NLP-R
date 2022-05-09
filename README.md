# Modelos-NLP R

[![MIT License](https://img.shields.io/apm/l/atomic-design-ui.svg?)](https://github.com/tterb/atomic-design-ui/blob/master/LICENSEs)
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)
[![author](https://img.shields.io/badge/author-RafaelGallo-red.svg)](https://github.com/RafaelGallo?tab=repositories) 
[![R](https://img.shields.io/badge/R-3.6.0-red.svg)](https://www.r-project.org/)
[![ggplot2](https://img.shields.io/badge/ggplot2-white.svg)](https://ggplot2.tidyverse.org/)
[![](https://img.shields.io/badge/dplyr-blue.svg)](https://dplyr.tidyverse.org/)
[![](https://img.shields.io/badge/readr-green.svg)](https://readr.tidyverse.org/)
[![](https://img.shields.io/badge/ggvis-black.svg)](https://ggvis.tidyverse.org/)
[![](https://img.shields.io/badge/Shiny-red.svg)](https://shiny.tidyverse.org/)
[![](https://img.shields.io/badge/plotly-green.svg)](https://plotly.com/)
[![](https://img.shields.io/badge/XGBoost-red.svg)](https://xgboost.readthedocs.io/en/stable/#)
[![](https://img.shields.io/badge/Caret-orange.svg)](https://caret.tidyverse.org/)

# Objetivo
Nesse projetos são voltado modelos de machine learning - Aplicando processo de linguagem natural NLP.
Objetivo e fazer análise de sentimentos na frases e sabe como está o corpotamentos das pessoas nas rede social como positivos, neutro, negativo.

![Logo](https://as2.ftcdn.net/v2/jpg/04/97/18/07/1000_F_497180791_7J0TPgYrfSXeXHjIp8XoRnuE6eW7zF1b.jpg)

## Autores

- [@RafaelGallo](https://github.com/RafaelGallo)
# Ferramentas
 
- R
- Ggplot2
- TwitteR
- Wordcloud

## Projetos

| Projeto               | Link                                                |
| ----------------- | ---------------------------------------------------------------- |
| Modelo machine learning - NLP Twitter |[Link](https://github.com/RafaelGallo/Modelos-NLP-R/blob/main/R/Model_NLP.R)|


## Demo modelo machine learning - Processamento de linguagem natural

```bash
# Demo modelo machine learning

# Importando bibliotecas
library(twitteR)
library(httr)
library(ggplot2)
library(knitr)
library(rmarkdown)
library(RColorBrewer)
library(wordcloud)
library(readr)

# Importando dataset
data <- read_csv("Dataset.csv")

# Visualizando os cinco primeiros dados
head(data)

# Visualizando os cinco últimos dados
tail(data)

# Linhas e colunas
dim(data)

# Tratamento dos textos
# Com este código aqui, estamos levando todo o texto para letras minúsculas, removendo números, removendo pontuação, palavras irrelevantes e assim por diante

nlp_corpus = tm_map(nlp_corpus, content_transformer(tolower))
nlp_corpus = tm_map(nlp_corpus, removeNumbers)
nlp_corpus = tm_map(nlp_corpus, removePunctuation)
nlp_corpus = tm_map(nlp_corpus, removeWords, stopwords("english"))
nlp_corpus = tm_map(nlp_corpus, stemDocument)
nlp_corpus = tm_map(nlp_corpus, stripWhitespace)
as.character(nlp_corpus[[1]])

# Criando dataframe palavras mais faladas
grad <- data.frame(word=names(feq), feq=feq)
head(grad)

positive <- subset(data,sentiment=="Positive")
negative <- subset(data_1,sentiment=="Negative")
neutral <- subset(data_1,sentiment=="Neutral")
head(positive)
head(negative)
head(neutral)

# Gerando uma nuvem palavras
wordcloud(positive$text, max.words = 100, scale = c(3,0.5))
wordcloud(negative$text, max.words = 100, scale = c(3,0.5))
wordcloud(neutral$text, max.words = 100, scale = c(3,0.5))

# Etapa 7 Divisão de dados 
# Divindo treino e teste para modelo

set.seed(222)
n_split = sample(2, nrow(dataset_1), prob = c(0.75,0.25), replace = TRUE)
train = dataset_1[n_split == 1,]
test = dataset_1[n_split == 2,]

# Visualizando os dados de treino
dim(train)

# Visualizando os dados de teste
dim(test)

# Tabela sentimentos dados treino
prop.table(table(train$Class))

# Tabela sentimentos dados teste
prop.table(table(test$Class))

# Etapa 8 Modelos machine learning 
# Modelo 01 - Naive Bayes

# Importtando a biblioteca naive bayes
library(e1071)

# Modelo 
model_naive_bayes <- naiveBayes(train, # Variavel treinamento 
                                train$Class, # Variavel alvo
                                laplace = 1, # Time
                                trControl = control,tuneLength = 7)

# Imprimindo o modelo
model_naive_bayes

# Previsão do modelo
model_naive_bayes_pred = predict(classifier_nb, type = 'class', newdata = test)
model_naive_bayes_pred

# Matriz confusão do modelo
confusionMatrix(model_naive_bayes_pred, test$Class)
```
## Documentação
[Dataset - Modelo NLP](https://www.kaggle.com/datasets/crowdflower/first-gop-debate-twitter-sentiment)

## Screenshots
![App Screenshot](https://datarefiner.com/static/img/linkedin_datarefiner_ui.gif)

## Suporte
Para suporte, mande um email para rafaelhenriquegallo@gmail.com ou entre em nosso canal do Slack.


## Referência

 - [Dataset](https://www.kaggle.com/datasets/crowdflower/first-gop-debate-twitter-sentiment)
 - [Kaggle](https://www.kaggle.com/)
 - [Stackoverflow](https://stackoverflow.com/questions/29854053/confusion-matrix-error)

