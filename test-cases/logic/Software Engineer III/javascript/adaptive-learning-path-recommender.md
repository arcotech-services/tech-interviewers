## Problema: Adaptive Learning Path Recommender

Você está desenvolvendo um sistema para recomendar um percurso de aprendizagem personalizado para alunos, com base nos módulos que eles já completaram e na disponibilidade de tempo para estudo. Cada módulo possui os seguintes atributos:
- **moduleId** (string)
- **subject** (string)
- **difficulty** (inteiro, de 1 a 10)
- **estimatedTime** (inteiro, em minutos)
- **prerequisites** (array de strings, representando os moduleId dos módulos que devem ser completados previamente)

O objetivo é recomendar um conjunto de módulos que:
- Não tenham sido completados pelo aluno (lista fornecida)
- Possuam todos os pré-requisitos satisfeitos
- Maximizem o total de dificuldade acumulada sem ultrapassar o tempo disponível para estudo

### Entrada:
- Uma lista de módulos (objetos com os atributos acima)
- Uma lista de strings representando os módulos já completados pelo aluno
- Um número representando o tempo disponível para estudo (em minutos)

### Saída:
- Uma combinação de módulos recomendados que maximize a soma das dificuldades sem exceder o tempo disponível e respeitando os pré-requisitos

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar os módulos em blocos de tamanho 5, simulando cenários com grandes conjuntos de dados.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 100 módulos.
3. **Limite de Complexidade:**
   - Garanta que sua solução não exceda uma complexidade de O(n log n).
4. **Persistência de Estado (Opcional):**
   - Projete a solução para retomar de onde parou em caso de interrupções.
5. **Relatório de Execução (Opcional):**
   - Forneça métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const modulos = [
  { moduleId: 'M1', subject: 'Matemática', difficulty: 5, estimatedTime: 30, prerequisites: [] },
  { moduleId: 'M2', subject: 'Matemática', difficulty: 7, estimatedTime: 45, prerequisites: ['M1'] },
  { moduleId: 'M3', subject: 'Física', difficulty: 6, estimatedTime: 40, prerequisites: [] },
  { moduleId: 'M4', subject: 'Química', difficulty: 8, estimatedTime: 50, prerequisites: ['M3'] },
  { moduleId: 'M5', subject: 'Matemática', difficulty: 9, estimatedTime: 60, prerequisites: ['M2'] },
  // ... outros módulos ...
];

const modulosCompletados = ['M1'];
const tempoDisponivel = 100; // minutos

function recomendarPercurso(modulos, modulosCompletados, tempoDisponivel) {
  // Sua solução aqui
  // Lembre-se de processar os módulos em blocos de 5
}

console.time('execucao');
console.log(recomendarPercurso(modulos, modulosCompletados, tempoDisponivel));
console.timeEnd('execucao');

// Saída esperada: por exemplo, uma combinação de módulos como ['M2', 'M3'] que respeitem as restrições.
``` 