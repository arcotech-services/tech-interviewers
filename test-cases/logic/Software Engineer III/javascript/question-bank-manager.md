## Problema: Question Bank Manager

Você está desenvolvendo um sistema para gerenciar um banco de questões para professores. Cada questão possui os atributos:
- **id** (string ou número identificador)
- **disciplina** (string, ex: 'Matemática', 'História')
- **dificuldade** (inteiro, de 1 a 10)
- **enunciado** (string, texto da questão)
- **tags** (array de strings)

O objetivo é filtrar e retornar as questões que atendam a certos critérios, por exemplo, de uma disciplina específica e com dificuldade mínima.

### Entrada:
- Uma lista de objetos, cada representando uma questão com os atributos: `id`, `disciplina`, `dificuldade`, `enunciado` e `tags`.
- Dois parâmetros de filtro: `disciplinaFiltro` (string) e `dificuldadeMinima` (inteiro).

### Saída:
- Uma lista das questões que pertencem à disciplina especificada e que tenham dificuldade maior ou igual à dificuldade mínima.

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar as questões em blocos de tamanho 5, simulando cenários com grandes conjuntos de dados.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 100 questões. Utilize `console.time()` e `console.timeEnd()` para medir o tempo de execução.
3. **Limite de Complexidade:**
   - Garanta que sua solução não exceda uma complexidade de O(n log n).
4. **Persistência de Estado (Opcional):**
   - Projete a solução para retomar de onde parou em caso de interrupções.
5. **Relatório de Execução (Opcional):**
   - Além da lista filtrada, forneça métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const questoes = [
  { id: 1, disciplina: 'Matemática', dificuldade: 8, enunciado: 'Qual o valor de π?', tags: ['geometria'] },
  { id: 2, disciplina: 'História', dificuldade: 5, enunciado: 'Quem foi Napoleão?', tags: ['guerras'] },
  { id: 3, disciplina: 'Matemática', dificuldade: 6, enunciado: 'Resolver equações do 2º grau', tags: ['algebra'] },
  { id: 4, disciplina: 'Matemática', dificuldade: 9, enunciado: 'Cálculo integral', tags: ['calculo'] },
  { id: 5, disciplina: 'Ciências', dificuldade: 7, enunciado: 'Explicar o efeito estufa', tags: ['geografia'] },
  // ...outras questões...
];

const disciplinaFiltro = 'Matemática';
const dificuldadeMinima = 7;

function filtrarQuestoes(questoes, disciplinaFiltro, dificuldadeMinima) {
  // Sua solução aqui
  // Lembre-se de processar as questões em blocos de 5
}

console.time('execucao');
console.log(filtrarQuestoes(questoes, disciplinaFiltro, dificuldadeMinima));
console.timeEnd('execucao');

// Saída esperada: array contendo, por exemplo, as questões com id 1 e 4.
``` 