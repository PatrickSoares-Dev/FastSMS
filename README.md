PHP (versão 7.0 ou posterior)
Composer (https://getcomposer.org/)
Postman (https://www.postman.com/) para testar os endpoints da API

Endpoints da API

1. Obter todos os usuários
Método: GET
URL: http://localhost/FastSMS/API/public_html/api/user/getUser

2. Obter um usuário por ID
Método: GET
URL: http://localhost/FastSMS/API/public_html/api/user/getUser/{id}
Substitua {id} pelo ID do usuário que você deseja recuperar.

3. Registrar um novo usuário
Método: POST
URL: http://localhost/FastSMS/API/public_html/api/user/registerNewUser
Corpo da solicitação (JSON): Forneça os dados do usuário a serem registrados no corpo da solicitação. Consulte o exemplo no código-fonte.

{
    "nome": "Nome do Novo Usuário",
    "data_nascimento": "1990-01-15",
    "sexo": "M",
    "nome_materno": "Mãe do Novo Usuário",
    "cpf": "123.456.789-01",
    "celular": "(11) 98765-4321",
    "cep": "12345-678",
    "endereco": "Rua das Flores, 123",
    "cidade": "São Paulo",
    "estado": "SP",
    "login": "novousuario",
    "senha": "senhadonovousuario",
    "email": "novousuario@example.com"
}

4. Atualizar um usuário por ID
Método: PUT
URL: http://localhost/FastSMS/API/public_html/api/user/updateUserById
Corpo da solicitação (JSON): Forneça o ID do usuário a ser atualizado e os campos que deseja atualizar no corpo da solicitação. Consulte o exemplo no código-fonte.

{
    "id": 1,
    "data": {
        "nome": "Novo Nome do Usuário",
        "cpf": "987.654.321-09",
        "email": "novonome@example.com"
    }
}


5. Excluir um usuário por ID
Método: DELETE
URL: http://localhost/FastSMS/API/public_html/api/user/deleteUserById/{id}
Substitua {id} pelo ID do usuário que você deseja excluir.

6. Fazer login de um usuário
Método: POST
URL: http://localhost/FastSMS/API/public_html/api/user/userLogin
Corpo da solicitação (JSON): Forneça o nome de login ou e-mail do usuário e a senha no corpo da solicitação. Consulte o exemplo no código-fonte.
Certifique-se de configurar essas solicitações no Postman e personalizá-las de acordo com os dados que você deseja usar para testar a API.

{
    "login": "nomedousuario",
    "senha": "senhadousuario"
}


-- Cria a tabela de usuários
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(255) NOT NULL,
    mae VARCHAR(255),
    cpf VARCHAR(14) UNIQUE NOT NULL,
    dataNascimento DATE,
    tel VARCHAR(15),
    sexo CHAR(1),
    cep VARCHAR(10),
    estado CHAR(2),
    cidade VARCHAR(255),
    numeroEndereco VARCHAR(10),
    endereco VARCHAR(255),
    complemento VARCHAR(255),
    email VARCHAR(255) UNIQUE,
    celular VARCHAR(15),
    senha VARCHAR(255) NOT NULL,
    tipo_user VARCHAR(50) NOT NULL
);

-- Insira registros de exemplo na tabela
INSERT INTO usuarios (nome, mae, cpf, dataNascimento, tel, sexo, cep, estado, cidade, numeroEndereco, endereco, complemento, email, celular, senha, tipo_user)
VALUES
    ('Patrick Soares de Oliveira', 'Maria da Silva Costa', '176.321.007-33', '2003-03-07', '(21) 9996-0260', 'Masculino', '23092-060', 'RJ', 'Rio de Janeiro', '09', 'BR-RJ\nTelecall Bloco 01 5 ANDAR', 'TEste', 'xuzonemo@mailinator.com', '(21) 99602-6088', '22Demaio@', 'usuário'),
    ('Usuário 1', 'Mãe 1', '123.456.789-01', '1990-01-15', '(11) 98765-4321', 'M', '12345-678', 'SP', 'São Paulo', '123', 'Rua das Flores, 123', 'Apto 101', 'usuario1@example.com', '(11) 98765-4321', 'senha123', 'usuário'),
    ('Usuário 2', 'Mãe 2', '987.654.321-09', '1985-05-20', '(21) 5555-5555', 'F', '54321-876', 'RJ', 'Rio de Janeiro', '456', 'Avenida Principal, 456', '', 'usuario2@example.com', '(21) 5555-5555', 'senha456', 'usuário'),
    ('Admin', 'Mãe Admin', '111.222.333-44', '1980-12-10', '(31) 7777-7777', 'M', '12345-678', 'MG', 'Belo Horizonte', '789', 'Rua Central, 789', 'Bloco B', 'admin@example.com', '(31) 7777-7777', 'senhaAdmin', 'admin');
