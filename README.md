# Gestao Livros

API inicial em Kotlin e Spring Boot, organizada para evoluir com arquitetura hexagonal.

## Requisitos

- JDK 21

O Gradle Wrapper ja esta incluido; nao e necessario instalar Gradle.

## Executar

No Windows:

```powershell
.\gradlew.bat bootRun
```

Executar os testes:

```powershell
.\gradlew.bat test
```

O Actuator disponibiliza a verificacao de saude em `/actuator/health`. A aplicacao
nao esta conectada a um banco de dados; a escolha de persistencia fica para uma
etapa posterior.

## Organizacao

Os pacotes da aplicacao ficam sob `com.example.gestaolivros`:

- `domain`: modelo e regras de negocio, sem dependencia de Spring.
- `application/port/in`: contratos dos casos de uso oferecidos pela aplicacao.
- `application/port/out`: contratos de que os casos de uso precisam.
- `application/service`: implementacao dos casos de uso.
- `adapter/in/web`: entrada HTTP, controllers e DTOs.
- `adapter/out`: adaptadores de saida, como persistencia e integracoes externas.
- `config`: configuracao e composicao dos componentes Spring.

As dependencias apontam dos adaptadores para a aplicacao e o dominio; os casos de
uso dependem de portas, nao de tecnologias concretas.

## Stack inicial

- Spring Web MVC e Bean Validation para a API HTTP.
- Spring Boot Actuator para health checks.
- JUnit 5 e Spring Boot Test para testes.
- Gradle Kotlin DSL com Wrapper para build reproduzivel.
