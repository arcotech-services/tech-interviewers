## Problema: Cálculo da Média Total Anual

Requisitos:

- O ano letivo é dividido em 4 bimestres.
- Cada bimestre terá 4 notas avaliativas.
- O programa deve:
    - Calcular a média de cada bimestre.
    - Calcular a média anual baseada nas médias dos 4 bimestres.
- O programa deve validar que todas as notas estão no intervalo de 0 a 10.
- As médias devem ser arredondadas para 2 casas decimais.
- Exiba as médias de cada bimestre e a média anual ao final.
- As notas devem estar pré-definidas no código (não será necessário o usuário digitar).

### Exemplo

```kotlin
data class Nota(val valor: Double) {
    init {
        require(valor in 0.0..10.0) { "A nota deve ser entre 0 e 10." }
    }
}

data class Bimestre(
    val nome: String, 
    val nota1: Nota, 
    val nota2: Nota, 
    val nota3: Nota, 
    val nota4: Nota
) {
    private val notas = listOf(nota1, nota2, nota3, nota4)
    val media: Double

    init {
        media = calcularMedia()
    }

    private fun calcularMedia(): Double {
        val mediaCalculada = notas.map { it.valor }.average()
        return "%.2f".format(mediaCalculada).toDouble()
    }
}

fun main() {
    val bimestres = listOf(
        Bimestre("Bimestre 1", Nota(8.5), Nota(7.0), Nota(9.0), Nota(10.0)),
        Bimestre("Bimestre 2", Nota(6.5), Nota(7.5), Nota(8.0), Nota(9.0)),
        Bimestre("Bimestre 3", Nota(7.0), Nota(7.0), Nota(8.5), Nota(9.5)),
        Bimestre("Bimestre 4", Nota(9.0), Nota(8.0), Nota(8.0), Nota(9.0)),
    )

    bimestres.forEach { bimestre ->
        println("${bimestre.nome}: Média = ${bimestre.media}")
    }

    val somaMedias = bimestres.sumOf { bimestre -> bimestre.media }
    val mediaAnual = "%.2f".format(somaMedias / bimestres.size)

    println("Média Anual: $mediaAnual")
}
```

#### Saída

```shell
Bimestre 1: Média = 8.63
Bimestre 2: Média = 7.75
Bimestre 3: Média = 8.0
Bimestre 4: Média = 8.5
Média Anual: 8.22
```