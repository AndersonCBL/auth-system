## Sobre o Projeto

Este é um projeto de autenticação de usuários desenvolvido como parte de um teste prático. Construído com [Laravel 10](https://laravel.com) e PHP 8.2, utiliza [Laravel Breeze](https://laravel.com/docs/10.x/starter-kits#laravel-breeze) para autenticação, [Blade](https://laravel.com/docs/10.x/blade) para templates, [Bootstrap](https://getbootstrap.com) para estilização e [SQLite](https://www.sqlite.org) como banco de dados. O projeto permite que usuários se cadastrem, façam login, editem seus dados (nome, e-mail, senha) e façam upload de uma foto de perfil, que é exibida no menu de navegação.

### Funcionalidades Implementadas

- [Autenticação com Laravel Breeze](https://laravel.com/docs/10.x/starter-kits#laravel-breeze): Registro, login e logout de usuários, com autenticação via e-mail e senha.
- [Cadastro de Usuário](https://laravel.com/docs/10.x/starter-kits#breeze-registration): Tela de registro com campos para nome, e-mail, senha e confirmação de senha, com senhas armazenadas usando hash (Bcrypt).
- [Login e Logout](https://laravel.com/docs/10.x/starter-kits#breeze-login): Tela de login com redirecionamento para o dashboard e funcionalidade de logout no menu.
- [Edição de Perfil](https://laravel.com/docs/10.x/starter-kits#breeze-profile-management): Atualização de nome, e-mail, senha e upload de foto de perfil, com validações para e-mails duplicados e senhas fortes.
- [Upload de Imagem de Perfil](https://laravel.com/docs/10.x/filesystem): Armazenamento local de imagens e exibição no menu de navegação, com uma imagem padrão para usuários sem foto.
- Interface traduzida para o português, incluindo telas e mensagens de validação.
- Redirecionamento da URL raiz (`/`) para a tela de login.
- Link para registro na tela de login.
- Retorno visual para ações (ex.: "Perfil atualizado com sucesso!").

## Requisitos

Para rodar o projeto, você precisará dos seguintes requisitos instalados:

- [PHP 8.2](https://www.php.net/downloads.php)
- [Composer](https://getcomposer.org/download/)
- [Node.js e npm](https://nodejs.org/en/download/)
- [SQLite](https://www.sqlite.org/download.html) (o projeto cria o banco automaticamente)
- [Git](https://git-scm.com/downloads)

## Instalação

Siga os passos abaixo para configurar e executar o projeto localmente. Todos os comandos necessários estão consolidados em um único bloco de código `bash` ao final desta seção.

- **Clone o repositório**:

  Clone o repositório para o seu ambiente local usando o Git. Substitua `<URL_DO_REPOSITORIO>` pela URL do repositório público no GitHub ou Bitbucket.

- **Instale as dependências do Composer**:

  Instale as dependências do PHP listadas no arquivo `composer.json`.

- **Copie o arquivo de ambiente**:

  Crie o arquivo de configuração `.env` a partir do modelo fornecido.

- **Configure o banco de dados SQLite**:

  Crie o arquivo do banco SQLite na pasta `database`. Em seguida, edite o arquivo `.env` e ajuste as configurações do banco. Substitua `/caminho/absoluto/para/laravel-auth-test` pelo caminho absoluto do seu projeto (ex.: `/home/user/laravel-auth-test`).

- **Gere a chave da aplicação**:

  Gere a chave única da aplicação Laravel.

- **Crie o link simbólico para armazenamento**:

  O projeto permite upload de imagens de perfil, que são armazenadas no disco `public`. Crie o link simbólico para acessar os arquivos.

- **Execute as migrações**:

  Crie as tabelas no banco de dados SQLite executando as migrações.

- **Instale as dependências do Node.js e compile os assets**:

  O projeto usa Bootstrap e JavaScript para a interface. Instale as dependências do Node.js e compile os assets.

- **Inicie o servidor**:

  Inicie o servidor embutido do Laravel.

- **Acesse o projeto**:

  Abra o navegador e vá para `http://localhost:8000`. Você será redirecionado para a tela de login.

- **Ajuste de permissões (se necessário)**:

  Se o upload de imagens não funcionar, ajuste as permissões do diretório `storage`. (Ajuste o usuário `www-data` conforme seu servidor web.)

### Todos os Comandos em um Único Bloco

Execute os seguintes comandos no terminal, na ordem apresentada:

```bash
# Clone o repositório
git clone <URL_DO_REPOSITORIO>
cd laravel-auth-test

# Instale as dependências do Composer
composer install

# Copie o arquivo de ambiente
cp .env.example .env

# Crie o arquivo do banco SQLite
touch database/database.sqlite

# Configure o .env (ajuste o caminho)
echo "DB_CONNECTION=sqlite" >> .env
echo "DB_DATABASE=/caminho/absoluto/para/laravel-auth-test/database/database.sqlite" >> .env

# Gere a chave da aplicação
php artisan key:generate

# Crie o link simbólico para armazenamento
php artisan storage:link

# Execute as migrações
php artisan migrate

# Instale as dependências do Node.js e compile os assets
npm install
npm run dev

# Inicie o servidor
php artisan serve

# Ajuste de permissões (se necessário)
chmod -R 775 storage
chown -R www-data:www-data storage
 ```
---

## Diferenciais
 Os seguintes diferenciais foram implementados para agregar valor ao projeto:

- **Upload de Imagem de Perfil**: Com armazenamento local e exibição no menu de navegação, incluindo uma imagem padrão.
- **Interface traduzida para o português.**
- **Middleware para Rotas Autenticadas**: Rotas protegidas por autenticação (padrão do Breeze).
## Observações
-**Senhas Fortes**: As senhas devem ter pelo menos 8 caracteres, uma letra minúscula, uma maiúscula e um número.
-**Imagem Padrão**: Coloque uma imagem em public/images/default-profile.png para usuários sem foto de perfil. Alternativamente, use uma placeholder como https://via.placeholder.com/32.
## Solução de Problemas
- **Erro ao acessar imagens**: Verifique se o link simbólico para armazenamento foi criado e se o diretório storage tem permissões de escrita.
- **Mensagens de validação em inglês**: Confirme que o locale em config/app.php está definido como pt_BR.
- **Erro ao rodar migrações**: Verifique se o caminho do DB_DATABASE no arquivo .env está correto e se o arquivo database/database.sqlite foi criado.
## Licença
Este projeto é licenciado sob a MIT License.
