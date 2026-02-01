# JAVA & JVM ENGINEERING STANDARDS

Activation: Glob(pom.xml, build.gradle, **/\*.java, **/\*.kt)

## 1. SPRING BOOT ARCHITECTURE

- **Layers**: Controller -> Service -> Repository.
- **Injection**: Constructor Injection only. Field injection (`@Autowired` on fields) is forbidden.
- **Configuration**: Use `@ConfigurationProperties` over `@Value`.

## 2. STYLE CONFLICT RESOLUTION

- **Global vs Language**:
  - **Variables/Methods**: Java standard is `camelCase`. `.agent/artifacts/conventions.md` asks for `snake_case`.
  - **RULE**: Follow `snake_case` for local variables and private methods to satisfy the Global Convention.
  - **EXCEPTION**: Use `camelCase` for Public APIs, JPA Entities, and Override methods where the framework requires it.
  - **Indentation**: Force Tabs (4).

## 3. NULL SAFETY

- **Java**: Use `Optional<T>`. Never return `null`.
- **Kotlin**: Use nullable types (`T?`) handling.

## 4. BUILD TOOLS

- **Maven/Gradle**: Wrapper usage (`./mvnw` or `./gradlew`) is mandatory.