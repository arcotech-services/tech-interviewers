## Problema: Gerenciamento e Estatísticas das Notas por Disciplina

Você está criando um componente React que permite ao usuário inserir uma nota (entre 0 e 10) para uma das seguintes disciplinas: História, Matemática ou Artes. O componente deve:

- Permitir que o usuário insira uma nota para uma das três disciplinas (História, Matemática ou Artes), com validação para garantir que as notas sejam entre 0 e 10.
- Exibir uma tabela com as notas inseridas para cada disciplina, mostrando:
  - O nome da disciplina.
  - O número de notas inseridas para aquela disciplina.
  - A média das notas.
  - A menor e a maior nota inserida.
- Usar apenas React e gerenciamento de estados (sem uso de bibliotecas externas).

### Entrada:

- Um formulário para inserção da nota e seleção da disciplina.
- O valor da nota deve ser numérico, entre 0 e 10.
- A disciplina deve ser escolhida entre as opções: História, Matemática ou Artes.

### Saída:

- Uma tabela que exibe:
  - O nome da disciplina.
  - O número de notas inseridas para cada disciplina.
  - A média das notas (arredondada para duas casas decimais).
  - A menor e a maior nota para cada disciplina.

### Regras e Restrições:

1. **Validação de Notas:** As notas inseridas devem ser números entre 0 e 10. Caso contrário, a nota não será adicionada e o sistema deve notificar o usuário.
2. **Cálculos:** A média das notas, a maior e a menor nota devem ser calculadas apenas com as notas válidas para cada disciplina.
3. **Uso de React States:** O componente deve gerenciar o estado das notas inseridas e das disciplinas.
4. **Sem Estilização:** Não é necessário se preocupar com a estilização, apenas com a funcionalidade.

### Exemplo básico

```jsx
import { useCallback, useMemo, useState } from "react";

const SUBJECTS = [
  { name: "Arts", id: "ARTS" },
  { name: "History", id: "HISTORY" },
  { name: "Mathematics", id: "MATHEMATICS" },
];

const SubjectGradesManager = () => {
  const [newGrade, setNewGrade] = useState(0);
  const [newSubject, setNewSubject] = useState("ARTS");
  const [subjectsGrades, setSubjectsGrades] = useState({
    ARTS: { grades: [] },
    HISTORY: { grades: [] },
    MATHEMATICS: { grades: [] },
  });

  const handleSubmit = (event) => {
    event.preventDefault();

    const formData = new FormData(event.target);
    const grade = Number(formData.get("grade"));
    const subject = formData.get("subject");

    if (!isNaN(grade) && grade >= 0 && grade <= 10) {
      setSubjectsGrades((prev) => ({
        ...prev,
        [subject]: { grades: [...prev[subject].grades, grade] },
      }));
      setNewSubject("ARTS");
      setNewGrade(0);
    } else {
      alert("Grade must be a number between 0 and 10");
    }
  };

  const getSubjectStats = useCallback((grades) => {
    const gradesCount = grades.length;

    if (gradesCount) {
      return {
        average: (
          grades.reduce((prev, curr) => prev + curr, 0) / grades.length
        ).toFixed(2),
        biggest: Math.max(...grades).toFixed(2),
        count: gradesCount,
        smallest: Math.min(...grades).toFixed(2),
      };
    }

    return {
      average: 0,
      biggest: 0,
      count: 0,
      smallest: 0,
    };
  }, []);

  const subjectsStats = useMemo(() => {
    return Object.entries(subjectsGrades).map(([subject, { grades }]) => {
      const { average, biggest, count, smallest } = getSubjectStats(grades);

      return {
        average,
        biggest,
        count,
        name: subject,
        smallest,
      };
    });
  }, [subjectsGrades, getSubjectStats]);

  return (
    <div>
      <h1>Subject Grades Manager</h1>
      <form onSubmit={handleSubmit}>
        <div>
          <label htmlFor="grade">Grade</label>
          <input
            max={10}
            min={0}
            name="grade"
            onChange={(event) => setNewGrade(Number(event.target.value))}
            required
            step={0.01}
            type="number"
            value={newGrade}
          />
        </div>
        <div>
          <label htmlFor="subject">Subject</label>
          <select
            name="subject"
            onChange={(event) => setNewSubject(event.target.value)}
            required
            value={newSubject}
          >
            {SUBJECTS.map(({ name, id }) => (
              <option value={id} key={id}>
                {name}
              </option>
            ))}
          </select>
        </div>
        <button type="submit">Add</button>
      </form>

      <table>
        <thead>
          <tr>
            <th>Subject</th>
            <th>Grades</th>
            <th>Grades Average</th>
            <th>Biggest Grade</th>
            <th>Smallest Grade</th>
          </tr>
        </thead>
        <tbody>
          {subjectsStats.map(({ average, biggest, count, name, smallest }) => (
            <tr key={name}>
              <td>{name}</td>
              <td>{count}</td>
              <td>{average}</td>
              <td>{biggest}</td>
              <td>{smallest}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
};

export default SubjectGradesManager;
```
