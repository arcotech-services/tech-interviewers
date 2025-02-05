## Problema: Sales Aggregator

Você está desenvolvendo um sistema para processar registros de vendas. Cada registro de venda é um objeto com os seguintes atributos:
- **produto** (string)
- **quantidade** (inteiro)
- **valor** (float)

O objetivo é agrupar os registros de vendas por produto, somando a quantidade total e o valor total para cada produto.

### Entrada:
- Uma lista de objetos, cada um representando um registro de venda com os atributos: `produto`, `quantidade` e `valor`.

### Saída:
- Um objeto (ou array) que apresenta, para cada produto, a soma total de `quantidade` e o total de `valor` das vendas.

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar os registros em blocos de tamanho 10, simulando cenários onde nem todos os dados estão disponíveis de uma vez.
2. **Tempo Máximo de Execução:**
   - A execução do algoritmo deve ser concluída em menos de 100ms para uma lista de 100 registros. Utilize `console.time()` e `console.timeEnd()` para medir o tempo de execução.
3. **Limite de Complexidade:**
   - Garanta que sua solução seja O(n), processando cada registro uma única vez.
4. **Persistência de Estado (Opcional):**
   - Projete a solução de forma que, caso o processamento seja interrompido, ela possa retomar de onde parou.
5. **Saída Detalhada (Opcional):**
   - Além da agregação, forneça um relatório com métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const vendas = [
  { produto: 'Notebook', quantidade: 2, valor: 2500.00 },
  { produto: 'Mouse', quantidade: 5, valor: 150.00 },
  { produto: 'Notebook', quantidade: 1, valor: 2500.00 },
  { produto: 'Teclado', quantidade: 3, valor: 300.00 },
  { produto: 'Mouse', quantidade: 2, valor: 150.00 },
  // ...outros registros...
];

function agruparVendas(vendas) {
  // Inicializa o objeto de agregação
  const resultado = {};

  // Função auxiliar para processar um bloco de registros
  const processarBloco = (bloco) => {
    bloco.forEach(registro => {
      const { produto, quantidade, valor } = registro;
      if (!resultado[produto]) {
        resultado[produto] = { totalQuantidade: 0, totalValor: 0 };
      }
      resultado[produto].totalQuantidade += quantidade;
      resultado[produto].totalValor += valor;
    });
  };

  // Processar os registros em blocos de tamanho 10
  const tamanhoBloco = 10;
  for (let i = 0; i < vendas.length; i += tamanhoBloco) {
    const bloco = vendas.slice(i, i + tamanhoBloco);
    processarBloco(bloco);
  }
  
  return resultado;
}

console.time('execucao');
console.log(agruparVendas(vendas));
console.timeEnd('execucao');

// Saída esperada: {
//   'Notebook': { totalQuantidade: 3, totalValor: 5000.00 },
//   'Mouse': { totalQuantidade: 7, totalValor: 1050.00 },
//   'Teclado': { totalQuantidade: 3, totalValor: 300.00 }
// }
``` 