## Problema: Travel Itinerary Planner

Você está desenvolvendo um sistema para planejar um roteiro de viagem. Cada destino tem os atributos:
- **nome** (string)
- **diversao** (inteiro que representa o grau de diversão do destino)
- **tempo** (inteiro representando o tempo necessário em minutos para visitar o destino)

O objetivo é selecionar um conjunto de destinos que maximize a diversão total, sem que a soma dos tempos ultrapasse o tempo máximo disponível para a viagem.

### Entrada:
- Uma lista de objetos, cada um representando um destino com os atributos: `nome`, `diversao` e `tempo`.
- Um número representando o tempo máximo disponível (em minutos) para a viagem.

### Saída:
- A combinação de destinos que maximiza a diversão total, sem exceder o tempo máximo disponível.

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar os destinos em blocos de tamanho 5, simulando cenários com grandes conjuntos de dados.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 100 destinos. Utilize `console.time()` e `console.timeEnd()` para medir o tempo de execução.
3. **Limite de Complexidade:**
   - Garanta que sua solução não exceda uma complexidade de O(n log n).
4. **Persistência de Estado (Opcional):**
   - Projete a solução de forma que, se o processamento for interrompido, ela possa retomar de onde parou.
5. **Relatório de Execução (Opcional):**
   - Além do roteiro ideal, forneça um relatório com métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const destinos = [
  { nome: 'Museu', diversao: 7, tempo: 90 },
  { nome: 'Parque', diversao: 9, tempo: 120 },
  { nome: 'Restaurante', diversao: 5, tempo: 60 },
  { nome: 'Teatro', diversao: 8, tempo: 150 },
  { nome: 'Praia', diversao: 10, tempo: 180 },
  // ...outros destinos...
];

const tempoMaximo = 300;

function planejarItinerario(destinos, tempoMaximo) {
  // Sua solução aqui
  // Lembre-se de processar os destinos em blocos de 5
}

console.time('execucao');
console.log(planejarItinerario(destinos, tempoMaximo));
console.timeEnd('execucao');

// Saída esperada: combinação ideal de destinos com o máximo de diversão dentro do tempo disponível
``` 