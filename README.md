# json-server-demo
json-server api 

playlist tutorial original (em inglês): https://www.youtube.com/playlist?list=PLC3y8-rFHvwhc9YZIdqNL5sWeTCGxF4ya <br>

1 -link customizado c/ db.json customizado para este exercício: https://github.com/gopinav/json-server-tutorials/tree/master <br>
2 -link json-server original: https://github.com/typicode/json-server<br>
3 -link jsonlint validador de JSON: https://jsonlint.com/<br>
4 -link vercel (hospedagem de API): https://vercel.com/<br>
5 -link json-server já configurado para o vercel: https://github.com/kitloong/json-server-vercel<br>

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

***filtrando dados:<br>
por categoria:<br>
http://127.0.0.1:4000/products?category=electronics<br>

*o produto 10 tem uma propriedade especial discount shipping, podemos filtrar por ela:<br>
http://127.0.0.1:4000/products?category=electronics&discount.type=shipping<br>

****organizando dados - sort<br>
http://127.0.0.1:4000/products?_sort=price  <br>

http://127.0.0.1:4000/products?_sort=price&_order=desc<br>

*** mais um nivel de ordenação incluindo a categoria<br>
http://127.0.0.1:4000/products?_sort=price,category&_order=desc,asc<br>

*** paginação<br>
http://127.0.0.1:4000/products?_page=1<br>
http://127.0.0.1:4000/products?_page=2<br>

**especificando o tamanho da pagina:<br>
http://127.0.0.1:4000/products?_page=1&_limit=2<br>
http://127.0.0.1:4000/products?_page=2&_limit=2<br>

http://127.0.0.1:4000/products?_page=1&_limit=5<br>
http://127.0.0.1:4000/products?_page=2&_limit=5<br>

**** entrar no inspector > network > link: é possivel ver a primeira pagina, próxima pagina e última pagina

***operadores<br>
**especificando um range de busca para aquela propriedade<br>
http://localhost:4000/products?price_gte=2000&price_lte=6000<br>
GTE = greather than or equal -> maior ou igual<br>
LTE = less than or equal -> menor ou igual<br>

** operador NOT EQUAL (NÃO IGUAL)<br>
http://localhost:4000/products?id_ne=1<br>
** id not equal to 1 -. vai listar os produtos cuja ID é diferente de 1<br>

**operador LIKE
** filtrando os produtos pela categoria começando com f<br>
http://localhost:4000/products?category_like=^f<br>

**BUSCA POR TEXTO FULL<br>
http://localhost:4000/products?q=in<br>

**RELACIONAMENTOS (JOIN) - irá listar os produtos incluindo as informações dos reviews daquele produto<br>
http://localhost:4000/products?_embed=reviews  -> TODOS OS PRODUTOS INCLUINDO REVIEWS<br>
http://localhost:4000/products?_embed=reviews -> SOMENTE O PRODUTO 1 INCLUINDO SUAS REVIEWS<br>


**RELACIONAMENTOS (EXPAND) - irá listar os reviews e expandir os produtos aos quais eles estão relacionados<br>
http://localhost:4000/reviews?_expand=product  -> irá listar as reviews e os produtos aos quais eles estão relacionados<br>
http://localhost:4000/reviews/1?_expand=product -> irá listar somente a review 1 e os produtos aos quais eles estão relacionados<br>


************** requisição do tipo POST - INCLUIR UM NOVO REGISTRO<br>
1- instalar extensão THUNDER CLIENT no VSCode<br>
2- na barra lateral esquerda clicar no novo icone<br>
3- new request<br>
4- colocar url http://localhost:4000/products<br>
5- mudar método para POST<br>
6- selecionar BODY, e em seguida, a aba JSON<br>
7- copiar a estutura de um objeto e colocar aqui, depois alterar os dados para o onbjeto que eu quero INCLUIR<br>
8- clicar em SEND e verificar a resposta (RESPONSE, na lateral direita)<br>

************** requisição do tipo PUT - ALTERAR UM REGISTRO (necessário enviar o novo objeto completo)<br>
1- alterar o tipo de requisição para PUT no Thunder Client<br>
2- incluir a ID do registro a ser alterado no URL, irá ficar assim exemplo: http://localhost:4000/products/11<br>
3- selecionar BODY, e em seguida, a aba JSON<br>
4 - colar o objeto a ser alterado, efetuar as modificações desejadas e clicar em SEND<br>
5- verificar a resposta (RESPONSE, na lateral direita)<br>


***************** requisição do tipo PATCH - ALTERAR SOMENTE UM CAMPO ESPECÍFICO DE UM REGISTRO<br>
1- alterar o tipo de requisição para PATCH no Thunder Client<br>
2- incluir a ID do registro a ser alterado no URL, irá ficar assim exemplo: http://localhost:4000/products/11<br>
3- selecionar BODY, e em seguida, a aba JSON<br>
4 - digitar aqui comente o que irá a ser alterado no objeto, por exemplo, para alterar o preço : { "price": 4000 }<br>
5- clicar em SEND e verificar a resposta (RESPONSE, na lateral direita)<br>

*************** requisição do tipo DELETE - APAGAR UM REGISTRO<br>
1- alterar o tipo de requisição para DELETE no Thunder Client<br>
2- incluir a ID do registro a ser DELETADO no URL, irá ficar assim exemplo: http://localhost:4000/products/11<br>
3- clicar em SEND e verificar a resposta (RESPONSE, na lateral direita)<br>
