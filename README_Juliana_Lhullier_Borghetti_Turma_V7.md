# Mini-Projeto de Análise de Dados - Varejo

# Sobre o projeto:
Primeiro projeto desenvolvido durante o curso Manipulação de Dados com Python e SQL no Senai/SC.

# Objetivo:
Explorar uma base de dados de varejo e praticar conceitos de análise de dados utilizando Python.

# Arquivos:
- Base Varejo.csv: base de dados utilizada no projeto, disponível em <https://www.kaggle.com/datasets/namespaiva/base-varejo/data?select=Base+Varejo.csv>;

- Mini_Projeto_Juliana_Lhullier_Borghetti_v7.ipynb: notebook com o código e análises;

- README_Juliana_Lhullier_Borghetti_v7.md: o presente arquivo, contendo explicações sobre o projetos, reflexões teóricas e insights obtidos a partir da análise dos dados.

# Ferramentas:

- Python
-Jupyter Notebook
- Visual Studio Code
- GitHub
_ GitHub Desktop
- Bibliotecas (Pandas, !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

#Autora: Juliana Lhullier Borghetti

# Primeiros passos:

- Importei o kagglehub;
- Importei as bibliotecas que conheço e creio que posso precisar (pandas, os, numpy, seaborn e matplotlib)
- Fiz a leitura do arquivo csv com pandas;
- Fiz o download do csv Kaggle e salvei no meu computador;
- Organizei os dados dentro da tabela;
- Fiz este README;
- Fiz um reposítório do GitHub e comecei a dar commits;
- Visualizei as informações do DataFrame;
- Verifiquei as 5 primeiras linhas do DataFrame;
- Verifiquei as últimas 5 linhas do DataFrame;
- Verifiquei 5 linhas aleatórias dentro do DataFrame;
- Verifiquei o tamanho do DataFrame;
- Verifiquei os nomes das colunas;
- Verifiqueia coluna "filhos";

- Verifiquei no material de apoio o que significava cada coluna:

1. DATA: Data da compra;
2. CO_ID: Identificação do número de compra (número da nota fiscal);
3. CL_ID: Identificação do cliente (número do cliente);
4. CL_GENERO: Sexo biológico informado pelo cliente;
5. CL_EC: Estado civil do cliente:
1: Casado ou união estável;
2: Divorciado;
3: Separado;
4. Solteiro;
5: Viúvo.
6. CL_FHL: Número de filhos do cliente;
7. CL_SEG: Segmentação econômica do cliente (classe A, B ou C);
8. PR_ID: Código do produto (SKU) adquirido;
9. PR_CAT: Categoria do produto adquirido;
10. PR_NOME: Nome do produto adquirido.

# Limpeza de dados:

- Antes de tudo, resolvi criar uma cópia do csv (df_varejo_limpo);

- Para melhor compreensão, renommei e verifiquei as colunas:
    "DATA": "data",
    "CO_ID": "ID_compra",
    "CL_ID": "ID_cliente",
    "CL_GENERO": "genero_cliente",
    "CL_EC": "estado_civil",
    "CL_FHL": "numero_filhos",
    "CL_SEG": "classe_economica",
    "PR_ID": "codigo_produto",
    "PR_CAT": "categoria_produto",
    "PR_NOME": "nome_produto"

- Como apareceram várias colunas "Unnamed", resolvi verificar se essas colunas estavam vazias. Resolvi verificar todos os valores ausentes no DataFrame;
- Aparentemente as colunas "Unnamed" estavam vazias (usando isna()), mas resolvi investigar mais a fundo;
- Verifiquei todas (all) as colunas vazias (isna) e criei uma variável (colunas_vazia) para armazenar esses resultados;
- Imprimi a contagem (len), o nome das colunas vazias e pedi uma lista;
- Optei por remover as colunas totalmente vazias com dropna(), pois considerei que não tinham utilidade para análise e podiam inclusive me confundir;
- Verifiquei novamente os valores ausentes em todas as colunas do DataFrame, não havia;
- Verifiquei duplicatas no DataFrame completo, depois por coluna "ID_compra" e então por linhas completas para garantir que não havia registros duplicados;
- Aparentemente, havia muitas linhas duplicadas no DataFrame. Fiz uma investigação comparando o total de linhas únicas e linhas duplicadas. Depois separei as linhas duplicadas para análise;

-Usei a lógica (if/else) para preencher categorias vazias com "Sem Categoria"

- Com os dados melhor organizados, verifiquei os tipos de dados contidos no DataFrame;
- Conferi se ainda havia ausentes e duplicatas;

- Ajustei os tipos de dados e verifiquei inconsistêcias
- Validei a regra do identificador de número de compra, convertendo a string de data da compra utilizando o módulo datetime.

 # Estatísticas
 # Padrões de agrupamento
 # Insights:
 1.
 2.
 3.
 4.
 5.
 6.
 Produzir um pequeno bloco de conclusões (3–6 tópicos) com os principais insights obtidos e possíveis problemas remanescentes na base
 # Conclusões 