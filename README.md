# TutorIA Exatas

Tutor de ENEM para Matemática, Física e Química usando LLaMA 3.1 via Groq + RAG no Dify.

## Estrutura

```
tutoria-exatas/
├── index.html        # Interface do chat
├── vercel.json       # Configuração da Vercel
├── api/
│   └── chat.js       # Proxy seguro para a API do Dify
└── README.md
```

## Deploy na Vercel

### 1. Suba o projeto no GitHub
- Crie um repositório no GitHub (pode ser privado)
- Faça upload de todos os arquivos desta pasta

### 2. Conecte na Vercel
- Acesse vercel.com e crie uma conta (pode entrar com o GitHub)
- Clique em "Add New Project"
- Selecione o repositório do GitHub
- Clique em "Deploy" (sem alterar nada)

### 3. Configure a variável de ambiente (API Key segura)
- No painel do projeto na Vercel, vá em **Settings → Environment Variables**
- Adicione:
  - **Name:** `DIFY_API_KEY`
  - **Value:** sua chave `app-...`
- Clique em **Save**
- Vá em **Deployments** e clique em **Redeploy**

Pronto! O site estará no ar em `seu-projeto.vercel.app`.
