## Problema: Optimized List Filtering Component

Você está desenvolvendo um componente React que renderiza eficientemente uma lista grande de itens e permite a filtragem dinâmica. O componente deve:
- Renderizar uma lista grande de itens utilizando virtualização (por exemplo, com `react-window`) para melhorar a performance.
- Permitir a filtragem da lista através de uma barra de pesquisa.
- Atualizar a lista renderizada de forma eficiente conforme o usuário digita.
- Manter uma boa performance mesmo com milhares de itens.

### Entrada:
- Uma lista grande de itens (ex: um array com 1000+ strings).
- Um termo de busca fornecido pelo usuário para filtrar os itens.

### Saída:
- Um componente que exibe os itens filtrados usando virtualização para renderização.

### Regras e Restrições:
1. **Virtualização de Lista:** Utilize uma biblioteca como `react-window` para renderizar a lista de forma virtual.
2. **Filtragem Dinâmica:** Implemente a filtragem dos itens de forma que a lista atualize enquanto o usuário digita.
3. **Otimização de Performance:** A atualização do componente deve ser feita de forma eficiente para não travar a interface.

### Exemplo Básico:
```jsx
import React, { useState, useMemo } from 'react';
import { FixedSizeList as List } from 'react-window';

function OptimizedListFiltering({ items }) {
  const [filter, setFilter] = useState('');
  
  const filteredItems = useMemo(() => {
    return items.filter(item => item.toLowerCase().includes(filter.toLowerCase()));
  }, [items, filter]);
  
  const Row = ({ index, style }) => (
    <div style={style}>
      {filteredItems[index]}
    </div>
  );
  
  return (
    <div>
      <input
        type='text'
        placeholder='Filtrar itens...'
        value={filter}
        onChange={(e) => setFilter(e.target.value)}
      />
      <List
        height={400}
        itemCount={filteredItems.length}
        itemSize={35}
        width='100%'
      >
        {Row}
      </List>
    </div>
  );
}

export default OptimizedListFiltering;
``` 