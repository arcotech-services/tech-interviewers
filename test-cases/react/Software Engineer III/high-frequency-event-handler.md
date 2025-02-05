## Problema: High Frequency Event Handler

Você está desenvolvendo um componente React que capta eventos de alta frequência, como os eventos de "mousemove". O objetivo do componente é melhorar a performance da aplicação utilizando técnicas de debounce para limitar a quantidade de atualizações de estado, evitando re-renderizações excessivas e possíveis travamentos.

### Entrada:
- Eventos de "mousemove" capturados pelo navegador.

### Saída:
- O componente deve exibir a posição atual do mouse (coordenadas x e y), atualizando o estado somente após um intervalo de debounce configurável (por exemplo, 200ms).

### Regras e Restrições:
1. **Debounce:** Implemente uma técnica de debounce para limitar a frequência de atualização do estado, de forma que o componente só processe os eventos após um intervalo de tempo determinado.
2. **Performance:** O componente não deve causar lentidão ou travamentos devido à alta frequência dos eventos.
3. **Personalização:** Permita a configuração do intervalo de debounce através de uma propriedade (prop) do componente.
4. **Complexidade:** Utilize hooks e técnicas como `useCallback` para evitar recriações desnecessárias de funções.

### Exemplo Básico:
```jsx
import React, { useState, useEffect, useCallback } from 'react';

// Hook customizado para debouncing
function useDebouncedCallback(callback, delay) {
  const [timeoutId, setTimeoutId] = useState(null);

  const debouncedFunction = useCallback((...args) => {
    if (timeoutId) {
      clearTimeout(timeoutId);
    }
    const id = setTimeout(() => {
      callback(...args);
    }, delay);
    setTimeoutId(id);
  }, [callback, delay, timeoutId]);

  return debouncedFunction;
}

function HighFrequencyEventHandler({ debounceDelay = 200 }) {
  const [mousePosition, setMousePosition] = useState({ x: null, y: null });

  const handleMouseMove = useDebouncedCallback((e) => {
    setMousePosition({ x: e.clientX, y: e.clientY });
  }, debounceDelay);

  useEffect(() => {
    window.addEventListener('mousemove', handleMouseMove);
    return () => {
      window.removeEventListener('mousemove', handleMouseMove);
    };
  }, [handleMouseMove]);

  return (
    <div>
      <h3>High Frequency Event Handler</h3>
      <p>Posição do Mouse: {mousePosition.x}, {mousePosition.y}</p>
    </div>
  );
}

export default HighFrequencyEventHandler;
``` 