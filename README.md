# ☕ Web Service RESTful com Spring Boot e JPA / Hibernate

![Java](https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5.5-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![Spring Data JPA](https://img.shields.io/badge/Spring_Data_JPA-ORM-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![H2 Database](https://img.shields.io/badge/H2_Database-In--Memory-4479A1?style=for-the-badge&logo=hibernate&logoColor=white)
![Maven](https://img.shields.io/badge/Apache_Maven-4.0.0-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)

---

## 📖 Sobre o Projeto

Este projeto é uma **API RESTful (Web Service)** desenvolvida em **Java 17** utilizando o framework **Spring Boot**. O foco principal é a implementação de um sistema back-end robusto, estruturado sob a arquitetura em camadas (*Layered Architecture*), aplicando boas práticas de Programação Orientada a Objetos (POO), mapeamento objeto-relacional (ORM) e manipulação de banco de dados relacional.

A aplicação disponibiliza endpoints REST para gerenciamento de um modelo de domínio completo (operações de CRUD - *Create, Read, Update, Delete*), incorporando tratamento centralizado de exceções, serialização de objetos e requisições HTTP padronizadas.

---

## 🎯 Funcionalidades e Arquitetura

O sistema foi desenhado visando desacoplamento, manutenibilidade e escalabilidade, dividindo as responsabilidades nas seguintes camadas:

1. **Camada de Apresentação (Web / Resources):**
   - Controladores REST (`@RestController`) que expõem os endpoints da API e respondem com objetos JSON.
   - Utilização de padrões HTTP corretos (status codes como `200 OK`, `201 Created`, `204 No Content`, `400 Bad Request`, `404 Not Found`).

2. **Camada de Serviço (Service Layer):**
   - Abriga as regras de negócio da aplicação (`@Service`).
   - Intermedia a comunicação entre os controladores REST e a camada de acesso a dados.

3. **Camada de Acesso a Dados (Repositories):**
   - Interfaces estendendo o `JpaRepository` do **Spring Data JPA**, oferecendo operações de persistência sem necessidade de código SQL repetitivo (boilerplate).

4. **Camada de Domínio (Entities):**
   - Entidades mapeadas com anotações JPA (`@Entity`, `@Table`, `@Id`, `@GeneratedValue`, etc.).
   - Gestão de relacionamentos relacionais entre objetos (`@OneToMany`, `@ManyToOne`, `@ManyToMany`, `@OneToOne`).

5. **Tratamento Excepcional e Validações:**
   - Implementação do padrão *Controller Advice* (`@ControllerAdvice`) para interceptar exceções na API e retornar respostas de erro customizadas e legíveis em formato JSON.

---

## 🛠️ Tecnologias Utilizadas

* **[Java 17](https://www.oracle.com/java/):** Linguagem de programação robusta, utilizando a versão LTS.
* **[Spring Boot 3.5.5](https://spring.io/projects/spring-boot):** Framework principal para simplificar a configuração e inicialização de aplicações Spring na web.
* **[Spring MVC / Web](https://docs.spring.io/spring-framework/reference/web.html):** Módulo para construção de APIs RESTful.
* **[Spring Data JPA / Hibernate](https://spring.io/projects/spring-data-jpa):** Módulo para persistência de dados relacional (ORM).
* **[H2 Database Engine](https://www.h2database.com/):** Banco de dados relacional em memória (*in-memory*), ideal para testes rápidos e desenvolvimento ágil.
* **[Apache Maven (Maven Wrapper)](https://maven.apache.org/):** Gerenciador de dependências e automação de build do projeto.

---

## 🚀 Como Executar o Projeto

### Pré-requisitos
* **Java Development Kit (JDK) 17** instalado na máquina.
* **Git** para clonagem do repositório.
*(Nota: Não é necessário ter o Maven pré-instalado no sistema, pois o projeto acompanha o Maven Wrapper (`mvnw`)*).

### Passo a Passo

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/SEU_USUARIO/NOME_DO_REPOSITORIO.git
   cd NOME_DO_REPOSITORIO
   ```

2. **Compile e execute o projeto usando o Maven Wrapper:**
   * **No Linux / macOS:**
     ```bash
     chmod +x mvnw
     ./mvnw spring-boot:run
     ```
   * **No Windows (Prompt de Comando ou PowerShell):**
     ```cmd
     mvnw.cmd spring-boot:run
     ```

3. **Acesse a API:**
   A aplicação será iniciada localmente na porta padrão `8080`.
   * **URL Base da API:** `http://localhost:8080`

---

## 🗄️ Acesso ao Banco de Dados H2 (Console)

O projeto está configurado para utilizar o banco de dados em memória **H2 Database**. Você pode gerenciar e inspecionar as tabelas criadas automaticamente pelo Hibernate através do navegador:

* **URL do Console H2:** `http://localhost:8080/h2-console`
* **Configurações padrão de acesso:**
  * **JDBC URL:** `jdbc:h2:mem:testdb` *(ou `jdbc:h2:mem:course` configurado no arquivo `application.properties`)*
  * **User Name:** `sa`
  * **Password:** *(deixe em branco)*

---

## 🔗 Exemplos de Endpoints (Rotas da API)

> *Obs: As rotas abaixo representam a estrutura padrão da API. Adeque os caminhos conforme os controladores e entidades implementados no repositório.*

| Método HTTP | Endpoint | Descrição | Status Code de Sucesso |
| :--- | :--- | :--- | :--- |
| **GET** | `/users` | Retorna a lista de todos os usuários cadastrados | `200 OK` |
| **GET** | `/users/{id}` | Busca um usuário específico por ID | `200 OK` |
| **POST** | `/users` | Cadastra um novo usuário | `201 Created` |
| **PUT** | `/users/{id}` | Atualiza os dados de um usuário existente | `200 OK` |
| **DELETE** | `/users/{id}` | Remove um usuário do banco de dados | `204 No Content` |

### Exemplo de Payload para Cadastro (`POST /users`):
```json
{
  "name": "Alex Green",
  "email": "alex@gmail.com",
  "phone": "977777777",
  "password": "password123"
}
```

---

## 📁 Estrutura de Pastas do Projeto

```text
course/
├── .mvn/wrapper/          # Configurações do Maven Wrapper
├── src/
│   ├── main/
│   │   ├── java/com/educandoweb/course/
│   │   │   ├── config/        # Classes de configuração (ex: instanciação do banco de teste)
│   │   │   ├── controllers/   # Controladores REST (Resources)
│   │   │   ├── entities/      # Entidades de domínio mapeadas com JPA
│   │   │   ├── repositories/  # Interfaces de acesso a dados (Spring Data JPA)
│   │   │   └── services/      # Camada de lógica de negócios
│   │   └── resources/
│   │       └── application.properties  # Configurações globais da aplicação
│   └── test/                  # Testes unitários e de integração
├── .gitignore
├── mvnw                   # Script do Maven Wrapper (Linux/macOS)
├── mvnw.cmd               # Script do Maven Wrapper (Windows)
└── pom.xml                # Configurações de build e dependências do Maven
```

---

## 📄 Licença

Este projeto é disponibilizado para fins de estudo e portfólio profissional. Sinta-se à vontade para utilizá-lo como referência ou contribuir com melhorias!

---
*Desenvolvido com dedicação para aprofundamento em arquitetura Back-End, Java e Ecossistema Spring.*