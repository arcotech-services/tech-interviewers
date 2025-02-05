## Problema: Exam Grading Analytics

Você está desenvolvendo um sistema para analisar os resultados de exames. Cada registro de exame possui os atributos:
- **examId** (string)
- **studentId** (string)
- **score** (número)

O objetivo é calcular métricas estatísticas dos resultados, incluindo:
- Média das pontuações
- Nota máxima
- Nota mínima
- Desvio padrão

### Entrada:
- Uma lista de objetos, cada representando um registro de exame com os atributos: `examId`, `studentId` e `score`.

### Saída:
- Um objeto contendo as métricas calculadas, por exemplo:
  ```javascript
  {
    media: 7.5,
    notaMaxima: 10,
    notaMinima: 5,
    desvioPadrao: 1.2
  }
  ```

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar os registros de exame em blocos de tamanho 20, simulando cenários com grandes conjuntos de dados.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 1000 registros. Utilize `console.time()` e `console.timeEnd()` para medir o tempo de execução.
3. **Limite de Complexidade:**
   - Garanta que sua solução seja O(n), processando cada registro uma única vez.
4. **Persistência de Estado (Opcional):**
   - Projete a solução para retomar de onde parou em caso de interrupções.
5. **Relatório de Execução (Opcional):**
   - Além das métricas, forneça informações de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const resultadosExame = [
  { examId: 'EX001', studentId: 'S001', score: 8 },
  { examId: 'EX001', studentId: 'S002', score: 7 },
  { examId: 'EX001', studentId: 'S003', score: 9 },
  { examId: 'EX001', studentId: 'S004', score: 6 },
  { examId: 'EX001', studentId: 'S005', score: 10 },
  // ...outros registros...
];

function analisarResultados(resultados) {
  // Sua solução aqui
  // Lembre-se de processar os registros em blocos de 20
}

console.time('execucao');
console.log(analisarResultados(resultadosExame));
console.timeEnd('execucao');

// Saída esperada: objeto com média, nota máxima, nota mínima e desvio padrão
``` 