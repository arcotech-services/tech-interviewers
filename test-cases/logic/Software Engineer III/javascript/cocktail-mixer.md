**Problema: Cocktail Mixer**

Você está desenvolvendo um sistema para otimizar a mistura de diferentes ingredientes para criar o coquetel perfeito. Cada ingrediente tem um valor específico de sabor e o coquetel deve ter um valor máximo de sabor sem exceder uma quantidade máxima permitida.

**Entrada:**
- Uma lista de objetos, cada um representando um ingrediente com os seguintes atributos: `nome` (string), `sabor` (inteiro), e `quantidade` (inteiro).
- Um número máximo de quantidade permitida para o coquetel.

**Saída:**
- A combinação de ingredientes que maximiza o valor total de sabor sem exceder a quantidade máxima permitida.

**Exemplo:**p
```javascript
const ingredientes = [
  { nome: 'Gin', sabor: 8, quantidade: 5 },
  { nome: 'Vermouth', sabor: 7, quantidade: 4 },
  { nome: 'Lemon', sabor: 3, quantidade: 2 },
  { nome: 'Sugar', sabor: 5, quantidade: 3 }
];

const maxQuantidade = 8;

function otimizarCoquetel(ingredientes, maxQuantidade) {
  // Solução a ser implementada
}

console.log(otimizarCoquetel(ingredientes, maxQuantidade));
// Saída esperada: combinação ótima de ingredientes com máximo sabor
```

[clique aqui para ter acesso a lista de cocktails](https://gist.githubusercontent.com/MatheusKindrazki/49ec156db487d66ba5234077614b6e7a/raw/6715e7f51150d6f0623ca2b432770164f41c4109/cocktail-mixer-data.json)

### Regras Adicionais:

Para tornar o desafio mais realista e avaliar a solução de maneira abrangente, as seguintes regras e restrições devem ser consideradas ao desenvolver sua solução:

1. **Processamento em Blocos:**
   - O algoritmo deve processar os ingredientes em blocos de tamanho 5. Isso significa que você não deve carregar todos os ingredientes na memória ao mesmo tempo. Isso simula trabalhar com conjuntos de dados grandes e ajuda a testar sua capacidade de otimizar o uso da memória.

2. **Tempo Máximo de Execução:**
   - A execução do algoritmo deve ser concluída em menos de 100ms para uma lista de 100 ingredientes. Utilize ferramentas de medição como `console.time()` para verificar o tempo de execução e otimizar seu código conforme necessário.

3. **Limite de Complexidade:**
   - Antes de começar a codificar, avalie a complexidade algorítmica esperada e garanta que sua solução não exceda O(n log n). Isso desafia você a projetar uma solução eficiente que lida bem com o crescimento dos dados.

4. **Persistência de Estado:** *(opcional)*
   - Projete a solução de forma que, se o processamento for interrompido, ela possa retomar de onde parou sem precisar reiniciar. Isso verifica sua habilidade de implementar uma solução robusta que mantém o estado entre execuções.

5. **Saída Detalhada:** *(opcional)*
   - Além de mostrar a combinação ideal de ingredientes, forneça um relatório sobre o tempo de execução, quantidade de memória usada e a complexidade do algoritmo. Isso ajuda a refletir sobre o impacto de sua solução nos recursos do sistema.
