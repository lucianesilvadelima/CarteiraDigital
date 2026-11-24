# Carteira Digital - Testes Automatizados I

Projeto desenvolvido para a disciplina **Testes Automatizados I (BE-JV-011)** utilizando Java e Spring Boot.

## Objetivo

Implementar uma API REST de Carteira Digital seguindo a arquitetura em camadas:

- Entity
- Repository
- Service
- Controller

Além disso, aplicar:

- JUnit 5  
- Mockito
- Selenium WebDriver
- JaCoCo
- TDD (Test Driven Development)

---

# Tecnologias Utilizadas

- Java 17
- Spring Boot
- Spring Data JPA
- H2 Database
- JUnit 5
- Mockito
- Selenium WebDriver
- Maven
- JaCoCo

---

# Estrutura do Projeto

```text
src
├── main
│   ├── java
│   │   ├── entity
│   │   ├── repository
│   │   ├── service
│   │   ├── controller
│   │   └── exception
│   │
│   └── resources
│       └── static
│           └── deposito.html
│
└── test
    └── java
        ├── service
        └── Selenium
```

# Entidade

## Conta

Possui os atributos:

```java
Long id;
String titular;
Double saldo;
```

---

# Regras de Negócio

## Consultar Saldo

Retorna o saldo atual da conta.

## Depositar

Adiciona valor ao saldo.

Validação:

```java
valor > 0
```

Caso contrário:

```java
IllegalArgumentException
```

## Transferir

Transfere valor entre contas.

Validação:

```java
saldoOrigem >= valorTransferencia
```

Caso contrário:

```java
SaldoInsuficienteException
```

---

# Testes Unitários

Implementados utilizando:

- JUnit 5
- Mockito

Cenários cobertos:

✅ Consultar saldo

✅ Realizar depósito

✅ Depósito inválido

✅ Transferência com saldo insuficiente

✅ Transferência realizada com sucesso

---

# Teste de Interface

Foi criada a página:

```text
deposito.html
```

Disponível em:

```text
http://localhost:8080/deposito.html
```

Automação realizada com Selenium WebDriver.

Fluxo testado:

1. Abrir página
2. Informar valor
3. Clicar em Depositar
4. Validar mensagem:

```text
Depósito realizado com sucesso
```

---

# Cobertura de Código

Relatório gerado utilizando JaCoCo.

Resultado obtido:

```text
85% de cobertura
```

Atendendo o requisito mínimo de 80%.

---

# Executando o Projeto

## Executar aplicação

Rodar:

```java
CarteiraDigitalApplication
```

A aplicação ficará disponível em:

```text
http://localhost:8080
```

---

# Executando os Testes

Rodar:

```text
ContaServiceTest
```

ou:

```bash
mvn test
```

---

# Gerar Relatório JaCoCo

```bash
mvn test
```

Abrir:

```text
target/site/jacoco/index.html
```

---

# Executando os Testes

## Testes Unitários

Os testes unitários utilizam:

- JUnit 5
- Mockito

Classes testadas:

- ContaService

Para executar pelo IntelliJ:

1. Abrir a classe:

```text
ContaServiceTest
```

2. Clicar com o botão direito na classe.

3. Selecionar:

```text
Run 'ContaServiceTest'
```

Resultado esperado:

```text
5 tests passed
```

---

## Teste de Interface (Selenium)

Antes de executar o Selenium:

1. Inicie a aplicação Spring Boot.

Executar:

```text
CarteiraDigitalApplication
```

2. Verifique se a página abre:

```text
http://localhost:8080/deposito.html
```

3. Execute a classe:

```text
DepositaHtmlSeleniumTest
```

Fluxo automatizado:

- Abre o Chrome
- Acessa a página de depósito
- Digita o valor 100
- Clica no botão Depositar
- Valida a mensagem:

```text
Depósito realizado com sucesso
```

---

## Executar Todos os Testes com Maven

No terminal:

```bash
mvn test
```

ou pelo IntelliJ:

```text
Maven
→ Lifecycle
→ test
```

---

# Gerar Relatório JaCoCo

Após executar os testes:

```text
Maven
→ Lifecycle
→ test
```

O relatório será gerado em:

```text
target/site/jacoco/index.html
```

Para visualizar:

1. Abrir:

```text
target/site/jacoco/index.html
```

2. Selecionar:

```text
Open in Browser
```

---

# Cobertura Obtida

Cobertura total do projeto:

```text
85%
```

Atendendo ao requisito mínimo de:

```text
80%
```

---

# Estrutura dos Testes

Os testes seguem o padrão:

```java
// Arrange (Preparação)
// Act (Ação)
// Assert (Verificação)
```

Exemplo:

```java
@Test
public void deveRealizarDeposito() {

    // Arrange
    Conta conta = new Conta(1L, "Luciane", 1000.0);

    // Act
    contaService.depositar(1L, 500.0);

    // Assert
    assertEquals(1500.0, conta.getSaldo());
}
```

# Autor

Luciane Silva de Lima
