## Problema: Peer Review Assignment Optimizer

Você está desenvolvendo um sistema para otimizar a atribuição de avaliações entre alunos. Cada submissão possui os seguintes atributos:
- **submissionId** (string): identificador único da submissão
- **studentId** (string): identificador do aluno que submeteu o trabalho

O objetivo é distribuir as avaliações de forma que:
- Cada submissão receba um número mínimo de revisões (minReviews)
- Nenhum aluno avalie sua própria submissão
- A carga de revisões seja distribuída de forma equilibrada entre os alunos

### Entrada:
- Uma lista de objetos representando submissões, cada um com os atributos: `submissionId` e `studentId`
- Um número representando o número mínimo de revisões que cada submissão deve receber (minReviews)

### Saída:
- Um objeto onde as chaves são os `submissionId` e os valores são arrays de `studentId` dos revisores atribuídos a essa submissão

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar as submissões em blocos de tamanho 5, simulando cenários com grandes conjuntos de dados.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 100 submissões. Utilize `console.time()` e `console.timeEnd()` para medir o tempo.
3. **Limite de Complexidade:**
   - Garanta que a solução não exceda uma complexidade de O(n log n).
4. **Persistência de Estado (Opcional):**
   - Projete a solução para retomar de onde parou em caso de interrupções.
5. **Relatório de Execução (Opcional):**
   - Além da atribuição, forneça métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const submissions = [
  { submissionId: 'sub1', studentId: 'S1' },
  { submissionId: 'sub2', studentId: 'S2' },
  { submissionId: 'sub3', studentId: 'S3' },
  { submissionId: 'sub4', studentId: 'S4' },
  { submissionId: 'sub5', studentId: 'S5' }
];

const minReviews = 2;

function otimizarAtribuicao(submissions, minReviews) {
  const assignment = {};
  const reviewCounts = {};

  // Inicializa a contagem de revisões para cada aluno
  submissions.forEach(sub => {
    reviewCounts[sub.studentId] = 0;
  });

  const blocoTamanho = 5;
  for (let i = 0; i < submissions.length; i += blocoTamanho) {
  // Sua solução aqui
  }

  return assignment;
}

console.time('execucao');
console.log(otimizarAtribuicao(submissions, minReviews));
console.timeEnd('execucao');

/* Saída esperada (exemplo):
{
  sub1: ['S2', 'S3'],
  sub2: ['S1', 'S3'],
  sub3: ['S1', 'S2'],
  sub4: ['S1', 'S2'],
  sub5: ['S1', 'S2']
}
*/ 