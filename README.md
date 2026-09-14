# Arquitetura de Impérios

Landing Page de alta conversão para o projeto "Arquitetura de Impérios" (Sérgio Dias Filho - Crescimento, Mídia e Escala).

## 🚀 Tecnologias e Diferenciais em JavaScript (Vanilla)

Este projeto foi construído sem dependências externas, garantindo performance e carregamento instantâneos. Os maiores diferenciais técnicos implementados em **JavaScript Puro** incluem:

1. **Sistema de Internacionalização Dinâmico (i18n):**
   - O site possui tradução nativa e dinâmica do **Português do Brasil (pt-BR)** para o **Espanhol do Paraguai (es-PY)** (idioma padrão da página: `<html lang="es-PY">`).
   - A troca de idioma ocorre instantaneamente via DOM (utilizando atributos `data-i18n`), sem necessidade de recarregar a página, proporcionando uma experiência de usuário (UX) fluida e ininterrupta.

2. **Geração Inteligente de Mensagens para WhatsApp:**
   - O formulário de captura coleta os dados da empresa e monta uma mensagem estruturada e contextualizada.
   - O link do WhatsApp gerado adapta automaticamente a mensagem inicial de acordo com o idioma selecionado pelo usuário no momento do clique.

3. **Gerenciamento de Estado de UI:**
   - Controle simplificado e eficiente de modais de vídeo, menu lateral (drawer) para mobile e animações de revelação em scroll (`Reveal`), tudo isso feito nativamente sem onerar o navegador com bibliotecas pesadas.

## 🛠 Como Adaptar e Manter
O projeto foi desenhado para manutenção fácil:
- **Textos e Traduções:** Todos os textos estão centralizados no objeto `I18N` dentro do `<script>` do arquivo `index.html`.
- **Configurações Globais:** Links de redes sociais, vídeo e número de WhatsApp estão organizados na constante `CONFIG` logo no início do bloco de script.

> Para detalhes aprofundados sobre a arquitetura e manutenção, leia o arquivo [relatorio_desenvolvimento.md](./relatorio_desenvolvimento.md) anexo a este repositório.
