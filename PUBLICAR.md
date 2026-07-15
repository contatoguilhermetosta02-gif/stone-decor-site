# Publicar o site da Stone Décor — passo a passo

> Fluxo (igual ao da Dex): **GitHub → Vercel → domínio (DNS no Squarespace/Workspace)**.
> O repositório local já está pronto e commitado (feito pelo Claude). Você faz só os passos abaixo.
> Depois de publicado: Claude edita → você dá `git push` → o site atualiza sozinho.

> ⚠️ **Antes de tudo:** decida o domínio (ex.: `stonedecor.com.br`). Ele serve para o **email** (`@stonedecor.com.br`) e para o **site**. Compre via Google Workspace (vem junto com o email) ou num registrador. Use o **mesmo domínio** para os dois.

---

## Titularidade e handover (ler antes de comprar o domínio)

> Como a Stone é **cliente** (não a Dex), defina a propriedade dos ativos no começo. Assim, se o contrato terminar um dia, a passagem é limpa.

**O site não tem refém:** é HTML/CSS estático. No pior caso, entrega-se a pasta `06-Site/` e o cliente hospeda onde quiser. Os ativos que importam na passagem de bastão são 3:

1. **Domínio** (o mais crítico — é o endereço do site e do email).
2. **Email / Google Workspace.**
3. **GitHub + Vercel** (fácil, sem lock-in: transfere o repo ou reimporta na conta do cliente).

### Onde o Google registra o domínio
Comprar o domínio **dentro do Google Workspace** registra ele via **Squarespace** (parceiro que comprou o antigo Google Domains). O DNS fica no Squarespace. Importante: o Google/Squarespace vende **gTLDs** (`.com`, `.net`…), **NÃO vende `.com.br`**.

| Se quiser… | Onde registra | Handover |
|---|---|---|
| `stonedecor.com` | Junto no Google Workspace (via Squarespace) | Transferir depois via Squarespace (auth code) — passa pela conta de quem comprou |
| **`stonedecor.com.br`** (recomendado p/ marca local) | **Registro.br** (separado, exige CNPJ) | Mínimo — registrando no **CNPJ da Stone**, o domínio já é do cliente desde o dia 1 |

### Modelo recomendado
- **Domínio `.com.br` no Registro.br, sob o CNPJ da Stone Décor**, com você como contato técnico/admin.
- **Google Workspace** criado no nome/cobrança da Stone, você como administrador.
- **GitHub/Vercel** podem ficar na conta da Dex por praticidade (transferência é trivial).

> Resultado: o ativo mais importante (domínio) e o email já nascem do cliente. No fim do contrato, você só **sai do acesso** — nada pra "devolver".

### No contrato
Inclua uma cláusula simples: *"Ao término, a Dex transfere domínio, email e código-fonte ao cliente em até X dias úteis."* Protege os dois lados.

---

## 0. Antes de publicar — trocar os placeholders
No site há marcadores que precisam virar dados reais:
- **WhatsApp:** ✅ trocado para `wa.me/5543920036388` em todas as páginas.
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
