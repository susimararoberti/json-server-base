<h1 align="center">Portfólio - API</h1>

<p align="center">
Este é o backend da aplicação Portfólio - API -> Seu objetivo é fornecer algumas rotas para criação de uma base simples para um portfólio de um desenvolvedor.
</p>
<br/>
<br/>
<h2 align="center">Endpoints</h2>

<p>A presente API tem um total de 10 endpoints.</p>
<p>O url de base desta API é: http://localhost:3001 </p><br/>

<h2 align="center">Rotas Públicas</h2><br/>

<p>Esta API possui apenas uma rota pública ou seja, não é preciso estar cadastrado ou logado/autenticado para listar as Tecnologias cadastradas pelos demais usuários.</p>
<p>Para acessar as tecnologias cadastradas é preciso utilizar o seguinte verbo e endpoint:</p><br/>
<p>` GET /tecs ` Formato de resposta - Status 200</p>
<span>[
	{
		"technologie": "CSS",
		"level": "Iniciante",
		"experience": "6 meses",
		"userId": 1,
		"id": 1
	}
]</span>
<p>Caso não haja nenhuma tecnologia cadastrada e respost será de um array vazio: [ ] </p><br>

<h2 align="center">Rotas de Cadastro e Login</h2><br/>

<p>As rotas a seguir são necessárias para a utilização de todos os demais endpoints envolvidos com a possibilidade de cadastrar/editar/excluir Tecnologias e ainda cadastrar/editar/excluir/listar Experiências (profissionais) dos usuários.</p><br>

<h3>Cadastro:</h3><br/>

<p>Para realização do cadastro de um novo usuário é necessário utilizar o endpoint abaixo:</p>
<p>`POST /register` </p>
<p>Formato da requisição:</p>
<span>{
	"email" : "alunokenzie@email.com",
	"password" : "987654"
}</span><br/><br/>
<p>Formato de resposta - Status 201</p>
<span>{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFsdW5vQGVtYWlsLmNvbSIsImlhdCI6MTY1NjYwODE3MSwiZXhwIjoxNjU2NjExNzcxLCJzdWIiOiIzIn0.mUtvqKHJpg_193N3wypZVP8iiXo_AxwiGaacIPQeZc4",
	"user": {
		"email": "alunokenzie@email.com",
		"id": 1
	}
}</span><br/><br/>

<h3>Login:</h3><br/>

<p>Para realização do login de um usuário já cadastrado, é necessário utilizar o endpoint abaixo:</p>
<p>`POST /login`</p>
<p>Formato da requisição:</p>
<span>{
	"email" : "alunokenzie@email.com",
	"password" : "987654"
}</span><br/><br/>
<p>Formato de resposta - Status 200</p>
<span>{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFsdW5vQGVtYWlsLmNvbSIsImlhdCI6MTY1NjYwODE3MSwiZXhwIjoxNjU2NjExNzcxLCJzdWIiOiIzIn0.mUtvqKHJpg_193N3wypZVP8iiXo_AxwiGaacIPQeZc4",
	"user": {
		"email": "alunokenzie@email.com",
		"id": 1
	}
}</span><br/><br/>
<p>Formato de erro - Status 400</p>
<span>Email incorreto:  "Cannot find user"</span><br>
<span>Senha incorreta:  "Incorrect password"</span><br>

<h2 align="center">Rotas Privadas</h2><br/>

<p>Nas rotas privadas é necessário informar no cabeçalho da requisição o campo "Authorization" da seguinte maneira:</p>
<p>> Authorization: Bearer {token}</p><br/>

<h3>Rotas de Tecnologias</h3><br/>
<h4>Cadastro de Tecnologias:</h4><br/>

<p>Para realização do cadastro de uma nova tecnologia é necessário utilizar o endpoint abaixo:</p>
<p>`POST /tecs`</p><br/>

<p>Formato da requisição</p>
<span>{
	"technologie" : "React",
	"level" : "Iniciante",
	"experience" : "6 meses",
	"userId" : 1
}</span><br/><br/>
<p>Formato de resposta - Status 200</p>
<span>{
	"technologie" : "React",
	"level" : "Iniciante",
	"experience" : "6 meses",
	"userId" : 1,
    "id" : 1
}</span><br/><br/><br/>

<h4>Edição de Tecnologias:</h4><br/>

<p>Para editar uma tecnologia cadastrada é necessário utilizar o endpoint abaixo:</p>
<p>`PUT /tecs/id`</p><br/>

<p>Formato da requisição</p>
<span>{
	"technologie" : "React",
	"level" : "Iniciante",
	"experience" : "12 meses",
	"userId" : 1
}</span><br/><br/>
<p>Formato de resposta - Status 200</p>
<span>{
	"technologie" : "React",
	"level" : "Iniciante",
	"experience" : "12 meses",
	"userId" : 1,
    "id" : 1
}</span><br/><br/>
<p>Formato de Erro - Status 404:  { }</p><br/><br/>

<h4>Exclusão de Tecnologias:</h4><br/>

<p>Para excluir uma tecnologia cadastrada é necessário utilizar o endpoint abaixo:</p>
<p>`DELETE /tecs/id`</p><br/>

<p>Formato da requisição</p>
<span>Não é necessário um corpo de requisição (apenas o id da tecnologia no endpoint e o token em Authorization)</span><br/><br/>
<p>Formato de resposta - Status 200:  { }</p><br/>
<p>Formato de Erro - Status 404:  { }</p><br/><br/>

<h3>Rotas de Experiências</h3><br/>
<h4>Cadastro de Experiências:</h4><br/>

<p>Para realização do cadastro de uma nova experiência é necessário utilizar o endpoint abaixo:</p>
<p>`POST /experience`</p><br/>

<p>Formato da requisição</p>
<span>{
	"company" : "X",
	"office" : "Desenvolvedor Back End",
	"period of experience" : "3 meses",
	"userId" : 1
}</span><br/><br/>
<p>Formato de resposta - Status 200</p>
<span>{
	"company": "X",
	"office": "Desenvolvedor Back End",
	"period of experience": "3 meses",
	"userId": 1,
	"id": 1
}</span><br/><br/>
<p>Formato de Erro - Status 403</p>
<p>"Private resource creation: request body must have a reference to the owner id" (quando não foi enviada ao menos uma informação no corpo da requisição)</p><br/><br/>

<h4>Edição de Experiências:</h4><br/>

<p>Para editar uma experiência cadastrada é necessário utilizar o endpoint abaixo:</p>
<p>`PUT /experience/id`</p><br/>

<p>Formato da requisição</p>
<span>{
	"company" : "X",
	"office" : "Desenvolvedor Back End",
	"period of experience" : "6 meses",
	"userId" : 1
}</span><br/><br/>
<p>Formato de resposta - Status 200</p>
<span>{
	"company": "X",
	"office": "Desenvolvedor Back End",
	"period of experience": "6 meses",
	"userId": 1,
	"id": 1
}</span><br/><br/>
<p>Formato de Erro - Status 403</p>
<p>"Private resource creation: request body must have a reference to the owner id" (quando não foi enviada ao menos uma informação no corpo da requisição)</p><br/><br/>

<h4>Exclusão de Experiências:</h4><br/>

<p>Para excluir uma experiência cadastrada é necessário utilizar o endpoint abaixo:</p>
<p>`DELETE /experience/id` </p><br/>

<p>Formato da requisição</p>
<span>Não é necessário um corpo de requisição (apenas o id da tecnologia no endpoint e o token em Authorization)</span><br/><br/>
<p>Formato de resposta - Status 200:  { }</p><br/>
<p>Formato de Erro - Status 404:  { }</p><br/>
<p>Formato de Erro - Status 403</p>
<p>"Private resource access: entity must have a reference to the owner id" (quando não foi informado o id da experiência a ser excluída)</p><br/>
<p>Formato de Erro - Status 401</p>
<p>"Cannot read property 'userId' of undefined" (quando não existe o id da experiência buscada)</p><br/><br/>

<h4>Listagem de Experiências:</h4><br/>

<p>Para listar as experiências cadastradas é necessário usar o seguinte endpoint:</p>
<p>`GET /experience` </p><br/>

<p>Formato da requisição</p>
<span>Não é necessário um corpo de requisição (apenas o token em Authorization - podendo ser o token do user que cadastrou ou outro usuário logado)</span><br/><br/>
<p>Formato de resposta - Status 200</p>
<span>[
	{
		"company": "Tech X",
		"office": "Desenvolvedor Front End",
		"period of experience": "2 anos",
		"userId": 3,
		"id": 1
	},
	{
		"company": "Dev Y",
		"office": "Desenvolvedor Back End",
		"period of experience": "1 ano",
		"userId": 3,
		"id": 2
	},
	{
		"company": "Now Dev",
		"office": "Desenvolvedor Full Stack",
		"period of experience": "9 meses",
		"userId": 3,
		"id": 3
	},
	{
		"company": "One",
		"office": "Desenvolvedor Front End",
		"period of experience": "10 meses",
		"userId": 3,
		"id": 4
	}
]</span><br/><br/>
<p>Formato de resposta - Status 200</p>
<span>[ ] (quando não há nenhuma experiência cadastrada)</span>
<p>Formato de Erro - Status 401</p>
<p>"Missing authorization header" (quando não foi informado o token na Authorization)</p><br/>
