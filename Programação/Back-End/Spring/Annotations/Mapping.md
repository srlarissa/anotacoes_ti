Cada um dos verbos HTTP tem uma annotation específica e derivada da annotation RequestMapping, tornando o código mais legível e seguindo o padrão REST.
# RequestMapping

> Serve para mapear requisições HTTP (URL, métodos, parâmetros, headers, etc.) para métodos ou classes de um controlador.

Pode ser usada tanto na **classe** quanto no **método**:

- **Classe:** Define um prefixo comum para todas as rotas do controlador;
- **Método:** Define a rota (e, as vezes, o tipo de requisição) atendida por aquele método específico.

# GetMapping

> Utilizado para **consultar dados**, **não** altera o estado do servidor e geralmente retorna as informações requisitadas em JSON ou outro formato.

```java
@GetMapping("/users")
public List<User> getUsers() {
    return userService.findAll();
}
```

# PostMapping

> Usado para **criar novos recursos** e normalmente o corpo da requisição, frequentemente em JSON, tem os dados para a criação.

```java
@PostMapping("/users")
public User createUser(@RequestBody User user) {
    return userService.save(user);
}
```

# PutMapping

> Utilizado para atualizar um recurso **inteiro**. Se o recurso já existe, ele é substituído pelos novos dados enviados.

```java
@PutMapping("/users/{id}")
public User updateUser(@PathVariable Long id, @RequestBody User user) {
    user.setId(id);
    return userService.update(user);
}
```

# PatchMapping

> Usado para atualizar **parcialmente** um recurso, só enviando, assim, os dados que desejamos atualizar.

```java
@PatchMapping("/users/{id}")
public User updateUserPartial(@PathVariable Long id, @RequestBody Map<String, Object> updates) {
    return userService.updatePartial(id, updates);
}
```

# DeleteMapping

> Remove um recurso.

```java
@DeleteMapping("/users/{id}")
public void deleteUser(@PathVariable Long id) {
    userService.delete(id);
}
```

