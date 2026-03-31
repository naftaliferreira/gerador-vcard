# gerador-vcard

# 📇 Gerador de vCard

Aplicação web estática para gerar arquivos de contato `.vcf` (vCard 3.0) diretamente no navegador, sem dependências externas e sem envio de dados para servidores.

---

## ✨ Funcionalidades

- Geração de arquivo `.vcf` compatível com **iOS, Android e Outlook**
- Download automático com o nome do contato como nome do arquivo
- Campos opcionais omitidos automaticamente do vCard quando não preenchidos
- Feedback visual inline (sem `alert()`)
- Suporte a submissão pelo teclado com **Enter**

---

## 🗂️ Campos suportados

| Campo | Obrigatório | Propriedade vCard |
|---|---|---|
| Nome completo | ✅ | `FN` |
| Telefone | ✅ | `TEL` |
| Email | — | `EMAIL` |
| Empresa | — | `ORG` |
| Cargo | — | `TITLE` |

---

## 🚀 Como usar

Nenhuma instalação necessária. Basta abrir o arquivo no navegador:

```bash
# Clone ou baixe o repositório, então abra diretamente:
open vcard-generator.html
```

Ou acesse via servidor local:

```bash
npx serve .
# ou
python -m http.server 8080
```

---

## 🏗️ Estrutura do projeto

```
vcard-generator.html   # Aplicação completa (HTML + CSS + JS em arquivo único)
README.md
```

Toda a lógica está contida em um único arquivo HTML autocontido. As únicas dependências externas são as fontes do Google Fonts (carregadas via CDN, sem impacto funcional se offline).

---

## 🧩 Arquitetura do JavaScript

O código é dividido em três funções com responsabilidade única:

```
gerarVCard()             → orquestra validação e dispara o download
gerarConteudoVCard()     → monta a string no formato vCard 3.0
baixarArquivo()          → cria o Blob e aciona o download via <a>
```

---

## 📐 Formato do arquivo gerado

O arquivo segue a especificação [vCard 3.0 (RFC 2426)](https://datatracker.ietf.org/doc/html/rfc2426), com quebras de linha `\r\n`:

```
BEGIN:VCARD
VERSION:3.0
FN:Maria Silva
TEL:+55 31 99999-0000
EMAIL:maria@empresa.com
ORG:Empresa Ltda
TITLE:Designer
END:VCARD
```

---

## 🎨 Design

- **Tema:** escuro, minimalista, estilo terminal
- **Tipografia:** DM Serif Display (títulos) + DM Mono (interface)
- **Paleta:** fundo `#0e0e0e` com acento verde-lima `#c8f060`
- **CSS Variables** para consistência e fácil customização

---

## 🌐 Compatibilidade

| Plataforma | Suporte |
|---|---|
| iOS (Contatos) | ✅ |
| Android (Contatos) | ✅ |
| Microsoft Outlook | ✅ |
| Google Contacts | ✅ |
| macOS Contatos | ✅ |

> Requer navegador moderno com suporte a `Blob`, `URL.createObjectURL` e ES6+.

---

## 📄 Licença

MIT — livre para uso, modificação e distribuição.