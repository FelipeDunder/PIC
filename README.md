# VeloTrack

Aplicação React + Vite com rotas, gráficos e layout mobile-first.

## Scripts

```bash
npm install         # instala dependências
npm run dev         # ambiente de desenvolvimento
npm run build       # build de produção (gera dist/)
npm run preview     # serve o build localmente
npm run deploy      # publica dist/ no branch gh-pages
```

## Publicando no GitHub Pages

O erro de tela em branco ocorre quando o GitHub Pages serve o `index.html` da branch `master`, que referencia `/src/main.jsx` (modo dev). Para que o site carregue, ele precisa servir os arquivos compilados do build. Há duas formas:

### 1. Usando a branch `gh-pages`

1. Execute `npm run deploy` para gerar o build e enviar o conteúdo de `dist/` para a branch `gh-pages`.
2. No repositório (`Settings → Pages`), em **Build and deployment**, escolha **Source: Deploy from a branch**.
3. Selecione **Branch: gh-pages** e **Folder: / (root)** e clique em **Save**.
4. Após o deploy terminar, acesse `https://felipedunder.github.io/PIC/` e limpe o cache do navegador.

### 2. Usando GitHub Actions (opção recomendada)

1. Em **Settings → Pages**, selecione **Source: GitHub Actions**.
2. O workflow `.github/workflows/deploy.yml` já está configurado: a cada push na `master` ele roda `npm ci`, `npm run build` e publica o artefato para o Pages.
3. Depois de salvar, vá em **Actions → Deploy to GitHub Pages → Run workflow** para disparar o primeiro deploy.
4. Aguarde o job completar; o link final aparecerá nos detalhes da execução.

> **Importante:** sempre que a página voltar a ficar branca, confira se o Pages não voltou a apontar para `master`. Ele precisa servir a branch `gh-pages` (opção 1) ou o workflow do Actions (opção 2). Enquanto o HTML servido for o do template Vite (com `<script src="/src/main.jsx">`), o navegador não carregará o app.

## Extras

- Tailwind CSS 4 (`@apply` e tokens definidos em `src/index.css`).
- React Router configurado com `HashRouter` para garantir navegação estável no Pages.
- Ícones do `lucide-react`, gráficos com `react-chartjs-2` e mapas via `react-leaflet` (dependendo das páginas usadas).
