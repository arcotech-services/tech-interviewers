## Problema: Simple Counter Component

Você está desenvolvendo um componente React simples que demonstra o gerenciamento de estado utilizando o hook useState. O componente deve:
- Exibir o valor atual do contador.
- Permitir incrementar o contador ao clicar em um botão.
- Permitir decrementar o contador ao clicar em outro botão.
- Opcionalmente, permitir resetar o contador para o valor inicial.

### Entrada:
- Um valor inicial (opcional, default = 0).

### Saída:
- Um componente que renderiza o valor atual do contador e botões para incrementar, decrementar e resetar o valor.

### Regras e Restrições:
1. O componente deve ser implementado utilizando o hook useState para gerenciamento de estado.
2. Deve atualizar a exibição do contador conforme os botões são clicados.
3. O código deve ser claro, conciso e de fácil entendimento.

### Exemplo Básico:
```jsx
import React, { useState } from 'react';

function SimpleCounter({ initialValue = 0 }) {
  const [count, setCount] = useState(initialValue);

  return (
    <div>
      <h2>Contador: {count}</h2>
      <button onClick={() => setCount(count + 1)}>Incrementar</button>
      <button onClick={() => setCount(count - 1)}>Decrementar</button>
      <button onClick={() => setCount(initialValue)}>Resetar</button>
    </div>
  );
}

export default SimpleCounter;
``` 