# nlpB
Projeto pessoal com o objetivo de aplicar técnicas de Processamento de Linguagem Natural (PLN) para analisar o texto da Bíblia em português. Utilizei diferentes abordagens para identificar padrões e explorar as relações semânticas presentes nesse texto.

# Passos do Projeto

# 1. Preparação do Ambiente e Carregamento dos Dados
Técnicas Utilizadas:
Linguagem de Programação: Python Bibliotecas: pandas, nltk, spacy, gensim, scikit-learn, matplotlib, seaborn, networkx, entre outras 

Motivação: Configurar um ambiente adequado para manipular e analisar dados textuais. Carregar o texto da Bíblia em um formato estruturado para facilitar o processamento. 

Implementação:Montei o Google Drive para acessar os arquivos. Instalei as bibliotecas necessárias. Carreguei o texto da Bíblia em formato JSON e o organizei em um DataFrame do pandas, contendo colunas como book_name, chapter, verse e text.

# 2. Pré-processamento do Texto
Técnicas Utilizadas:
Lematização: Utilizei o spaCy para reduzir palavras às suas formas básicas. Remoção de Stop Words e Pontuação: Com o NLTK e spaCy. Normalização do Texto: Convertemos todo o texto para letras minúsculas.

Motivação: Padronizar o texto para facilitar as análises posteriores. Reduzir a dimensionalidade dos dados, removendo palavras comuns que não agregam muito significado. Implementação:
Defini uma função preprocess_text para aplicar as etapas de pré-processamento. Criei uma nova coluna clean_text no DataFrame com o texto pré-processado.

# 3. Análise Exploratória de Dados
## 3.1 Contagem das Palavras Mais Frequentes
Técnicas Utilizadas:
Contagem de Frequências: Usei a classe Counter do módulo collections. 

Motivação: Identificar as palavras mais frequentes para entender os temas centrais do texto. Detectar possíveis ruídos ou necessidades adicionais de limpeza. Implementação:
Criei uma função get_word_frequencies para calcular a frequência das palavras. Calculei e exibi as palavras mais frequentes por livro e no total.

## 3.2 Visualização das Palavras Mais Frequentes
Técnicas Utilizadas:
Gráficos de Barras: Utilizei o matplotlib e seaborn. 

Motivação: Visualizar de forma intuitiva a distribuição das palavras. Facilitar a comparação entre diferentes livros ou seções. Implementação:
Plotei gráficos das palavras mais frequentes no total e por livro. Salvei os gráficos para análise posterior.

# 4. Modelagem de Tópicos
Técnicas Utilizadas:
Latent Dirichlet Allocation (LDA): Com a biblioteca gensim.

Motivação: Identificar tópicos subjacentes presentes no texto. Agrupar documentos (capítulos ou versículos) com base em similaridades temáticas. 

Implementação: Preparei os textos como listas de tokens. Criei um dicionário e um corpus para o LDA. Treinei o modelo LDA definindo o número de tópicos. Atribuí tópicos dominantes aos documentos.

# 5. Geração de Resumos
Técnicas Utilizadas:
Sumarização Automática: Usei o LexRankSummarizer da biblioteca sumy.

Motivação: Criar resumos concisos dos livros para captar os principais pontos. Auxiliar na compreensão geral do conteúdo sem a necessidade de ler todo o texto. 

Implementação: Concatenei o texto de cada livro. Utilizei o LexRankSummarizer para gerar resumos com um número definido de sentenças.

# 6. Treinamento de Embeddings de Palavras
Técnicas Utilizadas:
Word2Vec: Com a biblioteca gensim.
Motivação: Capturar relações semânticas entre palavras. Representar palavras em um espaço vetorial para análises posteriores. Implementação:
Preparei sentenças tokenizadas para o treinamento. Treinei o modelo Word2Vec com parâmetros definidos. Obtive os vetores de palavras e o vocabulário.

# 7. Visualização dos Embeddings
Técnicas Utilizadas:
Redução de Dimensionalidade: Usei t-SNE ou UMAP. Visualização Gráfica: Com matplotlib e seaborn.
Motivação: Visualizar a distribuição das palavras em um espaço bidimensional. Identificar agrupamentos semânticos e relações entre palavras. Implementação:
Reduzi os embeddings para 2 dimensões. Plotei um gráfico de dispersão das palavras, ajustando parâmetros para melhorar a legibilidade. Limitei o número de palavras plotadas para evitar poluição visual.

# 8. Análise de Similaridade Semântica
Técnicas Utilizadas:
Embeddings de Sentenças: Com SentenceTransformers e modelos pré-treinados como paraphrase-multilingual-MiniLM-L12-v2. Cálculo de Similaridade Coseno: Para medir a semelhança entre vetores.
Motivação: Encontrar versículos semelhantes em conteúdo e significado. Explorar conexões semânticas entre diferentes partes do texto. Implementação:
Gerei embeddings para cada versículo. Defini funções para encontrar versículos semelhantes por índice ou texto arbitrário. Utilizeia similaridade coseno para identificar os versículos mais próximos.

# 9. Classificação de Textos
Técnicas Utilizadas:
Representação TF-IDF: Para converter texto em vetores numéricos. Algoritmos de Classificação: Como Naive Bayes, SVM e Random Forest. Validação Cruzada e Métricas de Avaliação: Para avaliar o desempenho dos modelos. 
Motivação: Classificar versículos ou capítulos em categorias pré-definidas (Lei, História, Poesia, Profecia, Evangelhos, Cartas). Auxiliar em estudos temáticos e organização do texto. Implementação:
Defini as categorias e mapeei os livros a elas. Preparei os dados, transformando o texto em vetores TF-IDF. Dividi os dados em conjuntos de treinamento e teste. Treinei diferentes modelos e avaliei seu desempenho.

# 10. Análise de Rede de Coocorrência
Técnicas Utilizadas:
Reconhecimento de Entidades Nomeadas (NER): Com o spaCy para extrair entidades como pessoas, lugares e organizações. Construção de Grafos: Usando NetworkX para representar coocorrências. Visualização de Redes: Com matplotlib e PyVis.
Motivação: Analisar como entidades coocorrem no texto para entender relações e interações. Identificar entidades centrais e comunidades dentro da rede. Implementação:
Extraí entidades de cada versículo. Construí uma rede onde nós representam entidades e arestas representam coocorrências. Visualizei a rede e apliquei filtros para destacar entidades importantes.

# 11. Extração de Relações
Técnicas Utilizadas:
Padrões Sintáticos: Para identificar relações sujeito-verbo-objeto. Análise Sintática: Com o spaCy para extrair dependências gramaticais. Construção de DataFrames: Para estruturar as relações extraídas.
Motivação: Extrair relações específicas entre entidades, como interações e eventos. Criar uma base de dados estruturada das relações presentes no texto. Implementação:
Defini uma função para extrair relações com base em padrões sintáticos. Apliquei a função ao texto e coletei as relações. Construí um grafo de relações e o visualizei.

# 12. Análise e Visualização de Resultados
Técnicas Utilizadas:
Métricas de Centralidade: Como centralidade de grau para identificar entidades importantes. Detecção de Comunidades: Usando o algoritmo de Louvain para detectar comunidades na rede. Visualização Avançada: Com cores e tamanhos para destacar informações relevantes. Motivação: Identificar padrões e insights a partir das análises realizadas. Facilitar a interpretação dos dados através de visualizações claras e informativas. Implementação:
Calculei métricas de centralidade para identificar entidades centrais. Detectei comunidades na rede de coocorrência. Visualizei as redes com destaque para comunidades e relações importantes.

# Conclusão 
Neste projeto, consegui aplicar técnicas de Processamento de Linguagem Natural para analisar a Bíblia em português. Explorei aspectos como frequências de palavras, tópicos temáticos, similaridades semânticas, relações entre entidades e estruturas de rede.

