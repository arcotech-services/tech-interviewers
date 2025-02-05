# Simple Form Validation Component

## Problema

Desenvolva um componente de formulário simples utilizando React que valide entradas em tempo real. Por exemplo, valide se um endereço de email informado possui um formato correto.

## Objetivo

Criar um componente de formulário que permita ao usuário inserir dados (como um email) e que exiba mensagens de erro em tempo real caso a entrada não atenda aos critérios de validação.

## Requisitos

1. **Entrada de Dados:**
   - Exibir um campo de entrada para o usuário digitar um endereço de email.

2. **Validação em Tempo Real:**
   - Validar o formato do email conforme o usuário digita.
   - Exibir uma mensagem de erro abaixo do campo caso o email seja inválido.

3. **Feedback Visual:**
   - Alterar o estilo do campo (ex: borda vermelha) em caso de erro.
   - Remover a mensagem de erro e o estilo alterado quando o email se tornar válido.

4. **Uso de Hooks:**
   - Utilizar um componente funcional com o hook useState para gerenciar o estado da entrada e a mensagem de erro.

5. **Interação com o Usuário:**
   - Adicionar um botão de envio que só esteja habilitado quando a entrada for válida.

## Exemplo de Uso

- O usuário inicia a aplicação e vê um campo para inserir o email.
- Ao digitar um email com formato incorreto, uma mensagem de erro "Email inválido" é exibida e o campo recebe destaque visual (ex: borda vermelha).
- Quando o usuário corrige o email, a mensagem de erro some e o botão de envio é habilitado.

## Considerações

- Mantenha o código limpo e organizado com uma clara separação de responsabilidades.
- Utilize apenas as bibliotecas necessárias e as funcionalidades do React para criar a solução.
- Considere adicionar comentários ao código para explicar a lógica de validação.

## Avaliação

Este desafio avalia:
- Conhecimento básico de React, especialmente o uso de hooks (useState).
- Capacidade de implementar validação em tempo real em formulários.
- Habilidade de manipulação de estados e feedback visual de erros.

Boa sorte! 