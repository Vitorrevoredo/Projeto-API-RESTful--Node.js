# 📦 API RESTful com Node.js, Express e MongoDB

Esta é uma **API RESTful** desenvolvida em **Node.js** com **Express** e **MongoDB Atlas** (via **Mongoose**), implementando um fluxo de operações **CRUD** completo (Create, Read, Update, Delete) para gerenciamento de registros de pessoas.

---

## 📌 Sobre o Projeto

A API foi projetada para demonstrar a criação de endpoints HTTP padronizados, integração com banco de dados NoSQL em nuvem (MongoDB Atlas), validação básica de requisições, tratamento de erros HTTP e uso de variáveis de ambiente com `dotenv`.

---

## 🛠️ Tecnologias Utilizadas

- **Node.js**: Ambiente de execução JavaScript no servidor.
- **Express.js**: Framework web para roteamento e middlewares HTTP.
- **MongoDB Atlas & Mongoose**: Banco de dados NoSQL na nuvem e ODM para modelagem de schemas.
- **Dotenv**: Gerenciamento seguro de variáveis de ambiente.
- **Nodemon**: Utilitário de desenvolvimento para reinicialização automática do servidor.

---

## 📁 Estrutura do Projeto

```text
Projeto-API-RESTful--Node.js/
├── index.js               # Ponto de entrada do servidor Express e conexão com MongoDB
├── package.json           # Dependências e scripts de execução
├── .env                   # Variáveis de ambiente (DB_USER, DB_PASSWORD) - [Não versionado]
├── .gitignore             # Arquivos ignorados pelo Git
├── models/
│   └── Person.js          # Model/Schema do Mongoose para Pessoas
└── routes/
    └── personRoutes.js    # Rotas CRUD da API (/person)
```

---

## 🔑 Variáveis de Ambiente (`.env`)

Crie o arquivo `.env` na raiz do projeto contendo as credenciais de acesso ao seu cluster MongoDB:

```env
DB_USER=seu_usuario_mongodb
DB_PASSWORD=sua_senha_mongodb
```

---

## 🔌 Endpoints da API

### **1. Rota Inicial**
- **URL:** `GET /`
- **Descrição:** Endpoint de teste para verificar se o servidor está ativo.
- **Resposta (200 OK):**
  ```json
  {
    "message": "Oi, express!"
  }
  ```

---

### **2. Criar Pessoa**
- **URL:** `POST /person`
- **Body (JSON):**
  ```json
  {
    "name": "Carlos Eduardo",
    "salary": 4500.00,
    "approved": true
  }
  ```
- **Respostas:**
  - `201 Created`: `{ "message": "Pessoa inserida no sistema com sucesso!" }`
  - `422 Unprocessable Entity`: `{ "error": "O nome é obrigatório!" }`
  - `500 Internal Server Error`: Erro interno no servidor.

---

### **3. Listar Todas as Pessoas**
- **URL:** `GET /person`
- **Descrição:** Retorna a lista completa de pessoas cadastradas no banco de dados.
- **Resposta (200 OK):**
  ```json
  [
    {
      "_id": "65f1a2b3c4d5e6f7a8b9c0d1",
      "name": "Carlos Eduardo",
      "salary": 4500.00,
      "approved": true
    }
  ]
  ```

---

### **4. Buscar Pessoa por ID**
- **URL:** `GET /person/:id`
- **Exemplo:** `GET /person/65f1a2b3c4d5e6f7a8b9c0d1`
- **Respostas:**
  - `200 OK`: Retorna o objeto da pessoa encontrada.
  - `422 Unprocessable Entity`: `{ "message": "Usuário não encontrado!" }`

---

### **5. Atualizar Pessoa por ID**
- **URL:** `PATCH /person/:id`
- **Body (JSON):**
  ```json
  {
    "name": "Carlos Eduardo",
    "salary": 5200.00,
    "approved": true
  }
  ```
- **Respostas:**
  - `200 OK`: Retorna os dados atualizados.
  - `422 Unprocessable Entity`: Registro não encontrado para atualização.

---

### **6. Remover Pessoa por ID**
- **URL:** `DELETE /person/:id`
- **Exemplo:** `DELETE /person/65f1a2b3c4d5e6f7a8b9c0d1`
- **Respostas:**
  - `200 OK`: `{ "message": "Usuário removido com sucesso!" }`
  - `422 Unprocessable Entity`: Registro não encontrado.

---

## 🔧 Como Executar o Projeto

### **Pré-requisitos**
- **Node.js** (v14+) instalado.
- Um cluster configurado no **MongoDB Atlas**.

### **Passos para Instalação e Execução**

1. **Clonar o repositório:**
   ```bash
   git clone https://github.com/Vitorrevoredo/Projeto-API-RESTful--Node.js.git
   cd Projeto-API-RESTful--Node.js
   ```

2. **Instalar as dependências:**
   ```bash
   npm install
   ```

3. **Configurar o arquivo `.env`:**
   Crie o arquivo `.env` na raiz do projeto com as credenciais do seu MongoDB.

4. **Iniciar o servidor:**
   ```bash
   npm start
   ```

5. **Testar os Endpoints:**
   Acesse no navegador ou cliente HTTP (Postman, Insomnia): [http://localhost:3000](http://localhost:3000)
