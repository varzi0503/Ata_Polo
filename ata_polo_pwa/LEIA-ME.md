# Ata paralela: publicar e instalar

## O que está na pasta
- `index.html`: a app. É a mesma do protótipo, mais os tipos de letra locais e o código para funcionar offline.
- `manifest.webmanifest`: o nome, os ícones e o modo de ecrã inteiro com que a app se instala.
- `sw.js`: o service worker. Guarda todos os ficheiros no telemóvel para a app abrir sem rede.
- `icons/` e `fonts/`: os ícones e os tipos de letra. Nada é carregado de fora.

## 1. Publicar no GitHub Pages
1. Cria um repositório no GitHub, por exemplo `ata-polo`. No plano gratuito tem de ser público. O repositório só contém o código: os dados dos jogos nunca saem do telemóvel.
2. Envia o conteúdo desta pasta para a raiz do repositório:
   ```
   git init && git add . && git commit -m "Ata paralela v1"
   git branch -M main
   git remote add origin https://github.com/<utilizador>/ata-polo.git
   git push -u origin main
   ```
3. No repositório, vai a Settings → Pages → Source: "Deploy from a branch" → `main` / `/ (root)` → Save.
4. Ao fim de 1 ou 2 minutos, a app fica disponível em `https://<utilizador>.github.io/ata-polo/`.

## 2. Instalar no telemóvel do delegado
- **Android (Chrome):** abre o endereço, menu ⋮ → "Instalar app" ou "Adicionar ao ecrã principal".
- **iPhone (Safari):** abre o endereço, botão Partilhar → "Adicionar ao ecrã principal".
- **Atenção no iPhone:** a app instalada e o Safari guardam os dados em sítios separados. O delegado tem de abrir sempre pelo ícone, nunca pelo Safari.

## 3. Testar antes do primeiro jogo
1. Com rede, abre a app pelo ícone. Fecha-a e volta a abrir.
2. Em Definições, tem de aparecer "Pronto para usar sem rede."
3. Põe o telemóvel em modo de voo, fecha a app por completo e volta a abri-la. Tem de abrir com o registo intacto.

## 4. Publicar uma versão nova
1. Altera os ficheiros que precisares.
2. Em `sw.js`, muda `CACHE = 'ata-polo-v1'` para `v2`, `v3`, e assim por diante. **Sem este passo, os telemóveis continuam com a versão antiga.**
3. Em `index.html`, atualiza o texto "Versão 1".
4. Faz commit e push.
5. Da próxima vez que o delegado abrir a app com rede, aparece em Definições o botão "Há uma versão nova". A versão nova só entra quando ele carregar nesse botão, para nunca mudar a meio de um jogo.

## Cuidados
- "Limpar dados do site/navegador" e desinstalar a app apagam o registo. Copia o resumo no fim de cada jogo.
- Se mudares o endereço (outro repositório ou outro domínio), a app conta como nova e começa sem dados.
