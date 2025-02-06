## Problema: Student Grades Statistics Component

Você está criando um componente React que permite a adição de notas de alunos por meio de um formulário e exibe estatísticas relacionadas a essas notas. O componente deve:

- Permitir que o usuário adicione notas por meio de um formulário.
- Exibir o número total de notas válidas e a média das notas válidas (considerando apenas notas entre 0 e 10).
- Exibir a maior e a menor nota válida.
- Validar as notas: caso uma nota seja inferior a 0 ou superior a 10, ela deve ser ignorada no cálculo das estatísticas.

### Entrada:

- Um formulário que permite ao usuário adicionar uma nova nota a cada envio.
- O valor da nota inserida no formulário deve ser tratado e armazenado no estado do componente.

### Saída:

O componente deve exibir as seguintes estatísticas:

- O número total de notas válidas.
- A média das notas válidas.
- A maior e a menor nota válida.

### Regras e Restrições:

- **Validação de Notas:** Notas que forem inferiores a 0 ou superiores a 10 devem ser ignoradas no cálculo das estatísticas.
- **Cálculos:** A média, maior e menor nota devem ser calculadas apenas com as notas válidas.
- **Gerenciamento de Estado:** O componente deve gerenciar o estado das notas inseridas de maneira eficiente e garantir que as estatísticas sejam atualizadas automaticamente após cada adição de nota.
- **Exibição:** O componente deve exibir as estatísticas de forma clara e legível para o usuário (tabela, listagem, etc).

### Exemplo básico

```jsx
import { useMemo, useState } from "react";

function StudentGradesStatistics() {
  const [grades, setGrades] = useState([]);
  const [newGrade, setNewGrade] = useState(0);

  const generateId = () => {
    return (
      Math.random().toString(36).substring(2, 15) +
      Math.random().toString(36).substring(2, 15)
    );
  };

  // Podemos usar o hook useCallback para essa função, mas o ganho computacional
  // não seria significativo, pois ela não realiza cálculos complexos e não é
  // passada como prop para um componente filho, o que diminui o impacto de
  // re-criação da função em cada renderização.

  const handleSubmit = (event) => {
    event.preventDefault();

    const formData = new FormData(event.target);
    const newGrade = formData.get("grade");
    const parsedGrade = Number(newGrade);

    if (!isNaN(parsedGrade) && parsedGrade <= 10 && parsedGrade >= 0) {
      setGrades((prev) => [...prev, { id: generateId(), value: parsedGrade }]);
      setNewGrade(0);
    } else {
      alert("Grade must be a number between 0 and 10");
    }
  };

  // O uso de useMemo para o cálculo de valores como a maior e menor nota, e a média,
  // pode ser benéfico se o número de elementos em grades crescer substancialmente.
  // Caso contrário, se grades tiver um tamanho pequeno, podemos remover o useMemo.
  // Utilizar o useMemo aqui também evita os cálculos desnecessários em caso de mudança
  // no estado newGrade

  const biggestGrade = useMemo(() => {
    return grades.length ? Math.max(...grades.map((g) => g.value)) : 0;
  }, [grades]);

  const smallestGrade = useMemo(() => {
    return grades.length ? Math.min(...grades.map((g) => g.value)) : 0;
  }, [grades]);

  const gradesAvg = useMemo(() => {
    return grades.length
      ? grades.reduce((prev, curr) => prev + curr.value, 0) / grades.length
      : 0;
  }, [grades]);

  return (
    <div>
      <h1>Grades Manager</h1>
      <form onSubmit={handleSubmit}>
        <input
          max={10}
          min={0}
          name="grade"
          onChange={(event) => {
            setNewGrade(Number(event.target.value));
          }}
          step={0.01}
          type="number"
          value={newGrade}
        />
        <button type="submit">Add grade</button>
      </form>
      <div>
        <h2>Grades list</h2>
        <ul>
          {grades.map(({ id, value }) => (
            <li key={id}>{value}</li>
          ))}
        </ul>
      </div>
      <div>
        <h2>Statistics</h2>
        <p>Grades average: {gradesAvg.toFixed(2)}</p>
        <p>Biggest grade: {biggestGrade}</p>
        <p>Smallest grade: {smallestGrade}</p>
      </div>
    </div>
  );
}

export default StudentGradesStatistics;
```
