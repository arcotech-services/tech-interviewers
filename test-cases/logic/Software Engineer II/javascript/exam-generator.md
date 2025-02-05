## Problema: Exam Generator

Você está desenvolvendo um sistema para gerar automaticamente uma prova para professores. Cada questão possui os seguintes atributos:
- **id** (identificador único, string ou número)
- **materia** (string, ex: 'Matemática', 'Literatura')
- **dificuldade** (inteiro, de 1 a 10)
- **pontos** (inteiro, valor em pontos da questão)

O objetivo é selecionar uma combinação de questões que maximize o nível total de dificuldade, sem que a soma dos pontos exceda um limite máximo especificado para a prova.

### Entrada:
- Uma lista de objetos, cada representando uma questão com os atributos: `id`, `materia`, `dificuldade` e `pontos`.
- Um número representando o total máximo de pontos permitidos na prova.

### Saída:
- A combinação de questões que maximiza o total de dificuldade sem exceder o total máximo de pontos.

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar as questões em blocos de tamanho 5, simulando o processamento de grandes conjuntos de dados.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 100 questões. Utilize `console.time()` e `console.timeEnd()` para medir o tempo de execução.
3. **Limite de Complexidade:**
   - Garanta que sua solução não exceda uma complexidade de O(n log n).
4. **Persistência de Estado (Opcional):**
   - Projete a solução para retomar de onde parou em caso de interrupções.
5. **Relatório de Execução (Opcional):**
   - Além da prova gerada, forneça métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const questoes = [
  { id: 1, materia: 'Matemática', dificuldade: 8, pontos: 5 },
  { id: 2, materia: 'Literatura', dificuldade: 6, pontos: 3 },
  { id: 3, materia: 'Matemática', dificuldade: 7, pontos: 4 },
  { id: 4, materia: 'História', dificuldade: 5, pontos: 2 },
  { id: 5, materia: 'Matemática', dificuldade: 9, pontos: 6 },
  // ...outras questões...
];

const pontosMaximos = 10;

function gerarProva(questoes, pontosMaximos) {
  // Sua solução aqui
  // Lembre-se de processar as questões em blocos de 5
}

console.time('execucao');
console.log(gerarProva(questoes, pontosMaximos));
console.timeEnd('execucao');

// Saída esperada: combinação de questões que maximiza o total de dificuldade sem exceder 10 pontos.
``` 