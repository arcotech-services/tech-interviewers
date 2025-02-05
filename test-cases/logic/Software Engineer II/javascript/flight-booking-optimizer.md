## Problema: Flight Booking Optimizer

Você está desenvolvendo um sistema para otimizar reservas de voos. Cada voo possui os atributos:
- **flightNumber** (string)
- **custo** (número, valor da passagem)
- **duracao** (inteiro, duração do voo em minutos)
- **conforto** (inteiro, pontuação de conforto)

O objetivo é selecionar uma combinação de voos que maximize a pontuação total de conforto sem exceder um orçamento máximo.

### Entrada:
- Uma lista de objetos, cada representando um voo com os atributos: `flightNumber`, `custo`, `duracao` e `conforto`.
- Um número representando o orçamento máximo para a soma dos custos dos voos.

### Saída:
- A combinação de voos que maximiza a pontuação total de conforto sem exceder o orçamento.

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar os voos em blocos de tamanho 5, simulando grandes conjuntos de dados.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 100 voos. Utilize `console.time()` e `console.timeEnd()` para medir o tempo de execução.
3. **Limite de Complexidade:**
   - Garanta que sua solução não exceda uma complexidade de O(n log n).
4. **Persistência de Estado (Opcional):**
   - Projete a solução para retomar de onde parou caso o processamento seja interrompido.
5. **Relatório de Execução (Opcional):**
   - Além da combinação ideal, forneça métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const voos = [
  { flightNumber: 'AB123', custo: 300, duracao: 180, conforto: 8 },
  { flightNumber: 'CD456', custo: 450, duracao: 240, conforto: 9 },
  { flightNumber: 'EF789', custo: 200, duracao: 150, conforto: 7 },
  { flightNumber: 'GH012', custo: 350, duracao: 210, conforto: 8 },
  { flightNumber: 'IJ345', custo: 400, duracao: 200, conforto: 9 },
  // ...outros voos...
];

const orcamentoMaximo = 1000;

function otimizarReservas(voos, orcamentoMaximo) {
  // Sua solução aqui
  // Lembre-se de processar os voos em blocos de 5
}

console.time('execucao');
console.log(otimizarReservas(voos, orcamentoMaximo));
console.timeEnd('execucao');

// Saída esperada: combinação ideal de voos com o máximo conforto sem exceder o orçamento
``` 