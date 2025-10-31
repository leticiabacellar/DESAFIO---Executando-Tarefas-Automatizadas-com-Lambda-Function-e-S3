# ⚙️ **Desafio: Tarefas Automatizadas com AWS Lambda e S3**

---

## 📚 **Descrição**

Este repositório foi criado como parte do **Bootcamp Santander AWS Cloud da DIO**, com o objetivo de consolidar meus conhecimentos sobre **execução de tarefas automatizadas utilizando AWS Lambda e Amazon S3**.  
Durante este desafio, pratiquei conceitos de **arquitetura serverless**, **eventos automatizados** e **integração entre serviços AWS**.

---

## 🎯 **Objetivos de Aprendizagem**

Ao concluir este desafio, fui capaz de:

- ⚡ Aplicar os conceitos de **funções Lambda** em um ambiente prático;  
- ☁️ Compreender como integrar **Lambda e S3** para execução automática de tarefas;  
- 🧾 Documentar processos técnicos de forma clara e organizada;  
- 🧠 Utilizar o **GitHub** como ferramenta de versionamento e compartilhamento técnico.  

---

## 🧩 **Passo a Passo Realizado**

### **1️⃣ Acesso ao Console da AWS**
Acessei o **AWS Management Console** e utilizei os serviços:
- **Amazon S3**, para armazenar e gerenciar arquivos;
- **AWS Lambda**, para criar e executar funções sem servidor (serverless).

---

### **2️⃣ Criação do Bucket no Amazon S3**
Criei um **bucket** para hospedar e armazenar arquivos que seriam processados automaticamente pela Lambda.

Configurações utilizadas:
- Nome do bucket: `lambda-automation-larissa`
- Região: `us-east-1` (padrão)
- Acesso público: **desabilitado** por segurança
- Versionamento: **habilitado** (para manter histórico dos arquivos)

Após a criação, o bucket ficou pronto para receber uploads.

---

### **3️⃣ Criação da Função Lambda**
Acessei o serviço **AWS Lambda** e criei uma nova função:

| Configuração | Valor |
|--------------|--------|
| **Nome da função:** | `lambda-s3-trigger` |
| **Runtime:** | Python 3.9 |
| **Permissões:** | Permitir que a Lambda acesse o S3 (função IAM automática) |

---

### **4️⃣ Adicionando o Código da Função**

No editor de código da Lambda, inseri o seguinte script:

```python
import json

def lambda_handler(event, context):
    print("Evento recebido do S3:")
    print(json.dumps(event))
    return {
        'statusCode': 200,
        'body': json.dumps('Execução bem-sucedida! Arquivo processado com sucesso.')
    }
```

Esse código é responsável por:

- Ler o evento gerado pelo S3 (como upload de arquivo);
- Exibir as informações do arquivo recebido;
- Retornar uma mensagem confirmando a execução.

Cliquei em Deploy para aplicar as alterações.


### 5️⃣ Criando o Trigger (Gatilho)

Configurei a função Lambda para ser disparada automaticamente quando um novo arquivo for enviado ao S3.

- No painel da Lambda, adicionei um gatilho (trigger):

- Serviço: S3

- Bucket: lambda-automation-larissa

- Evento: All object create events (todos os uploads)

Salvei a configuração e testei o fluxo.


### 6️⃣ Testando a Automação

Fiz upload de um arquivo de teste (teste.txt) no bucket S3.

Resultado:

- O evento acionou automaticamente a função Lambda.
- No console de logs do CloudWatch, foi possível ver a execução bem-sucedida com os detalhes do arquivo enviado.

✅ Mensagem retornada:
Execução bem-sucedida! Arquivo processado com sucesso.


### 💭 Insights Aprendidos

✨ A arquitetura Serverless simplifica o desenvolvimento, removendo a necessidade de gerenciar servidores.
🔁 A integração S3 + Lambda é poderosa para automatizar tarefas como processamento de imagens, logs ou backups.
🧩 O uso de gatilhos (triggers) permite que as funções executem apenas quando necessário, reduzindo custos.
🔐 O IAM é essencial para controlar permissões e garantir segurança entre serviços.
📊 O CloudWatch é uma ferramenta indispensável para monitorar execuções e depurar funções Lambda.

### 🧰 Ferramentas e Tecnologias Utilizadas

- ☁️ Amazon Web Services (AWS)
- 🧠 AWS Lambda
- 🗂️ Amazon S3
- 🔐 IAM (Identity and Access Management)
- 📈 Amazon CloudWatch
- 💻 Python 3.9
- 🧾 Git e GitHub


### 🔗 Referências

- 📘 Documentação AWS Lambda
- 🗂️ Documentação Amazon S3
- 💡 Bootcamp Santander AWS Cloud - DIO

### 🏁 Conclusão

Esse desafio foi fundamental para entender na prática como a AWS permite automatizar tarefas com Lambda e S3, explorando o conceito de Serverless.
A experiência reforçou meu aprendizado sobre integração entre serviços AWS, segurança, e automação inteligente.
Agora, tenho uma visão mais clara de como usar esses recursos para criar soluções escaláveis e eficientes na nuvem. ☁️💻

👩‍💻 Autora: Larissa Bacellar Marçal
📅 Bootcamp Santander AWS Cloud – DIO
🚀 “Aprendizado constante é o combustível da evolução.”
