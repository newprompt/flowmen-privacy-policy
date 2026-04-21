# FlowMen — static site (GitHub Pages)

Site estático com 3 páginas legais pra satisfazer a exigência da App Store
e Google Play por URL pública de Privacy Policy e Support.

## Arquivos

```
site/
├── index.html           # Landing com links pras 3 páginas
├── privacy-pt-br.html   # Política de Privacidade (pt-BR)
├── privacy-en.html      # Privacy Policy (EN)
├── support.html         # FAQ + contato
├── style.css            # CSS compartilhado (mobile-first, dark mode)
├── .nojekyll            # Evita que GitHub Pages rode Jekyll
└── README.md            # Este arquivo
```

## Como publicar no GitHub Pages

### Passo 1 — crie um repo público novo

No GitHub, novo repo com nome sugerido `flowmen-site` (ou outro — o nome
vira parte da URL). Marque **Public** (GitHub Pages Free exige).

### Passo 2 — copie o conteúdo desta pasta pra raiz do repo

```bash
# Clone o repo novo em outro diretório
cd ~/code
git clone https://github.com/<seu-user>/flowmen-site.git
cd flowmen-site

# Copie os arquivos desta pasta pra raiz do repo novo
cp ~/Documents/flowmen/docs/store/site/* ./
cp ~/Documents/flowmen/docs/store/site/.nojekyll ./

git add .
git commit -m "Initial site"
git push
```

### Passo 3 — ative Pages

No GitHub do repo `flowmen-site`:

1. **Settings → Pages**
2. **Source:** `Deploy from a branch`
3. **Branch:** `main` · **Folder:** `/ (root)` · **Save**

Aguarde 1-2 minutos. A URL final aparece no topo da página de Settings
(tipo `https://<seu-user>.github.io/flowmen-site/`).

### Passo 4 — valide no navegador

Abra as 4 URLs e verifique que carregam:

```
https://<seu-user>.github.io/flowmen-site/
https://<seu-user>.github.io/flowmen-site/privacy-pt-br.html
https://<seu-user>.github.io/flowmen-site/privacy-en.html
https://<seu-user>.github.io/flowmen-site/support.html
```

### Passo 5 — avise o Claude

Me responda aqui com as 2 URLs principais:

- **Privacy Policy URL**: `https://<seu-user>.github.io/flowmen-site/privacy-pt-br.html`
- **Support URL**: `https://<seu-user>.github.io/flowmen-site/support.html`

Eu atualizo todas as referências cruzadas nos outros arquivos do
`docs/store/` (review-notes.md, pre-submit-checklist.md, etc.) pra bater.

## Domínio próprio (opcional, futuro)

Se um dia você comprar `flowmen.app` ou `newprompt.com.br`, dá pra
apontar pro GitHub Pages via DNS + criar um arquivo `CNAME` na raiz do
repo com `flowmen.app`. GitHub cuida do certificado HTTPS sozinho.

Não precisa agora — a URL padrão do GitHub Pages serve direito pra
App/Play Store.

## Atualizar o site depois

Qualquer mudança: edita os arquivos, `git push`, GitHub Pages reflete em
~1 minuto. Não precisa rebuild nem nada.

## Por que HTML e não Markdown?

GitHub Pages **suporta** Markdown via Jekyll, mas:

1. Exige front-matter YAML em cada arquivo
2. Precisa de um tema (ou CSS custom)
3. Pode renderizar inconsistente dependendo da versão do Jekyll

HTML estático é:

1. **Zero build step** — o que você escreve é o que aparece
2. **Portável** — funciona em qualquer host (Netlify, Vercel, Cloudflare
   Pages, servidor próprio)
3. **Mais rápido** no carregamento (sem template engine)
4. **Mais controle** sobre SEO, meta tags, Open Graph

O `.nojekyll` na raiz é só uma garantia: força o GitHub Pages a servir
os arquivos crus sem tentar rodar Jekyll.
