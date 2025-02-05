## Problema: Análise Estatística do Desempenho Acadêmico

Requisitos:

1) Um grupo de **15 estudantes** tem suas notas registradas para cada um dos 4 bimestres.
2) Cada estudante tem exatamente **4 notas por bimestre** (como no primeiro teste).
3) O programa deve:
    - Calcular a **média anual** de cada estudante.
    - Identificar:
        - **Top 3 melhores estudantes** (com base na média anual).
        - **Estudantes com maior progresso** (a maior diferença positiva entre o primeiro e o último bimestre).
        - **Estudantes com notas constantes** (diferença entre as médias dos bimestres nunca ultrapassa 1.0).
    - Exibir:
        - A lista dos **Top 3 estudantes** (nome e média anual).
        - O **estudante com maior progresso** (nome e progresso).
        - A lista de estudantes com **notas constantes**.
4) Todos os dados devem ser pré-definidos no código.
5) As médias e diferenças devem ser arredondadas para **2 casas decimais**.

### Exemplo

```kotlin
import kotlin.math.abs

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

data class Estudante(
    val nome: String,
    val bimestre1: Bimestre,
    val bimestre2: Bimestre,
    val bimestre3: Bimestre,
    val bimestre4: Bimestre,
) {
    private val bimestres = listOf(bimestre1, bimestre2, bimestre3, bimestre4)
    val mediaAnual: Double 
    val progresso: Double
    val temNotasConstantes: Boolean

    init {
        mediaAnual = calcularMedia()
        progresso = bimestre4.media - bimestre1.media
        temNotasConstantes = temNotasConstantes()
    }

    private fun calcularMedia(): Double {
        val mediaCalculada = bimestres.map { it.media }.average()
        return "%.2f".format(mediaCalculada).toDouble()
    }

    private fun temNotasConstantes(): Boolean {
        val medias = bimestres.map { it.media }
        for (i in 1 until medias.size) {
            if (abs(medias[i] - medias[i - 1]) > 1.0) {
                return false
            }
        }
        return true
    }
}

fun main() {
    val estudantes = listOf(
        Estudante(
            "Ana",
            Bimestre("Bimestre 1", Nota(8.0), Nota(7.5), Nota(9.0), Nota(8.5)),
            Bimestre("Bimestre 2", Nota(8.5), Nota(8.0), Nota(9.0), Nota(8.5)),
            Bimestre("Bimestre 3", Nota(9.0), Nota(8.5), Nota(9.5), Nota(9.0)),
            Bimestre("Bimestre 4", Nota(9.5), Nota(9.0), Nota(9.0), Nota(9.5))
        ),
        Estudante(
            "Carlos",
            Bimestre("Bimestre 1", Nota(6.0), Nota(6.5), Nota(7.0), Nota(6.8)),
            Bimestre("Bimestre 2", Nota(7.0), Nota(7.5), Nota(8.0), Nota(7.8)),
            Bimestre("Bimestre 3", Nota(7.5), Nota(8.0), Nota(8.5), Nota(8.2)),
            Bimestre("Bimestre 4", Nota(8.5), Nota(8.8), Nota(9.0), Nota(8.9))
        ),
        Estudante(
            "Maria",
            Bimestre("Bimestre 1", Nota(9.0), Nota(8.5), Nota(9.5), Nota(9.0)),
            Bimestre("Bimestre 2", Nota(9.0), Nota(8.8), Nota(9.0), Nota(9.2)),
            Bimestre("Bimestre 3", Nota(9.2), Nota(9.0), Nota(9.5), Nota(9.3)),
            Bimestre("Bimestre 4", Nota(9.5), Nota(9.5), Nota(9.5), Nota(9.5))
        ),
        Estudante(
            "Pedro",
            Bimestre("Bimestre 1", Nota(7.0), Nota(6.5), Nota(7.0), Nota(7.0)),
            Bimestre("Bimestre 2", Nota(6.8), Nota(7.0), Nota(7.5), Nota(7.2)),
            Bimestre("Bimestre 3", Nota(7.5), Nota(7.5), Nota(8.0), Nota(7.8)),
            Bimestre("Bimestre 4", Nota(8.0), Nota(8.0), Nota(8.5), Nota(8.2))
        ),
        Estudante(
            "Lucas",
            Bimestre("Bimestre 1", Nota(8.5), Nota(8.0), Nota(9.0), Nota(8.5)),
            Bimestre("Bimestre 2", Nota(9.0), Nota(9.0), Nota(9.5), Nota(9.2)),
            Bimestre("Bimestre 3", Nota(9.5), Nota(9.5), Nota(9.8), Nota(9.5)),
            Bimestre("Bimestre 4", Nota(10.0), Nota(9.8), Nota(10.0), Nota(10.0))
        ),
        Estudante(
            "Júlia",
            Bimestre("Bimestre 1", Nota(6.0), Nota(6.0), Nota(6.5), Nota(6.2)),
            Bimestre("Bimestre 2", Nota(6.5), Nota(6.8), Nota(7.0), Nota(6.5)),
            Bimestre("Bimestre 3", Nota(7.0), Nota(7.2), Nota(7.5), Nota(7.0)),
            Bimestre("Bimestre 4", Nota(7.5), Nota(7.8), Nota(8.0), Nota(7.8))
        ),
        Estudante(
            "Fernanda",
            Bimestre("Bimestre 1", Nota(8.0), Nota(8.0), Nota(8.5), Nota(8.2)),
            Bimestre("Bimestre 2", Nota(8.5), Nota(8.5), Nota(9.0), Nota(8.8)),
            Bimestre("Bimestre 3", Nota(9.0), Nota(9.0), Nota(9.5), Nota(9.2)),
            Bimestre("Bimestre 4", Nota(9.5), Nota(9.5), Nota(10.0), Nota(9.8))
        ),
        Estudante(
            "Rafael",
            Bimestre("Bimestre 1", Nota(7.0), Nota(7.5), Nota(8.0), Nota(7.5)),
            Bimestre("Bimestre 2", Nota(8.0), Nota(8.5), Nota(9.0), Nota(8.5)),
            Bimestre("Bimestre 3", Nota(9.0), Nota(9.5), Nota(10.0), Nota(9.5)),
            Bimestre("Bimestre 4", Nota(10.0), Nota(10.0), Nota(10.0), Nota(10.0))
        ),
        Estudante(
            "Sophia",
            Bimestre("Bimestre 1", Nota(5.5), Nota(6.0), Nota(6.5), Nota(6.0)),
            Bimestre("Bimestre 2", Nota(6.0), Nota(6.5), Nota(7.0), Nota(6.5)),
            Bimestre("Bimestre 3", Nota(7.0), Nota(7.5), Nota(8.0), Nota(7.5)),
            Bimestre("Bimestre 4", Nota(8.5), Nota(9.0), Nota(9.5), Nota(9.0))
        ),
        Estudante(
            "Gabriel",
            Bimestre("Bimestre 1", Nota(8.0), Nota(8.0), Nota(8.5), Nota(8.0)),
            Bimestre("Bimestre 2", Nota(8.5), Nota(8.5), Nota(9.0), Nota(8.5)),
            Bimestre("Bimestre 3", Nota(9.0), Nota(9.0), Nota(9.5), Nota(9.2)),
            Bimestre("Bimestre 4", Nota(9.5), Nota(9.8), Nota(10.0), Nota(9.8))
        ),
        Estudante(
            "Isabela",
            Bimestre("Bimestre 1", Nota(7.5), Nota(7.0), Nota(7.5), Nota(7.2)),
            Bimestre("Bimestre 2", Nota(7.8), Nota(7.8), Nota(8.0), Nota(7.8)),
            Bimestre("Bimestre 3", Nota(8.0), Nota(8.2), Nota(8.5), Nota(8.2)),
            Bimestre("Bimestre 4", Nota(8.5), Nota(8.8), Nota(9.0), Nota(8.8))
        ),
        Estudante(
            "Felipe",
            Bimestre("Bimestre 1", Nota(6.0), Nota(6.5), Nota(7.0), Nota(6.5)),
            Bimestre("Bimestre 2", Nota(7.0), Nota(7.5), Nota(8.0), Nota(7.5)),
            Bimestre("Bimestre 3", Nota(8.0), Nota(8.5), Nota(9.0), Nota(8.5)),
            Bimestre("Bimestre 4", Nota(9.0), Nota(9.5), Nota(10.0), Nota(9.5))
        ),
        Estudante(
            "Lara",
            Bimestre("Bimestre 1", Nota(8.0), Nota(7.5), Nota(8.0), Nota(7.8)),
            Bimestre("Bimestre 2", Nota(8.2), Nota(8.5), Nota(8.5), Nota(8.5)),
            Bimestre("Bimestre 3", Nota(8.8), Nota(9.0), Nota(9.2), Nota(9.0)),
            Bimestre("Bimestre 4", Nota(9.5), Nota(9.8), Nota(10.0), Nota(9.8))
        ),
        Estudante(
            "Mariana",
            Bimestre("Bimestre 1", Nota(6.5), Nota(6.0), Nota(6.8), Nota(6.5)),
            Bimestre("Bimestre 2", Nota(7.0), Nota(7.2), Nota(7.5), Nota(7.2)),
            Bimestre("Bimestre 3", Nota(7.8), Nota(8.0), Nota(8.2), Nota(8.0)),
            Bimestre("Bimestre 4", Nota(8.5), Nota(8.8), Nota(9.0), Nota(8.8))
        ),
        Estudante(
            "Henrique",
            Bimestre("Bimestre 1", Nota(7.0), Nota(7.5), Nota(8.0), Nota(7.5)),
            Bimestre("Bimestre 2", Nota(8.0), Nota(8.5), Nota(9.0), Nota(8.5)),
            Bimestre("Bimestre 3", Nota(9.0), Nota(9.5), Nota(10.0), Nota(9.5)),
            Bimestre("Bimestre 4", Nota(10.0), Nota(10.0), Nota(10.0), Nota(10.0))
        )
    )

    val top3 = estudantes.sortedByDescending { it.mediaAnual }.take(3)
    println("Top 3 Estudantes:")
    top3.forEach { println("${it.nome}: ${it.mediaAnual}") }
    println("")
    
    val maiorProgresso = estudantes.maxByOrNull { it.progresso }
    println("Estudante com Maior Progresso: ${maiorProgresso?.nome} (${"%.2f".format(maiorProgresso?.progresso)} pontos de progresso)\n")
    
    val constantes = estudantes.filter { it.temNotasConstantes }
    println("Estudantes com Notas Constantes: "+ constantes.joinToString(", ") { it.nome })
}
```

#### Saída

```shell
Top 3 Estudantes:
Lucas: 9.3
Maria: 9.19
Fernanda: 8.94

Estudante com Maior Progresso: Sophia (3.00 pontos de progresso)

Estudantes com Notas Constantes: Ana, Carlos, Maria, Pedro, Lucas, Júlia, Fernanda, Rafael, Gabriel, Isabela, Felipe, Lara, Mariana, Henrique
```