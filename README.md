


# Projeto Laravel 11 com Pacote de Autenticação Laravel/UI

## Preparar ambiente de desenvolvimento

### Instalar e configurar os programas

- PHP versão 8.2 ou 8.3
- Composer versão 2.7 ou superior
- Node.js(npm) versão 20.1 ou superior
- Mysql serve
- Visual studio code (vscode)
- Dbeaver
- Git versão 2.4 ou superior
- Criar conta no Github


**Habilitar as extensões no arquivo `php.ini`**

```
extension=zip
extension=fileinfo
extension=curl
extension=openssl
extension=gd
extension=mysqli
extension=pdo_mysql
extension=pdo_pgsql
extension=pdo_sqlite
extension=pgsql
extension=sqlite3
extension=mbstring

```

### Habilitar a exibição de erros em tela, o tipo de erro a ser reportado e o registro de logs de erros:

````
display_errors = on
error_reporting = E_ALL
log_errors = on
error_log = /tmp/php_errors.log

````

#### Aumentar o limite de memória (em mb), bem como o tempo de execução máximo de cada script (em segundos):

````
memory_limit = 256M
max_execution_time = 120

````



#### Permitir o upload de arquivos e aumentar os limites de upload e envio de formulários:

````
session.gc_maxlifetime = 14000

````
## Criar o Projeto Laravel 11

Para criar o projeto laravel 11, execute o comando:

```bash
composer create-project laravel/laravel:^11.0 exemple-app

```
Para executar o servidor web embutido do Laravel, utilize o comando:

```bash
php artisan serve

```

Com servidor em execução acesse pelo o navegador o link: `http://localhost:8000` ou `127.0.0.1:8000`.

## Instalar e configurar o pacote Laravel/UI

Para instalaro pacote Laravel/UI, execute os comandos abaixo:

```bash
composer require laravel/ui
php artisan ui vue --auth
npm install
npm run build (ou vite build -watch)

```

### Traduzir manualmente o idioma dos arquivos:

- `resources\views\auth\app.blade.php`
- `resources\views\auth\login.blade.php`
- `resources\views\auth\register.blade.php`
- `resources\views\auth\passwords\email.blade.php`
- `resources\views\auth\passwords\reset.blade.php`

### Traduzir mensagens de retornodo laravel para o idiona português brasileiro:

1. Fazer o download dos arquivos de tradução pt-br:
https://drive.google.com/file/d/1MCfa-WWYhQuaN6qbp3YKfTTueovZI1Vl/view?usp=sharing

2. Executar o comando: `php artisan lang:publish`;

3. Descompactar o arquivo `Laravel_pt-BR.rar`;

4. Copiar a pasta `pt-br` para a pasta `lang`;

5. Modificar no arquivo `.env` o valor das variáveis `APP_LOCALE` e `APP_FALLBACK_LOCALE` para `pt-br`: 

```
APP_LOCALE=pt-br
APP_FALLBACK_LOCALE=pt-br

```

##  Configuração do fuso horário do Brasil

Modificar no arquivo `.env` o valor da variável `APP_TIMEZONE` para `America/Sao_Paulo`: 

```
APP_TIMEZONE=America/Sao_Paulo

```

## Configurar a Redefinição de Senha do Usuário

### Instalar o **MailHog**

Para testar a configuração de redefinição de senha, iremos utilizar o **MailHog** que é uma ferramenta de desenvolvimento que permite capturar e exibir e-mails enviados por aplicativos durante o desenvolvimento local, ele simular um servidor de e-mail SMTP local.

1. Acesse o link para download do **MailHog**: https://github.com/mailhog/MailHog/releases.

2. Faça o download do arquivo binário (executável) do **MailHog** de acordo com seu Sistema Operacional.

3. Inicie o **MailHog** executando o arquivo baixado, será apresentado na tela do terminal o seguinte conteúdo (ou algo parecido):
**5. Criar o arquivo `database.sqlite` dentro do diretório `database`:**

```
2024/04/02 04:37:21 Using in-memory storage
2024/04/02 04:37:22 [SMTP] Binding to address: 0.0.0.0:1025
[HTTP] Binding to address: 0.0.0.0:8025
2024/04/02 04:37:22 Serving under http://0.0.0.0:8025/
Creating API v1 with WebPath:
Creating API v2 with WebPath:
[APIv1] KEEPALIVE /api/v1/events
[APIv1] KEEPALIVE /api/v1/events
```

4. No seu navegador e acesse `http://localhost:8025` para carregar a tela do **MailHog**, deverá constar a informação `Connected`, se não estiver constando `Connected` algo deu errado.
