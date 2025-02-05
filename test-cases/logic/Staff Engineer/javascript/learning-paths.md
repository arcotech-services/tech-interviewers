**Problema: Gerenciador de Trilhas de Aprendizagem**

Seu objetivo é criar um sistema que optimize a seleção de cursos para formar uma trilha de aprendizado que maximize a pontuação total de engajamento dos alunos, sem exceder um tempo máximo de duração permitido para a trilha. Cada curso tem uma pontuação de engajamento estimada e uma duração específica.

**Entrada:**
- Uma lista de objetos, cada um representando um curso com os seguintes atributos: `titulo` (string), `pontuacaoEngajamento` (inteiro), e `duracao` (inteiro).
- Um número máximo de duração permitida para a trilha de aprendizado.

**Saída:**
- A combinação de cursos que maximiza o valor total de engajamento sem exceder a duração máxima permitida.


[clique aqui para ter acesso a lista de cursos](https://gist.githubusercontent.com/MatheusKindrazki/69024cfb06463e1f1c5dfd24299fbd2f/raw/11a60feebec1a68a1f21c1105072d4bd8dec5148/courses-data.json)

**Exemplo:**
```javascript
const cursos = [
  { titulo: 'JavaScript Avançado', pontuacaoEngajamento: 9, duracao: 5 },
  { titulo: 'Design UX', pontuacaoEngajamento: 7, duracao: 4 },
  { titulo: 'Introdução a AI', pontuacaoEngajamento: 10, duracao: 6 },
  { titulo: 'Desenvolvimento Backend', pontuacaoEngajamento: 4, duracao: 3 }
];
const maxDuracao = 10;

function otimizarTrilha(cursos, maxDuracao) {
  // Solução a ser implementada
}

console.log(otimizarTrilha(cursos, maxDuracao));
// Saída esperada: combinação ótima de cursos com máximo engajamento
```


#### Saída de Exemplo:
```plaintext
{
  cursosSelecionados: ['JavaScript Avançado', 'Design UX'],
  pontuacaoEngajamentoTotal: 16,
  duracaoTotal: 9
}
```

### Descrição do Retorno

1. **cursosSelecionados:** Uma lista com os títulos dos cursos escolhidos, disponíveis na trilha de aprendizado.
2. **pontuacaoEngajamentoTotal:** A soma total das pontuações de engajamento dos cursos selecionados.
3. **duracaoTotal:** A soma total das durações de todos os cursos selecionados, garantindo que não exceda o `maxDuracao`.


### Regras Adicionais:
Para tornar o desafio mais realista e abrangente, sugerimos as seguintes regras e restrições:

1. **Processamento em Blocos:**
   - O algoritmo deve processar os cursos em blocos de tamanho 5. Isso significa que você não deve carregar todos os cursos na memória ao mesmo tempo, simulando o trabalho com grandes conjuntos de dados e testando sua capacidade de otimização de memória.

2. **Tempo Máximo de Execução:**
   - A execução do algoritmo deve ser concluída em menos de 100ms para uma lista de 200 cursos. Utilize ferramentas como `console.time()` para otimizar o tempo de execução.

3. **Limite de Complexidade:**
   - Garanta que a solução não exceda O(n log n). Projete uma solução eficiente que suporte o crescimento dos dados.

4. **Persistência de Estado:** _(opcional)_
   - Projete a solução de forma que, se o processamento for interrompido, possa retomar de onde parou sem reiniciar. Isso verifica a habilidade de implementar uma solução robusta que mantém o estado.

5. **Saída Detalhada:** _(opcional)_
   - Além de mostrar a combinação ideal de cursos, forneça um relatório sobre o tempo de execução, quantidade de memória usada e a complexidade do algoritmo.
