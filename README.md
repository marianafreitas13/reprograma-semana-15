# reprograma-semana-15
on6-xp-s15-jwt
Autenticação
Criar rota autenticada
Instalar "jsonwebtoken" via npm install $ npm install jsonwebtoken

Gerar chave pelo https://travistidwell.com/jsencrypt/demo/ e guardar a chave pública

Instalar dotenv-safe $ npm install dotenv-safe

Criar arquivo .env.example e .env, ambos com chave chamada SECRET $ SECRET=chave_rsa_aqui_sem_aspas

Carregar as variáveis de ambiente no projeto, no arquivo tarefasRoute.js $ require('dotenv-safe').config();

Criar variável contendo a SECRET $ const secret = process.env.SECRET

Criar método de autenticação em getAll

Pegar o header de autorização e enviar uma mensagem de erro 401 quando vir vazio $ const authHeader = request.get('authorization');

Passar bearer token no header de autenticação via Postman $ Bearer TOKEN_JWT_AQUI

Verificar token JWT e enviar uma mensagem de erro 403 caso seja inválido $ jwt.verify(token, SECRET, (error) => {...});

Criar rota para criar colaboradoras
Criar rota para criar usuária em colaboradorasRoute.js $ router.post('/', controller.create);

Criar model de colaboradoras com id, nome, email e senha

Criar método no controller para criar colaboradora

Criar uma colaborada de teste via Postman

Criptografar senha das colaboradoras
Instalar bcrypt $ npm install bcrypt

Fazer require do bcrypt no colaboradorasController.js $ const bcrypt = require('bcrypt');

Gerar hash com senha recebida no body da request $ bcrypt.hashSync(request.body.senha, 10);

Criar nova colabora no banco com a senha hasherizada e o login (email) recebido no body da request

Criar rota de login
Criar rota de login em colaboradorasRoute.js $ router.post('/login', controller.login);

Buscar colaboradora a partir do email recebido na request, e mostrar um erro 404 caso não encontre $ Colaboradoras.findOne({ email: req.body.email }, function(error, colaboradora) {...}

Comparar senha de colaboradora encontra com a senha recebida via request, e mostrar um erro 401 caso seja diferente $ bcrypt.compareSync(request.body.senha, colaboradoraEncontrada.senha);

Fazer require do plugin JWT $ const jwt = require('jsonwebtoken');

Importar SECRET e gerar token JWT a partir do nome e secret e devolver na request $ jwt.sign({ name: colaboradora.name }, SECRET);

Bater na rota getAll via Postman com o token gerado
