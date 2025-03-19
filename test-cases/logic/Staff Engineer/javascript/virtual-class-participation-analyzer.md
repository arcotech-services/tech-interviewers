### Desafio: **Analisador de Participação de Estudantes em Aulas Online**

**Contexto:**
Você foi contratado para construir um módulo de análise de participação de alunos em uma plataforma educacional que oferece aulas online. A plataforma permite que os estudantes participem de aulas ao vivo e registrem sua presença e participação durante a sessão. Seu trabalho é implementar uma solução que analise os dados de participação para ajudar os professores a avaliar o engajamento dos alunos de forma eficiente.

#### Dados de entrada:
Você recebe um conjunto de dados representando os alunos e suas participações nas aulas. Cada entrada no dado representa um aluno e seu comportamento durante uma aula online.

Os dados de entrada são uma lista de objetos, onde cada objeto contém as seguintes propriedades:

- **studentId**: Um identificador único para cada aluno.
- **name**: O nome do aluno.
- **participation**: Um número que representa o nível de participação do aluno durante a aula. Pode ser:
  - `0`: O aluno não participou da aula.
  - `1`: O aluno assistiu à aula sem interagir.
  - `2`: O aluno fez perguntas ou respondeu ativamente durante a aula.
- **duration**: O tempo (em minutos) que o aluno assistiu à aula.

#### Requisitos:
1. **Relatório de participação**: Crie uma função `generateReport` que receba os dados de participação dos alunos e gere um relatório com as seguintes informações:
   - **Participação total**: A soma das participações de todos os alunos (ou seja, a soma de todos os valores em `participation`).
   - **Participação ativa**: O número de alunos que participaram ativamente (ou seja, `participation` igual a 2).
   - **Média de tempo assistido**: O tempo médio de participação de todos os alunos.
   - **Aluno mais participativo**: O aluno que mais interagiu durante a aula (quem teve maior valor em `participation` e `duration`).
   
2. **Classificação de engajamento**: Implemente uma função `classifyEngagement` que retorne uma classificação de engajamento para cada aluno com base no tempo assistido e no nível de participação. A classificação deve ser atribuída da seguinte forma:
   - Se o aluno participou ativamente e assistiu mais de 70% da aula, classifique-o como "Engajado".
   - Se o aluno assistiu à aula, mas não interagiu, classifique-o como "Passivo".
   - Se o aluno não participou ou assistiu menos de 30% da aula, classifique-o como "Desengajado".

3. **Análise de Tendências**: Implementar uma função `analyzeTrends` que analise os dados e retorne:
   - **Aluno com maior tempo de aula assistido**: Qual aluno assistiu mais tempo no total.
   - **Aluno com menor tempo de aula assistido**: Qual aluno assistiu menos tempo no total.
   - **Aluno com maior variação de participação**: Qual aluno teve a maior variação entre o tempo assistido e o nível de participação (ou seja, o maior `duration` dividido por `participation`).

#### Exemplos:

**Entrada 1**:

```javascript
const students = [
  { studentId: 1, name: 'João', participation: 2, duration: 60 },
  { studentId: 2, name: 'Maria', participation: 1, duration: 50 },
  { studentId: 3, name: 'José', participation: 0, duration: 40 },
  { studentId: 4, name: 'Ana', participation: 2, duration: 75 }
];
```

**Saída Esperada 1**:
```javascript
generateReport(students);
// {
//   totalParticipation: 5,
//   activeParticipants: 2,
//   averageDuration: 56.25,
//   mostParticipativeStudent: { name: 'Ana', participation: 2, duration: 75 }
// }

classifyEngagement(students);
// [
//   { name: 'João', engagement: 'Engajado' },
//   { name: 'Maria', engagement: 'Passivo' },
//   { name: 'José', engagement: 'Desengajado' },
//   { name: 'Ana', engagement: 'Engajado' }
// ]

analyzeTrends(students);
// {
//   studentWithMostTime: { name: 'Ana', duration: 75 },
//   studentWithLeastTime: { name: 'José', duration: 40 },
//   studentWithHighestParticipationVariance: { name: 'Ana', participationVariance: 37.5 }
// }
```

[clique aqui para ter acesso a lista completa de alunos](https://gist.githubusercontent.com/MatheusKindrazki/da84cc69824d77acd8721f14497d596f/raw/cced4fd2fcd3748995b9f08c004150f9c3097a38/students-data.json)

#### Desafios extras:

- **Escalabilidade**: Como a solução funcionaria com milhares de alunos e grandes volumes de dados?
- **Tratamento de exceções**: O código lida com entradas inválidas, como `null` ou `undefined` nos dados?
- **Testes unitários**: O candidato pode ser desafiado a criar testes para garantir que o código esteja funcionando corretamente.
