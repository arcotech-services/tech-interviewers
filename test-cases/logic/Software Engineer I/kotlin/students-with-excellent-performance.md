## Problema: Identificação de Estudantes com Desempenho Excelente

Requisitos:

1) Dado um grupo de estudantes e suas médias anuais, o programa deve identificar:
    - Estudantes com média maior ou igual a 9.0.
    - Estudantes que ficaram abaixo de 7.0 (indicando necessidade de recuperação).
2) A lista de estudantes e suas médias deve ser pré-definida.
3) O programa deve exibir:
    - A quantidade de estudantes excelentes (média ≥ 9.0).
    - A quantidade de estudantes em recuperação (média < 7.0).
    - Uma lista detalhada com os nomes e suas classificações (Excelente, Recuperação, Regular).


### Exemplo

```kotlin
data class Estudante(
    val nome: String,
    val mediaAnual: Double,
)

fun main() {
    val estudantes = listOf(
        Estudante("Ana", 9.5),
        Estudante("Carlos", 6.8),
        Estudante("Maria", 8.0),
        Estudante("Pedro", 7.2),
        Estudante("Lucas", 9.0),
        Estudante("Júlia", 6.5),
        Estudante("Fernanda", 8.5),
    )

    val estudantesExcelentes = estudantes.filter { it -> it.mediaAnual >= 9.0 }
    val estudantesEmRecuperacao = estudantes.filter { it -> it.mediaAnual < 7.0 }
    val estudantesRegulares = estudantes.filter { it -> it.mediaAnual >= 7.0 && it.mediaAnual < 9.0 }
    
    println("Alunos Excelentes (média ≥ 9.0): "+ estudantesExcelentes.joinToString(", ") { it.nome })
    println("Alunos em Recuperação (média < 7.0): "+ estudantesEmRecuperacao.joinToString(", ") { it.nome })
    println("Alunos Regulares (média entre 7.0 e 8.9): "+ estudantesRegulares.joinToString(", ") { it.nome })
}

```

#### Saída

```shell
Alunos Excelentes (média ≥ 9.0): Ana, Lucas
Alunos em Recuperação (média < 7.0): Carlos, Júlia
Alunos Regulares (média entre 7.0 e 8.9): Maria, Pedro, Fernanda
```