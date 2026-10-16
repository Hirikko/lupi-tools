# 🕹️ Lupi to Lupinho: Adaptadores de Compatibilidade

E aí! Seja bem-vindo ao repositório. 

Se você tá tentando rodar os seus jogos feitos para o console **Lupi** direto no simulador **Lupinho** no PC, esse kit de scripts em Lua vai te dar uma força. A ideia é servir de ponte entre os dois sistemas para fazer o código conversar sem travar.

---

## 🛠️ O que é cada arquivo? (Explicação rápida)

Aqui está o resumo direto do que cada um desses quatro arquivos faz no seu projeto:

1. **`btn.lua` (O Mapeador de Botões)**
   * **O que faz:** Centraliza e organiza todos os botões do controle (setinhas direcionais e botões de ação), mapeando as variáveis para que o jogo saiba exatamente o que você está apertando.

2. **`ui-adapter.lua` (O Tradutor de Inputs)**
   * **O que faz:** Gerencia os estados de até três jogadores diferentes (`0`, `1` e `2`) e traduz comandos textuais (tipo `"confirm"` ou `"left"`) para os botões reais do controle de forma fluida.

3. **`palt-hex-compat.lua` (O Conversor de Cores)**
   * **O que faz:** Converte códigos de cores tradicionais (como RGB ou hexadecimais `#RRGGBB`) para a paleta de cores oficial que o Lupinho reconhece, mantendo o visual do jogo intacto.

4. **`lupinho-compat.lua` (O Localizador de Sprites)**
   * **O que faz:** Dá uma super força na hora de buscar os gráficos/desenhos. Se o seu jogo tenta achar um sprite pelo caminho da pasta (ex: `"personagem/player"`), ele faz uma varredura recursiva na árvore de tabelas até achar o arquivo certo.

---

## ⚠️ AVISO IMPORTANTE: Vai funcionar de primeira?

Olha, **não dá para garantir que vai rodar 100% de cara em qualquer projeto**. 

Cada desenvolvedor tem um estilo único de codar, usa estruturas diferentes e acaba chamando funções de um jeito próprio. Nos nossos testes práticos com **18 jogos diferentes**:
* Cerca de **13 jogos funcionaram de primeira** só com os adaptadores.
* Alguns exigiram **pequenos ajustes no código** para encaixar nas funções.
* E alguns poucos **nem chegaram a abrir** (pedindo refatorações maiores).

Então encare esses arquivos como uma base sólida, mas esteja pronto para meter a mão na massa se o seu jogo tiver alguma particularidade!

---

## 🚀 Como instalar e usar no seu projeto

### 1. Coloque os arquivos na raiz
Jogue os quatro arquivos (`btn.lua`, `ui-adapter.lua`, `palt-hex-compat.lua` e `lupinho-compat.lua`) direto na **pasta raiz** do seu projeto, junto com o seu arquivo principal.

### 2. Adicione os requires no `main.lua`
No início do seu `main.lua`, você precisa importar todos eles para carregar as funções de adaptação. Faça assim:

```lua
-- Carregando os adaptadores de compatibilidade do Lupi para o Lupinho
local BTN = require("btn")
local Input = require("ui-adapter")
local Palette = require("palt-hex-compat")
require("lupinho-compat")
```

Pronto! Agora é testar no Lupinho e ver o que rola. Bom projeto e bom código! ⚡
