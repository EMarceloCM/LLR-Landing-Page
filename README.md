# Linguas Discens · landing page

Site de apresentação do app Android Linguas Discens (LLR). HTML e CSS puros, sem build, publicado no GitHub Pages por GitHub Actions.

## Estrutura

- `site/index.html` e `site/styles.css`: a página, feita a partir do design "Linguas Discens — Landing page".
- `site/fonts/`: Bricolage Grotesque e Figtree (woff2, licença OFL ao lado).
- `.github/workflows/pages.yml`: publica a pasta `site/` a cada push na `main` e a cada release publicada.

## Os APKs

Os APKs não entram no repositório: o universal passa de 100 MB, o limite do GitHub para um arquivo. Eles ficam como anexos de uma release, e o workflow os baixa da release mais recente e põe ao lado do `index.html`. Se o `index.html` apontar para um APK que não está na release, o workflow falha em vez de publicar um link quebrado.

## Primeira publicação

1. Crie o repositório no GitHub e envie este projeto para a branch `main`.
2. Em Settings > Pages, em "Build and deployment", escolha a fonte **GitHub Actions**.
3. Crie uma release (por exemplo `v1.0.0`) e anexe os dois APKs de `LLR/dist/`:
   - `linguas-discens-1.0.0-arm64-v8a.apk`
   - `linguas-discens-1.0.0.apk`

Publicar a release dispara o workflow e o site sai em `https://<usuário>.github.io/<repositório>/`. O workflow do primeiro push falha porque ainda não existe release; a partir da release ele passa.

## Nova versão do app

1. No LLR, `npm run version:bump` e `npm run release` (gera os APKs em `dist/`).
2. Aqui, troque a versão nos links e nos textos da seção "Baixar" do `site/index.html` (nomes dos arquivos, tamanhos em MB e "Versão x.y.z") e faça o push.
3. Crie a release `vx.y.z` com os APKs novos anexados.

## Ver localmente

Copie os APKs de `LLR/dist/` para `site/` (o `.gitignore` os ignora) e abra o `site/index.html` no navegador, ou sirva a pasta:

```bash
npx serve site
```
