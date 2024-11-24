# ApInsta

ApInsta é uma API de rede social construída em **.NET 9**, seguindo os princípios de **DDD (Domain-Driven Design)**, **Clean Architecture** e **Clean Code**. Esta versão inicial inclui funcionalidades básicas para autenticação de usuários e organização de dados.

---

## Funcionalidades

- Registro de novos usuários.
- Autenticação com JWT (JSON Web Tokens).
- Gerenciamento de usuários via repositórios.
- Estrutura organizada com **DDD** e **Camadas**:
  - **Domain**: Contém as entidades principais do sistema.
  - **Application**: Implementação de serviços e casos de uso.
  - **Infrastructure**: Persistência de dados com **Entity Framework Core**.
  - **API**: Endpoints para interação com o sistema.

---

## Tecnologias Utilizadas

- **C#** com **.NET 9**
- **Entity Framework Core** para persistência.
- **SQL Server** como banco de dados.
- **JWT** para autenticação.
- **FluentValidation** para validação de dados.
- **Swagger** para documentação da API.

---

## Pré-requisitos

Antes de começar, você precisará ter instalado:

- [SDK do .NET 9](https://dotnet.microsoft.com/download)
- [SQL Server](https://www.microsoft.com/pt-br/sql-server/sql-server-downloads)
- Um editor como [Visual Studio Code](https://code.visualstudio.com/) ou [Visual Studio](https://visualstudio.microsoft.com/).

---

## Configuração do Projeto

1. Clone o repositório:
   ```bash
	   git clone https://github.com/LucasDevolps/ApInsta
	   cd ApInsta
   ```

2. Configure a string de conexão no arquivo appsettings.json:

    ```json
		{
		  "ConnectionStrings": {
			"DefaultConnection": "Server=localhost;Database=BASE;User Id=sa;Password=Bkur6etc@10;TrustServerCertificate=True;"
		  }
		}
	```
3. Restaure as dependências:

    dotnet restore

4. Crie o banco de dados e aplique as migrações:

    dotnet ef database update --startup-project src/ApInsta.API --project src/ApInsta.Infrastructure

5. Execute a aplicação:
    
    dotnet run --project src/ApInsta.API

6. Acesse o Swagger para testar os endpoints:


## Estrutura do Projeto

    src/
    ├── ApInsta.API           # Camada de apresentação (endpoints)
    ├── ApInsta.Application   # Casos de uso e validações
    ├── ApInsta.Core          # Contratos e interfaces gerais
    ├── ApInsta.Domain        # Entidades e lógica de domínio
    ├── ApInsta.Infrastructure# Persistência de dados e repositórios
    └── ApInsta.Service       # Serviços auxiliares (futuro)

## Endpoints Principais

### Autenticação
    POST /auth/register

    Registro de um novo usuário.

    Body (JSON):

    {
        "name": "fulano",
        "email": "fulano@ciclano.com",
        "password": "password123"
    }

    POST /auth/login
    Autenticação de usuário.
    Body (JSON):

    {
        "login": "johndoe@example.com",
        "password": "password123"
    }



