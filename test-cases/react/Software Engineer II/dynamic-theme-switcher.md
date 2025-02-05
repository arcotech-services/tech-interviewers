## Problema: Dynamic Theme Switcher

Você está desenvolvendo um componente React que permite a troca dinâmica de temas (claro/escuro) na aplicação. O componente deve:
- Utilizar a React Context API para gerenciar o estado do tema globalmente.
- Persistir a escolha do tema no localStorage para que a preferência seja mantida após o recarregamento da página.
- Medir o desempenho da troca de tema e registrar métricas de renderização no console.
- Fornecer uma interface com um botão para alternar entre os temas.

### Entrada:
- Interação do usuário, através de um clique em um botão para alternar o tema.

### Saída:
- A aplicação altera seu tema (claro/escuro), e a escolha é salva no localStorage.
- Métricas de desempenho (ex: tempo de troca) são registradas no console.

### Regras e Restrições:
1. **Gerenciamento de Estado:** Utilize a React Context API para gerenciar o estado do tema de forma global.
2. **Persistência:** Utilize localStorage para salvar e recuperar a preferência do tema.
3. **Medição de Performance:** Utilize `console.time` e `console.timeEnd` para medir o tempo de troca de tema.
4. **Interface:** Forneça um botão para alternar o tema.

### Exemplo Básico:
```jsx
import React, { createContext, useState, useEffect, useContext } from 'react';

const ThemeContext = createContext();

export function ThemeProvider({ children }) {
  const [theme, setTheme] = useState('light');

  useEffect(() => {
    const storedTheme = localStorage.getItem('themePreference');
    if (storedTheme) {
      setTheme(storedTheme);
    }
  }, []);

  const toggleTheme = () => {
    console.time('themeToggle');
    const newTheme = theme === 'light' ? 'dark' : 'light';
    setTheme(newTheme);
    localStorage.setItem('themePreference', newTheme);
    console.timeEnd('themeToggle');
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

export function useTheme() {
  return useContext(ThemeContext);
}

function DynamicThemeSwitcher() {
  const { theme, toggleTheme } = useTheme();
  const styles = {
    background: theme === 'light' ? '#fff' : '#333',
    color: theme === 'light' ? '#333' : '#fff',
    padding: '20px',
    textAlign: 'center'
  };

  return (
    <div style={styles}>
      <h2>Dynamic Theme Switcher</h2>
      <p>Tema atual: {theme}</p>
      <button onClick={toggleTheme}>Alternar Tema</button>
    </div>
  );
}

export default DynamicThemeSwitcher;
``` 