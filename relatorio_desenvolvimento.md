# Relatório de Desenvolvimento: Arquitetura de Impérios

## 1. Visão Geral do Projeto
O projeto **Arquitetura de Impérios** foi desenvolvido como uma Landing Page (Single Page Application) focada em conversão, apresentação de serviços de crescimento, mídia e escala. A página foi estruturada para entregar alta performance, design premium (focado em tons de preto e dourado) e interações dinâmicas, mantendo um código limpo e de fácil manutenção.

## 2. Tecnologias Utilizadas
A abordagem escolhida para este projeto priorizou a **ausência de dependências externas** (Zero Dependencies) para garantir o carregamento instantâneo da página:
- **HTML5 Semântico:** Estruturação clara do conteúdo, favorecendo acessibilidade e SEO.
- **CSS3 (Vanilla):** Utilização intensiva de variáveis CSS (CSS Custom Properties) para gerenciar o design system de forma centralizada (cores, sombras, espaçamentos). O design inclui micro-animações, efeitos "glassmorphism", gradientes refinados e backgrounds dinâmicos. Não foram utilizados frameworks como Tailwind ou Bootstrap.
- **JavaScript (Vanilla):** Toda a lógica de interatividade, incluindo o sistema de internacionalização (i18n), validação do formulário, controle do modal e geração de links, foi escrita em JS puro.

## 3. Estrutura do Código e Facilidade de Manutenção
O arquivo principal `index.html` contém tudo o que é necessário para a página funcionar (HTML, CSS em `<style>` e JS em `<script>`). Isso facilita a edição pontual, pois todas as referências estão no mesmo contexto.

### 3.1. Design System e Estilização
As principais cores e métricas de design estão armazenadas na raiz do CSS (`:root`). Para alterar a paleta de cores ou arredondamento dos elementos, basta modificar estas variáveis:
```css
:root {
    --bg: #070606;
    --gold: #d6a84e;
    --text: rgba(255, 255, 255, .88);
    /* ... outras variaveis ... */
}
```

### 3.2. Sistema de Internacionalização (i18n)
O grande diferencial técnico deste projeto é o sistema embutido de tradução entre **Espanhol do Paraguai (es-PY)** e **Português do Brasil (pt-BR)**.
- **Como funciona:** O objeto JavaScript `I18N` contém dicionários para os idiomas suportados. Elementos HTML que precisam ser traduzidos possuem o atributo `data-i18n="chave_da_traducao"`. O script varre o DOM e substitui os textos dinamicamente com base na seleção do usuário, sem precisar recarregar a página.
- **Como adaptar/adicionar textos:** Para modificar uma tradução, basta ir à constante `I18N` no script e alterar o valor da chave correspondente nos objetos `es` e `pt`. Se precisar de um novo elemento traduzível, adicione `data-i18n="nova_chave"` na tag HTML e adicione a "nova_chave" nos dicionários.

### 3.3. Configurações Globais (WhatsApp, Links e Vídeo)
Para garantir manutenção facilitada por pessoas não técnicas (ou em edições rápidas), todas as configurações cruciais foram isoladas num objeto `CONFIG` no início do `<script>`:
```javascript
const CONFIG = {
    videoEmbed: "LINK_DO_YOUTUBE",
    heroFallbackUnsplash: "LINK_DA_IMAGEM",
    whatsapp: {
        phoneE164: "SEU_NUMERO_AQUI", // Ex: 5959XXXXXXXX (Paraguai) ou 55XXXXXXXX (Brasil)
        message_es: "Sua mensagem em Espanhol",
        message_pt: "Sua mensagem em Português"
    },
    instagramUrl: "LINK_DO_INSTAGRAM"
};
```

### 3.4. Geração Dinâmica de Mensagens (Formulário)
O formulário de aplicação capta as informações (Nome, Empresa, Segmento, Faturamento e Objetivo) e constrói dinamicamente um texto formatado para o WhatsApp, que respeita o idioma atual da página.

## 4. Próximos Passos e Adaptações
O estado atual do projeto é maduro e pronto para produção. Para futuras adaptações:
1. **Adição de Novas Seções:** Copie a estrutura `<section class="... reveal">` existente. Isso garante que a nova seção respeitará as animações de entrada ao rolar a página.
2. **Separação de Arquivos (Refatoração futura):** Caso o projeto cresça consideravelmente, o CSS e o JS podem ser extraídos para arquivos `.css` e `.js` separados, melhorando o cacheamento do navegador. No estágio atual (Landing Page única), a abordagem inline/single-file é mais vantajosa para velocidade de carregamento (menos requisições HTTP).
