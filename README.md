# 🌐 Publicação de Site Estático com AWS S3 — Run as Cloud

Este repositório contém os arquivos e instruções utilizadas no laboratório **Run as Cloud**, cujo objetivo é **publicar um site estático na AWS utilizando o Amazon S3 (Simple Storage Service)**.

## 🚀 Objetivo

Aprender a configurar e hospedar um site estático (HTML, CSS, JS) em um bucket S3 da AWS, tornando-o acessível publicamente via navegador. Também são abordadas configurações importantes de permissões e políticas para corrigir erros como o **403 Forbidden**.
## 📘 O que você vai aprender

- O que é o Amazon S3
- Diferença entre sites estáticos e dinâmicos
- Como criar um bucket S3 e configurar a hospedagem estática
- Como lidar com erro 403 (Access Denied)
- Como aplicar uma política pública de leitura no bucket

## ☁️ O que é o Amazon S3?

O **Amazon S3 (Simple Storage Service)** é um serviço da AWS que permite armazenar arquivos na nuvem de forma segura, escalável e acessível. Ideal para guardar imagens, vídeos, documentos e também hospedar sites estáticos.

---

## 🧱 O que é um site estático?

Um **site estático** é composto apenas por arquivos HTML, CSS e JavaScript. Ele não depende de servidores ou bancos de dados para gerar conteúdo dinâmico, tornando-se leve e rápido.

### Exemplos:
- Portfólios
- Currículos online
- Páginas de eventos
- Sites institucionais simples

---

## 🧰 Tecnologias Utilizadas

- **Amazon S3 (AWS)**
- **HTML5**
- **CSS3**
- **Console AWS**

## 📁 Conteúdo do Repositório

- `index.html` – Página principal do site
- `img/` – Pasta com imagens utilizadas no site

📥 [Clique aqui para baixar os arquivos do site (index.html + img/)](https://drive.google.com/file/d/1FV32ta8Vp8Xf71o31W_-jqaDNeMbLr1B/view?usp=sharing)

## 🧪 Etapas Realizadas no Laboratório

1️⃣. **Criação do Bucket S3**
   - Acesse o [Console da AWS](https://aws.amazon.com/console/)
   - Vá em **S3 > Criar bucket**
   - Nome Bucket: `meusite-runascloud` << esse deve ser um nome único utilizado mude para o nome do seu Bucket <<
   - Desmarque **"Bloquear acesso público"** (temporariamente)
   - Avance com padrão e crie

  ![image (20)](https://github.com/user-attachments/assets/4ba8ec03-76af-47b5-b794-3f0b94ea22e2)

  ![image (21)](https://github.com/user-attachments/assets/738c05e1-3cb2-4f1c-b5c2-0e6b10741d7c) 

  ![image (22)](https://github.com/user-attachments/assets/17eb049f-ac5b-4d92-90ee-ec64cb17ce12)

  ![image (23)](https://github.com/user-attachments/assets/1ef7730a-c928-4482-8e75-5fd554515d08)

### 2️⃣. Fazer upload dos arquivos
- Faça upload de:
  - `index.html`
  - Pasta `img/` com imagens
![image (24)](https://github.com/user-attachments/assets/79bc7ffe-7ec3-415b-9bba-a4b4b70022c6)

### 3️⃣. Habilitar hospedagem estática
- Vá na aba **Propriedades** do bucket
- Ative a opção **Website estático**
  - Documento de índice: `index.html`
  - Documento de erro: `error.html` (opcional)
- Salve e copie a **URL do endpoint**
  
![image (25)](https://github.com/user-attachments/assets/63e29329-f1ad-4eee-99b0-99b87f1ba68c)

### 4️⃣. Tentar acessar o site
Você verá um erro:  

![image](https://github.com/user-attachments/assets/98424607-04bb-4d21-a42b-e19edf0f2e8b) 

❗
 POR QUE ISSO ACONTECE? 
Sem uma política de permissão pública no bucket, ninguém pode acessar os 
arquivos, nem mesmo o site estático.

### 5️⃣. Corrigir o erro com política pública
- Vá em **Permissions > Bucket Policy**
- Cole a seguinte política (substitua pelo nome real do seu bucket):

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::meu-site-runascloud/*"
    }
  ]
}

````
![image (26)](https://github.com/user-attachments/assets/d6021ccf-1b57-4db1-b8ec-407cfbaaed42) 

Substitua meusite-runascloud pelo nome real do seu bucket.

- Salve a política

### 6️⃣. Acessar novamente

- Volte para a aba de hospedagem estática

- Acesse o link do endpoint

- O seu site estará publicado! 🎉


![image (27)](https://github.com/user-attachments/assets/d954e0c2-845c-45e8-a5c5-9cac4790965c)

http://s3-runas-cloud-site.s3-website-us-east-1.amazonaws.com/

### 📷 Evidências da Atividade

✔️ Print do bucket criado

✔️ Print da hospedagem estática ativada

✔️ Print do erro 403 (AccessDenied)

✔️ Print do site funcionando no navegador 

👍 Parabéns!
Você concluiu com sucesso o Laboratório Publicação de Site Estático com AWS S3 da comunidade Run as Cloud!

### ⚠️ Observações
Ao final da atividade, limpe o ambiente para evitar custos adicionais na AWS.

### 📢 Compartilhe seu progresso!
Marque a comunidade Run as Cloud no LinkedIn  https://www.linkedin.com/company/run-as-cloud/?viewAsMember=true

Também marque os organizadores Grupos de Estudos :

Heberton Geovane  https://www.linkedin.com/in/heberton-geovane/

Maik Biazi   https://www.linkedin.com/in/maik-biazi-47b9291a5/

Michel Ernesto https://www.linkedin.com/in/mernesto/
