# 📧 Stone Décor — Setup de email (Registro.br + Google Workspace)

> Ordem certa: **1º registrar o domínio no Registro.br → 2º criar o Google Workspace e conectar esse domínio.**
> Por quê: o Workspace pergunta "já tem domínio?". Tendo o `.com.br` pronto, você escolhe "usar domínio existente" e evita cair na compra do `.com` pelo Google (via Squarespace).

---

## 1. Registrar o domínio no Registro.br
1. Acesse **https://registro.br**.
2. Pesquise **`stonedecor.com.br`** (ou a variação escolhida) e confira se está disponível.
3. Registre **no CNPJ da Stone Décor** (titularidade já do cliente = handover limpo). Custo ~R$40/ano.
4. Conclua o pagamento. O domínio fica ativo em minutos.

> Guarde o login do Registro.br — é onde você edita o DNS (verificação, email e, depois, o site).

## 2. Criar o Google Workspace
1. Acesse **https://workspace.google.com** → **Começar / Iniciar teste**.
2. Plano: **Business Starter** (suficiente pra Stone — ver justificativa no histórico).
3. Preencha nome da empresa (Stone Décor) e nº de usuários (quantas caixas de email — ex.: dono + equipe).
4. Quando perguntar do domínio, escolha **"Sim, já tenho um domínio"** e digite **`stonedecor.com.br`**.
5. Crie o usuário admin (ex.: `contato@stonedecor.com.br` ou um nome do dono).

## 3. Verificar a posse do domínio (registro TXT)
1. O Google mostra um **registro TXT** (ex.: `google-site-verification=...`).
2. No **Registro.br** → painel do domínio → **DNS / Editar Zona** → **Adicionar registro**:
   - Tipo: **TXT** · Nome/host: `@` (ou em branco) · Valor: o texto que o Google deu.
3. Volte ao Google e clique **Verificar**. (Pode levar de minutos a algumas horas.)

## 4. Ativar o email (registros MX)
1. O Google mostra os **registros MX**. Hoje costuma ser **um único**:
   - Tipo: **MX** · Nome: `@` · Prioridade: `1` · Valor: `smtp.google.com`
   - ⚠️ **Use sempre os valores que o Google mostrar na sua tela** (se forem os 5 antigos `aspmx...`, use esses).
2. Adicione esse(s) MX no **DNS do Registro.br** (mesmo painel do passo 3).
3. Salve. Em algumas horas o email está funcionando.

## 5. Criar as contas de email
- No **Admin do Google** (admin.google.com) → **Usuários** → adicionar cada pessoa (ex.: `contato@`, `vendas@`, nome do dono).
- Configure o app **Gmail** no celular/computador de cada um.

---

## Depois: publicar o site (mesmo painel de DNS)
Quando formos publicar o site (GitHub → Vercel), você aponta o domínio pra Vercel **no mesmo DNS do Registro.br** (um registro **A** e/ou **CNAME** que a Vercel indicar). Ver `PUBLICAR.md`.

> Importante: mexer no A/CNAME (site) **não afeta** os MX (email). São registros diferentes na mesma zona.

## Contas necessárias (resumo)
| Conta | Nova pra Stone? | Observação |
|---|---|---|
| Registro.br | **Sim** (no CNPJ da Stone) | Dono do domínio |
| Google Workspace | **Sim** (Starter, nome da Stone) | Email |
| GitHub | **Não** — reusar a da Dex | Só criar repo `stone-decor-site` |
| Vercel | **Não** — reusar a da Dex | Só criar projeto novo |
