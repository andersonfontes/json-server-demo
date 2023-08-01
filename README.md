# json-server-demo
json-server api 

playlist tutorial original (em inglês): https://www.youtube.com/playlist?list=PLC3y8-rFHvwhc9YZIdqNL5sWeTCGxF4ya

1 -link customizado c/ db.json customizado para este exercício: https://github.com/gopinav/json-server-tutorials/tree/master
2 -link json-server original: https://github.com/typicode/json-server
3 -link jsonlint validador de JSON: https://jsonlint.com/
4 -link vercel (hospedagem de API): https://vercel.com/
5 -link json-server já configurado para o vercel: https://github.com/kitloong/json-server-vercel

AULA JSON-SERVER LOCAL:

1- baixar arquivos do link 1
2- comandos terminal:
npm init -y
npm install json-server

3- mudar dentro do arquivo package.json,  para -- watch db.json
3.1 - apagar a segunda linha que está dentro dos {} dentro do arquivo routes.json (e também a vírgula)

4- comando para iniciar a api: npm run serve-json

http://127.0.0.1:4000/products

http://127.0.0.1:4000/reviews

http://127.0.0.1:4000/products/1

http://127.0.0.1:4000/products/5

http://127.0.0.1:4000/reviews/1

*********** requisições do tipo GET - BUSCAR DADOS

***filtrando dados:
por categoria:
http://127.0.0.1:4000/products?category=electronics

*o produto 10 tem uma propriedade especial discount shipping, podemos filtrar por ela:
http://127.0.0.1:4000/products?category=electronics&discount.type=shipping

****organizando dados - sort
http://127.0.0.1:4000/products?_sort=price  

http://127.0.0.1:4000/products?_sort=price&_order=desc

*** mais um nivel de ordenação incluindo a categoria
http://127.0.0.1:4000/products?_sort=price,category&_order=desc,asc

*** paginação
http://127.0.0.1:4000/products?_page=1
http://127.0.0.1:4000/products?_page=2

**especificando o tamanho da pagina:
http://127.0.0.1:4000/products?_page=1&_limit=2
http://127.0.0.1:4000/products?_page=2&_limit=2

http://127.0.0.1:4000/products?_page=1&_limit=5
http://127.0.0.1:4000/products?_page=2&_limit=5

**** entrar no inspector > network > link: é possivel ver a primeira pagina, próxima pagina e última pagina

***operadores
**especificando um range de busca para aquela propriedade
http://localhost:4000/products?price_gte=2000&price_lte=6000
GTE = greather than or equal -> maior ou igual
LTE = less than or equal -> menor ou igual

** operador NOT EQUAL (NÃO IGUAL)
http://localhost:4000/products?id_ne=1
** id not equal to 1 -. vai listar os produtos cuja ID é diferente de 1

**operador LIKE
** filtrando os produtos pela categoria começando com f
http://localhost:4000/products?category_like=^f

**BUSCA POR TEXTO FULL
http://localhost:4000/products?q=in

**RELACIONAMENTOS (JOIN) - irá listar os produtos incluindo as informações dos reviews daquele produto
http://localhost:4000/products?_embed=reviews  -> TODOS OS PRODUTOS INCLUINDO REVIEWS
http://localhost:4000/products?_embed=reviews -> SOMENTE O PRODUTO 1 INCLUINDO SUAS REVIEWS


**RELACIONAMENTOS (EXPAND) - irá listar os reviews e expandir os produtos aos quais eles estão relacionados
http://localhost:4000/reviews?_expand=product  -> irá listar as reviews e os produtos aos quais eles estão relacionados
http://localhost:4000/reviews/1?_expand=product -> irá listar somente a review 1 e os produtos aos quais eles estão relacionados


************** requisição do tipo POST - INCLUIR UM NOVO REGISTRO
1- instalar extensão THUNDER CLIENT no VSCode
2- na barra lateral esquerda clicar no novo icone
3- new request
4- colocar url http://localhost:4000/products
5- mudar método para POST
6- selecionar BODY, e em seguida, a aba JSON
7- copiar a estutura de um objeto e colocar aqui, depois alterar os dados para o onbjeto que eu quero INCLUIR
8- clicar em SEND e verificar a resposta (RESPONSE, na lateral direita)

************** requisição do tipo PUT - ALTERAR UM REGISTRO (necessário enviar o novo objeto completo)
1- alterar o tipo de requisição para PUT no Thunder Client
2- incluir a ID do registro a ser alterado no URL, irá ficar assim exemplo: http://localhost:4000/products/11
3- selecionar BODY, e em seguida, a aba JSON
4 - colar o objeto a ser alterado, efetuar as modificações desejadas e clicar em SEND
5- verificar a resposta (RESPONSE, na lateral direita)


***************** requisição do tipo PATCH - ALTERAR SOMENTE UM CAMPO ESPECÍFICO DE UM REGISTRO
1- alterar o tipo de requisição para PATCH no Thunder Client
2- incluir a ID do registro a ser alterado no URL, irá ficar assim exemplo: http://localhost:4000/products/11
3- selecionar BODY, e em seguida, a aba JSON
4 - digitar aqui comente o que irá a ser alterado no objeto, por exemplo, para alterar o preço : { "price": 4000 }
5- clicar em SEND e verificar a resposta (RESPONSE, na lateral direita)

*************** requisição do tipo DELETE - APAGAR UM REGISTRO
1- alterar o tipo de requisição para DELETE no Thunder Client
2- incluir a ID do registro a ser DELETADO no URL, irá ficar assim exemplo: http://localhost:4000/products/11
3- clicar em SEND e verificar a resposta (RESPONSE, na lateral direita)
