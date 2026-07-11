# 🚀 AFY — Site de Apresentação

Site oficial do **AFY AutoBot**, a plataforma inteligente de automação para afiliados.

## 📁 Estrutura

```
site/
├── index.html       # Landing page (pública - todos podem ver)
├── dashboard.html   # Dashboard do Bot (protegido por senha)
└── README.md        # Este arquivo
```

## 🆓 Hospedagem Gratuita (Cloudflare Pages)

### Passo 1: Criar conta no Cloudflare

1. Acesse [cloudflare.com](https://cloudflare.com) e crie uma conta **gratuita**
2. Verifique seu email

### Passo 2: Fazer upload do site

**Opção A — Upload direto (mais rápido):**

1. Acesse [dash.cloudflare.com](https://dash.cloudflare.com) → **Workers & Pages**
2. Clique em **Create application** → **Pages** → **Upload assets**
3. Faça upload dos arquivos `index.html` e `dashboard.html`
4. Seu site estará disponível em: `https://seudominio.pages.dev`

**Opção B — Conectar com GitHub (recomendado):**

1. Crie um repositório no GitHub
2. Faça push dos arquivos do site
3. No Cloudflare Pages, clique em **Create application** → **Pages**
4. Conecte com seu GitHub e selecione o repositório
5. Configure: **Production branch** → `main`
6. **Build settings**: Framework = **None** (é só HTML estático)
7. Clique em **Save & Deploy**

### Passo 3: Configurar domínio personalizado (afy.com.br, afy.app, etc.)

Você precisa comprar um domínio em um registrador como:
- **Cloudflare Registrar** (preço de custo, ~R$30-50/ano)
- **Porkbun** (preços baixos)
- **Registro.br** (para domínios `.com.br`)

**Configuração:**

1. No Cloudflare Pages, vá em seu projeto → **Custom domains**
2. Clique em **Set up a custom domain**
3. Digite seu domínio (ex: `afy.com.br`)
4. O Cloudflare vai configurar os DNS automaticamente
5. Pronto! ✅

### Passo 4 (Opcional): Proteger o dashboard com Cloudflare Access

Para uma camada extra de segurança além da senha do dashboard:

1. No Cloudflare Dashboard, vá em **Zero Trust** → **Access** → **Applications**
2. Clique em **Add an application** → **Self-hosted**
3. Configure:
   - **Application domain**: `dashboard.afy.com.br/*` (seu domínio)
   - **Policy**: Allow - apenas emails específicos ou qualquer email Google
4. Salve. Agora, antes de acessar o dashboard, o usuário precisa fazer login social.

## 🔒 Configurar a Senha do Dashboard

A senha padrão é **`afy2024`**. Para alterar:

1. Abra o arquivo `dashboard.html`
2. Localize a linha:
   ```javascript
   const PASSWORD_HASH = "7c6a61b68d5b65e0e3d6c9c4c7a5f3e1d8b2a4f6c0e8d2a4b6c8e0f2a4b6c8d";
   ```
3. Gere o hash SHA-256 da sua nova senha em: [https://emn178.github.io/online-tools/sha256.html](https://emn178.github.io/online-tools/sha256.html)
4. Substitua o hash no arquivo
5. Faça o deploy novamente

---

## 💡 Dicas

- O site é **100% estático** — funciona sem servidor backend
- Os links "Acessar Bot" e "Dashboard" apontam para `dashboard.html`
- Para integrar com seu bot real, basta atualizar os links no HTML

## 🛠️ Tecnologias

- HTML5 + CSS3 (Tailwind CSS + DaisyUI)
- JavaScript puro (sem frameworks)
- Lucide Icons
- CryptoJS (para hash da senha no navegador)

---

Feito com ❤️ para afiliados brasileiros 🇧🇷
