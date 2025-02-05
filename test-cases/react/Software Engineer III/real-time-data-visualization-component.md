## Problema: Real-time Data Visualization Component

Você está desenvolvendo um componente React que se conecta a uma fonte de dados em tempo real e renderiza um gráfico que se atualiza dinamicamente. O componente deve:
- Se inscrever em um fluxo de dados em tempo real (por exemplo, utilizando WebSocket ou um simulador com `setInterval`).
- Renderizar um gráfico (por exemplo, um gráfico de linhas) que apresenta os dados recebidos de forma contínua.
- Otimizar a renderização para evitar re-renderizações desnecessárias, utilizando técnicas como memoization ou componentes puros.
- Medir ou logar métricas de desempenho (como tempo entre atualizações) no console.

### Entrada:
- Uma função `subscribeToData` que simula a emissão de dados em tempo real (pode ser implementada com `setInterval`).

### Saída:
- Um componente que exibe um gráfico dinâmico com os dados em tempo real e apresenta um fallback de carregamento inicial.

### Regras e Restrições:
1. **Assincronia e Subscrição:**
   - O componente deve se inscrever ao fluxo de dados em tempo real ao montar e se desinscrever ao desmontar.
2. **Otimização de Renderização:**
   - Utilize técnicas de memoization (ex: `React.memo` ou `useMemo`) para evitar re-renderizações desnecessárias ao atualizar o gráfico.
3. **Medição de Performance:**
   - Registre métricas de desempenho, como o tempo entre atualizações, utilizando `console.time` ou `console.log`.
4. **Fallback Inicial:**
   - Utilize `Suspense` ou um estado de carregamento para exibir um fallback enquanto o primeiro lote de dados é recebido.

### Exemplo Básico:
```jsx
import React, { useState, useEffect, useMemo } from 'react';

// Função que simula a inscrição em um fluxo de dados em tempo real
function subscribeToData(callback) {
  const intervalId = setInterval(() => {
    // Gera um número aleatório como dado
    const newData = Math.floor(Math.random() * 100);
    callback(newData);
  }, 1000);
  
  return () => clearInterval(intervalId);
}

function RealTimeChart() {
  const [data, setData] = useState([]);

  useEffect(() => {
    console.time('firstData');
    const unsubscribe = subscribeToData(newData => {
      setData(prevData => {
        const updated = [...prevData, newData];
        // Log de exemplo para medir o tempo entre atualizações
        console.log('Novo dado recebido:', newData);
        return updated;
      });
      console.timeEnd('firstData');
    });
    
    return () => {
      unsubscribe();
    };
  }, []);

  // Use useMemo para evitar re-renderizações desnecessárias do gráfico
  const chartData = useMemo(() => {
    // Simula o processamento de dados para o gráfico
    return data.map((point, index) => ({ x: index, y: point }));
  }, [data]);

  return (
    <div>
      <h3>Real-time Data Visualization</h3>
      {chartData.length === 0 ? (
        <div>Carregando dados...</div>
      ) : (
        <ul>
          {chartData.map(item => (
            <li key={item.x}>Tempo {item.x}: {item.y}</li>
          ))}
        </ul>
      )}
    </div>
  );
}

export default RealTimeChart;

// Nota: Em uma aplicação real, utilize uma biblioteca de gráficos, como Recharts ou Victory, para renderizar o gráfico visualmente.
``` 