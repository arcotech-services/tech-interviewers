## Problema: Sistema de Gestão de Frequência Escolar

Requisitos:

1) O curso tem **4 meses**, e cada mês tem **20 aulas**.
2) Cada aluno terá um registro de **presenças** (quantas aulas ele compareceu por mês).
3) O sistema deve calcular:
    - A **frequência mensal** (porcentagem de aulas frequentadas no mês).
    - A **frequência anual** (média das frequências mensais).
    - Se o aluno está **aprovado** ou **reprovado** por falta.
4) O critério de aprovação é uma frequência **mínima de 75%** no total das aulas.
5) O sistema deve validar que a quantidade de aulas frequentadas está entre **0 e 20** por mês.
6) A saída deve exibir a **frequência mensal, frequência anual e status de aprovação**.
7) Os dados de presença devem estar **pré-definidos no código**.
8) O programa deve ser implementado utilizando **POO (Programação Orientada a Objetos)**.

### Exemplo

```kotlin
data class FrequenciaMensal(
    val mes: String,
    val frequencia: Int
) {
    val porcentagem: Double

    companion object {
        const val MAX_FREQUENCIA = 20
    }

    init {
        require(frequencia in 0..MAX_FREQUENCIA) { "O número de aulas frequentadas deve estar entre 0 e $MAX_FREQUENCIA" }
        porcentagem = calcularPorcentagem()
    }

    private fun calcularPorcentagem(): Double {
        return (frequencia.toDouble() / MAX_FREQUENCIA) * 100
    }
}

data class Estudante(
    val nome: String,
    val frequenciasMensais: List<FrequenciaMensal>
)

enum class Situacao {
    Aprovado,
    Reprovado
}

class SituacaoEstudante(
    val estudante: Estudante
) {
    val situacao: Situacao
    val mediaFrequenciaAnual: Double

    init {
        mediaFrequenciaAnual = estudante
            .frequenciasMensais
            .map { it.porcentagem }
            .average()

        situacao = if (estahAprovado()) Situacao.Aprovado else Situacao.Reprovado
    }

    private fun estahAprovado(): Boolean {
        return mediaFrequenciaAnual >= 75
    }
}

fun main() {
    val frequencias = listOf(
        FrequenciaMensal("Janeiro", 18),
        FrequenciaMensal("Fevereiro", 16),
        FrequenciaMensal("Março", 14),
        FrequenciaMensal("Abril", 20),
    )

    val estudante = Estudante("Carlos", frequencias)

    val situacaoEstudante = SituacaoEstudante(estudante)

    println("Aluno: ${estudante.nome}")
    println("Situacao: ${situacaoEstudante.situacao}")
    estudante.frequenciasMensais.forEach {
        println("${it.mes}: ${it.porcentagem}% de frequência")
    }
    println("Média frequência anual: ${situacaoEstudante.mediaFrequenciaAnual}")
}

```

#### Saída

```shell
Aluno: Carlos
Situacao: Aprovado
Janeiro: 90.0% de frequência
Fevereiro: 80.0% de frequência
Março: 70.0% de frequência
Abril: 100.0% de frequência
Média frequência anual: 85.0
```