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

# Autor

Luciane Silva de Lima
