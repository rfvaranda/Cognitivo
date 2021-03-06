# Cognitivo

# Requisitos

1. Conversão do formato dos arquivos: Converter o arquivo CSV presente no diretório data/input/users/load.csv, 
para um formato colunar de alta performance de leitura de sua escolha. Justificar brevemente a escolha do formato;

    CSV to Parquet  -  Justificativas:

    1 – Como somente as colunas necessárias são escaneadas as consultas tendem a ser muito mais rápidas.

    2 – É possível otimizar o fluxo de dados entre o processador e a memória.

    3 – Os dados são mais facilmente comprimidos, pois os dados em forma de colunas são mais semelhantes entre si do que em linhas.

    4 – Os dados em ‘Parquet’ já vem mapeados.

2. Deduplicação dos dados convertidos: No conjunto de dados convertidos haverão múltiplas entradas para um mesmo registro, 
variando apenas os valores de alguns dos campos entre elas. Será necessário realizar um processo de deduplicação destes dados, 
a fim de apenas manter a última entrada de cada registro, usando como referência o id para identificação dos registros duplicados e a 
data de atualização (update_date) para definição do registro mais recente;

    Foi utilizado agregação no dataframe para identificar a maior data para cada id e depois feito join com o dataframe original.
    
3. Conversão do tipo dos dados deduplicados: No diretório config haverá um arquivo JSON de configuração (types_mapping.json),
 contendo os nomes dos campos e os respectivos tipos desejados de output. Utilizando esse arquivo como input, realizar um processo
 de conversão dos tipos dos campos descritos, no conjunto de dados deduplicados;
 
    Foi utilizado a opção inferSchema=True no momento da leitura do CSV original.
    
4. Todas as operações devem ser realizadas utilizando Spark. O serviço de execução fica a seu critério, 
podendo utilizar tanto serviços locais como serviços em cloud. Justificar brevemente o serviço escolhido (EMR, Glue, Zeppelin, etc.)

    Foi utilizado um cluster Hadoop, pela facilidade de utilização do pyspark para leitura e conversão dos arquivos.
    

