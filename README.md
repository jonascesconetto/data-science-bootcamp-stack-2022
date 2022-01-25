# Bootcamp de Data Science da STACK - 2022
## Human Resource Analytics
Diante do problema apresentado foi solicitado uma analise de dados que responda as seguintes questões:
- Quais os fatores influenciam para um colaborador deixar a empresa?
    - Pessoas satisfeitas?
    - Ambiente de trabalho?
        - Cargo, departamento
    - Salário?
    - Tempo na empresa?
- Podemos nos antecipar e saber se um determinado colaborador vai sair da empresa?
    - Desempenho do colaborador
    - Carga de trabalho
- Como diminuir o turnover?
- Como reter pessoas?
## 💻 Principais Tecnologias, Softwares e Bibliotecas
- Docker
- Apache AirFlow (Data Pipeline)
- MINIO (Data Lake)
- MySQL
- Python
- PYCARET
- Streamlit
- Pandas
- Scikit Learn
## ⚙ Configuração dos serviços
### MySQL
1. Crie um container para o `banco de dados` usando docker
    ```PowerShell
    docker run --name mysqlbd1 -e MYSQL_ROOT_PASSWORD=bootcamp -p "3307:3306" -d mysql
    ```
### MINIO
1. Crie um container para o `data lake` usando docker
    ```PowerShell
    docker run --name minio -d -p 9000:9000 -p 9001:9001 -v "$PWD/datalake:/data" minio/minio server /data --console-address ":9001” 
    ```
2. Abra o browser e digite: 
    **http://localhost:9001/login**
3. Faça o login com as seguintes credenciais:
    username: `minioadmin`
    password: `minioadmin`
### Apache AirFlow
1. Crie um container para o `Apache AirFlow` usando docker
    ```PowerShell
    docker run -d -p 8080:8080 -v "$PWD/airflow/dags:/opt/airflow/dags/" --entrypoint=/bin/bash --name airflow apache/airflow:2.1.1-python3.8 -c '(airflow db init && airflow users create --username admin --password stack --firstname Felipe --lastname Lastname --role Admin --email admin@example.org); airflow webserver & airflow scheduler'
    ```
2. Instale as bibliotecas necessárias para o ambiente:
    - Execute o comando abaixo para se conectar ao container do airflow:
    ```
    docker container exec -it ctn-airflow bash
    ```
    - Em seguida instale as bibliotecas:
    ```
    pip install pymysql xlrd openpyxl minio
    ```
3. Se não der nenhum erro, acesse a interface web do Apache Airflow com o endereço: 
    **https://localhost:8080**
4. Faça o login de acesso ao Apache Airflow
