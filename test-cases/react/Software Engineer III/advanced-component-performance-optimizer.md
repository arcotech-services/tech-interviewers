## Problema: Advanced Component Performance Optimizer

Você está desenvolvendo um componente React avançado que carrega dados de forma assíncrona utilizando Lazy Loading e Suspense. O componente deve:
- Carregar um conjunto grande de dados de forma assíncrona, utilizando `React.lazy` para divisão de código (code splitting).
- Utilizar `Suspense` para exibir um fallback enquanto os dados estão sendo carregados.
- Implementar um Error Boundary para capturar e tratar erros durante o carregamento.
- Medir o desempenho do componente (por exemplo, tempo de renderização) e exibir essas métricas no console.
- Se necessário, processar renderizações em blocos para não bloquear a interface.

### Entrada:
- Uma função assíncrona `fetchData` que retorna uma lista de itens (por exemplo, um array de objetos).

### Saída:
- Um componente que exibe a lista de itens carregados e um fallback de carregamento enquanto os dados são recuperados, além de exibir métricas de desempenho no console.

### Regras e Restrições:
1. **Divisão de Código:** Utilize `React.lazy` para carregar o componente que renderiza os dados.
2. **Medição de Performance:** Utilize ferramentas do React ou APIs do browser para medir o tempo de renderização.
3. **Tratamento de Erros:** Implemente um Error Boundary para capturar erros durante o carregamento.
4. **Processamento em Blocos (Opcional):** Se o conjunto de dados for muito grande, processe a renderização em blocos.
5. **Tempo Máximo de Execução:** A operação de carregamento e renderização deve ser realizada de forma eficiente.

### Exemplo Básico:
```jsx
import React, { Suspense } from 'react';

const DataComponent = React.lazy(() => import('./DataComponent'));

function AdvancedComponent() {
  console.time('renderTime');
  return (
    <Suspense fallback={<div>Carregando dados...</div>}>
      <DataComponent fetchData={fetchData} />
    </Suspense>
  );
}

export default AdvancedComponent;

// Em DataComponent, implemente a lógica de fetch e renderização da lista de dados.
``` 