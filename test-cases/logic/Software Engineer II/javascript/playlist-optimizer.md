## Problema: Playlist Optimizer

Você está desenvolvendo um sistema para criar a playlist musical ideal. Cada canção possui os atributos:
- **nome** (string)
- **humor** (inteiro que representa o impacto emocional da canção)
- **duração** (inteiro representando a duração em segundos)

O objetivo é selecionar um conjunto de canções que maximize o humor total, sem que a soma das durações exceda um tempo máximo especificado para a playlist.

### Entrada:
- Uma lista de objetos, cada um representando uma canção com os seguintes atributos: `nome`, `humor` e `duracao`.
- Um número representando a duração máxima permitida (em segundos) para a playlist.

### Saída:
- A combinação de canções que maximiza o humor total sem exceder a duração máxima permitida.

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar as canções em blocos de tamanho 10, sem carregar todas as canções na memória de uma vez.
2. **Tempo Máximo de Execução:**
   - A solução deve ser concluída em menos de 100ms para uma lista de 100 canções. Utilize `console.time()` e `console.timeEnd()` para medir o tempo de execução.
3. **Limite de Complexidade:**
   - Garanta que sua solução não exceda uma complexidade de O(n log n).
4. **Persistência de Estado (Opcional):**
   - Projete a solução de modo que, se o processamento for interrompido, ela possa retomar de onde parou sem reiniciar.
5. **Relatório de Execução (Opcional):**
   - Além da playlist ideal, forneça um relatório com métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const musicas = [
  { nome: 'Song A', humor: 5, duracao: 210 },
  { nome: 'Song B', humor: 8, duracao: 180 },
  { nome: 'Song C', humor: 3, duracao: 200 },
  { nome: 'Song D', humor: 6, duracao: 150 },
  { nome: 'Song E', humor: 7, duracao: 240 },
  // ...outras músicas...
];

const duracaoMaxima = 600;

function otimizarPlaylist(musicas, duracaoMaxima) {
  // Sua solução aqui
  // Lembre-se de processar as músicas em blocos de 10
}

console.time('execucao');
console.log(otimizarPlaylist(musicas, duracaoMaxima));
console.timeEnd('execucao');

// Saída esperada: combinação ótima de músicas com o máximo humor total dentro do limite de duração
``` 