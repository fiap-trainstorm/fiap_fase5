# pbl_fase5_farmtech

# FarmTech Solutions – Análise Exploratória, Tendências de Safra e Modelagem Preditiva

## Contexto
Este projeto faz parte da *Fase 5 do PBL FIAP*.  
O cenário envolve a *FarmTech Solutions*, que presta serviços de Inteligência Artificial para uma fazenda de médio porte (200 hectares).  
O objetivo é analisar os dados de clima e solo, explorar tendências de rendimento das culturas, identificar cenários discrepantes (outliers) e *criar modelos preditivos supervisionados para estimar o rendimento da safra*.

## Escopo do Projeto
- *Análise exploratória dos dados (EDA)*  
- *Identificação de tendências de rendimento via clusterização (KMeans + PCA)*  
- *Detecção de cenários discrepantes (outliers com DBSCAN e boxplots)*  
- *Modelagem Preditiva Supervisionada (Regressão)*  
- *Documentação e vídeo explicativo dessa análise*

## Dataset
Arquivo: crop_yield.csv  
Variáveis principais:
- Cultura  
- Precipitação (mm/dia)  
- Umidade específica a 2m (g/kg)  
- Umidade relativa a 2m (%)  
- Temperatura a 2m (ºC)  
- Rendimento (ton/ha)  

## Principais Etapas da Análise
1. *Exploração inicial* – estatísticas descritivas, distribuições e correlações.  
2. *Clusterização (KMeans + PCA)* – identificação de tendências de rendimento e agrupamentos distintos de culturas.  
3. *Detecção de outliers (DBSCAN + análises estatísticas)* – identificação de pontos discrepantes de produtividade.  
4. *Exportação de casos suspeitos* – arquivo adicional com registros extremos.  
5. *Modelagem preditiva (Meta 3)*  
   - Construção de *cinco modelos de regressão* para prever rendimento:  
     - Regressão Linear  
     - Árvore de Decisão  
     - Random Forest  
     - Gradient Boosting  
     - Support Vector Regressor (SVR)  
   - Uso de *Pipeline* para pré-processamento (OneHotEncoder + StandardScaler).  
   - *Validação cruzada (KFold)* e *GridSearchCV* para otimização de hiperparâmetros.  
   - Avaliação por métricas de regressão: *R², MAE e RMSE*.  
   - Comparação dos modelos em tabela e gráficos.  
   - Salvamento do *melhor modelo* em .joblib para uso futuro.  
   - Exemplo de *inferência com novos dados* incluso no notebook.  

## Estrutura do Repositório
- VicenzoDeSimoneMontefusco_rm563810_pbl_fase4.ipynb → Notebook com análise exploratória, clusterização, outliers e modelagem preditiva.  
- crop_yield.csv → Base de dados fornecida.  
- suspected_outliers_and_extremes.csv → Registros suspeitos/exportados como potenciais *outliers*.  
- LeticiaGomezPinheiro_rm561332_pbl_fase4_ipynb → Resultados comparativos dos modelos preditivos. 

### Sobre o arquivo de outliers
O arquivo suspected_outliers_and_extremes.csv contém as linhas do dataset que apresentaram *valores discrepantes* segundo:
- Análise estatística (boxplots, z-score)  
- Clusterização DBSCAN  

Esse material serve como *evidência* dos cenários incomuns de rendimento e pode apoiar decisões futuras da fazenda, como investigar condições climáticas anômalas ou problemas pontuais no solo.

### Sobre os modelos preditivos
A etapa de modelagem mostrou que algoritmos de ensemble (como Random Forest e Gradient Boosting) apresentaram melhor desempenho, com maior capacidade de capturar relações não lineares entre clima, solo e rendimento.  
O modelo vencedor foi salvo em .joblib para servir como *ferramenta de apoio à decisão* para a fazenda.  

## 🎥 Demonstração em Vídeo
➡ [Link para o vídeo no YouTube](placeholder) (modo não listado)

## Conclusões
- Foram identificadas *tendências claras* nos rendimentos com base em clima e solo.  
- Clusters distintos de produtividade foram encontrados, revelando perfis diferentes de culturas.  
- Alguns *outliers* foram detectados, que podem indicar erros de coleta ou situações reais de stress agrícola.  
- Foram treinados e comparados *cinco modelos preditivos supervisionados; os melhores apresentaram **bom poder explicativo* para prever o rendimento.  
- O melhor modelo foi salvo para uso em cenários reais de previsão.  
- Limitações: dataset relativamente pequeno, análise restrita a variáveis fornecidas.
