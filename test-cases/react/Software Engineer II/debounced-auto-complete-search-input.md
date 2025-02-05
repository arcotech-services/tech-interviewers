## Problema: Debounced Auto-Complete Search Input

Você está desenvolvendo um componente React que implementa um campo de busca com auto-complete, utilizando debounce para limitar as requisições e atualizações enquanto o usuário digita. O componente deve:
- Capturar a entrada do usuário e, utilizando debounce, chamar uma função assíncrona que retorna sugestões.
- Exibir as sugestões retornadas de forma dinâmica enquanto o usuário digita.
- Evitar requisições excessivas ao servidor, atualizando as sugestões somente após um intervalo configurável (por exemplo, 300ms).

### Entrada:
- Um input de texto onde o usuário digita a consulta.
- Uma função assíncrona `fetchSuggestions` que recebe o termo de pesquisa e retorna um array de sugestões.

### Saída:
- Um componente que exibe as sugestões de auto-complete logo abaixo do campo de busca.

### Regras e Restrições:
1. **Debounce:** Utilize uma técnica de debounce para limitar as requisições, de forma que a função `fetchSuggestions` seja chamada somente após um intervalo de tempo sem novas atualizações.
2. **Otimização:** A filtragem e atualização da lista de sugestões devem ser feitas de forma eficiente, sem causar travamentos na interface.
3. **Medição de Performance (Opcional):** Registre o tempo de resposta da função `fetchSuggestions` para fins de debug.

### Exemplo Básico:
```jsx
import React, { useState, useEffect } from 'react';

// Hook customizado para debouncing
function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => {
      clearTimeout(timer);
    };
  }, [value, delay]);

  return debouncedValue;
}

function DebouncedAutoCompleteSearch({ fetchSuggestions, debounceDelay = 300 }) {
  const [query, setQuery] = useState('');
  const [suggestions, setSuggestions] = useState([]);
  
  // Aplica debounce ao valor inserido
  const debouncedQuery = useDebounce(query, debounceDelay);

  useEffect(() => {
    if (debouncedQuery.trim() === '') {
      setSuggestions([]);
      return;
    }

    // Chama a função assíncrona para buscar sugestões
    fetchSuggestions(debouncedQuery).then(results => {
      setSuggestions(results);
    });
  }, [debouncedQuery, fetchSuggestions]);

  return (
    <div>
      <input
        type="text"
        placeholder="Digite para pesquisar..."
        value={query}
        onChange={(e) => setQuery(e.target.value)}
      />
      <ul>
        {suggestions.map((sugg, index) => (
          <li key={index}>{sugg}</li>
        ))}
      </ul>
    </div>
  );
}

export default DebouncedAutoCompleteSearch;
``` 