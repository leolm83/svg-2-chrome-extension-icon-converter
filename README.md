# Chrome Extension Icon Generator

![Licença](https://img.shields.io/badge/license-MIT-blue.svg)
![JavaScript](https://img.shields.io/badge/javascript-pure-yellow.svg)
![Plataforma](https://img.shields.io/badge/platform-browser--based-brightgreen.svg)

Uma ferramenta web utilitária, minimalista e de alta performance voltada para desenvolvedores. Ela permite converter arquivos vetoriais **SVG** nos tamanhos exatos de ícones em formato **PNG** exigidos pela Google Chrome Web Store e pelo ecossistema de extensões (Manifest V3), empacotando tudo em um único arquivo `.ZIP`.

Todo o processamento é feito diretamente no navegador do usuário (Client-Side) utilizando recursos nativos.

---

## 🌐 Demonstração Online

A ferramenta está hospedada e pronta para uso em:  
👉 **[https://leolm83.github.io/svg-2-chrome-extension-icon-converter/](https://leolm83.github.io/svg-2-chrome-extension-icon-converter/)**

---

## 🚀 Recursos

- **Conversão Inteligente:** Utiliza a API do HTML5 Canvas com amostragem bilinear de alta qualidade (`imageSmoothingQuality: 'high'`) para reduzir os vetores sem serrilhados bruscos.
- **Nomenclatura Padrão de Mercado:** Os arquivos já são gerados com os nomes exatos mapeados no ecossistema Chromium (`icon16.png`, `icon32.png`, `icon48.png` e `icon128.png`).
- **Download Unificado (.ZIP):** Agrupa todos os formatos gerados e exporta em um único arquivo compactado instantaneamente usando a biblioteca `JSZip`.
- **UI Responsiva e Acessível (A11y):** Interface moderna construída com CSS Grid, variáveis nativas (Design Tokens) e suporte completo a interações via teclado (`Enter` / `Espaço`) e Drag and Drop.
- **Zero Dependências de Servidor:** Um único arquivo HTML autônomo. Sem necessidade de Node.js, compilações ou comandos `npm install`.

---

## 📐 Tamanhos Gerados & Casos de Uso

A ferramenta gera os quatro formatos essenciais recomendados pelo Google:

| Nome do Arquivo | Resolução | Caso de Uso principal no Chrome |
| :--- | :--- | :--- |
| `icon16.png` | 16 x 16 px | Favicon em páginas internas da extensão e ícone de menu de contexto. |
| `icon32.png` | 32 x 32 px | Otimização visual para telas de computadores Windows. |
| `icon48.png` | 48 x 48 px | Exibição na página de gerenciamento de extensões (`chrome://extensions`). |
| `icon128.png` | 128 x 128 px | Exibição durante a instalação e destaque na listagem da Chrome Web Store. |

---

## 🛠️ Como Usar

Você pode utilizar a ferramenta de duas formas:

### Opção 1: Uso Online (Recomendado)
1. Acesse a [versão web da ferramenta](https://leolm83.github.io/svg-2-chrome-extension-icon-converter/).

### Opção 2: Uso Local
1. Baixe ou copie o código do arquivo `index.html`.
2. Dê um duplo clique no arquivo `index.html` para abri-lo em qualquer navegador moderno (Chrome, Edge, Firefox, Brave, Safari).

### Passos na Interface:
1. Arraste seu arquivo `.svg` para a área demarcada ou clique nela para selecionar o arquivo.
2. Visualize os resultados no grid quadriculado (que valida a transparência alpha do PNG).
3. Clique em **"Baixar Todos (.ZIP)"** ou baixe os formatos individualmente através dos botões de cada card.

---

## 📂 Integração no `manifest.json`

Após extrair o arquivo `.zip` gerado dentro da pasta raiz da sua extensão do Chrome, basta mapear os ícones no seu arquivo de manifesto da seguinte forma:

```json
{
  "manifest_version": 3,
  "name": "Nome da Sua Extensão",
  "version": "1.0.0",
  "icons": {
    "16": "icon16.png",
    "32": "icon32.png",
    "48": "icon48.png",
    "128": "icon128.png"
  },
  "action": {
    "default_icon": {
      "16": "icon16.png",
      "32": "icon32.png"
    }
  }
}