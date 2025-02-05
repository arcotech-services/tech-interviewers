## Problema: Warehouse Inventory Balancer

Você está desenvolvendo um sistema para balancear o inventário entre diferentes armazéns. Cada armazém possui os atributos:
- **produto** (string)
- **quantidadeAtual** (inteiro)
- **capacidadeMaxima** (inteiro)

O objetivo é distribuir um número total de unidades de um determinado produto entre os armazéns, de forma a maximizar a ocupação sem ultrapassar a capacidade máxima de cada armazém.

### Entrada:
- Uma lista de objetos, cada um representando um armazém com os atributos: `produto`, `quantidadeAtual` e `capacidadeMaxima`.
- Um número representando o total de unidades disponíveis para distribuir.

### Saída:
- Um objeto que mostra, para cada armazém, quantas unidades adicionais foram alocadas, garantindo que a soma das alocações não exceda o total disponível e que nenhuma alocação ultrapasse a capacidade máxima.

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar os armazéns em blocos de tamanho 5, simulando cenários com grandes conjuntos de dados.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 100 armazéns. Utilize `console.time()` e `console.timeEnd()` para medir o tempo de execução.
3. **Limite de Complexidade:**
   - Garanta que sua solução não exceda uma complexidade de O(n log n).
4. **Persistência de Estado (Opcional):**
   - Projete a solução de modo que, se o processamento for interrompido, ela possa retomar de onde parou.
5. **Relatório de Execução (Opcional):**
   - Além da distribuição ideal, forneça métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const armazens = [
  { produto: 'Notebook', quantidadeAtual: 50, capacidadeMaxima: 100 },
  { produto: 'Notebook', quantidadeAtual: 30, capacidadeMaxima: 80 },
  { produto: 'Notebook', quantidadeAtual: 20, capacidadeMaxima: 50 },
  { produto: 'Notebook', quantidadeAtual: 40, capacidadeMaxima: 100 },
  { produto: 'Notebook', quantidadeAtual: 60, capacidadeMaxima: 120 },
  // ...outros armazéns...
];

const unidadesDisponiveis = 100;

function balancearInventario(armazens, unidadesDisponiveis) {
  // Sua solução aqui
  // Lembre-se de processar os armazéns em blocos de 5
}

console.time('execucao');
console.log(balancearInventario(armazens, unidadesDisponiveis));
console.timeEnd('execucao');

// Saída esperada: um objeto indicando a alocação adicional por armazém, sem exceder a capacidade máxima.
``` 