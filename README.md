# Vitrine do Jota Studio — MVP 0.1.0

Aplicativo web instalável (PWA), responsivo para celular e computador, com estrutura inicial para futura embalagem Android.

## O que funciona nesta versão
- Criar conteúdo com título, formato, categoria, roteiro, legenda, hashtags e CTA.
- Salvar rascunhos.
- Enviar conteúdo para aprovação manual.
- Aprovar ou rejeitar.
- Agendar localmente para data e horário.
- Registrar manualmente que um conteúdo foi publicado.
- Histórico, contadores e exportação/importação de backup JSON.
- Interface responsiva e cache básico para abrir offline após a primeira visita.

## Limitações importantes
- Os dados ficam no armazenamento local do navegador/dispositivo. Não há sincronização entre aparelhos.
- O botão “Registrar publicação” NÃO publica no Instagram; apenas registra uma publicação que você já realizou manualmente.
- Não há geração real de IA, voz, música, renderização de MP4, agendamento em servidor ou conexão com a Meta nesta versão.
- A aprovação manual é preservada como regra de produto; qualquer futura integração de publicação deverá verificar uma aprovação explícita no servidor antes de enviar conteúdo.
- Para instalar como PWA, o app precisa ser servido por HTTPS (ou localhost). Abrir o `index.html` diretamente não habilita instalação/offline corretamente.

## Executar localmente
Com Python 3 instalado, dentro desta pasta:

```bash
python -m http.server 8000
```

Abra `http://localhost:8000` no navegador.

## Publicar gratuitamente para teste
Hospede esta pasta em um serviço de hospedagem estática com plano gratuito que ofereça HTTPS. Depois, abra o endereço no Chrome/Android e use “Instalar app” ou “Adicionar à tela inicial”.

## Preparar versão Android (APK)
A estrutura pode ser empacotada com Capacitor. Requer Node.js, Android Studio e Android SDK instalados. O APK não é compilado automaticamente por este pacote.

Exemplo de preparação:

```bash
npm init -y
npm install @capacitor/core @capacitor/cli
npx cap init "Vitrine do Jota Studio" "br.com.vitrinedojota.studio" --web-dir .
npm install @capacitor/android
npx cap add android
npx cap open android
```

No Android Studio, gere um APK de teste pelo menu Build > Build Bundle(s) / APK(s) > Build APK(s).

## Próximas etapas de desenvolvimento
1. Persistência em banco remoto e autenticação.
2. Upload e armazenamento de mídia.
3. Geração de roteiros/legendas com IA.
4. Renderização MP4 com identidade visual, voz e áudio.
5. Painel de aprovação com registro auditável.
6. Integração oficial Instagram Graph/API e agendador backend.
7. Publicação de teste somente após aprovação explícita.

## Identidade pré-configurada
- Marca: Vitrine do Jota
- Instagram: @vitrinedojota.rj
- WhatsApp: +55 (21) 97292-7109
- Cores: preto e azul neon
- Horários sugeridos: 12h30 e 19h30
- Meta editorial: 14 conteúdos por semana

## Gerar APK pelo celular usando GitHub Actions

Este pacote inclui um fluxo de compilação na nuvem. Assim, não é necessário instalar Android Studio no celular.

1. Crie uma conta no GitHub e um repositório novo.
2. Envie todos os arquivos desta pasta para o repositório (incluindo a pasta `.github`).
3. No repositório, abra a aba **Actions**.
4. Escolha **Gerar APK Android** e toque em **Run workflow**.
5. Quando a execução terminar, abra a execução concluída e baixe o artefato **vitrine-do-jota-apk**.
6. Extraia o ZIP baixado e instale `app-debug.apk` no Android. O sistema poderá pedir autorização para instalar apps dessa fonte.

O APK gerado é uma versão de teste/debug. Para distribuir publicamente na Play Store, será necessário gerar uma versão assinada de produção e cumprir os requisitos atuais da loja.
