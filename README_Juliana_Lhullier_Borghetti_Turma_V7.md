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
- Organizei os dados dentro da tabela, conforme orientação do professor;
- Fiz este README;
- Fiz um reposítório do GitHub e comecei a dar commits;
- Visualizei as informações do DataFrame, visualizei que havia 4 colunas com todos os valores nulos e nenhum mais;
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

- 830.000 linhas sem dados ausentes... 184.330 linhas duplicadas quando verifiquei o duplicated no DataFrame completo;
- Havia 811.529 duplicados na coluna "ID_compra";

- Resolvi verificar então registros duplicados nas colunas "data", "ID_compra", "ID_cliente" e "nome_produto", pois parecia ser a mesma compra, pelo mesmo cliente, mas poderiam ser diferentes produtos. 
- Havia ainda 176.327 linhas duplicadas no DataFrame. 

- Resolvi verificar registros duplicados nas colunas "data", "ID_compra", "ID_cliente" sem "nome_produto"
- Havia novamente 811.529;

- Resolvi verificar então registros duplicados verificando cada uma delas, todas as colunas;
- Havia 96.553 duplicatas;

- Fiz uma investigação comparando o total de linhas únicas e linhas duplicadas. Depois separei as linhas duplicadas para análise. Não consegui resolver, empaquei.
- Linhas duplicadas:  184.330
- Linhas únicas:  733.447

- Com a ajuda do professor e colegas, entre as opções drop_duplicates() e nunique(), optei por fazer os dois para conferir. O drop_duplicates foi a solução.

- Apesar de não haver valores vazios de acordo com as informações já obtidas com info(), conferi com isna() a coluna "categoria_produto", visto que era pedido na documentação do mini-projeto "usar a lógica (if/else) para preencher as categorias vazias com "Sem Categoria"";
- Verifiquei (com a ajuda do professor) que havia os valores "#N/D" nas colunas "categoria_produto" e "nome_produto". Usei a lógica (if/else) para preencher as categorias com "#N/D" substituindo por "Sem Categoria";
  
- Com o DataFrame limpo, verifiquei novamente os tipos de dados;

- Verifiquei os tipos de dados e verifiquei inconsistêcias nas colunas str (string) usando .unique() para conferir se havia caracteres especiais, letras minúsculas, variações que pediriam tratamento. Não havia.

 # Módulo Datetime

 - Importei a classe date do módulo datetime;
- Conferi o formato e tipo de dados da coluna "data";
 -  Converti o texto para datetime (validei a regra do identificador de número de compra, convertendo a string de data da compra utilizando o módulo datetime)
- Conferi a conversão;
- Conferi se há algum valor nulo após a conversão;
-  Conferi algumas linhas para garantir;
- Conferi as informações para ter certeza.

 # Estatísticas

- Como percebi anteriormente, o número de filhos por cliente se repetia. Assim, as estatísticas provenientes exclusivamente da coluna "numero_filhos" não seriam confiáveis;
- Por essa razão, comparei a quantidade de clientes únicos com a quantidade de linhas na coluna do número de filhos ("ID_cliente" e "numero_filhos");
- Havia apenas 1.000 clientes únicos para 733.447 registros do número de filhos;
- Agrupei um único valor de número de filhos por cliente usando o groupby() para cruzar os dados das duas colunas ("ID_cliente" e "numero_filhos") e o .first() para selecionar o primeiro valor não-nulo de filhos para cada cliente;
-  Contei quantos clientes tinham cada número de filhos (0, 1, 2, 3, 4) usando value_counts() e pedi para ordenar em ordem crescente com .sort_index();
- Assim, verifiquei que: 527 cliente não tinham filhos, 125 clientes tinham 1 filho, 130 clientes tinham 2 filhos, 121 clientes tinham 3 filhos e 97 clientes tinham 4 filhos;
- Utilizei "estatísticas descritivas básicas para a coluna de número de filhos do cliente (média; mediana; desvio padrão; máximo; mínimo; e contagem, quartis)" propostas para o mini-projeto;
- Como describe não traz a moda, fiz separadamente usando .mode();
- Para melhor visualização, fiz a mesma operação com print(), levando em conta as seguintes estatísticas:
* Contagem (count) = Das 733.447, foram considerados 1.000 clientes únicos;
* Mínimo (min) = O valor mínimo de filhos encontrado foi zero (sem filhos);
* Máximo (max) = O número máximo de filhos foi 4;
* Média (mean) = A soma do número total de filhos dividido pelo número de registros válidos resultou na média de 1.14 filhos por cliente;  
* Desvio padrão (std) = O desvio padrão do número de filhos foi de cerca de 1.41, indicando uma dispersão dos valores em relação á média;
* Quartis (Q1, Q2, Q3, Q4) = Até 50% dos cliente não tem filhos, 75% tem até 2 filhos e o restante dos cliente têm 3 a 4 filhos.

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


 George:

 Tratamento de Nulos em Dimensões Físicas: Para a coluna de nome do produto (PR_NOME), a decisão foi remover as linhas com valores nulos. A justificativa é que um registro de compra sem a descrição do produto perde seu valor analítico granular. Como a categoria do produto já foi preservada na etapa anterior, a remoção não compromete a análise macro.

Identificação de pedidos: A base possui várias linhas com o mesmo CO_ID porque um pedido pode incluir vários produtos. Remover essas linhas descartaria itens legítimos; por isso, o script preserva as linhas e usa nunique() para contar cada pedido apenas uma vez nos agrupamentos. Após a limpeza, a base contém 826.350 linhas de produtos e 18.469 pedidos distintos.

Conversão de Tipos (Datas): A coluna DATA foi convertida de texto para o tipo datetime utilizando a função pd.to_datetime. Datas inválidas (como 30/02) foram convertidas para nulas e posteriormente removidas, assegurando a consistência para futuras análises temporais.

Exportação dos Dados: Ao final do processo de limpeza, a base tratada foi exportada no formato df_limpo.csv, conforme exigido nas etapas do projeto.
3. Principais Insights Obtidos
A partir das estatísticas descritivas e dos agrupamentos realizados, destacam-se os seguintes pontos:

Qualidade dos Dados: O script remove as colunas extras e as linhas sem nome de produto, padroniza categorias e descarta datas inválidas. As várias linhas de um mesmo CO_ID são preservadas para não apagar produtos do pedido.
Liderança por Gênero: O gênero F aparece em 9.614 pedidos distintos, contra 8.855 do gênero M.
Categorias com mais pedidos: Alimentos está presente em 18.267 pedidos distintos, seguido por Higiene (17.610) e Limpeza (17.475). Essa contagem indica presença em pedidos, não faturamento ou unidades vendidas.
Perfil Familiar (Número de Filhos): Na coluna CL_FHL, calculada uma vez por cliente, a média é 1,14 e a mediana é 0 filho(s). A mediana igual a zero indica que pelo menos metade dos clientes válidos tem valor zero.
Oportunidade de Negócio: Alimentos é uma categoria a investigar em análises futuras. A contagem de pedidos, isoladamente, não permite estimar faturamento nem retorno de campanhas