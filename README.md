# Trilha JS Developer - Pokedex

Vamos passar por cada parte do código:

### **1. `index.html`**
Este é o arquivo HTML principal que define a estrutura da página da Pokédex. Abaixo, explico cada parte:

- **`<!DOCTYPE html>`**: Declaração que informa ao navegador que este é um documento HTML5.
- **`<html lang="pt-BR">`**: Define o idioma como português do Brasil.
- **`<meta charset="UTF-8" />`**: Define a codificação de caracteres como UTF-8, garantindo suporte a caracteres especiais.
- **`<meta name="viewport" content="width=device-width, initial-scale=1.0" />`**: Garante que a página seja responsiva e se adapte a diferentes tamanhos de tela.
- **`<title>Pokédex</title>`**: Define o título da página.
- **Normalize CSS**: Um arquivo CSS externo que "normaliza" o estilo padrão dos navegadores, criando uma base consistente para o estilo da página.
- **Font Roboto**: Faz a inclusão da fonte Roboto de forma assíncrona, que será usada nos textos da página.
- **Nosso CSS**: Inclui dois arquivos CSS locais para estilização: `global.css` (estilos globais) e `pokedex.css` (estilos específicos para a Pokédex).
- **`<section class="content">`**: Um container que envolve o conteúdo da Pokédex.
  - **`<h1>`**: Título da Pokédex.
  - **`<ol id="pokemonList" class="pokemons">`**: Uma lista ordenada que será preenchida com os Pokémons.
  - **Botão de "Load More"**: Carrega mais Pokémons ao clicar.
- **JS**: Importa três arquivos JavaScript: `pokemon-model.js` (define a classe `Pokemon`), `poke-api.js` (faz as chamadas à API de Pokémons) e `main.js` (lógica de carregamento dos Pokémons na página).

### **2. `main.js`**
Este arquivo controla a lógica da aplicação. Explicação por partes:

- **`pokemonList`** e **`loadMoreButton`**: Seleciona o elemento da lista de Pokémons e o botão de "Load More".
- **`maxRecords`**: Define o número máximo de registros de Pokémons (151, referentes aos Pokémons da primeira geração).
- **`limit`** e **`offset`**: Controlam a quantidade de Pokémons carregados por vez (10) e o deslocamento para a próxima "página".
- **`convertPokemonToLi(pokemon)`**: Converte um objeto Pokémon para um item de lista (`<li>`) em HTML, que inclui o número, nome, tipos e uma imagem.
- **`loadPokemonItens(offset, limit)`**: Chama a função `pokeApi.getPokemons` para buscar os Pokémons da API e atualiza a lista (`pokemonList`) com os dados retornados.
- **Evento do botão "Load More"**: Atualiza o `offset` e carrega mais Pokémons. Se o número total de registros ultrapassar `maxRecords`, o botão é removido.

### **3. `poke-api.js`**
Este arquivo contém as funções para interagir com a API de Pokémons. Explicação:

- **`convertPokeApiDetailToPokemon(pokeDetail)`**: Converte os dados da API para uma instância da classe `Pokemon`. Extrai o número, nome, tipos e a foto do Pokémon.
- **`pokeApi.getPokemonDetail(pokemon)`**: Faz uma chamada `fetch` para a API para buscar os detalhes de um Pokémon específico.
- **`pokeApi.getPokemons(offset, limit)`**: Busca uma lista de Pokémons com base no `offset` e `limit`. Para cada Pokémon, faz uma chamada individual para obter os detalhes usando `getPokemonDetail`.

### **4. `pokemon-model.js`**
Este arquivo define a classe `Pokemon`, que será usada para armazenar e organizar as informações de cada Pokémon.

- **`Pokemon`**: A classe possui propriedades como `number`, `name`, `type`, `types` (um array de tipos) e `photo` (imagem).

### **5. `global.css`**
Define os estilos globais da página.

- **`* { ... }`**: Define o uso da fonte Roboto e ajusta o comportamento de alguns elementos como `box-sizing` e `max-width`.
- **`body`**: Define o fundo do corpo da página.
- **`.content`**: Configura o tamanho e o estilo do container principal, tornando-o responsivo (via media queries) e adaptável a diferentes larguras de tela.

### **6. `pokedex.css`**
Este arquivo estiliza especificamente os elementos da Pokédex.

- **`.pokemons`**: Define um layout em grid para os itens da lista de Pokémons. O número de colunas varia conforme a largura da tela (via media queries).
- **Classes de Tipos** (ex: `.grass`, `.fire`, etc.): Cada tipo de Pokémon tem uma cor de fundo específica, representando seu tipo (grama, fogo, água, etc.).
- **`.pokemon`**: Define o layout de cada card de Pokémon, incluindo margens, bordas arredondadas e o estilo para número e nome.
- **`.pagination`**: Estiliza o container do botão "Load More", centralizando-o.
- **Media Queries**: Adaptam a quantidade de colunas na grid conforme o tamanho da tela (1 coluna em telas pequenas, até 4 colunas em telas grandes).

### **Conclusão**
O projeto é bem estruturado, separando HTML, CSS e JavaScript de forma modular. Cada arquivo tem sua função clara:
- `index.html`: Estrutura da página.
- `main.js`: Controle da lógica de carregamento dos Pokémons.
- `poke-api.js`: Comunicação com a API de Pokémons.
- `pokemon-model.js`: Define o modelo de dados para os Pokémons.
- `global.css`: Estilos globais e responsividade.
- `pokedex.css`: Estilos específicos da Pokédex e seus itens (Pokémons).

Isso tudo cria uma aplicação Pokédex dinâmica, capaz de carregar e exibir os Pokémons em lotes, conforme o usuário navega pela página.
