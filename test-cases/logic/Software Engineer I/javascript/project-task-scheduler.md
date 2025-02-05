## Problema: Project Task Scheduler

Você está desenvolvendo um sistema para agendar tarefas de um projeto. Cada tarefa possui os atributos:
- **nome** (string)
- **duracao** (inteiro, duração da tarefa em horas)
- **recompensa** (inteiro, valor de recompensa ou prioridade atribuída à tarefa)
- **prazo** (inteiro, deadline em horas a partir do início do projeto)

O objetivo é selecionar um conjunto de tarefas que maximize a recompensa total, sem que a soma das durações ultrapasse o tempo total disponível para o projeto e respeitando os prazos individuais das tarefas.

### Entrada:
- Uma lista de objetos, cada representando uma tarefa com os atributos: `nome`, `duracao`, `recompensa` e `prazo`.
- Um número representando o tempo total disponível (em horas) para o projeto.

### Saída:
- A combinação de tarefas que maximiza a recompensa total, respeitando o limite de tempo e os prazos.

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar as tarefas em blocos de tamanho 3.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 100 tarefas. Utilize `console.time()` e `console.timeEnd()` para medir o tempo.
3. **Limite de Complexidade:**
   - Garanta que a solução seja, no máximo, O(n log n).
4. **Persistência de Estado (Opcional):**
   - Projete a solução para retomar de onde parou em caso de interrupções.
5. **Relatório de Execução (Opcional):**
   - Além do agendamento ideal, forneça métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const tarefas = [
  { nome: 'Design', duracao: 4, recompensa: 10, prazo: 8 },
  { nome: 'Desenvolvimento', duracao: 6, recompensa: 15, prazo: 10 },
  { nome: 'Testes', duracao: 3, recompensa: 8, prazo: 6 },
  { nome: 'Deploy', duracao: 2, recompensa: 5, prazo: 7 },
  { nome: 'Documentação', duracao: 5, recompensa: 7, prazo: 12 },
  // ...outras tarefas...
];

const tempoTotal = 12;

function agendarTarefas(tarefas, tempoTotal) {
  // Sua solução aqui
  // Lembre-se de processar as tarefas em blocos de 3
}

console.time('execucao');
console.log(agendarTarefas(tarefas, tempoTotal));
console.timeEnd('execucao');

// Saída esperada: combinação de tarefas que maximiza a recompensa total dentro do tempo disponível e respeita os prazos
``` 