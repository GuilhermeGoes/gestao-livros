# AGENTS

## Visão geral

Este repositório contém uma API inicial em Kotlin com Spring Boot para gestão de livros, organizada para evoluir seguindo arquitetura hexagonal.

- Linguagem: Kotlin
- Framework: Spring Boot 4.x
- Java: 21
- Build: Gradle via wrapper

## Estrutura esperada

- `domain`: entidades, regras de negócio e tipos do núcleo.
- `application/port/in`: casos de uso e contratos de entrada.
- `application/port/out`: portas de saída para persistência e integrações.
- `application/service`: implementação dos casos de uso.
- `adapter/in/web`: controllers, DTOs e entrada HTTP.
- `adapter/out`: adaptadores de infraestrutura (persistência, integrações externas).
- `config`: composição e configuração do Spring.

## Regras de desenvolvimento

- Mantenha o domínio livre de dependências de frameworks e bibliotecas de infraestrutura.
- Os casos de uso devem depender apenas de portas, nunca de implementações concretas.
- Adaptadores devem implementar contratos de saída/entrada definidos na camada de aplicação.
- Preserve o fluxo de dependências da arquitetura hexagonal: adapters -> application -> domain.
- Priorize clareza e nomes expressivos em Kotlin.
- Evite acoplamento direto de controllers a regras de negócio; orquestração deve acontecer nos casos de uso.

## Testes e validação

Antes de finalizar alterações, execute os testes do projeto:

```powershell
./gradlew.bat test
```

Para rodar a aplicação localmente:

```powershell
./gradlew.bat bootRun
```

Use o Actuator em `/actuator/health` para checagens rápidas de saúde quando necessário.

## Convenções

- Prefira adicionar testes para comportamento e regras de negócio.
- Não introduza dependências novas sem necessidade clara.
- Mantenha commits e alterações focados no escopo que está sendo trabalhado.
- Se algo for ambíguo ou a solução exigir decisão de arquitetura, documente a escolha no próprio código ou na descrição da tarefa.

## Comandos rápidos

```powershell
# iniciar app
./gradlew.bat bootRun

# rodar testes
./gradlew.bat test

# limpar build
./gradlew.bat clean
```
