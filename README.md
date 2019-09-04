# docker-wordpress

Use the WP api:
To get posts use:
localhost:8000/wp-json/wp/v2/posts

added plug in JWT authentication for WP REST API
some config to .htaccess

added to .htaccess

RewriteCond %{HTTP:Authorization} ^(._)
RewriteRule ^(._) - [E=HTTP_AUTHORIZATION:%1]
SetEnvIf Authorization "(.\*)" HTTP_AUTHORIZATION=\$1

go to wp-config.php
define('JWT_AUTH_SECRET_KEY', 'your-top-secret-key');
define('JWT_AUTH_CORS_ENABLE', true);

Namespace and Endpoints
When the plugin is activated, a new namespace is added

/jwt-auth/v1
Also, two new endpoints are added to this namespace

Endpoint | HTTP Verb
/wp-json/jwt-auth/v1/token | POST
/wp-json/jwt-auth/v1/token/validate | POST

In your headers
Set your content-type application/json
Authorization Bearer "Your token ID"
