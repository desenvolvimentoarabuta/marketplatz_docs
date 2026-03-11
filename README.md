# Swagger Documentation for Marketplatz API

Este diretório contém a especificação OpenAPI (`openapi.yaml`) e a interface interativa (`index.html`) gerada com `swagger-ui`.

## Rotas atualizadas e sincronizadas
- **Auth**: `/auth/register`, `/auth/login`, `/auth/me`, `/auth/logout`
- **Products**: `/products`, `/products/{id}`, `/categories/{id}`
- **Cart**: `GET`, `POST`, `PUT`, `DELETE` em `/cart`
- **Favorites**: Listagem, verificação, adição e remoção em `/favorites`
- **Orders**: Full CRUD em `/orders`
- **Order Items**: Gerenciamento granular em `/order-items`
- **User**: Perfil, Foto, Senha em `/users`
- **Commons**: `/units`, `/status`, `/payments`, `/categories`, `/subcategories`, `/promotions`

### Todas as rotas do sistema (arquivo `app/Config/Routes.php`)
- `GET /` → Web\User\HomeController::index
- `GET /perfil` → Web\User\UserController::index (`auth`)
- `POST /perfil/upload-photo` → Web\User\UserController::uploadPhoto (`auth`)

#### Dashboard administrador (`admin/dashboard`)
- `GET /admin/dashboard/exportxls/(:segment)`
- `GET /admin/dashboard/` (index)
- `GET /admin/dashboard/vendas`
- `GET /admin/dashboard/vendedores`
- `GET /admin/dashboard/clientes`
- `GET /admin/dashboard/financeiro`
- `GET /admin/dashboard/desempenho`
- `GET /admin/dashboard/export/(:segment)`
- `GET /admin/dashboard/exportxml/(:segment)`

#### Operador
- `GET /operator/new-page`
- `GET /operator`
- `GET /operator/banners`
- `POST /operator/banners/store`
- `GET /operator/banners/edit/(:num)`
- `POST /operator/banners/update/(:num)`
- `POST /operator/banners/delete/(:num)`
- `POST /operator/banners/update-order`
- `POST /operator/banners/toggle-status/(:num)`

#### APIs públicas
- `GET /api/v1/banners/ativos`
- `GET /api/v1/promotions`

#### APIs protegidas (jwt)
- `POST /api/v1/favorites/toggle`
- `POST /api/v1/favorites/check`
- `GET /api/v1/favorites/`
- `POST /api/v1/products/{id}/favorite`
- `GET /api/v1/products/{id}/favorite`
- `GET /api/v1/user` (show)
- `PUT /api/v1/user/update`
- `POST /api/v1/user/update-password`
- `POST /api/v1/user/update-photo`
- `DELETE /api/v1/user/delete`

> Os namespaces exibidos acima referem-se aos controladores usados no backend. Para rotas web você pode consultar o README da pasta `docs/backend/api` para detalhes adicionais.

### Como atualizar
1. Edite `openapi.yaml` adicionando ou ajustando rotas, parâmetros e exemplos.
2. O `index.html` referenciará automaticamente `openapi.yaml`.
3. Suba o conteúdo para o repositório de documentação (GitHub Pages, Netlify ou similar).

## Integração com documentação existente
O repositório principal já possui uma pasta `docs/` com markdowns descritivos das APIs (
`docs/backend/api/*.md`). Esses arquivos não são automaticamente convertidos pelo Swagger;
para mantê-los juntos você pode:

- Incluir um link do `README.md` desta pasta para os md existentes.
- Converter os markdowns em um site estático com MkDocs/Docusaurus e hospedar ao lado da API.

> **Nota**: o OpenAPI especifíca apenas os endpoints. qualquer explicação adicional (fluxos,
> parâmetros complexos, exemplos de uso em Javascript/CLI etc.) ainda precisam estar nos md
> ou em outro lugar.
