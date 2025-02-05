## Problema: Virtual Classroom Participation Analyzer

Você está desenvolvendo um sistema para analisar os registros de interação em uma sala de aula virtual e calcular métricas de engajamento. Cada registro de evento possui os seguintes atributos:
- **studentId** (string): identificador do aluno que gerou o evento
- **eventType** (string): tipo de evento (ex: 'question', 'answer', 'comment', 'like', etc.)

Além dos registros de evento, você receberá o número total de alunos matriculados na sala.

O objetivo é calcular as seguintes métricas:
- **Taxa de Participação**: porcentagem de alunos que geraram ao menos um evento, calculada como (número de alunos participantes / total de alunos) * 100.
- **Média de Eventos por Aluno Participante**: média de eventos entre os alunos que interagiram.
- **Distribuição de Tipos de Evento**: um objeto que descreve quantas vezes cada tipo de evento ocorreu.

### Entrada:
- Uma lista de objetos representando os eventos, cada um com os atributos `studentId` e `eventType`.
- Um número representando o total de alunos matriculados na sala.

### Saída:
- Um objeto contendo as métricas calculadas, por exemplo:
  ```javascript
  {
    participationRate: 75,          // em porcentagem
    averageEventsPerParticipant: 4.2,
    eventDistribution: { question: 15, answer: 10, comment: 5 }
  }
  ```

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar os eventos em blocos de tamanho 20, simulando o processamento de grandes conjuntos de dados.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 1000 eventos. Utilize `console.time()` e `console.timeEnd()` para medir o tempo de execução.
3. **Limite de Complexidade:**
   - Garanta que sua solução seja O(n), processando cada evento uma única vez.
4. **Persistência de Estado (Opcional):**
   - Projete a solução para retomar de onde parou em caso de interrupções.
5. **Relatório de Execução (Opcional):**
   - Além das métricas, forneça informações de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const eventos = [
  { studentId: 'S1', eventType: 'question' },
  { studentId: 'S2', eventType: 'answer' },
  { studentId: 'S1', eventType: 'like' },
  { studentId: 'S3', eventType: 'comment' },
  { studentId: 'S2', eventType: 'question' },
  { studentId: 'S4', eventType: 'like' },
  { studentId: 'S3', eventType: 'answer' },
  { studentId: 'S1', eventType: 'comment' }
  // ... outros eventos ...
];

const totalAlunos = 10;

function analisarParticipacao(eventos, totalAlunos) {
  const participantes = new Set();
  const eventCounts = {};
  let totalEventos = 0;
  
  const tamanhoBloco = 20;
  
  for (let i = 0; i < eventos.length; i += tamanhoBloco) {
    const bloco = eventos.slice(i, i + tamanhoBloco);
    bloco.forEach(evento => {
      participantes.add(evento.studentId);
      eventCounts[evento.eventType] = (eventCounts[evento.eventType] || 0) + 1;
      totalEventos++;
    });
  }
  
  const numParticipantes = participantes.size;
  const participationRate = (numParticipantes / totalAlunos) * 100;
  const averageEventsPerParticipant = numParticipantes > 0 ? totalEventos / numParticipantes : 0;
  
  return {
    participationRate,
    averageEventsPerParticipant,
    eventDistribution: eventCounts
  };
}

console.time('execucao');
console.log(analisarParticipacao(eventos, totalAlunos));
console.timeEnd('execucao');

// Saída esperada: um objeto contendo as métricas descritas acima.

</rewritten_file> 