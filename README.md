# Spring Boot + Keycloak

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Exemplo de aplicação do keycloak com spring boot

### Tecnologias

Tecnologias usadas no projeto

* [Keycloak]
* [Lombook]
* [Spring Data JPA]
* [Spring Security]
* [HSQLDB]

### Instalação

##### Keycloak (DOCKER)

```sh
$ docker run -p 8080:8080 -e KEYCLOAK_USER=admin -e KEYCLOAK_PASSWORD=admin quay.io/keycloak/keycloak:11.0.3
```
Acessar o keycloak na URL: http://localhost:8080/auth
Logar com o usuário: admin e senha: admin

Realm
Adicionar um novo Realm com o nome: KeycloakSpringBootExample

Clients
Criar um client id com o nome: keycloak-example
Em Valid Redirect URIs: http://localhost:8081/*

Roles
Adiconar duas novas roles ao realm com o nome: user e admin

Users
Adiconar três novos usuarios: 1 com a role use, 1 com a role admin e o último com as duas roles.
Em Credentials adicionar uma senha e clicar em Set Password

Entrar na URL: http://localhost:8080/auth/realms/KeycloakSpringBootExample/account/ e trocar a senha do usuário cadastrado no keycloak.

URLS POSTMAN
http://localhost:8080/auth/realms/KeycloakSpringBootExample/protocol/openid-connect/token
Adicionar ao Body - x-www-form-urlencoded
    - client_id: keycloak-example
    - username: usuario
    - password: senha cadastrada no keycloak
    - grant_type: password

http://localhost:8080/auth/realms/KeycloakSpringBootExample/protocol/openid-connect/token
Adicionar ao Body - x-www-form-urlencoded
    - client_id: keycloak-example
    - refresh_token: refreshtoken retornado na url acima.
    - grant_type: refresh_token
    
##### Projeto
```sh
$ mvn clean spring-boot:run
```
Acessar o projeto na URL: http://locahost:8081/


### Referências

 - https://medium.com/devops-dudes/securing-spring-boot-rest-apis-with-keycloak-1d760b2004e
 - https://www.baeldung.com/spring-boot-keycloak
 - https://www.keycloak.org/getting-started/getting-started-docker
