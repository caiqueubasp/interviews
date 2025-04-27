1 - Semantico: Nao
2 - Box Model, Especificidade, SaaS: Nao
3 - Map, Filter, Reduce: OK
4 - Framework, Vue, React, Angular: OK
5 - Composition API: Nao
6 - TESTE: Nao
7 - Composable: Nao
8 - Git: Nao
9 - Acessibilidade: Nao
11 - IA - Qual ferramenta de ia vc usa? Como isso tem te ajudado?

# PERGUNTAS DA ENTREVISTA (FRONTEND JUNIOR)

## HTML

# Pergunta:
O que é HTML semântico e por que ele é importante no desenvolvimento web?

Resposta:
HTML semântico refere-se ao uso de tags que descrevem claramente o propósito do conteúdo. Por exemplo, usar <header> para cabeçalhos, <article> para artigos, e <footer> para rodapés. Isso melhora a acessibilidade, SEO e facilita a manutenção do código.

Exemplo:

Semântico:

Semântico:

```html
<article>
    <h1>Título do Artigo</h1>
    <p>Conteúdo do artigo.</p>
</article>
```

Não Semântico:

```html
<div>
  <h1>Título do Artigo</h1>
  <p>Conteúdo do artigo.</p>
</div>
```

O primeiro exemplo ajuda navegadores e leitores de tela a entenderem melhor o conteúdo.

--------------------------------------------------------------------------------

# Pergunta:
O que é o Box Model no CSS e como ele influencia o layout de uma página?

Resposta:
O Box Model é um conceito fundamental no CSS que define como os elementos são renderizados na página. Cada elemento é representado como uma caixa retangular composta por quatro áreas: content, padding, border e margin.

Estrutura do Box Model:

Content: Área onde o conteúdo (texto, imagens) é exibido.
Padding: Espaço entre o conteúdo e a borda.
Border: Contorno ao redor do padding.
Margin: Espaço externo entre o elemento e outros elementos.
Exemplo:

```html
<div style="width: 200px; padding: 10px; border: 5px solid black; margin: 20px;">
  Caixa de Exemplo
</div>
```

Cálculo do tamanho total:

Largura total = content + padding + border + margin.
No exemplo acima:
Content: 200px
Padding: 10px (esquerda + direita = 20px)
Border: 5px (esquerda + direita = 10px)
Margin: 20px (esquerda + direita = 40px)
Total: 270px de largura.

O Box Model é essencial para ajustar o layout e evitar problemas de espaçamento entre elementos.

--------------------------------------------------------------------------------

# Pergunta:
O que é especificidade no CSS e como ela influencia a aplicação de estilos?

Resposta:
Especificidade é o mecanismo que o CSS usa para determinar qual regra será aplicada quando múltiplas regras se aplicam ao mesmo elemento. Ela é calculada com base no tipo de seletor utilizado.

Regras de especificidade:

Inline styles (ex.: style="color: red;") têm a maior prioridade.
IDs (#id) têm mais peso que classes ou elementos.
Classes, pseudo-classes (:hover), e atributos ([type="text"]) têm menos peso que IDs.
Elementos (div, p, h1) e pseudo-elementos (::before, ::after) têm o menor peso.
Exemplo:


```css

/* Especificidade: 0, 0, 1, 0 */
p {
  color: blue;
}

/* Especificidade: 0, 0, 2, 0 */
p.highlight {
  color: green;
}

/* Especificidade: 0, 1, 0, 0 */
#main p {
  color: red;
}

```

Resultado:

Um <p> simples será azul.
Um <p class="highlight"> será verde.
Um <p> dentro de um elemento com id="main" será vermelho.
Dica:
Evite usar muitos seletores com alta especificidade (como IDs) para facilitar a manutenção do código. Use classes sempre que possível.

A ordem de força da especificidade no CSS, do maior para o menor, é a seguinte:

Inline styles (ex.: style="color: red;")

Especificidade: 1, 0, 0, 0
IDs (ex.: #id)

Especificidade: 0, 1, 0, 0
Classes, pseudo-classes (ex.: :hover), e atributos (ex.: [type="text"])

Especificidade: 0, 0, 1, 0
Elementos (ex.: div, p, h1) e pseudo-elementos (ex.: ::before, ::after)

Especificidade: 0, 0, 0, 1
Nota: Quanto maior a especificidade, maior a prioridade da regra CSS aplicada.

---------------------------------------------------------------------------

# Pergunta:
O que é Sass e quais são suas principais vantagens em relação ao CSS tradicional?

Resposta:
Sass (Syntactically Awesome Stylesheets) é um pré-processador CSS que adiciona funcionalidades como variáveis, aninhamento, mixins e herança, tornando o desenvolvimento de estilos mais eficiente e organizado.

Principais vantagens:

Variáveis: Permitem armazenar valores reutilizáveis.

```scss

$primary-color: #3498db;

body {
  background-color: $primary-color;
}

```

Aninhamento: Facilita a leitura e organização do código.

```scss

nav {
  ul {
    li {
      a {
        color: #333;
      }
    }
  }
}

```

Mixins: Reutilizam blocos de código.

```scss

@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  @include flex-center;
}

```

Herança: Compartilha estilos entre seletores.

```scss

%button-style {
  padding: 10px;
  border-radius: 5px;
}

.btn-primary {
  @extend %button-style;
  background-color: blue;
}

```

Uso:
Sass é ideal para projetos grandes, onde a organização e reutilização de estilos são essenciais. Ele é compilado para CSS antes de ser usado no navegador.

---------------------------------------------------------------------------

# Pergunta:

Qual é a diferença entre os métodos .forEach(), .map(), .filter(), .reduce() e .find() no JavaScript?

Resposta:
.forEach()

Executa uma função para cada elemento do array, mas não retorna um novo array.


```js

const arr = [1, 2, 3];
arr.forEach(num => console.log(num * 2)); // 2, 4, 6

```

.map()

Cria um novo array com os resultados da função aplicada a cada elemento.

```js

const arr = [1, 2, 3];
const doubled = arr.map(num => num * 2);
console.log(doubled); // [2, 4, 6]

```

.filter()

Cria um novo array com os elementos que atendem a uma condição.
Exemplo:

```js

const arr = [1, 2, 3, 4];
const evens = arr.filter(num => num % 2 === 0);
console.log(evens); // [2, 4]

```

.reduce()

Reduz o array a um único valor, acumulando os resultados.
Exemplo:

```js

const arr = [1, 2, 3, 4];
const sum = arr.reduce((acc, num) => acc + num, 0);
console.log(sum); // 10

```

.find()

Retorna o primeiro elemento que atende a uma condição.
Exemplo:


```js

const arr = [1, 2, 3, 4];
const firstEven = arr.find(num => num % 2 === 0);
console.log(firstEven); // 2

```

Resumo:

Use .forEach() para iterar sem criar um novo array.
Use .map() para transformar elementos e criar um novo array.
Use .filter() para selecionar elementos com base em uma condição.
Use .reduce() para calcular um único valor (ex.: soma, média).
Use .find() para localizar o primeiro elemento que atende a uma condição.

---------------------------------------------------------------------------

# Pergunta:

O que é a Composition API no Vue.js e quais são suas vantagens em relação à Options API?

Resposta:
A Composition API é uma abordagem introduzida no Vue 3 que permite organizar o código de forma mais flexível e reutilizável, utilizando funções para compor a lógica de componentes.

Principais vantagens:

Melhor organização:

Permite agrupar lógica relacionada em funções reutilizáveis, facilitando a manutenção.
Exemplo:

```js

import { ref } from 'vue';

export default {
  setup() {
    const count = ref(0);
    const increment = () => count.value++;
    return { count, increment };
  },
};

```

Reutilização de lógica:

Composables podem ser criados para compartilhar lógica entre componentes.

Exemplo:

```js

// useCounter.js
import { ref } from 'vue';

export function useCounter() {
  const count = ref(0);
  const increment = () => count.value++;
  return { count, increment };
}


// Componente
import { useCounter } from './useCounter';

export default {
  setup() {
    const { count, increment } = useCounter();
    return { count, increment };
  },
};

```

Melhor suporte para TypeScript:

A Composition API facilita o uso de tipagem estática, tornando o código mais robusto.
Diferença para a Options API:

Na Options API, a lógica é separada por opções (data, methods, computed), o que pode dificultar a leitura em componentes grandes.
Na Composition API, a lógica é agrupada por funcionalidade, tornando o código mais modular e reutilizável.
Quando usar:

Use a Composition API em projetos que exigem lógica complexa ou reutilização de código. Para projetos simples, a Options API ainda é válida.


---------------------------------------------------------------------------

# Pergunta:

O que são Composables no Vue.js e como eles são usados?

Resposta:
Composables são funções reutilizáveis criadas com a Composition API no Vue.js. Elas permitem encapsular e compartilhar lógica entre componentes de forma eficiente.

```js

// useCounter.js
import { ref } from 'vue';

export function useCounter() {
  const count = ref(0);
  const increment = () => count.value++;
  const decrement = () => count.value--;
  return { count, increment, decrement };
}

```

```js

<script>
import { useCounter } from './useCounter';

export default {
  setup() {
    const { count, increment, decrement } = useCounter();
    return { count, increment, decrement };
  },
};
</script>

<template>
  <div>
    <p>Contador: {{ count }}</p>
    <button @click="increment">Incrementar</button>
    <button @click="decrement">Decrementar</button>
  </div>
</template>

```

Vantagens dos Composables:

Reutilização de lógica:

Permite compartilhar lógica entre diferentes componentes sem duplicação de código.
Organização:

Ajuda a separar a lógica de negócios do código do componente, tornando-o mais limpo e fácil de manter.
Flexibilidade:

Pode ser usado em qualquer componente que utilize a Composition API.
Dica:
Use Composables para lógica que será reutilizada em vários componentes, como manipulação de estado, chamadas de API ou interações com o DOM.

```js

// useCounter.js
import { ref } from 'vue';

export function useCounter() {
  const count = ref(0);
  const increment = () => count.value++;
  const decrement = () => count.value--;
  return { count, increment, decrement };
}

```


---------------------------------------------------------------------------


# Pergunta:

O que é o Jest e como o Vue Test Utils pode ser usado para testar componentes Vue?

Resposta:
Jest:
Jest é um framework de testes em JavaScript que permite criar testes unitários, de integração e de snapshot. Ele é amplamente utilizado por sua simplicidade e suporte nativo a mocks, spies e cobertura de código.

Vue Test Utils:
Vue Test Utils é uma biblioteca oficial para testar componentes Vue. Ela fornece ferramentas para montar componentes, interagir com eles e verificar seu comportamento.


```js

<!-- HelloWorld.vue -->
<template>
  <div>
    <p>{{ message }}</p>
    <button @click="updateMessage">Clique aqui</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "Olá, mundo!",
    };
  },
  methods: {
    updateMessage() {
      this.message = "Mensagem atualizada!";
    },
  },
};
</script>

```

```js

// HelloWorld.spec.js
import { mount } from "@vue/test-utils";
import HelloWorld from "@/components/HelloWorld.vue";

describe("HelloWorld.vue", () => {
  it("exibe a mensagem inicial", () => {
    const wrapper = mount(HelloWorld);
    expect(wrapper.text()).toContain("Olá, mundo!");
  });

  it("atualiza a mensagem ao clicar no botão", async () => {
    const wrapper = mount(HelloWorld);
    await wrapper.find("button").trigger("click");
    expect(wrapper.text()).toContain("Mensagem atualizada!");
  });
});

```

Vantagens do Jest e Vue Test Utils:

Jest:

Rápido e fácil de configurar.
Suporte a mocks e spies nativo.
Geração de relatórios de cobertura de código.
Vue Test Utils:

Permite montar componentes para testes.
Simula interações do usuário, como cliques e eventos.
Verifica o estado e as propriedades dos componentes.
Dica:
Use Jest com Vue Test Utils para garantir que seus componentes Vue funcionem corretamente em diferentes cenários.


---------------------------------------------------------------------------

# Pergunta:
O que é Git Flow e como ele organiza o fluxo de trabalho em um repositório?

Resposta:

Git Flow é uma estratégia de ramificação (branching) para organizar o fluxo de trabalho em projetos Git. Ele define um conjunto de regras para criar, gerenciar e mesclar branches, facilitando o desenvolvimento colaborativo e o controle de versões.

Branches principais:

main (ou master): Contém o código de produção estável. Apenas versões finalizadas e testadas são mescladas aqui.
develop: Contém o código em desenvolvimento. Serve como base para novas funcionalidades e integrações.
Branches temporários:

Feature branches:
Usados para desenvolver novas funcionalidades.
Criados a partir de develop e mesclados de volta quando concluídos.
Exemplo: git checkout -b feature/nova-funcionalidade develop.
Release branches:
Usados para preparar uma nova versão de produção.
Criados a partir de develop e mesclados em main e develop após o lançamento.
Exemplo: git checkout -b release/1.0 develop.
Hotfix branches:
Usados para corrigir problemas críticos em produção.
Criados a partir de main e mesclados em main e develop.
Exemplo: git checkout -b hotfix/corrigir-bug main.
Fluxo básico:

Desenvolver novas funcionalidades em feature branches.
Preparar versões em release branches.
Corrigir bugs críticos em hotfix branches.
Vantagens:

Organização clara do desenvolvimento.
Separação entre código em desenvolvimento e produção.
Facilita o trabalho em equipe e o controle de versões.


-------------------------------------------------------------------------

# Pergunta:

Qual é a diferença entre git rebase e git merge?

Resposta:
git merge:

Combina duas branches criando um commit de merge.
Mantém o histórico completo, incluindo todos os commits das branches envolvidas.
Exemplo:

```bash
git checkout feature
git merge main
```

Resultado: Um novo commit de merge é criado.

Vantagens:

Preserva o histórico completo do projeto.
Útil para projetos onde o histórico detalhado é importante.

Desvantagens:

O histórico pode ficar poluído com muitos commits de merge.

Quando usar:

Use merge quando quiser preservar o histórico completo do projeto.
Use rebase para criar um histórico mais limpo, especialmente em branches locais antes de compartilhar o código.
Dica:
Evite usar rebase em branches que já foram enviadas para o repositório remoto, pois isso pode causar conflitos para outros desenvolvedores.

-------------------------------------------------------------------------

# Pergunta:
O que é acessibilidade no desenvolvimento web e como o conceito de mobile first se aplica ao design responsivo?

Resposta:
Acessibilidade:
Acessibilidade no desenvolvimento web significa criar interfaces que possam ser usadas por todas as pessoas, incluindo aquelas com deficiências visuais, auditivas, motoras ou cognitivas.

Boas práticas de acessibilidade:

Uso de tags semânticas:
Exemplo: <header>, <main>, <footer> ajudam leitores de tela a entender a estrutura da página.
Textos alternativos (alt):
Adicione descrições em imagens para usuários com leitores de tela.
Exemplo:


```html
<img src="imagem.jpg" alt="Descrição da imagem">
```

Contraste de cores:
Certifique-se de que o texto seja legível para pessoas com daltonismo ou baixa visão.
Use ferramentas como WebAIM Contrast Checker.
Navegação por teclado:
Garanta que todos os elementos interativos (botões, links) possam ser acessados sem mouse.
Exemplo: Use tabindex para ajustar a ordem de navegação.

Mobile First:
O conceito de mobile first prioriza o design e desenvolvimento para dispositivos móveis antes de adaptá-lo para telas maiores (como desktops).

Por que usar mobile first?

```css

body {
  font-size: 16px; /* Estilo padrão para mobile */
}

@media (min-width: 768px) {
  body {
    font-size: 18px; /* Estilo para tablets e desktops */
  }
}

```

A maioria dos usuários acessa a web por dispositivos móveis.
Garante uma experiência otimizada em telas menores.
Como aplicar mobile first:

Escreva estilos para dispositivos móveis primeiro:

Use media queries para adicionar estilos para telas maiores.
Exemplo:
Simplifique o layout:

Priorize conteúdo essencial e navegação simples para telas pequenas.
Dica:
Combine acessibilidade e mobile first para criar experiências inclusivas e responsivas, garantindo que todos os usuários possam acessar e interagir com o conteúdo, independentemente do dispositivo ou das limitações.