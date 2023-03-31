Necessário instalar e configurar o plugin (JWT Authentication for WP-API)

link: https://br.wordpress.org/plugins/jwt-authentication-for-wp-rest-api/


JSON Web Token (JWT)
Necessário para salvarmos a autenticação do usuário. Enviamos o nome de usuário + senha, e o mesmo retorna uma string com um Token, que poderá ser utilizado nas próximas requisições para autenticarmos o usuário.

1 Instalar o plugin

JWT Authentication for WP-API

2 Modificar o .htaccess

RewriteEngine on
RewriteCond %{HTTP:Authorization} ^(.*)
RewriteRule ^(.*) - [E=HTTP_AUTHORIZATION:%1]

3 Modificar o wp-config

Gere uma string aqui: https://api.wordpress.org/secret-key/1.1/salt/

define('JWT_AUTH_SECRET_KEY', 'STRING AQUI');
define('JWT_AUTH_CORS_ENABLE', true);

4 Ativar o plugin

5 Salvar os links permanentes para dar um refresh nas rotas

Uso
Um POST para o url com o usuário e senha irá retornar um JWT, o mesmo deve ser enviado nas requisições que dependem de autenticação.

/json/jwt-auth/v1/token
/json/jwt-auth/v1/token/validate