# thz-api-jvm — REST API Java 25 (Spring Boot)

API REST oficial do THZ-LANG, construída com Spring Boot para Java 25. Expõe os recursos do motor [`thz-core-jvm`](../thz-core-jvm) via endpoints HTTP para consumo por dashboards corporativos, IDEs web e microsserviços externos.

---

## 🌟 Endpoints Oferecidos

| Endpoint | Método | Descrição |
|---|---|---|
| `/api/health` | GET | Diagnóstico de integridade e versão do engine |
| `/api/analyze` | POST | Análise estática unificada (léxico + sintaxe + semântica + governança) |
| `/api/hover` | POST | Informações de hover (tipo, assinatura, linha e coluna) |
| `/api/ast` | POST | Extração da Árvore de Sintaxe Abstrata (AST) em JSON |
| `/api/format` | POST | Formatação canônica idempotente |
| `/api/doc` | POST | Geração de documentação técnica em Markdown e Mermaid |
| `/api/audit` | POST | Auditoria formal de requisitos e governança viva |
| `/api/ir` | POST | Geração de representação intermediária THZ-IR e LLVM IR |
| `/api/simd` | POST | Verificação de conformidade de laços vetorizados SIMD (R1–R5) |

---

## 🚀 Compilação e Empacotamento

A partir da raiz do monorepo:
```bash
# Compilar o arquivo JAR executável
./gradlew :thz-api-jvm:bootJar
```

Gera o arquivo `JVM/thz-api-jvm/build/libs/thz-api-jvm-0.4.0.jar`.

---

## 🛠️ Execução

```bash
# Executar diretamente via Gradle
./gradlew :thz-api-jvm:bootRun

# Ou executar o JAR compilado
java -jar JVM/thz-api-jvm/build/libs/thz-api-jvm-0.4.0.jar
```

A API é disponibilizada por padrão em `http://localhost:8080`.

---

## 💡 Exemplo de Requisição

```bash
# Análise de código via cURL
curl -X POST http://localhost:8080/api/analyze \
  -H "Content-Type: application/json" \
  -d '{"fonte": "programa Ola { fn main(): Int { print \"Ola mundo\"; retorne 0; } }"}'
```

---

## 📦 Dependência do Core

```kotlin
implementation("thz.lang:thz-core:0.4.0")
```
Resolvido via Gradle Composite Build a partir de `../thz-core-jvm`.
