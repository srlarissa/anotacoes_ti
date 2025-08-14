
É a principal estrutura do Maven, a qual torna possível definir:

- Nome do projeto;
- Dependências que serão utilizadas e suas versões;
- Plugins de build;
- Etapas de compilação e testes.

### Exemplo

```java
<project>
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.larissa</groupId>
  <artifactId>meu-projeto</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-core</artifactId>
      <version>5.3.10</version>
    </dependency>
  </dependencies>
</project>
```
