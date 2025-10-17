## 📚 Sistema de Gerenciamento de Biblioteca — MySQL + phpMyAdmin  


![MySQL](https://img.shields.io/badge/MySQL-Database-orange?style=for-the-badge&logo=mysql)
![phpMyAdmin](https://img.shields.io/badge/phpMyAdmin-Interface-yellow?style=for-the-badge&logo=phpmyadmin)

---

## 🧠 Sobre o Projeto  
Este projeto foi desenvolvido como parte de uma atividade prática de **Banco de Dados**, com o objetivo de criar e manipular um sistema de **empréstimos de livros**.  
O ambiente utilizado foi o **phpMyAdmin**, permitindo a execução e visualização das tabelas em um banco **MySQL**.

---

# 🛠️ Tecnologia Utilizada  
  - 🧩 **phpMyAdmin**  


---

## 🗃️ Estrutura do Banco de Dados  

####🧾 Tabela: `livros`  

| Campo | Tipo | Descrição |
|--------|------|-----------|
| id | INT (PK) | Identificador único do livro |
| titulo | VARCHAR(65) | Título do livro |
| autor | VARCHAR(50) | Nome do autor |
| gênero | VARCHAR(35) | Categoria literária |
| Anopublicacao | DATE | Ano de publicação |

---

### 👥 Tabela: `usuario1`  

| Campo | Tipo | Descrição |
|--------|------|-----------|
| id | INT (PK) | Identificador único |
| nome | VARCHAR(50) | Nome do usuário |
| email | VARCHAR(50) | E-mail |
| Tipousuario | ENUM | Tipo de usuário: `professor`, `aluno`, `funcionario` |

---

### 📅 Tabela: `empréstimo`  

| Campo | Tipo | Descrição |
|--------|------|-----------|
| id | INT (PK) | Identificador único |
| usuario_id | INT (FK) | Referência ao usuário |
| livro_id | INT (FK) | Referência ao livro |
| Dataemprestimo | DATE | Data do empréstimo |
| Datadevolucao | DATE | Data prevista para devolução |

---

## 💾 Inserindo Dados  

```sql
INSERT INTO livros (titulo, autor, gênero, Anopublicacao)
VALUES 
('Dom Casmurro', 'Machado de Assis', 'Romance', 1899),
('O Pequeno Príncipe', 'Antoine de Saint-Exupéry', 'Fábula / Filosófico', 1943),
('Clean Code', 'Robert C. Martin', 'Tecnologia', 2008),
('1984', 'George Orwell', 'Ficção Científica', 1949),
('Python para Análise de Dados', 'Wes McKinney', 'Tecnologia', 2017);

-- Exibir todos os livros em ordem alfabética
SELECT * FROM livros ORDER BY titulo ASC;

-- Exibir apenas os usuários do tipo 'aluno'
SELECT * FROM usuario1 WHERE Tipousuario = 'aluno';

-- Filtrar empréstimos realizados em março
SELECT * FROM emprestimo WHERE MONTH(Dataemprestimo) = 3;

-- Listar livros de tecnologia
SELECT * FROM livros WHERE gênero = 'Tecnologia' ORDER BY titulo ASC;

-- Atualizar o ano de publicação de um livro
UPDATE livros SET Anopublicacao = 2025 WHERE id = 6;

-- Deletar um livro específico
DELETE FROM livros WHERE id = 6;

-- Remover empréstimos antigos (mais de 15 dias)
DELETE FROM emprestimo WHERE Dataemprestimo < DATE_SUB(CURDATE(), INTERVAL 15 DAY);

✨ Autora

👩‍💻 Ana Carolina
📧 anaacarolinafonsecasouza@gmail.com
