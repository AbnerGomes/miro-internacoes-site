# Guia de Publicação — Miro Ribeiro Internações

Este guia explica como publicar o site (arquivos `index.html`, `css/`, `js/` e `assets/`)
no seu domínio **www.mirointernacoes.com**, hospedado na **HostGator**.

> Antes de publicar: substitua os placeholders marcados com `TODO` ou `[EXEMPLO]` no
> `index.html` — e-mail, endereço/mapa, redes sociais e depoimentos reais.

---

## Visão geral dos arquivos

```
miro-internacoes-app/
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── script.js
├── assets/
│   └── images/
└── GUIA-PUBLICACAO.md   (não precisa subir este arquivo)
```

Esses são **todos** os arquivos que precisam ir para o servidor. Não é necessário
build, npm install nem nenhum passo de compilação — é HTML/CSS/JS puro.

---

## Cenário 1 — Hospedagem tradicional com cPanel/FTP (genérico)

Válido para qualquer provedor com cPanel (HostGator, Hostinger, Locaweb, GoDaddy etc.).

### Opção A — Gerenciador de Arquivos do cPanel (mais simples, sem programa extra)

1. Acesse o **cPanel** do seu provedor (geralmente em `seudominio.com/cpanel` ou pelo
   link enviado por e-mail na contratação).
2. Abra **Gerenciador de Arquivos** (File Manager).
3. Entre na pasta **`public_html`** (é a raiz pública do domínio principal).
   - Se o domínio for um "addon domain", a pasta pode ser `public_html/mirointernacoes.com`.
4. Se já existir um site antigo ali, faça backup: selecione tudo → **Comprimir** →
   baixe o `.zip` gerado para o seu computador antes de apagar.
5. Compacte a pasta do site novo (`index.html`, `css/`, `js/`, `assets/`) em um `.zip`
   no seu computador.
6. No Gerenciador de Arquivos, clique em **Upload**, envie o `.zip` para dentro de
   `public_html`.
7. Volte ao Gerenciador de Arquivos, clique com o botão direito no `.zip` enviado →
   **Extract** (Extrair) — direto dentro de `public_html`.
8. Confirme que `index.html` ficou **diretamente dentro de `public_html`**
   (não dentro de uma subpasta tipo `public_html/miro-internacoes-app/`). Se ficou
   numa subpasta, selecione todo o conteúdo dela e use **Move** para mover para a raiz.
9. Apague o `.zip` depois de extrair (deixa mais organizado).
10. Acesse `https://www.mirointernacoes.com` no navegador para conferir.

### Opção B — Via FTP (FileZilla ou similar)

1. No cPanel, vá em **Contas FTP** e anote (ou crie) um usuário FTP, com host,
   usuário, senha e porta (geralmente porta 21, ou 22 se for SFTP).
2. Baixe e instale o [FileZilla](https://filezilla-project.org/) (gratuito).
3. Conecte com os dados do cPanel:
   - **Host:** `ftp.mirointernacoes.com` (ou o IP informado pela HostGator)
   - **Usuário / Senha:** os dados da conta FTP
   - **Porta:** 21 (FTP) ou 22 (SFTP, se disponível)
4. No painel direito (servidor remoto), navegue até `public_html`.
5. No painel esquerdo (seu computador), navegue até a pasta do site
   (`miro-internacoes-app`).
6. Selecione `index.html`, `css`, `js` e `assets` e arraste para `public_html`
   no painel direito.
7. Aguarde o upload terminar (a pasta `assets/images` tem várias imagens, pode levar
   alguns minutos).
8. Acesse `https://www.mirointernacoes.com` para conferir.

### Depois de publicar (nos dois casos)

- **SSL/HTTPS:** na maioria dos planos cPanel (incluindo HostGator) o certificado
  SSL grátis (AutoSSL/Let's Encrypt) já vem ativo ou pode ser ativado em
  **SSL/TLS Status** → selecione o domínio → **Run AutoSSL**. Confirme que o site abre
  com o cadeado em `https://www.mirointernacoes.com`.
- **Redirecionar `mirointernacoes.com` para `www.mirointernacoes.com`** (ou o
  contrário): cPanel → **Domains/Redirects**, crie um redirecionamento 301 da versão
  sem `www` para a versão com `www` (ou vice-versa, o que você preferir usar como
  principal).

---

## Cenário 2 — Passo a passo específico no painel da HostGator

Como seu domínio **www.mirointernacoes.com** já está na HostGator, o caminho mais
direto é usar o próprio cPanel dela (é o mesmo mecanismo do Cenário 1, só que com
os nomes de tela exatos da HostGator):

1. Acesse **https://portal.hostgator.com.br** (ou o link de acesso que veio no
   e-mail de boas-vindas) e faça login com seus dados de cliente.
2. No painel do cliente, localize o domínio `mirointernacoes.com` e clique em
   **Acessar cPanel** (ou **Gerenciar**).
3. Dentro do cPanel da HostGator, procure o ícone **Gerenciador de Arquivos**
   (fica na seção "Arquivos").
4. Entre em `public_html`.
   - **Importante:** se esse domínio foi adicionado como domínio adicional
     (addon domain) dentro de uma conta que já tem outro site principal, a pasta
     correta pode ser `public_html/mirointernacoes.com` em vez de `public_html`
     direto. Para confirmar, vá em **Domínios** no cPanel e veja qual "Document
     Root" está associado a `www.mirointernacoes.com`.
5. **Se já existe um site publicado nesse domínio:** selecione todos os arquivos
   atuais, clique em **Comprimir** e baixe o `.zip` para seu computador como backup
   antes de remover/substituir.
6. Compacte localmente a pasta do site (`index.html`, `css/`, `js/`, `assets/`) em
   um único `.zip`.
7. No Gerenciador de Arquivos da HostGator, clique em **Carregar** (Upload), arraste
   o `.zip` e aguarde a barra de progresso terminar.
8. Volte à listagem de arquivos, clique com o botão direito no `.zip` → **Extrair**.
9. Confira se `index.html` está direto na raiz correta (`public_html` ou
   `public_html/mirointernacoes.com`, conforme o passo 4). Se necessário, mova os
   arquivos extraídos para o nível certo usando **Mover**.
10. Exclua o `.zip` enviado (não precisa mais dele no servidor).
11. Ainda no cPanel da HostGator, vá em **SSL/TLS Status**, marque o domínio e
    clique em **Run AutoSSL** para garantir o cadeado HTTPS (a HostGator costuma
    já deixar isso ativo por padrão nos planos com cPanel).
12. Acesse `https://www.mirointernacoes.com` numa aba anônima do navegador para
    validar sem cache.

### Se preferir usar FTP na HostGator

1. No cPanel da HostGator, vá em **Contas FTP**, crie uma conta (ou use a principal).
2. Use os dados de host (`ftp.mirointernacoes.com`), usuário e senha no FileZilla,
   exatamente como descrito na **Opção B** do Cenário 1.
3. Envie os arquivos para `public_html` (ou a pasta correspondente ao addon domain).

### Checklist final pós-publicação

- [ ] `https://www.mirointernacoes.com` abre corretamente com cadeado (HTTPS)
- [ ] Botão flutuante de WhatsApp abre conversa com o número certo
- [ ] Menu mobile (ícone hambúrguer) abre e fecha corretamente no celular
- [ ] Testar em pelo menos um celular real (Android e/ou iPhone)
- [ ] Substituir os placeholders: e-mail, endereço/mapa, Instagram, Facebook
- [ ] Substituir os depoimentos `[EXEMPLO]` por relatos reais autorizados
- [ ] (Opcional) Cadastrar o domínio no **Google Search Console** para indexação

---

## Como adicionar o mapa do Google Maps depois

Quando você tiver o endereço definitivo:

1. Abra o [Google Maps](https://maps.google.com), pesquise o endereço da clínica.
2. Clique em **Compartilhar** → aba **Incorporar um mapa** → copie o código `<iframe>`.
3. No arquivo `index.html`, procure o comentário `TODO` dentro da seção de contato
   (`<div class="contato-map">`) e substitua o bloco `.map-placeholder` pelo `<iframe>`
   copiado.
4. Suba o arquivo atualizado novamente (repita o upload do `index.html`).

---

Qualquer dúvida na hora de publicar, me chame que eu te ajudo a revisar antes de ir
para o ar.
