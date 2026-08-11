# atividadesKotlin
Registro de scripts de resposta das atividades

Hello World

fun main() {
    val name = "Mary"
    val age = 20
    
    println("$name is $age years old")
}

Basic types

fun main() {
    val a: Int = 1000 
    val b: String = "log message"
    val c: Double = 3.14
    val d: Long = 100_000_000_000_000
    val e: Boolean = false
    val f: Char = '\n'
    
    println(a)
    println(b)
    println(c)
    println(d)
    println(e)
}

Collections

Exercicio 1

fun main() {
    val greenNumbers = listOf(1, 4, 23)
    val redNumbers = listOf(17, 2)

    println(greenNumbers.size + redNumbers.size)
}

Exercicio 2

fun main() {
    val SUPPORTED = setOf("HTTP", "HTTPS", "FTP")
    val requested = "smtp"

    val isSupported = SUPPORTED.contains(requested.uppercase())

    println("Support for $requested: $isSupported")
}

Exercicio 3

fun main() {
    val number2word = mapOf(
        1 to "one",
        2 to "two",
        3 to "three"
    )

    val n = 2

    println("$n is spelled as '${number2word[n]}'")
}

Control flow

Conditional expressions practice﻿

Exercicio 1

import kotlin.random.Random

fun main() {
    val firstResult = Random.nextInt(6)
    val secondResult = Random.nextInt(6)

    if (firstResult == secondResult) {
        println("You win :)")
    } else {
        println("You lose :(")
    }
}

Exercicio 2

fun main() {
    val button = "A"

    println(
        when (button) {
            "A" -> "Yes"
            "B" -> "No"
            "X" -> "Menu"
            "Y" -> "Nothing"
            else -> "There is no such button"
        }
    )
}

Loops practice﻿

Exercicio 1 - while

fun main() {
    var pizzaSlices = 0

    while (pizzaSlices < 8) {
        pizzaSlices++
        println("There's only $pizzaSlices slice/s of pizza :(")
    }

    println("There are $pizzaSlices slices of pizza. Hooray! We have a whole pizza! :D")
}

Exercicio 1 - do-while

fun main() {
    var pizzaSlices = 0

    do {
        pizzaSlices++
        println("There's only $pizzaSlices slice/s of pizza :(")
    } while (pizzaSlices < 8)

    println("There are $pizzaSlices slices of pizza. Hooray! We have a whole pizza! :D")
}

Exercicio 2

fun main() {
    for (number in 1..100) {
        if (number % 15 == 0) {
            println("fizzbuzz")
        } else if (number % 3 == 0) {
            println("fizz")
        } else if (number % 5 == 0) {
            println("buzz")
        } else {
            println(number)
        }
    }
}

Exercicio 3

fun main() {
    val words = listOf("dinosaur", "limousine", "magazine", "language")

    for (word in words) {
        if (word.startsWith("l")) {
            println(word)
        }
    }
}

Functions

Exercicio 1

import kotlin.math.PI

fun circleArea(radius: Int): Double {
    return PI * radius * radius
}

fun main() {
    println(circleArea(2))
}

Exercicio 2

import kotlin.math.PI

fun circleArea(radius: Int): Double = PI * radius * radius

fun main() {
    println(circleArea(2))
}

Exercicio 3

fun intervalInSeconds(
    hours: Int = 0,
    minutes: Int = 0,
    seconds: Int = 0
) =
    ((hours * 60) + minutes) * 60 + seconds

fun main() {
    println(intervalInSeconds(hours = 1, minutes = 20, seconds = 15))
    println(intervalInSeconds(minutes = 1, seconds = 25))
    println(intervalInSeconds(hours = 2))
    println(intervalInSeconds(minutes = 10))
    println(intervalInSeconds(hours = 1, seconds = 1))
}

Lambda expressions practice﻿

Exercicio 1

fun main() {
    val actions = listOf("title", "year", "author")
    val prefix = "https://example.com/book-info"
    val id = 5

    val urls = actions.map { action -> "$prefix/$id/$action" }

    println(urls)
}

Exercicio 2

fun repeatN(n: Int, action: () -> Unit) {
    repeat(n) {
        action()
    }
}

fun main() {
    repeatN(5) {
        println("Hello")
    }
}

Classes

Exercicio 1

data class Employee(
    val name: String,
    var salary: Int
)

fun main() {
    val emp = Employee("Mary", 20)
    println(emp)
    emp.salary += 10
    println(emp)
}

Exercicio 2

data class Person(val name: Name, val address: Address, val ownsAPet: Boolean = true)

data class Name(val firstName: String, val lastName: String)

data class Address(val street: String, val city: City)

data class City(val name: String, val country: String)

fun main() {
    val person = Person(
        Name("John", "Smith"),
        Address("123 Fake Street", City("Springfield", "US")),
        ownsAPet = false
    )
}

Exercicio 3

import kotlin.random.Random

data class Employee(val name: String, var salary: Int)

class RandomEmployeeGenerator(
    var minSalary: Int,
    var maxSalary: Int
) {
    val names = listOf("John", "Mary", "Ann", "Paul")

    fun generateEmployee(): Employee {
        val name = names.random()
        val salary = Random.nextInt(minSalary, maxSalary)
        return Employee(name, salary)
    }
}

fun main() {
    val empGen = RandomEmployeeGenerator(10, 30)

    println(empGen.generateEmployee())
    println(empGen.generateEmployee())
    println(empGen.generateEmployee())

    empGen.minSalary = 50
    empGen.maxSalary = 100

    println(empGen.generateEmployee())
}

Null Safety

Exercicio

data class Employee(val name: String, var salary: Int)

fun employeeById(id: Int) = when(id) {
    1 -> Employee("Mary", 20)
    2 -> null
    3 -> Employee("John", 21)
    4 -> Employee("Ann", 23)
    else -> null
}

fun salaryById(id: Int) = employeeById(id)?.salary ?: 0

fun main() {
    println((1..5).sumOf { id -> salaryById(id) })
}
