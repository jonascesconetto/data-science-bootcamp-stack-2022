# Bootcamp de Data Science da STACK - 2022

## 🚀 Sobre
[...]

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
### Estrutura de diretório local
- Crie um diretório na sua máquina para ser o ponto central onde vamos armazenar a estrutura de arquivos, diretórios e execução de scripts.
    - **Windows**   
        *C:\bootcampds*  
    - **Linux ou Mac**
        */home/<seunome>/bootcampds*
### MySQL
- Crie um container para o `banco de dados` usando docker
   ```PowerShell
   docker run --name mysqlbd1 -e MYSQL_ROOT_PASSWORD=bootcamp -p "3307:3306" -d mysql
   ```
### MINIO
- Crie um container para o `data lake` usando docker
    `docker run --name minio -d -p 9000:9000 -p 9001:9001 -v "$PWD/datalake:/data" minio/minio server /data --console-address ":9001” `
### **Apache AirFlow**
- Crie um container para o `Apache AirFlow` usando docker
    `docker run -d -p 8080:8080 -v "$PWD/airflow/dags:/opt/airflow/dags/" --entrypoint=/bin/bash --name airflow apache/airflow:2.1.1-python3.8 -c '(airflow db init && airflow users create --username admin --password stack --firstname Felipe --lastname Lastname --role Admin --email admin@example.org); airflow webserver & airflow scheduler'`

