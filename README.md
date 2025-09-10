# pbl_fase5_farmtech

# FarmTechIOT - Sistema de Monitoramento e Irrigação
# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
<a href= "https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Admnistração Paulista" border="0" width=40% height=40%></a>
</p>

<br>


## 👨‍🎓 Integrantes: 
- <a href="https://www.linkedin.com/company/inova-fusca">Anna Cecilia Moreira Cabral</a>
- <a href="https://www.linkedin.com/company/inova-fusca">Heitor Exposito de Sousa</a>
- <a href="https://www.linkedin.com/company/inova-fusca">Letícia Gomez Pinheiro</a> 
- <a href="https://www.linkedin.com/company/inova-fusca">Thiago Sabato Romano</a> 
- <a href="https://www.linkedin.com/company/inova-fusca">Vicenzo de Simone Montefusco</a>

## 👩‍🏫 Professores:
### Tutor(a) 
- <a href="https://www.linkedin.com/company/inova-fusca">Leonardo Ruiz Orabona</a>
### Coordenador(a)
- <a href="https://www.linkedin.com/company/inova-fusca">Andre Godoi Chiovato</a>
## **Projeto Base: Sistema de Irrigação Inteligente Simulado**
---

## **Parte I: Análise Exploratória, Tendências de Safra e Modelagem Preditiva


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

## 🎥 Demonstrações em Vídeo (em ordem)
➡ [Link para o vídeo no YouTube](https://youtu.be/BuuzKaYh6yI) (modo não listado)
➡ [Link para o vídeo no YouTube](https://youtu.be/8ZvZNoZpl7E) (modo não listado)


## Conclusões
- Foram identificadas *tendências claras* nos rendimentos com base em clima e solo.  
- Clusters distintos de produtividade foram encontrados, revelando perfis diferentes de culturas.  
- Alguns *outliers* foram detectados, que podem indicar erros de coleta ou situações reais de stress agrícola.  
- Foram treinados e comparados *cinco modelos preditivos supervisionados; os melhores apresentaram **bom poder explicativo* para prever o rendimento.  
- O melhor modelo foi salvo para uso em cenários reais de previsão.  
- Limitações: dataset relativamente pequeno, análise restrita a variáveis fornecidas.

---

## **Parte II: Estratégia de Implantação em Nuvem e Análise de Custos**

Esta seção, formatada para o arquivo README.md do repositório GitHub, aborda a segunda entrega do projeto: a análise de custos e a escolha estratégica de uma infraestrutura de nuvem na AWS para hospedar a API do modelo de Machine Learning.

### **Seção 1: Estimativa de Custos de Infraestrutura AWS**

O objetivo é estimar o custo mensal para hospedar a API do modelo de Machine Learning em uma instância de nuvem, comparando duas regiões da AWS: São Paulo (sa-east-1) e Norte da Virgínia (us-east-1).

#### **1.1. Metodologia e Configuração**

A estimativa foi realizada utilizando a Calculadora de Preços da AWS (AWS Pricing Calculator). A configuração da máquina virtual (instância EC2) e do armazenamento (EBS) segue estritamente os requisitos definidos no projeto:

* **Sistema Operacional:** Linux  
* **vCPUs:** 2  
* **Memória:** 1 GiB  
* **Rede:** Até 5 Gigabit  
* **Armazenamento (HD):** 50 GB  
* **Modelo de Preços:** On-Demand (100%)

Para atender a esses requisitos, foi selecionada a família de instâncias t4g, que utiliza processadores AWS Graviton baseados em Arm, oferecendo uma excelente relação preço-desempenho. A instância <a href="https://aws.amazon.com/ec2/instance-types/t4/">t4g.small</a> (2 vCPUs, 2 GiB de memória) foi escolhida, pois atende aos requisitos de CPU e oferece um pouco mais de memória, o que é benéfico para a estabilidade da aplicação. Para o armazenamento, foi selecionado um volume EBS do tipo gp3 (General Purpose SSD), que oferece um desempenho de linha de base consistente e custo-efetivo.

#### **1.2. Estimativa de Custos para a Região de São Paulo (sa-east-1)**
<p align="center">
<a><img src="assets/t4g-sp.jpeg" alt="AWS - São Paulo" border="0" width=40% height=40%></a>
</p>
A seguir, a captura de tela da estimativa de custos mensais para a configuração especificada na região de São Paulo.

* Custo Mensal Estimado (São Paulo):  
* Instância EC2 (t4g.small): $19.56 USD  
* Volume EBS (gp3, 50 GB): $7.60 USD  
* Total Mensal: $27.16 USD

#### **1.3. Estimativa de Custos para a Região da Virgínia do Norte (us-east-1)**
<p align="center">
<a><img src="assets/t4g-nv.jpeg" alt="AWS - São Paulo" border="0" width=40% height=40%></a>
</p>
A seguir, a captura de tela da estimativa de custos mensais para a mesma configuração na região da Virgínia do Norte.

* Custo Mensal Estimado (Virgínia do Norte):  
* Instância EC2 (t4g.small): $12.26 USD  
* Volume EBS (gp3, 50 GB): $4.00 USD  
* Total Mensal: $16.26 USD

#### **1.4. Tabela Comparativa de Custos**

A tabela abaixo resume a comparação de custos mensais entre as duas regiões.

| Componente | Custo em São Paulo (sa-east-1) | Custo em N. Virgínia (us-east-1) |
| :---- | :---- | :---- |
| Instância EC2 (t4g.small) | $19.56 USD | $12.29 USD | $12.26 USD |
| Armazenamento EBS (50 GB gp3) | $7.60 USD | $4.00 USD |
| **Total Mensal Estimado** | **$27.16 USD** | **$16.26 USD** |

Conclusão da Análise de Custos:  
Com base exclusivamente no preço, a solução mais barata é hospedar a infraestrutura na região da Virgínia do Norte (us-east-1), que representa uma economia de aproximadamente 37.7% em comparação com a região de São Paulo.

### **Seção 2: Seleção Estratégica da Região de Implantação**

A escolha de uma região de nuvem para uma aplicação de produção transcende a simples análise de custos. Fatores como desempenho (latência) e conformidade legal (soberania de dados) são críticos e, muitas vezes, decisivos.

#### **2.1. Fator 1: Desempenho e Latência de Rede**

A latência de rede é o tempo de atraso na comunicação entre dois pontos em uma rede. Para uma aplicação de FarmTech que recebe dados de sensores em tempo real de uma fazenda no Brasil, a baixa latência é crucial. Uma alta latência pode comprometer a capacidade de monitoramento e controle em tempo real, tornando a aplicação ineficaz.

* **São Paulo (sa-east-1):** Por estar geograficamente localizada no Brasil, a latência entre os sensores na fazenda e os servidores da AWS em São Paulo seria mínima, tipicamente inferior a 30 milissegundos (ms).  
* **Virgínia do Norte (us-east-1):** A distância física entre o Brasil e os Estados Unidos introduz uma latência significativa. A comunicação entre essas duas regiões geralmente apresenta uma latência de 120-180 ms ou mais.

Esse atraso de mais de 100 ms tornaria qualquer sistema de resposta rápida (como acionamento de irrigação baseado em um sensor de umidade) inviável. Portanto, do ponto de vista do desempenho, a região de São Paulo é a única escolha viável.

#### **2.2. Fator 2: Restrições Legais e Soberania de Dados**

O armazenamento de dados fora do território nacional levanta questões de soberania de dados e conformidade com a legislação local. No Brasil, a **Lei Geral de Proteção de Dados (LGPD - Lei nº 13.709/2018)** regula o tratamento de dados pessoais.

* **Transferência Internacional de Dados:** Armazenar dados de sensores que possam ser vinculados a uma pessoa física (o proprietário da fazenda, por exemplo) em servidores nos EUA é considerado uma "transferência internacional de dados" pela LGPD.  
* **Requisitos da LGPD:** A LGPD permite a transferência internacional, mas impõe condições rigorosas, como a garantia de que o país de destino oferece um nível de proteção de dados adequado ou a utilização de cláusulas contratuais específicas aprovadas pela Autoridade Nacional de Proteção de Dados (ANPD).  
* **Simplificação da Conformidade:** Embora a transferência seja legalmente possível, ela adiciona uma camada de complexidade jurídica e de conformidade. Manter os dados fisicamente no Brasil, na região de São Paulo, é a maneira mais simples e segura de garantir a conformidade com a LGPD e evitar riscos legais, alinhando-se com as discussões sobre a importância de manter dados de brasileiros em território nacional.

#### **2.3. Recomendação Final e Justificativa**

A análise de fatores não financeiros revela que a opção mais barata nem sempre é a melhor. A decisão de implantar uma solução de produção deve equilibrar custo, desempenho, segurança e conformidade legal.

Recomendação:  
Apesar de ser a opção mais cara, a região da AWS de São Paulo (sa-east-1) é a escolha correta e recomendada para hospedar a API da FarmTech Solutions.  
Justificativa:  
Os requisitos operacionais de baixa latência para o processamento de dados de sensores em tempo real e as imperativas legais de conformidade com a LGPD e soberania de dados superam em muito a economia de custos oferecida pela região da Virgínia do Norte. Optar pela solução mais barata resultaria em uma aplicação com desempenho inadequado e exposta a riscos jurídicos significativos. A escolha pela região de São Paulo garante uma solução robusta, performática e legalmente compatível para o mercado brasileiro.

---

---

## **Parte III: Projetos "Ir Além"**

Esta seção detalha a implementação de dois projetos avançados opcionais, demonstrando capacidades em Internet das Coisas (IoT) e Machine Learning na Borda (TinyML).

### **Seção 3: Sistema de Coleta e Comunicação de Dados com ESP32**

Este projeto detalha a construção de um dispositivo IoT para coletar dados ambientais relevantes para a agricultura e transmiti-los para uma plataforma na nuvem via MQTT.

#### **3.1. Objetivo e Arquitetura do Projeto**

* **Objetivo:** Desenvolver um protótipo funcional que simula a coleta de dados de campo, utilizando um microcontrolador ESP32 e sensores para medir temperatura, umidade do ar e umidade do solo.  
* **Seleção de Sensores:**  
  * **DHT22:** Escolhido para medir temperatura e umidade do ar. É um sensor digital popular, preciso e de fácil integração, diretamente relevante para as variáveis do nosso modelo de ML. 
  * **Sensor Capacitivo de Umidade do Solo:** Preferido em relação ao resistivo por sua maior durabilidade e resistência à corrosão, fornecendo leituras mais estáveis ao longo do tempo, o que é crucial para aplicações agrícolas.
* **Protocolo de Comunicação:**  
  * **MQTT (Message Queuing Telemetry Transport):** Selecionado por ser um protocolo de publicação/assinatura extremamente leve e eficiente, projetado para dispositivos com recursos limitados e redes instáveis, o que o torna o padrão da indústria para aplicações IoT e é totalmente suportado pelo Azure IoT Hub.
* **Plataforma de Backend:**  
  * **Azure IoT Hub:** Um serviço gerenciado na nuvem da Microsoft que atua como um hub de mensagens central para comunicação bidirecional entre aplicações IoT e os dispositivos que gerencia. Foi escolhido por sua alta escalabilidade, segurança robusta (autenticação por dispositivo e tokens SAS) e integração nativa com o ecossistema Azure, permitindo que os dados dos sensores sejam facilmente processados por outros serviços como Azure Stream Analytics, Azure Functions ou armazenados para análises futuras.

#### 3.2. Simulação do Circuito no Wokwi - Projeto FarmTechIOT

Para facilitar o desenvolvimento e a validação do projeto sem a necessidade de hardware físico imediato, no primeiro momento foi criada uma simulação completa no Wokwi. O Wokwi é um simulador online que permite projetar circuitos e executar código para microcontroladores como o ESP32.

#### Funcionalidades Principais

-   **Monitoramento em Tempo Real:** Leitura contínua dos dados de temperatura e umidade do ambiente.
-   **Display Local:** Exibição das informações em um display LCD 20x4, incluindo leituras dos sensores, status da bomba e hora atual.
-   **Irrigação Automatizada:** Acionamento automático de uma bomba d'água (através de um relé) quando a umidade do ar cai abaixo de um limiar pré-definido.
-   **Conectividade Wi-Fi:** Conecta-se a uma rede Wi-Fi para acesso a serviços de rede.
-   **Sincronização de Horário:** Obtém a data e hora atuais de um servidor NTP (Network Time Protocol).
-   **Publicação de Dados (Opcional):** Envia os dados dos sensores em formato JSON para um broker MQTT, permitindo monitoramento remoto, armazenamento de histórico e integração com outras plataformas de IoT.

#### 3.3. Protótipo do Circuito Real - Projeto AgTech

#### Funcionalidades Principais

-   **Monitoramento em Tempo Real:** Leitura contínua dos dados de temperatura e umidade do ambiente.
-   **Display Local:** Exibição das informações em um display LCD 20x4, incluindo leituras dos sensores, status da bomba e hora atual.
-   **Conectividade Wi-Fi:** Conecta-se a uma rede Wi-Fi para acesso a serviços de rede.
-   **Sincronização de Horário:** Obtém a data e hora atuais de um servidor NTP (Network Time Protocol).
-   **Publicação de Dados:** Envia os dados dos sensores em formato JSON para um broker MQTT, permitindo monitoramento remoto, armazenamento de histórico e integração com outras plataformas de IoT.

### 3.4. Camada de Dispositivos IoT

#### ESP8266 NodeMCU - Especificações
- **Microcontrolador**: ESP8266-12E com WiFi integrado
- **Display**: OLED SSD1306 128x64 para status local
- **Conectividade**: WiFi 2.4GHz com TLS 1.2
- **Frequência de Telemetria**: 2 segundos (configurável)
- **Seleção de Sensores:**  
  * **DHT22:** Para medir a umidade do ar.  
  * **BH1750:** Um sensor de luz ambiente digital que se comunica via I2C, fornecendo medições precisas em lux. É ideal para monitorar as condições de iluminação que afetam a fotossíntese e a saúde da planta.

### 3.5. Demonstração**

O vídeo a seguir, postado no YouTube como "não listado", demonstra o funcionamento completo do sistema, mostrando o primeiro prototipo e a visualização dos dados chegando em tempo real no Azure IoT Hub, monitorado através da ferramenta Azure IoT Explorer.

* **Link do Vídeo:** 
➡ [Link para o vídeo no YouTube](https://youtube.com/shorts/SjePsIXvCro?si=avZwUKmB7DZ-m2kS) (modo não listado)