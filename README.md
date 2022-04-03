# DIO - AWS EMR - BigData Python

Repositório de cógido do Dio Live Coding com **AWS EMR** e Python.

Neste repositório constam arquivos de configuração e execução de Análise de Dados.

[Cassiano Peres](https://github.com/cassianobrexbit/)  
Instrutor, Digital Innovation One

## Instruções para AWS

### Acessar S3

* Go to https://s3.console.aws.amazon.com/s3/
* Criar estrutura de Data Lake : _dio-live-datalake_
* Criar estrutura de pastas:
   * _data_
   * _output_
   * _temp_

### Acessar EMR

* Go to https://console.aws.amazon.com/elasticmapreduce/
* O cluster será criado pelo MrJob e não pelo console 
* Infraestrutura como código

Configurar o MrJob acessando o arquivo _`nano ~/.mrjob.conf`_

### Criar chave SSH

* Acessar Console do EC2: https://console.aws.amazon.com/ec2/ -> Key Pairs -> Create Key Pair	
* Download .pem file

### Obter Id e chave secreta AWS para configurar MrJob
* Profile
* My Security Credentials: https://console.aws.amazon.com/iam/home?region={region}#/security_credentials
* Access Keys - Create new access key
* Fazer download - única chance de visualizar

### Acessar S3

Upload de livro _**SherlockHolmes.txt**_ para o bucket
____

## Ambiente linux

Algumas etapas para realizar em sua máquina de trabalho:

**Criar ambiente virtual python:**  
_`virtualenv --python=python3.6 venv_diolive`_

Instalar **[VSCode Editor](https://code.visualstudio.com/)**, acessar pelo terminal com o comando `code .`

### Ambiente virtual python

Habilitar o ambiente virtual python com o comando:  
_`source venv_diolive/bin/activate`_

**Criar algoritmo de análise de palavras:**

* Arquivo _`wordcount-test.py`_
* map-reduce-count : contar
* Instalar boto3: _`pip install boto3`_
* Instalar mrjob: _`pip install mrjob`_

### Processando a contagem de palavras do livro

Finalizar executando o contador de palavras via terminal:  
```bash
python3 wordcount-test.py -r \
emr s3://{s3_bucket_name}/data/SherlockHolmes.txt \
--output-dir=s3://{s3_bucket_name}/output/logs1 \
--cloud-tmp-dir=s3://{s3_bucket_name}/temp/
```
