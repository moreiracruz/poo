# Modelo Completo de Orientação a Objetos em Java com Explicações, Diagramas UML e Comparações com Python, JavaScript e Kotlin

A Orientação a Objetos (OO) é um paradigma de programação que organiza o software em torno de "objetos", que são instâncias de "classes". Vamos explorar os conceitos fundamentais da OO em Java, com exemplos práticos, diagramas UML, e comparações com Python, JavaScript e Kotlin.

---

## 1. **Conceitos Fundamentais da OO**

### 1.1 **Classes e Objetos**
- **Classe**: Um modelo ou blueprint que define atributos (dados) e métodos (comportamentos) que os objetos terão.
- **Objeto**: Uma instância de uma classe.

**Exemplo em Java**:
```java
class Carro {
    String marca;
    String modelo;
    int ano;

    Carro(String marca, String modelo, int ano) {
        this.marca = marca;
        this.modelo = modelo;
        this.ano = ano;
    }

    void ligar() {
        System.out.println(modelo + " está ligado!");
    }
}

// Objeto
public class Main {
    public static void main(String[] args) {
        Carro meuCarro = new Carro("Toyota", "Corolla", 2022);
        meuCarro.ligar();  // Saída: Corolla está ligado!
    }
}
```

**Comparação com Python**:
```python
class Carro:
    def __init__(self, marca, modelo, ano):
        self.marca = marca
        self.modelo = modelo
        self.ano = ano

    def ligar(self):
        print(f"{self.modelo} está ligado!")

meu_carro = Carro("Toyota", "Corolla", 2022)
meu_carro.ligar()  # Saída: Corolla está ligado!
```

**Comparação com JavaScript**:
```javascript
class Carro {
    constructor(marca, modelo, ano) {
        this.marca = marca;
        this.modelo = modelo;
        this.ano = ano;
    }

    ligar() {
        console.log(`${this.modelo} está ligado!`);
    }
}

const meuCarro = new Carro("Toyota", "Corolla", 2022);
meuCarro.ligar();  // Saída: Corolla está ligado!
```

**Comparação com Kotlin**:
```kotlin
class Carro(val marca: String, val modelo: String, val ano: Int) {
    fun ligar() {
        println("$modelo está ligado!")
    }
}

fun main() {
    val meuCarro = Carro("Toyota", "Corolla", 2022)
    meuCarro.ligar()  // Saída: Corolla está ligado!
}
```

---

### 1.2 **Encapsulamento**
O encapsulamento esconde os detalhes internos de um objeto e expõe apenas o necessário, protegendo os dados e controlando o acesso.

**Exemplo em Java**:
```java
class ContaBancaria {
    private double saldo;

    ContaBancaria(double saldo) {
        this.saldo = saldo;
    }

    void depositar(double valor) {
        if (valor > 0) {
            saldo += valor;
        }
    }

    double getSaldo() {
        return saldo;
    }
}

public class Main {
    public static void main(String[] args) {
        ContaBancaria conta = new ContaBancaria(1000);
        conta.depositar(500);
        System.out.println(conta.getSaldo());  // Saída: 1500.0
    }
}
```

**Comparação com Python**:
```python
class ContaBancaria:
    def __init__(self, saldo):
        self.__saldo = saldo  # Atributo privado

    def depositar(self, valor):
        if valor > 0:
            self.__saldo += valor

    def get_saldo(self):
        return self.__saldo

conta = ContaBancaria(1000)
conta.depositar(500)
print(conta.get_saldo())  # Saída: 1500
```

**Comparação com JavaScript**:
```javascript
class ContaBancaria {
    #saldo;  // Atributo privado

    constructor(saldo) {
        this.#saldo = saldo;
    }

    depositar(valor) {
        if (valor > 0) {
            this.#saldo += valor;
        }
    }

    getSaldo() {
        return this.#saldo;
    }
}

const conta = new ContaBancaria(1000);
conta.depositar(500);
console.log(conta.getSaldo());  // Saída: 1500
```

**Comparação com Kotlin**:
```kotlin
class ContaBancaria(private var saldo: Double) {
    fun depositar(valor: Double) {
        if (valor > 0) {
            saldo += valor
        }
    }

    fun getSaldo(): Double {
        return saldo
    }
}

fun main() {
    val conta = ContaBancaria(1000.0)
    conta.depositar(500.0)
    println(conta.getSaldo())  // Saída: 1500.0
}
```

---

### 1.3 **Herança**
Permite que uma classe herde atributos e métodos de outra classe, promovendo reutilização de código.

**Exemplo em Java**:
```java
class Animal {
    String nome;

    Animal(String nome) {
        this.nome = nome;
    }

    void fazerSom() {
        System.out.println("Som do animal");
    }
}

class Cachorro extends Animal {
    Cachorro(String nome) {
        super(nome);
    }

    @Override
    void fazerSom() {
        System.out.println("Au Au!");
    }
}

public class Main {
    public static void main(String[] args) {
        Cachorro dog = new Cachorro("Rex");
        dog.fazerSom();  // Saída: Au Au!
    }
}
```

**Comparação com Python**:
```python
class Animal:
    def __init__(self, nome):
        self.nome = nome

    def fazer_som(self):
        print("Som do animal")

class Cachorro(Animal):
    def fazer_som(self):
        print("Au Au!")

dog = Cachorro("Rex")
dog.fazer_som()  # Saída: Au Au!
```

**Comparação com JavaScript**:
```javascript
class Animal {
    constructor(nome) {
        this.nome = nome;
    }

    fazerSom() {
        console.log("Som do animal");
    }
}

class Cachorro extends Animal {
    fazerSom() {
        console.log("Au Au!");
    }
}

const dog = new Cachorro("Rex");
dog.fazerSom();  // Saída: Au Au!
```

**Comparação com Kotlin**:
```kotlin
open class Animal(val nome: String) {
    open fun fazerSom() {
        println("Som do animal")
    }
}

class Cachorro(nome: String) : Animal(nome) {
    override fun fazerSom() {
        println("Au Au!")
    }
}

fun main() {
    val dog = Cachorro("Rex")
    dog.fazerSom()  // Saída: Au Au!
}
```

---

### 1.4 **Polimorfismo**
Permite que objetos de diferentes classes sejam tratados como objetos de uma classe base, mas se comportem de maneira diferente.

**Exemplo em Java**:
```java
class Animal {
    void fazerSom() {
        System.out.println("Som do animal");
    }
}

class Cachorro extends Animal {
    @Override
    void fazerSom() {
        System.out.println("Au Au!");
    }
}

class Gato extends Animal {
    @Override
    void fazerSom() {
        System.out.println("Miau!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal meuAnimal = new Cachorro();
        meuAnimal.fazerSom();  // Saída: Au Au!

        meuAnimal = new Gato();
        meuAnimal.fazerSom();  // Saída: Miau!
    }
}
```

**Comparação com Python**:
```python
class Animal:
    def fazer_som(self):
        print("Som do animal")

class Cachorro(Animal):
    def fazer_som(self):
        print("Au Au!")

class Gato(Animal):
    def fazer_som(self):
        print("Miau!")

meu_animal = Cachorro()
meu_animal.fazer_som()  # Saída: Au Au!

meu_animal = Gato()
meu_animal.fazer_som()  # Saída: Miau!
```

**Comparação com JavaScript**:
```javascript
class Animal {
    fazerSom() {
        console.log("Som do animal");
    }
}

class Cachorro extends Animal {
    fazerSom() {
        console.log("Au Au!");
    }
}

class Gato extends Animal {
    fazerSom() {
        console.log("Miau!");
    }
}

let meuAnimal = new Cachorro();
meuAnimal.fazerSom();  // Saída: Au Au!

meuAnimal = new Gato();
meuAnimal.fazerSom();  // Saída: Miau!
```

**Comparação com Kotlin**:
```kotlin
open class Animal {
    open fun fazerSom() {
        println("Som do animal")
    }
}

class Cachorro : Animal() {
    override fun fazerSom() {
        println("Au Au!")
    }
}

class Gato : Animal() {
    override fun fazerSom() {
        println("Miau!")
    }
}

fun main() {
    var meuAnimal: Animal = Cachorro()
    meuAnimal.fazerSom()  // Saída: Au Au!

    meuAnimal = Gato()
    meuAnimal.fazerSom()  // Saída: Miau!
}
```

---

### 1.5 **Abstração**
A abstração simplifica a complexidade ao expor apenas os detalhes relevantes de um objeto.

**Exemplo em Java**:
```java
abstract class Forma {
    abstract double area();
}

class Circulo extends Forma {
    double raio;

    Circulo(double raio) {
        this.raio = raio;
    }

    @Override
    double area() {
        return 3.14 * (raio * raio);
    }
}

public class Main {
    public static void main(String[] args) {
        Forma circulo = new Circulo(5);
        System.out.println(circulo.area());  // Saída: 78.5
    }
}
```

**Comparação com Python**:
```python
from abc import ABC, abstractmethod

class Forma(ABC):
    @abstractmethod
    def area(self):
        pass

class Circulo(Forma):
    def __init__(self, raio):
        self.raio = raio

    def area(self):
        return 3.14 * (self.raio ** 2)

circulo = Circulo(5)
print(circulo.area())  # Saída: 78.5
```

**Comparação com JavaScript**:
```javascript
class Forma {
    area() {
        throw new Error("Método 'area' deve ser implementado");
    }
}

class Circulo extends Forma {
    constructor(raio) {
        super();
        this.raio = raio;
    }

    area() {
        return 3.14 * (this.raio * this.raio);
    }
}

const circulo = new Circulo(5);
console.log(circulo.area());  // Saída: 78.5
```

**Comparação com Kotlin**:
```kotlin
abstract class Forma {
    abstract fun area(): Double
}

class Circulo(val raio: Double) : Forma() {
    override fun area(): Double {
        return 3.14 * (raio * raio)
    }
}

fun main() {
    val circulo = Circulo(5.0)
    println(circulo.area())  // Saída: 78.5
}
```

---

### 1.6 **Interfaces**
Interfaces definem um contrato que as classes devem seguir, sem implementar detalhes.

**Exemplo em Java**:
```java
interface Pagavel {
    void pagar(double valor);
}

class Boleto implements Pagavel {
    @Override
    public void pagar(double valor) {
        System.out.println("Pagando boleto no valor de R$" + valor);
    }
}

public class Main {
    public static void main(String[] args) {
        Pagavel boleto = new Boleto();
        boleto.pagar(100);  // Saída: Pagando boleto no valor de R$100.0
    }
}
```

**Comparação com Python**:
```python
from abc import ABC, abstractmethod

class Pagavel(ABC):
    @abstractmethod
    def pagar(self, valor):
        pass

class Boleto(Pagavel):
    def pagar(self, valor):
        print(f"Pagando boleto no valor de R${valor}")

boleto = Boleto()
boleto.pagar(100)  # Saída: Pagando boleto no valor de R$100
```

**Comparação com JavaScript**:
```javascript
class Pagavel {
    pagar(valor) {
        throw new Error("Método 'pagar' deve ser implementado");
    }
}

class Boleto extends Pagavel {
    pagar(valor) {
        console.log(`Pagando boleto no valor de R$${valor}`);
    }
}

const boleto = new Boleto();
boleto.pagar(100);  // Saída: Pagando boleto no valor de R$100
```

**Comparação com Kotlin**:
```kotlin
interface Pagavel {
    fun pagar(valor: Double)
}

class Boleto : Pagavel {
    override fun pagar(valor: Double) {
        println("Pagando boleto no valor de R$$valor")
    }
}

fun main() {
    val boleto = Boleto()
    boleto.pagar(100.0)  // Saída: Pagando boleto no valor de R$100.0
}
```

---

## 2. **Princípios SOLID**

### 2.1 **Single Responsibility Principle (SRP)**
Uma classe deve ter apenas uma razão para mudar, ou seja, uma única responsabilidade.

**Exemplo em Java**:
```java
class Relatorio {
    void gerarRelatorio(String dados) {
        System.out.println("Relatório: " + dados);
    }
}

class EnviadorEmail {
    void enviarEmail(String destinatario, String mensagem) {
        System.out.println("Email enviado para " + destinatario + ": " + mensagem);
    }
}
```

**Comparação com Python**:
```python
class Relatorio:
    def gerar_relatorio(self, dados):
        print(f"Relatório: {dados}")

class EnviadorEmail:
    def enviar_email(self, destinatario, mensagem):
        print(f"Email enviado para {destinatario}: {mensagem}")
```

**Comparação com JavaScript**:
```javascript
class Relatorio {
    gerarRelatorio(dados) {
        console.log(`Relatório: ${dados}`);
    }
}

class EnviadorEmail {
    enviarEmail(destinatario, mensagem) {
        console.log(`Email enviado para ${destinatario}: ${mensagem}`);
    }
}
```

**Comparação com Kotlin**:
```kotlin
class Relatorio {
    fun gerarRelatorio(dados: String) {
        println("Relatório: $dados")
    }
}

class EnviadorEmail {
    fun enviarEmail(destinatario: String, mensagem: String) {
        println("Email enviado para $destinatario: $mensagem")
    }
}
```

---

### 2.2 **Open/Closed Principle (OCP)**
Classes devem estar abertas para extensão, mas fechadas para modificação.

**Exemplo em Java**:
```java
abstract class Desconto {
    abstract double calcular(double valor);
}

class DescontoNatal extends Desconto {
    @Override
    double calcular(double valor) {
        return valor * 0.1;
    }
}

class DescontoBlackFriday extends Desconto {
    @Override
    double calcular(double valor) {
        return valor * 0.2;
    }
}
```

**Comparação com Python**:
```python
class Desconto:
    def calcular(self, valor):
        pass

class DescontoNatal(Desconto):
    def calcular(self, valor):
        return valor * 0.1

class DescontoBlackFriday(Desconto):
    def calcular(self, valor):
        return valor * 0.2
```

**Comparação com JavaScript**:
```javascript
class Desconto {
    calcular(valor) {
        throw new Error("Método 'calcular' deve ser implementado");
    }
}

class DescontoNatal extends Desconto {
    calcular(valor) {
        return valor * 0.1;
    }
}

class DescontoBlackFriday extends Desconto {
    calcular(valor) {
        return valor * 0.2;
    }
}
```

**Comparação com Kotlin**:
```kotlin
abstract class Desconto {
    abstract fun calcular(valor: Double): Double
}

class DescontoNatal : Desconto() {
    override fun calcular(valor: Double): Double {
        return valor * 0.1
    }
}

class DescontoBlackFriday : Desconto() {
    override fun calcular(valor: Double): Double {
        return valor * 0.2
    }
}
```

---

### 2.3 **Liskov Substitution Principle (LSP)**
Objetos de uma classe base devem poder ser substituídos por objetos de uma classe derivada sem alterar a corretude do programa.

**Exemplo em Java**:
```java
class Pato {
    void voar() {
        System.out.println("Voando...");
    }
}

class PatoSelvagem extends Pato {
    @Override
    void voar() {
        System.out.println("Voando alto!");
    }
}

class PatoDeBorracha extends Pato {
    @Override
    void voar() {
        System.out.println("Não voa, é de borracha!");
    }
}
```

**Comparação com Python**:
```python
class Pato:
    def voar(self):
        print("Voando...")

class PatoSelvagem(Pato):
    def voar(self):
        print("Voando alto!")

class PatoDeBorracha(Pato):
    def voar(self):
        print("Não voa, é de borracha!")
```

**Comparação com JavaScript**:
```javascript
class Pato {
    voar() {
        console.log("Voando...");
    }
}

class PatoSelvagem extends Pato {
    voar() {
        console.log("Voando alto!");
    }
}

class PatoDeBorracha extends Pato {
    voar() {
        console.log("Não voa, é de borracha!");
    }
}
```

**Comparação com Kotlin**:
```kotlin
open class Pato {
    open fun voar() {
        println("Voando...")
    }
}

class PatoSelvagem : Pato() {
    override fun voar() {
        println("Voando alto!")
    }
}

class PatoDeBorracha : Pato() {
    override fun voar() {
        println("Não voa, é de borracha!")
    }
}
```

---

### 2.4 **Interface Segregation Principle (ISP)**
Interfaces devem ser específicas para o cliente, evitando métodos desnecessários.

**Exemplo em Java**:
```java
interface Impressora {
    void imprimir();
}

interface Scanner {
    void escanear();
}

class Multifuncional implements Impressora, Scanner {
    @Override
    public void imprimir() {
        System.out.println("Imprimindo...");
    }

    @Override
    public void escanear() {
        System.out.println("Escaneando...");
    }
}
```

**Comparação com Python**:
```python
from abc import ABC, abstractmethod

class Impressora(ABC):
    @abstractmethod
    def imprimir(self):
        pass

class Scanner(ABC):
    @abstractmethod
    def escanear(self):
        pass

class Multifuncional(Impressora, Scanner):
    def imprimir(self):
        print("Imprimindo...")

    def escanear(self):
        print("Escaneando...")
```

**Comparação com JavaScript**:
```javascript
class Impressora {
    imprimir() {
        throw new Error("Método 'imprimir' deve ser implementado");
    }
}

class Scanner {
    escanear() {
        throw new Error("Método 'escanear' deve ser implementado");
    }
}

class Multifuncional extends Impressora {
    imprimir() {
        console.log("Imprimindo...");
    }
}

class Multifuncional extends Scanner {
    escanear() {
        console.log("Escaneando...");
    }
}
```

**Comparação com Kotlin**:
```kotlin
interface Impressora {
    fun imprimir()
}

interface Scanner {
    fun escanear()
}

class Multifuncional : Impressora, Scanner {
    override fun imprimir() {
        println("Imprimindo...")
    }

    override fun escanear() {
        println("Escaneando...")
    }
}
```

---

### 2.5 **Dependency Inversion Principle (DIP)**
Dependa de abstrações, não de implementações concretas.

**Exemplo em Java**:
```java
interface BancoDeDados {
    void salvar(String dados);
}

class MySQL implements BancoDeDados {
    @Override
    public void salvar(String dados) {
        System.out.println("Salvando no MySQL: " + dados);
    }
}

class MongoDB implements BancoDeDados {
    @Override
    public void salvar(String dados) {
        System.out.println("Salvando no MongoDB: " + dados);
    }
}
```

**Comparação com Python**:
```python
from abc import ABC, abstractmethod

class BancoDeDados(ABC):
    @abstractmethod
    def salvar(self, dados):
        pass

class MySQL(BancoDeDados):
    def salvar(self, dados):
        print(f"Salvando no MySQL: {dados}")

class MongoDB(BancoDeDados):
    def salvar(self, dados):
        print(f"Salvando no MongoDB: {dados}")
```

**Comparação com JavaScript**:
```javascript
class BancoDeDados {
    salvar(dados) {
        throw new Error("Método 'salvar' deve ser implementado");
    }
}

class MySQL extends BancoDeDados {
    salvar(dados) {
        console.log(`Salvando no MySQL: ${dados}`);
    }
}

class MongoDB extends BancoDeDados {
    salvar(dados) {
        console.log(`Salvando no MongoDB: ${dados}`);
    }
}
```

**Comparação com Kotlin**:
```kotlin
interface BancoDeDados {
    fun salvar(dados: String)
}

class MySQL : BancoDeDados {
    override fun salvar(dados: String) {
        println("Salvando no MySQL: $dados")
    }
}

class MongoDB : BancoDeDados {
    override fun salvar(dados: String) {
        println("Salvando no MongoDB: $dados")
    }
}
```

---

## 3. **Segurança em OO**
- **Encapsulamento**: Protege dados sensíveis.
- **Validações**: Evite dados inválidos.
- **Imutabilidade**: Use objetos imutáveis para evitar alterações inesperadas.
- **Controle de Acesso**: Use modificadores como `private`, `protected`, e `public`.

**Exemplo em Java**:
```java
class Usuario {
    private String nome;
    private String senha;

    Usuario(String nome, String senha) {
        this.nome = nome;
        this.senha = senha;
    }

    boolean autenticar(String senha) {
        return this.senha.equals(senha);
    }
}
```

**Comparação com Python**:
```python
class Usuario:
    def __init__(self, nome, senha):
        self.nome = nome
        self.__senha = senha  # Atributo privado

    def autenticar(self, senha):
        return self.__senha == senha
```

**Comparação com JavaScript**:
```javascript
class Usuario {
    #senha;  // Atributo privado

    constructor(nome, senha) {
        this.nome = nome;
        this.#senha = senha;
    }

    autenticar(senha) {
        return this.#senha === senha;
    }
}
```

**Comparação com Kotlin**:
```kotlin
class Usuario(private val nome: String, private val senha: String) {
    fun autenticar(senha: String): Boolean {
        return this.senha == senha
    }
}
```

---

## 4. **Testes Unitários**
Testes unitários garantem que cada parte do código funcione corretamente.

**Exemplo em Java**:
```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class CarroTest {
    @Test
    void testLigar() {
        Carro carro = new Carro("Toyota", "Corolla", 2022);
        carro.ligar();
        assertEquals("Corolla está ligado!", carro.ligar());
    }
}
```

**Comparação com Python**:
```python
import unittest

class TestCarro(unittest.TestCase):
    def test_ligar(self):
        carro = Carro("Toyota", "Corolla", 2022)
        self.assertEqual(carro.ligar(), "Corolla está ligado!")

if __name__ == "__main__":
    unittest.main()
```

**Comparação com JavaScript**:
```javascript
const assert = require('assert');

class Carro {
    constructor(marca, modelo, ano) {
        this.marca = marca;
        this.modelo = modelo;
        this.ano = ano;
    }

    ligar() {
        return `${this.modelo} está ligado!`;
    }
}

describe('Carro', function() {
    it('deve ligar corretamente', function() {
        const carro = new Carro("Toyota", "Corolla", 2022);
        assert.strictEqual(carro.ligar(), "Corolla está ligado!");
    });
});
```

**Comparação com Kotlin**:
```kotlin
import org.junit.Test
import kotlin.test.assertEquals

class CarroTest {
    @Test
    fun testLigar() {
        val carro = Carro("Toyota", "Corolla", 2022)
        assertEquals("Corolla está ligado!", carro.ligar())
    }
}
```

---

## 5. **Padrões de Projeto**
- **Singleton**: Garante uma única instância de uma classe.
- **Factory**: Cria objetos sem especificar a classe exata.
- **Observer**: Notifica mudanças em um objeto para outros objetos.

**Exemplo em Java (Singleton)**:
```java
class Configuracao {
    private static Configuracao instancia;

    private Configuracao() {}

    public static Configuracao getInstancia() {
        if (instancia == null) {
            instancia = new Configuracao();
        }
        return instancia;
    }
}
```

**Comparação com Python**:
```python
class Configuracao:
    _instancia = None

    def __new__(cls):
        if cls._instancia is None:
            cls._instancia = super().__new__(cls)
        return cls._instancia
```

**Comparação com JavaScript**:
```javascript
class Configuracao {
    static instancia;

    constructor() {
        if (Configuracao.instancia) {
            return Configuracao.instancia;
        }
        Configuracao.instancia = this;
    }
}
```

**Comparação com Kotlin**:
```kotlin
object Configuracao {
    // Propriedades e métodos aqui
}
```

## 6. **Modificadores de Acesso**

Os modificadores de acesso controlam a visibilidade de classes, atributos, métodos e construtores. Eles são essenciais para garantir o encapsulamento e a segurança do código.

### 6.1 **`public`**
- **Visibilidade**: Acesso em qualquer lugar.
- **Uso**: Quando um membro precisa ser acessível globalmente.

**Exemplo em Java**:
```java
public class Animal {
    public String nome;

    public void fazerSom() {
        System.out.println("Som do animal");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal();
        animal.nome = "Rex";  // Acesso permitido
        animal.fazerSom();     // Acesso permitido
    }
}
```

**Comparação com Python**:
- Em Python, todos os membros são públicos por padrão.
```python
class Animal:
    def __init__(self, nome):
        self.nome = nome  # Público por padrão

    def fazer_som(self):
        print("Som do animal")

animal = Animal("Rex")
animal.nome = "Max"  # Acesso permitido
animal.fazer_som()   # Acesso permitido
```

**Comparação com JavaScript**:
- Em JavaScript, todos os membros são públicos por padrão.
```javascript
class Animal {
    constructor(nome) {
        this.nome = nome;  // Público por padrão
    }

    fazerSom() {
        console.log("Som do animal");
    }
}

const animal = new Animal("Rex");
animal.nome = "Max";  // Acesso permitido
animal.fazerSom();    // Acesso permitido
```

**Comparação com Kotlin**:
- Em Kotlin, `public` é o modificador padrão.
```kotlin
class Animal(var nome: String) {  // Público por padrão
    fun fazerSom() {
        println("Som do animal")
    }
}

fun main() {
    val animal = Animal("Rex")
    animal.nome = "Max"  // Acesso permitido
    animal.fazerSom()    // Acesso permitido
}
```

---

### 6.2 **`private`**
- **Visibilidade**: Acesso apenas dentro da própria classe.
- **Uso**: Para ocultar detalhes de implementação.

**Exemplo em Java**:
```java
class ContaBancaria {
    private double saldo;

    public void depositar(double valor) {
        if (valor > 0) {
            saldo += valor;
        }
    }

    public double getSaldo() {
        return saldo;
    }
}

public class Main {
    public static void main(String[] args) {
        ContaBancaria conta = new ContaBancaria();
        conta.depositar(1000);
        System.out.println(conta.getSaldo());  // Acesso permitido
        // System.out.println(conta.saldo);    // Erro: saldo é privado
    }
}
```

**Comparação com Python**:
- Em Python, usa-se `__` para indicar privacidade.
```python
class ContaBancaria:
    def __init__(self):
        self.__saldo = 0  # Privado

    def depositar(self, valor):
        if valor > 0:
            self.__saldo += valor

    def get_saldo(self):
        return self.__saldo

conta = ContaBancaria()
conta.depositar(1000)
print(conta.get_saldo())  # Acesso permitido
# print(conta.__saldo)    # Erro: saldo é privado
```

**Comparação com JavaScript**:
- Em JavaScript, usa-se `#` para indicar privacidade.
```javascript
class ContaBancaria {
    #saldo = 0;  // Privado

    depositar(valor) {
        if (valor > 0) {
            this.#saldo += valor;
        }
    }

    getSaldo() {
        return this.#saldo;
    }
}

const conta = new ContaBancaria();
conta.depositar(1000);
console.log(conta.getSaldo());  // Acesso permitido
// console.log(conta.#saldo);   // Erro: saldo é privado
```

**Comparação com Kotlin**:
- Em Kotlin, usa-se `private`.
```kotlin
class ContaBancaria {
    private var saldo: Double = 0.0  // Privado

    fun depositar(valor: Double) {
        if (valor > 0) {
            saldo += valor
        }
    }

    fun getSaldo(): Double {
        return saldo
    }
}

fun main() {
    val conta = ContaBancaria()
    conta.depositar(1000.0)
    println(conta.getSaldo())  // Acesso permitido
    // println(conta.saldo)    // Erro: saldo é privado
}
```

---

### 6.3 **`protected`**
- **Visibilidade**: Acesso dentro da própria classe, subclasses e pacote (em Java).
- **Uso**: Para permitir acesso a subclasses, mas não ao público geral.

**Exemplo em Java**:
```java
class Animal {
    protected String nome;

    protected void fazerSom() {
        System.out.println("Som do animal");
    }
}

class Cachorro extends Animal {
    void latir() {
        fazerSom();  // Acesso permitido
        System.out.println("Au Au!");
    }
}

public class Main {
    public static void main(String[] args) {
        Cachorro dog = new Cachorro();
        dog.nome = "Rex";  // Acesso permitido
        dog.latir();       // Acesso permitido
    }
}
```

**Comparação com Python**:
- Python não tem `protected`, mas usa convenções como `_` para indicar "protegido".
```python
class Animal:
    def __init__(self, nome):
        self._nome = nome  # Convenção para protegido

    def _fazer_som(self):  # Convenção para protegido
        print("Som do animal")

class Cachorro(Animal):
    def latir(self):
        self._fazer_som()  # Acesso permitido
        print("Au Au!")

dog = Cachorro("Rex")
dog._nome = "Max"  # Acesso permitido (mas não recomendado)
dog.latir()        # Acesso permitido
```

**Comparação com JavaScript**:
- JavaScript não tem `protected`.
```javascript
class Animal {
    constructor(nome) {
        this._nome = nome;  // Convenção para protegido
    }

    _fazerSom() {  // Convenção para protegido
        console.log("Som do animal");
    }
}

class Cachorro extends Animal {
    latir() {
        this._fazerSom();  // Acesso permitido
        console.log("Au Au!");
    }
}

const dog = new Cachorro("Rex");
dog._nome = "Max";  // Acesso permitido (mas não recomendado)
dog.latir();        // Acesso permitido
```

**Comparação com Kotlin**:
- Em Kotlin, `protected` é semelhante ao Java.
```kotlin
open class Animal {
    protected var nome: String = ""

    protected fun fazerSom() {
        println("Som do animal")
    }
}

class Cachorro : Animal() {
    fun latir() {
        fazerSom()  // Acesso permitido
        println("Au Au!")
    }
}

fun main() {
    val dog = Cachorro()
    dog.nome = "Rex"  // Acesso permitido
    dog.latir()       // Acesso permitido
}
```

---

### 6.4 **`default` (pacote)**
- **Visibilidade**: Acesso apenas dentro do mesmo pacote.
- **Uso**: Para restringir o acesso a classes do mesmo pacote.

**Exemplo em Java**:
```java
class Animal {
    String nome;  // Default (pacote)

    void fazerSom() {
        System.out.println("Som do animal");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal();
        animal.nome = "Rex";  // Acesso permitido (mesmo pacote)
        animal.fazerSom();    // Acesso permitido
    }
}
```

**Comparação com Python**:
- Python não tem um conceito direto de "default".
```python
# Em Python, todos os membros são públicos por padrão.
```

**Comparação com JavaScript**:
- JavaScript não tem um conceito direto de "default".
```javascript
// Em JavaScript, todos os membros são públicos por padrão.
```

**Comparação com Kotlin**:
- Kotlin não tem um conceito direto de "default".
```kotlin
// Em Kotlin, o padrão é `public`.
```

---

## 7. **Modificadores de Classes**

### 7.1 **`final`**
- **Uso**: Impede que uma classe seja herdada ou que um método seja sobrescrito.
- **Exemplo em Java**:
```java
final class Animal {
    final void fazerSom() {
        System.out.println("Som do animal");
    }
}

// class Cachorro extends Animal {}  // Erro: Animal é final
```

**Comparação com Python**:
- Python não tem `final`, mas pode-se usar convenções ou decoradores.
```python
class Animal:
    def fazer_som(self):
        print("Som do animal")

# Convenção para indicar que a classe não deve ser herdada
class Cachorro(Animal):  # Funciona, mas não recomendado
    pass
```

**Comparação com JavaScript**:
- JavaScript não tem `final`.
```javascript
class Animal {
    fazerSom() {
        console.log("Som do animal");
    }
}

class Cachorro extends Animal {}  // Funciona
```

**Comparação com Kotlin**:
- Em Kotlin, `final` é o padrão para classes e métodos.
```kotlin
open class Animal {
    open fun fazerSom() {
        println("Som do animal")
    }
}

class Cachorro : Animal() {
    override fun fazerSom() {
        println("Au Au!")
    }
}
```

---

### 7.2 **`sealed`**
- **Uso**: Restringe quais classes podem herdar de uma classe.
- **Exemplo em Java (Java 17+)**:
```java
sealed class Animal permits Cachorro, Gato {
    abstract void fazerSom();
}

final class Cachorro extends Animal {
    @Override
    void fazerSom() {
        System.out.println("Au Au!");
    }
}

final class Gato extends Animal {
    @Override
    void fazerSom() {
        System.out.println("Miau!");
    }
}
```

**Comparação com Kotlin**:
- Kotlin tem suporte nativo para `sealed`.
```kotlin
sealed class Animal {
    abstract fun fazerSom()
}

class Cachorro : Animal() {
    override fun fazerSom() {
        println("Au Au!")
    }
}

class Gato : Animal() {
    override fun fazerSom() {
        println("Miau!")
    }
}
```

---

## 8. **Testes Unitários**

### Exemplo em Java (JUnit):
```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class ContaBancariaTest {
    @Test
    void testDepositar() {
        ContaBancaria conta = new ContaBancaria();
        conta.depositar(1000);
        assertEquals(1000, conta.getSaldo());
    }
}
```

**Comparação com Python (unittest)**:
```python
import unittest

class TestContaBancaria(unittest.TestCase):
    def test_depositar(self):
        conta = ContaBancaria()
        conta.depositar(1000)
        self.assertEqual(conta.get_saldo(), 1000)

if __name__ == "__main__":
    unittest.main()
```

**Comparação com JavaScript (Jest)**:
```javascript
const ContaBancaria = require('./ContaBancaria');

test('depositar 1000 aumenta o saldo para 1000', () => {
    const conta = new ContaBancaria();
    conta.depositar(1000);
    expect(conta.getSaldo()).toBe(1000);
});
```

**Comparação com Kotlin (JUnit)**:
```kotlin
import org.junit.Test
import kotlin.test.assertEquals

class ContaBancariaTest {
    @Test
    fun testDepositar() {
        val conta = ContaBancaria()
        conta.depositar(1000.0)
        assertEquals(1000.0, conta.getSaldo())
    }
}
```

---
Vamos explorar os **modificadores de acesso** e **modificadores de classes** em Java, com exemplos práticos, comparações entre linguagens (Java, Python, JavaScript e Kotlin), e como eles se relacionam com **testes unitários**.

---

## 1. **Modificadores de Acesso**

Os modificadores de acesso controlam a visibilidade de classes, atributos, métodos e construtores. Eles são essenciais para garantir o encapsulamento e a segurança do código.

### 1.1 **`public`**
- **Visibilidade**: Acesso em qualquer lugar.
- **Uso**: Quando um membro precisa ser acessível globalmente.

**Exemplo em Java**:
```java
public class Animal {
    public String nome;

    public void fazerSom() {
        System.out.println("Som do animal");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal();
        animal.nome = "Rex";  // Acesso permitido
        animal.fazerSom();     // Acesso permitido
    }
}
```

**Comparação com Python**:
- Em Python, todos os membros são públicos por padrão.
```python
class Animal:
    def __init__(self, nome):
        self.nome = nome  # Público por padrão

    def fazer_som(self):
        print("Som do animal")

animal = Animal("Rex")
animal.nome = "Max"  # Acesso permitido
animal.fazer_som()   # Acesso permitido
```

**Comparação com JavaScript**:
- Em JavaScript, todos os membros são públicos por padrão.
```javascript
class Animal {
    constructor(nome) {
        this.nome = nome;  // Público por padrão
    }

    fazerSom() {
        console.log("Som do animal");
    }
}

const animal = new Animal("Rex");
animal.nome = "Max";  // Acesso permitido
animal.fazerSom();    // Acesso permitido
```

**Comparação com Kotlin**:
- Em Kotlin, `public` é o modificador padrão.
```kotlin
class Animal(var nome: String) {  // Público por padrão
    fun fazerSom() {
        println("Som do animal")
    }
}

fun main() {
    val animal = Animal("Rex")
    animal.nome = "Max"  // Acesso permitido
    animal.fazerSom()    // Acesso permitido
}
```

---

### 1.2 **`private`**
- **Visibilidade**: Acesso apenas dentro da própria classe.
- **Uso**: Para ocultar detalhes de implementação.

**Exemplo em Java**:
```java
class ContaBancaria {
    private double saldo;

    public void depositar(double valor) {
        if (valor > 0) {
            saldo += valor;
        }
    }

    public double getSaldo() {
        return saldo;
    }
}

public class Main {
    public static void main(String[] args) {
        ContaBancaria conta = new ContaBancaria();
        conta.depositar(1000);
        System.out.println(conta.getSaldo());  // Acesso permitido
        // System.out.println(conta.saldo);    // Erro: saldo é privado
    }
}
```

**Comparação com Python**:
- Em Python, usa-se `__` para indicar privacidade.
```python
class ContaBancaria:
    def __init__(self):
        self.__saldo = 0  # Privado

    def depositar(self, valor):
        if valor > 0:
            self.__saldo += valor

    def get_saldo(self):
        return self.__saldo

conta = ContaBancaria()
conta.depositar(1000)
print(conta.get_saldo())  # Acesso permitido
# print(conta.__saldo)    # Erro: saldo é privado
```

**Comparação com JavaScript**:
- Em JavaScript, usa-se `#` para indicar privacidade.
```javascript
class ContaBancaria {
    #saldo = 0;  // Privado

    depositar(valor) {
        if (valor > 0) {
            this.#saldo += valor;
        }
    }

    getSaldo() {
        return this.#saldo;
    }
}

const conta = new ContaBancaria();
conta.depositar(1000);
console.log(conta.getSaldo());  // Acesso permitido
// console.log(conta.#saldo);   // Erro: saldo é privado
```

**Comparação com Kotlin**:
- Em Kotlin, usa-se `private`.
```kotlin
class ContaBancaria {
    private var saldo: Double = 0.0  // Privado

    fun depositar(valor: Double) {
        if (valor > 0) {
            saldo += valor
        }
    }

    fun getSaldo(): Double {
        return saldo
    }
}

fun main() {
    val conta = ContaBancaria()
    conta.depositar(1000.0)
    println(conta.getSaldo())  // Acesso permitido
    // println(conta.saldo)    // Erro: saldo é privado
}
```

---

### 1.3 **`protected`**
- **Visibilidade**: Acesso dentro da própria classe, subclasses e pacote (em Java).
- **Uso**: Para permitir acesso a subclasses, mas não ao público geral.

**Exemplo em Java**:
```java
class Animal {
    protected String nome;

    protected void fazerSom() {
        System.out.println("Som do animal");
    }
}

class Cachorro extends Animal {
    void latir() {
        fazerSom();  // Acesso permitido
        System.out.println("Au Au!");
    }
}

public class Main {
    public static void main(String[] args) {
        Cachorro dog = new Cachorro();
        dog.nome = "Rex";  // Acesso permitido
        dog.latir();       // Acesso permitido
    }
}
```

**Comparação com Python**:
- Python não tem `protected`, mas usa convenções como `_` para indicar "protegido".
```python
class Animal:
    def __init__(self, nome):
        self._nome = nome  # Convenção para protegido

    def _fazer_som(self):  # Convenção para protegido
        print("Som do animal")

class Cachorro(Animal):
    def latir(self):
        self._fazer_som()  # Acesso permitido
        print("Au Au!")

dog = Cachorro("Rex")
dog._nome = "Max"  # Acesso permitido (mas não recomendado)
dog.latir()        # Acesso permitido
```

**Comparação com JavaScript**:
- JavaScript não tem `protected`.
```javascript
class Animal {
    constructor(nome) {
        this._nome = nome;  // Convenção para protegido
    }

    _fazerSom() {  // Convenção para protegido
        console.log("Som do animal");
    }
}

class Cachorro extends Animal {
    latir() {
        this._fazerSom();  // Acesso permitido
        console.log("Au Au!");
    }
}

const dog = new Cachorro("Rex");
dog._nome = "Max";  // Acesso permitido (mas não recomendado)
dog.latir();        // Acesso permitido
```

**Comparação com Kotlin**:
- Em Kotlin, `protected` é semelhante ao Java.
```kotlin
open class Animal {
    protected var nome: String = ""

    protected fun fazerSom() {
        println("Som do animal")
    }
}

class Cachorro : Animal() {
    fun latir() {
        fazerSom()  // Acesso permitido
        println("Au Au!")
    }
}

fun main() {
    val dog = Cachorro()
    dog.nome = "Rex"  // Acesso permitido
    dog.latir()       // Acesso permitido
}
```

---

### 1.4 **`default` (pacote)**
- **Visibilidade**: Acesso apenas dentro do mesmo pacote.
- **Uso**: Para restringir o acesso a classes do mesmo pacote.

**Exemplo em Java**:
```java
class Animal {
    String nome;  // Default (pacote)

    void fazerSom() {
        System.out.println("Som do animal");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal();
        animal.nome = "Rex";  // Acesso permitido (mesmo pacote)
        animal.fazerSom();    // Acesso permitido
    }
}
```

**Comparação com Python**:
- Python não tem um conceito direto de "default".
```python
# Em Python, todos os membros são públicos por padrão.
```

**Comparação com JavaScript**:
- JavaScript não tem um conceito direto de "default".
```javascript
// Em JavaScript, todos os membros são públicos por padrão.
```

**Comparação com Kotlin**:
- Kotlin não tem um conceito direto de "default".
```kotlin
// Em Kotlin, o padrão é `public`.
```

---

## 2. **Modificadores de Classes**

### 2.1 **`final`**
- **Uso**: Impede que uma classe seja herdada ou que um método seja sobrescrito.
- **Exemplo em Java**:
```java
final class Animal {
    final void fazerSom() {
        System.out.println("Som do animal");
    }
}

// class Cachorro extends Animal {}  // Erro: Animal é final
```

**Comparação com Python**:
- Python não tem `final`, mas pode-se usar convenções ou decoradores.
```python
class Animal:
    def fazer_som(self):
        print("Som do animal")

# Convenção para indicar que a classe não deve ser herdada
class Cachorro(Animal):  # Funciona, mas não recomendado
    pass
```

**Comparação com JavaScript**:
- JavaScript não tem `final`.
```javascript
class Animal {
    fazerSom() {
        console.log("Som do animal");
    }
}

class Cachorro extends Animal {}  // Funciona
```

**Comparação com Kotlin**:
- Em Kotlin, `final` é o padrão para classes e métodos.
```kotlin
open class Animal {
    open fun fazerSom() {
        println("Som do animal")
    }
}

class Cachorro : Animal() {
    override fun fazerSom() {
        println("Au Au!")
    }
}
```

---

### 2.2 **`sealed`**
- **Uso**: Restringe quais classes podem herdar de uma classe.
- **Exemplo em Java (Java 17+)**:
```java
sealed class Animal permits Cachorro, Gato {
    abstract void fazerSom();
}

final class Cachorro extends Animal {
    @Override
    void fazerSom() {
        System.out.println("Au Au!");
    }
}

final class Gato extends Animal {
    @Override
    void fazerSom() {
        System.out.println("Miau!");
    }
}
```

**Comparação com Kotlin**:
- Kotlin tem suporte nativo para `sealed`.
```kotlin
sealed class Animal {
    abstract fun fazerSom()
}

class Cachorro : Animal() {
    override fun fazerSom() {
        println("Au Au!")
    }
}

class Gato : Animal() {
    override fun fazerSom() {
        println("Miau!")
    }
}
```

---

## 3. **Testes Unitários**

### Exemplo em Java (JUnit):
```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class ContaBancariaTest {
    @Test
    void testDepositar() {
        ContaBancaria conta = new ContaBancaria();
        conta.depositar(1000);
        assertEquals(1000, conta.getSaldo());
    }
}
```

**Comparação com Python (unittest)**:
```python
import unittest

class TestContaBancaria(unittest.TestCase):
    def test_depositar(self):
        conta = ContaBancaria()
        conta.depositar(1000)
        self.assertEqual(conta.get_saldo(), 1000)

if __name__ == "__main__":
    unittest.main()
```

**Comparação com JavaScript (Jest)**:
```javascript
const ContaBancaria = require('./ContaBancaria');

test('depositar 1000 aumenta o saldo para 1000', () => {
    const conta = new ContaBancaria();
    conta.depositar(1000);
    expect(conta.getSaldo()).toBe(1000);
});
```

**Comparação com Kotlin (JUnit)**:
```kotlin
import org.junit.Test
import kotlin.test.assertEquals

class ContaBancariaTest {
    @Test
    fun testDepositar() {
        val conta = ContaBancaria()
        conta.depositar(1000.0)
        assertEquals(1000.0, conta.getSaldo())
    }
}
```

## Conclusão
Os modificadores de acesso e de classes são fundamentais para controlar a visibilidade e o comportamento do código. Eles ajudam a garantir encapsulamento, segurança e organização. As comparações entre Java, Python, JavaScript e Kotlin mostram que, embora os conceitos sejam semelhantes, a sintaxe e as implementações podem variar. Testes unitários são essenciais para validar o comportamento do código em todos os cenários.
