## Problema: Smart Curriculum Scheduler

Você está desenvolvendo um sistema para gerar um cronograma curricular semanal. O sistema deve alocar disciplinas de acordo com os períodos preferidos, a disponibilidade dos instrutores e respeitando a carga horária máxima de cada instrutor, sem sobreposição de aulas no mesmo período.

Cada disciplina possui os seguintes atributos:
- **disciplina** (string): nome da disciplina
- **periodosPreferidos** (array de strings): períodos nos quais a disciplina pode ser dada (ex: 'morning', 'afternoon', 'evening')
- **duracao** (inteiro): duração da aula em horas
- **instructorId** (string): identificador do instrutor responsável

Cada instrutor possui os seguintes atributos:
- **id** (string): identificador do instrutor
- **nome** (string)
- **disponibilidade** (array de strings): períodos em que o instrutor está disponível para dar aulas
- **cargaMaxima** (inteiro): carga horária máxima (em horas) que o instrutor pode ministrar por semana

O objetivo é criar um cronograma semanal (por exemplo, de Segunda a Sexta) que:
- Aloque as disciplinas em períodos que estejam entre os períodos preferidos da disciplina e dentro da disponibilidade do instrutor
- Não ultrapasse a carga horária máxima do instrutor
- Não tenha sobreposição: um mesmo instrutor não pode dar duas aulas no mesmo período

### Entrada:
- Uma lista de disciplinas (objetos com os atributos: `disciplina`, `periodosPreferidos`, `duracao` e `instructorId`)
- Uma lista de instrutores (objetos com os atributos: `id`, `nome`, `disponibilidade` e `cargaMaxima`)

### Saída:
- Um objeto representando o cronograma semanal, onde as chaves são os dias da semana (ex: 'Monday', 'Tuesday', etc.) e os valores são arrays de alocações. Cada alocação deve conter:
  - **periodo** (string): período do dia
  - **disciplina** (string)
  - **instrutor** (string)

### Regras e Restrições:
1. **Processamento em Blocos:**
   - O algoritmo deve processar as disciplinas em blocos de tamanho 3, simulando cenários de grandes conjuntos de dados.
2. **Tempo Máximo de Execução:**
   - A solução deve ser executada em menos de 100ms para uma lista de 100 disciplinas. Use `console.time()` e `console.timeEnd()` para medir o tempo de execução.
3. **Limite de Complexidade:**
   - Garanta que sua solução não exceda uma complexidade de O(n log n).
4. **Persistência de Estado (Opcional):**
   - Projete a solução para retomar de onde parou em caso de interrupções.
5. **Relatório de Execução (Opcional):**
   - Forneça métricas de desempenho, como tempo de execução e uso de memória.

### Exemplo:
```javascript
const disciplinas = [
  { disciplina: 'Matemática', periodosPreferidos: ['morning', 'afternoon'], duracao: 2, instructorId: 'I1' },
  { disciplina: 'História', periodosPreferidos: ['afternoon'], duracao: 1, instructorId: 'I2' },
  { disciplina: 'Ciências', periodosPreferidos: ['morning'], duracao: 2, instructorId: 'I1' },
  { disciplina: 'Literatura', periodosPreferidos: ['evening'], duracao: 1, instructorId: 'I3' },
  { disciplina: 'Física', periodosPreferidos: ['morning', 'evening'], duracao: 2, instructorId: 'I2' }
  // ... outras disciplinas ...
];

const instrutores = [
  { id: 'I1', nome: 'Prof. Silva', disponibilidade: ['morning', 'afternoon'], cargaMaxima: 4 },
  { id: 'I2', nome: 'Prof. Oliveira', disponibilidade: ['morning', 'afternoon', 'evening'], cargaMaxima: 3 },
  { id: 'I3', nome: 'Prof. Souza', disponibilidade: ['evening'], cargaMaxima: 2 }
];

function gerarCronograma(disciplinas, instrutores) {
  // Sua solução aqui
  // Lembre-se de processar as disciplinas em blocos de 3
}

console.time('execucao');
console.log(gerarCronograma(disciplinas, instrutores));
console.timeEnd('execucao');

/* Saída esperada (exemplo):
{
  Monday: [ { periodo: 'morning', disciplina: 'Matemática', instrutor: 'Prof. Silva' }, ... ],
  Tuesday: [ ... ],
  ...
}
*/
``` 