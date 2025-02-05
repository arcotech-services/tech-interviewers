## Problema: Student Grade Calculator

Você está desenvolvendo um sistema para calcular a nota final de alunos com base em seus desempenhos em diferentes exames. Cada aluno possui os seguintes atributos:
- **id** (string)
- **nome** (string)
- **exames** (array de objetos), onde cada objeto contém:
  - **exame** (string)
  - **notaObtida** (número)
  - **notaMaxima** (número)

O objetivo é calcular a nota final de cada aluno como uma porcentagem, utilizando a fórmula:

     notaFinal = (soma das notas obtidas / soma das notas máximas) * 100

### Entrada:
- Uma lista de objetos, cada representando um aluno com os atributos: `id`, `nome` e `exames`.

### Saída:
- Um array de objetos, onde cada objeto contém:
  - **id**
  - **nome**
  - **notaFinal** (número, em porcentagem)

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar os alunos em blocos de tamanho 10, simulando cenários com grandes conjuntos de dados.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 100 alunos. Utilize `console.time()` e `console.timeEnd()` para medir o tempo de execução.
3. **Limite de Complexidade:**
   - Garanta que sua solução seja O(n), processando cada aluno uma única vez.
4. **Persistência de Estado (Opcional):**
   - Projete a solução para retomar de onde parou em caso de interrupções.
5. **Relatório de Execução (Opcional):**
   - Além do resultado final, forneça métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const alunos = [
  {
    id: 'A1',
    nome: 'João',
    exames: [
      { exame: 'Matemática', notaObtida: 80, notaMaxima: 100 },
      { exame: 'História', notaObtida: 70, notaMaxima: 100 }
    ]
  },
  {
    id: 'A2',
    nome: 'Maria',
    exames: [
      { exame: 'Matemática', notaObtida: 90, notaMaxima: 100 },
      { exame: 'História', notaObtida: 85, notaMaxima: 100 },
      { exame: 'Ciências', notaObtida: 80, notaMaxima: 100 }
    ]
  },
  // ...outros alunos...
];

function calcularNotasAlunos(alunos) {
  const resultado = [];
  const tamanhoBloco = 10;
  
  for (let i = 0; i < alunos.length; i += tamanhoBloco) {
    // Sua solução aqui
  }
  
  return resultado;
}

console.time('execucao');
console.log(calcularNotasAlunos(alunos));
console.timeEnd('execucao');

// Saída esperada: array de objetos com id, nome e notaFinal calculada para cada aluno.
