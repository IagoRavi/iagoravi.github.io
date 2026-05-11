# Setup GitHub Pages — Passo a Passo

> Como publicar seu portfólio em `https://iagoravi.github.io` em ~15 minutos.

---

## 📦 O que você vai publicar

Os 4 arquivos que produzimos:
- `index.html` — site portfólio
- `assets/dashboard-despesas.png`
- `assets/dashboard-ouvidoria.png`
- `assets/dashboard-contratos.png`

---

## 🚀 PASSO 1 — Criar o repositório especial

**Importante:** o GitHub Pages tem uma regra mágica — se você criar um repo com o nome **exato `iagoravi.github.io`**, ele vira automaticamente um site público em `https://iagoravi.github.io`.

> ⚠️ **Atenção:** seu username GitHub é `IagoRavi` (com I e R maiúsculos). Mas o nome do repo do GitHub Pages **deve ser todo minúsculo**: `iagoravi.github.io`. O GitHub aceita essa diferença.

**Como criar:**

1. Acesse https://github.com/new (logado)
2. Preencha:
   - **Repository name:** `iagoravi.github.io` ⚠️ (exatamente assim, minúsculo)
   - **Description:** "My personal portfolio · Data Analyst & BI Developer"
   - **Visibility:** ✅ **Public** (precisa ser público pro Pages funcionar no plano free)
   - ✅ Marque **"Add a README file"** (pode deixar)
   - **NÃO** adicione `.gitignore` nem licença ainda — adicionaremos depois se quiser
3. Clique em **"Create repository"**

---

## 📁 PASSO 2 — Subir os arquivos do portfólio

Tem 3 formas de fazer isso. Escolha a que preferir.

### Opção A — Interface web (mais simples)

1. No repositório recém-criado, clique em **"Add file" → "Upload files"**
2. Arraste os arquivos:
   - `index.html` (no topo do repo)
   - Crie a pasta `assets` arrastando os 3 PNGs (você consegue arrastar uma pasta inteira)
3. Na parte de baixo da página:
   - **Commit message:** `Initial portfolio commit`
   - Clique em **"Commit changes"**

### Opção B — Git via terminal (mais rápido se você já tem Git)

```bash
# Clone o repo
git clone https://github.com/IagoRavi/iagoravi.github.io.git
cd iagoravi.github.io

# Copie os arquivos do portfólio para essa pasta
# (substitua [CAMINHO] pelo caminho onde você baixou os arquivos)
cp [CAMINHO]/index.html .
mkdir -p assets
cp [CAMINHO]/assets/*.png assets/

# Adicione, commit e push
git add .
git commit -m "Initial portfolio commit"
git push origin main
```

### Opção C — GitHub Desktop (interface visual)

1. Abra GitHub Desktop
2. **File → Clone Repository → escolha `iagoravi.github.io`**
3. Copie os arquivos do portfólio para a pasta clonada
4. No GitHub Desktop, escreva commit message: `Initial portfolio commit`
5. Clique em **"Commit to main"** → depois em **"Push origin"**

---

## ⚙️ PASSO 3 — Ativar GitHub Pages

> Importante: na maioria dos casos, GitHub Pages é **ativado automaticamente** quando o repo se chama `username.github.io`. Mas confirme:

1. No repositório, vá em **Settings** (aba do topo)
2. Menu lateral esquerdo → clique em **Pages**
3. Em **"Build and deployment"**:
   - **Source:** "Deploy from a branch"
   - **Branch:** `main` / `/ (root)`
4. Clique em **"Save"** se necessário
5. Aguarde 1-3 minutos enquanto o GitHub publica

---

## 🌐 PASSO 4 — Acessar seu site

Após 1-3 minutos, acesse:

**https://iagoravi.github.io**

> 💡 Se aparecer 404 nos primeiros minutos, espere mais um pouco — o GitHub demora para o primeiro deploy. Tente em 5 min.

---

## ✅ PASSO 5 — Validar tudo

Abra o site e confira:

- [ ] Hero com nome "Iago Ravi" e headline aparecendo
- [ ] Toggle PT/EN funcionando (clique no botão "PT" no topo)
- [ ] Imagens dos 3 dashboards carregando na seção "Projects"
- [ ] Links das dashboards (.gov.br) funcionando ao clicar
- [ ] Link do GitHub apontando para `github.com/IagoRavi`
- [ ] Link do LinkedIn correto
- [ ] Email `iago.ravi@outlook.com` correto
- [ ] Site responsivo no celular (abra do seu telefone)

---

## 🔄 PASSO 6 — Como atualizar depois

Sempre que quiser mudar algo:

**Via interface web:**
1. Vá no repo → clique no arquivo (ex: `index.html`)
2. Clique no lápis (✏️) "Edit this file"
3. Faça a alteração
4. Commit changes
5. Aguarde 1-2 min e atualize o site

**Via Git terminal:**
```bash
# Edite o arquivo localmente
git add .
git commit -m "Update [o que mudou]"
git push
```

---

## 🚧 PASSO 7 — Adicionar ao LinkedIn (importante!)

Depois que o site estiver no ar:

1. Vá no seu LinkedIn
2. **Editar perfil** → **Informações de contato** (ícone ao lado do headline)
3. Em **"Site"**, adicione:
   - **URL:** `https://iagoravi.github.io`
   - **Tipo:** "Portfolio"
4. Salvar

Também adicione na seção **"Em destaque"**:
1. Editar "Em destaque" → "+ Adicionar"
2. **Adicionar link**: `https://iagoravi.github.io`
3. **Título:** "Personal Portfolio · iagoravi.github.io"
4. **Descrição:** "Featured projects, certifications, and tech stack — bilingual (EN/PT)"
5. Salvar

---

## 🔐 PASSO 8 — Subir o repositório IFRS17 sanitizado (opcional, mas recomendado)

Quando quiser tornar o IFRS17 público (referência):

1. Crie um **novo repo público:** `ifrs17-validation-engine-demo`
2. Use o template `README_template_IFRS17.md` que produzi
3. Suba apenas:
   - Estrutura de código genérica (sem regras do cliente)
   - Schema Pydantic genérico
   - Testes com dados sintéticos
   - Documentação da arquitetura

Eu posso te ajudar a estruturar esse repo numa próxima sessão se quiser.

---

## 🎯 (Bônus) Domínio próprio depois

Se mais pra frente quiser ter um domínio próprio (ex: `iagoravi.com`):

1. Compre o domínio (Registro.br ~R$ 40/ano, Namecheap ~$10/ano)
2. No repo `iagoravi.github.io`, vá em **Settings → Pages**
3. Em **"Custom domain"**, digite seu domínio
4. Configure os DNS no registrar conforme [docs do GitHub](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
5. Ative ✅ "Enforce HTTPS"

Mas pra começar, `iagoravi.github.io` já é mais que suficiente — vários devs sêniores usam o `.github.io` como portfólio principal sem problema.

---

## 🐛 Troubleshooting

**Site não aparece após 5 minutos:**
- Confira se o nome do repo é exatamente `iagoravi.github.io` (minúsculo)
- Confira se o repo é público (Settings → Visibility)
- Confira se Pages está ativo (Settings → Pages)
- Tente abrir em aba anônima (cache pode confundir)

**Imagens não carregam:**
- Confira se a pasta se chama `assets` (não `Assets` ou `images`)
- Confira se os nomes dos PNGs estão corretos:
  - `dashboard-despesas.png`
  - `dashboard-ouvidoria.png`
  - `dashboard-contratos.png`

**Toggle de idioma não funciona:**
- Pode ser cache do navegador — pressione Ctrl+Shift+R pra forçar reload

---

## 📊 Próximos passos depois de publicar

1. ✅ Compartilhe o link em **propostas de freela** (Upwork, Toptal)
2. ✅ Adicione o link no **rodapé das suas mensagens** profissionais
3. ✅ Inclua no **header dos CVs** (PT e EN) — substitua `linkedin.com/in/iago-ravi` por `iagoravi.github.io`
4. ✅ Mencione em **conexões e InMails** no LinkedIn
5. ✅ Use Google Search Console (grátis) pra ver quando começar a aparecer no Google

Boa publicação! 🚀
