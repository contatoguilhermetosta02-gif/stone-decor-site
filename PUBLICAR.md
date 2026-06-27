# Publicar o site da Stone Décor — passo a passo

> Fluxo (igual ao da Dex): **GitHub → Vercel → domínio (DNS no Squarespace/Workspace)**.
> O repositório local já está pronto e commitado (feito pelo Claude). Você faz só os passos abaixo.
> Depois de publicado: Claude edita → você dá `git push` → o site atualiza sozinho.

> ⚠️ **Antes de tudo:** decida o domínio (ex.: `stonedecor.com.br`). Ele serve para o **email** (`@stonedecor.com.br`) e para o **site**. Compre via Google Workspace (vem junto com o email) ou num registrador. Use o **mesmo domínio** para os dois.

---

## 0. Antes de publicar — trocar os placeholders
No site há marcadores que precisam virar dados reais:
- **WhatsApp:** `wa.me/5543000000000` → número real (procure por `5543000000000` em `index.html`, `blog.html` e `blog/`).
- **Projetos:** os 3 cards e os créditos `[@arquiteto]` em `index.html` → fotos e @ reais.
- (Opcional) Instagram já aponta para `@stonedecorlondrina`.

## 1. Criar conta no GitHub (se ainda não tem)
- https://github.com → **Sign up**. Use o e-mail da Stone (quando o Workspace estiver pronto) ou um e-mail seu.
- Confirme o e-mail.

## 2. Criar o repositório
- GitHub → **+** → **New repository**.
- **Repository name:** `stone-decor-site`
- Visibilidade: **Private** (recomendado) ou Public.
- **NÃO** marque "Add a README" (o repo local já tem arquivos).
- **Create repository** → copie a URL (`https://github.com/SEU-USUARIO/stone-decor-site.git`).

## 3. Conectar o repo local e enviar (push)
No terminal (troque a URL pela sua):
```bash
cd "/Users/guilhermetosta/Desktop/Dex Produtora/Stone Décor/06-Site"
git remote add origin https://github.com/SEU-USUARIO/stone-decor-site.git
git push -u origin main
```
> Na primeira vez pede login do GitHub (abre o navegador). É normal.

## 4. Publicar na Vercel
- https://vercel.com → **Sign up** → **Continue with GitHub**.
- **Add New… → Project** → escolha **stone-decor-site** → **Import**.
- **Framework Preset:** **Other** (é HTML puro, sem build).
- **Deploy**. Em ~30s o site está num endereço tipo `stone-decor-site.vercel.app`. **Confira se abriu certo.**

## 5. Apontar o domínio (DNS)
**Na Vercel:** Projeto → **Settings → Domains** → digite seu domínio (ex.: `stonedecor.com.br`) → **Add**. Adicione também `www.` (aceite o redirect). A Vercel mostra **os registros exatos** (geralmente um **A** `@` e um **CNAME** `www`).

**No painel de DNS do domínio** (Squarespace/Workspace ou registrador):
- Vá em **DNS / DNS Settings → Add Record**.
- Crie os registros que a Vercel pediu. **Use sempre os valores que a Vercel mostrar na sua tela.**
- Salve. Propagação leva de minutos a horas; HTTPS (cadeado) é automático.

## 6. Conferir e finalizar
- Abra `https://[seu-dominio]` — deve carregar com cadeado.
- Atualize o link na **bio do Instagram** e no **Google Business**.

---

## Depois: como atualizar o site
Quando o Claude editar algo:
```bash
cd "/Users/guilhermetosta/Desktop/Dex Produtora/Stone Décor/06-Site"
git add .
git commit -m "ajuste no site"
git push
```
