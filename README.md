# QUANTUM-CHAOS
GROOVY
#!/usr/bin/env groovy

import java.util.concurrent.*
import java.security.MessageDigest
import java.math.BigDecimal
import java.math.MathContext
import java.util.Random

println "==============================="
println "      QUANTUM CHAOS START"
println "==============================="

// ========================================
// 1. Logistic Chaos Sequence
// ========================================
class ChaosMath {

    static List<BigDecimal> logistic(double r, double x0, int iterations) {
        def results = []
        BigDecimal x = new BigDecimal(x0, MathContext.DECIMAL128)

        iterations.times {
            x = r * x * (1 - x)
            results << x
        }
        return results
    }

    static BigInteger factorial(int n) {
        if (n <= 1) return 1
        return n * factorial(n - 1)
    }

    static BigInteger power(BigInteger base, int exp) {
        if (exp == 0) return 1
        return base * power(base, exp - 1)
    }
}

// ========================================
// 2. Algorithmic ASCII Art Generator
// ========================================
class ArtGenerator {

    static void wavePattern(int height, int width) {
        for (int i = 0; i < height; i++) {
            String line = ""
            for (int j = 0; j < width; j++) {
                double value = Math.sin((i + j) * 0.3)
                if (value > 0.5)
                    line += "*"
                else if (value > 0)
                    line += "+"
                else
                    line += "."
            }
            println line
        }
    }

    static void spiral(int size) {
        char[][] matrix = new char[size][size]
        int top = 0, bottom = size - 1
        int left = 0, right = size - 1

        while (true) {
            if (left > right) break
            for (int i = left; i <= right; i++)
                matrix[top][i] = '#'
            top++

            if (top > bottom) break
            for (int i = top; i <= bottom; i++)
                matrix[i][right] = '#'
            right--

            if (left > right) break
            for (int i = right; i >= left; i--)
                matrix[bottom][i] = '#'
            bottom--

            if (top > bottom) break
            for (int i = bottom; i >= top; i--)
                matrix[i][left] = '#'
            left++
        }

        matrix.each { row ->
            println row.collect { it ?: ' ' }.join()
        }
    }
}

// ========================================
// 3. Cryptographic Distortion
// ========================================
class CryptoWarp {

    static String sha512(String input) {
        MessageDigest md = MessageDigest.getInstance("SHA-512")
        byte[] hash = md.digest(input.bytes)
        return hash.collect { String.format("%02x", it) }.join()
    }

    static String chaosEncrypt(String text) {
        String reversed = text.reverse()
        String mixed = reversed.collect { (it as char) + 3 }.join()
        return sha512(mixed)
    }
}

// ========================================
// 4. Parallel Universe Computation
// ========================================
class ParallelDimension {

    static void runThreads() {
        ExecutorService executor = Executors.newFixedThreadPool(3)

        3.times { index ->
            executor.submit {
                Random rand = new Random()
                println "Thread ${index} starting..."

                5.times {
                    int value = rand.nextInt(1000)
                    println "Thread ${index} => ${value * value}"
                    sleep(200)
                }

                println "Thread ${index} finished."
            }
        }

        executor.shutdown()
        executor.awaitTermination(5, TimeUnit.SECONDS)
    }
}

// ========================================
// 5. Functional Stream Transformations
// ========================================
class FunctionalFlux {

    static void transform() {
        def numbers = (1..20).toList()

        def result = numbers
                .findAll { it % 2 == 0 }
                .collect { it * it }
                .collect { it + 5 }
                .sort()

        println "Functional Result: ${result}"
    }
}

// ========================================
// MAIN EXECUTION FLOW
// ========================================

println "\n-- CHAOTIC LOGISTIC MAP --"
def chaos = ChaosMath.logistic(3.9, 0.5, 15)
chaos.eachWithIndex { val, index ->
    println "Step ${index} : ${val}"
}

println "\n-- FACTORIAL 15 --"
println ChaosMath.factorial(15)

println "\n-- WAVE PATTERN --"
ArtGenerator.wavePattern(15, 60)

println "\n-- SPIRAL ART --"
ArtGenerator.spiral(20)

println "\n-- CRYPTO DISTORTION --"
println CryptoWarp.chaosEncrypt("Braj Kishor Das Groovy Power")

println "\n-- PARALLEL DIMENSION --"
ParallelDimension.runThreads()

println "\n-- FUNCTIONAL FLUX --"
FunctionalFlux.transform()

println "\n==============================="
println "      QUANTUM CHAOS END"
println "==============================="
# OUTPUT
https://i.supaimg.com/c6c1103a-90cd-4aa6-bdab-712bef40ba41.png
