# Sistema de Cadastro e Gerenciamento de Usuários

Este é um sistema simples para cadastro, edição, listagem e exclusão de usuários, desenvolvido com PHP, MySQL e Bootstrap para o frontend. O sistema segue uma estrutura MVC básica e utiliza práticas de segurança, como hash de senhas e verificação CSRF.

## **Tecnologias Utilizadas**

- **Backend**: PHP 7.4 ou superior
- **Banco de Dados**: MySQL
- **Frontend**: HTML, CSS, JavaScript, Bootstrap
- **Controle de Versão**: Git (opcional)
- **Servidor Web**: Apache (usando XAMPP ou similar)

## **Pré-requisitos**

Antes de rodar o projeto, você precisa ter os seguintes itens instalados:

- [PHP 7.4 ou superior](https://www.php.net/downloads.php)
- [MySQL](https://dev.mysql.com/downloads/)
- [XAMPP ou LAMP](https://www.apachefriends.org/index.html) (opcional, para rodar PHP e MySQL localmente)
- [Git](https://git-scm.com/) (opcional, para controle de versão)

## **Passos para Rodar o Projeto**

### **1. Clone o Repositório**

Primeiro, clone o repositório para sua máquina local:

```bash
git clone https://github.com/Robertwtoledo/crud_para_chromasoft.git
cd crud_para_chromasoft

2. Configuração do Banco de Dados
Crie o banco de dados no MySQL com o nome sistema_usuarios .

Você pode criar o banco de dados usando o seguinte comando SQL:

sql
Copiar código
CREATE DATABASE sistema_usuarios;
Importe a estrutura do banco de dados. Utilize o arquivo database.sql ou execute o seguinte SQL para criar a tabela de usuários:

sql
Copiar código
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    senha VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
3. Configuração do Arquivo de Conexão com o Banco de Dados
Abra o arquivo config/database.php.

Modifique as configurações de conexão com o banco de dados conforme o seu ambiente:

php
Copiar código
<?php
$host = 'localhost'; // Endereço do servidor de banco de dados
$dbname = 'sistema_usuarios'; // Nome do banco de dados
$username = 'root'; // Nome de usuário do MySQL
$password = ''; // Senha do MySQL (deixe vazio se não houver senha)

try {
    $pdo = new PDO("mysql:host=$host;dbname=$dbname", $username, $password);
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
    echo 'Erro na conexão: ' . $e->getMessage();
}
?>
4. Configuração do Servidor Web
Se você estiver utilizando o XAMPP ou LAMP, siga as instruções abaixo:

Inicie o Apache e MySQL no painel de controle do XAMPP ou LAMP.
Coloque o diretório do projeto na pasta htdocs (no caso do XAMPP) ou a pasta correspondente no LAMP.
Acesse o projeto pelo navegador, acessando http://localhost/user_management/.
5. Acessando o Sistema
Após configurar o servidor, você pode acessar as páginas de cadastro, edição e listagem de usuários diretamente no seu navegador:

Cadastro de Usuário: http://localhost/user_management/views/cadastro.html
Listagem de Usuários: http://localhost/user_management/views/index.html
Edição de Usuário: http://localhost/user_management/views/editar.html?id={id}
6. Testando a API
A API de usuários está disponível nas seguintes rotas:

Listar Usuários: GET /controllers/UserController.php
Criar Usuário: POST /controllers/UserController.php
Atualizar Usuário: PUT /controllers/UserController.php
Excluir Usuário: DELETE /controllers/UserController.php
Você pode testar essas rotas utilizando ferramentas como Postman ou diretamente no frontend.

7. Dependências
Este projeto não depende de bibliotecas externas além do Bootstrap para o frontend. No entanto, caso você deseje adicionar mais funcionalidades
