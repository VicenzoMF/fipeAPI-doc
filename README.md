# FipeAPI - Documentação

Para começar gostaria de sinalizar que já possuo ciencia da latência para cada requisição. Existem dois motivos que causam toda essa demora, mas os dois seriam resolvidos caso haja mais recursos para investir nisso.
##### Localização do servidor:
O servidor está localizado nos Estados Unidos, o que causa um atraso na comunicação do servidor com o site da FIPE, no processamento e na devolução da requisição.
##### Processo que está sendo utilizado:
Atualmente, o processo utilizado é que cada vez que uma requisição é feita, um web scraping é realizado apenas para aquela requisição, gerando um atraso muito longo para cada solicitação. Se eu possuísse uma máquina dedicada exclusivamente para rodar esta API, poderia fazer um scraping completo mensalmente e armazenar todos os dados. Quando uma requisição ocorresse, poderia buscar nestes dados, diminuindo muito a latência.

Por que eu deveria fazer isso todo mês? Além dos preços dos veículos mudarem, novos modelos são lançados ao longo do ano. Portanto, se o scraping fosse feito anualmente, por exemplo, haveriam veículos que não poderiam ser requisitados.
## Como utilizar

link da API: https://api-7yaz6r4tpq-uc.a.run.app/

##### GET marcas

Para retornar todas marcas disponíveis para pesquisa, basta colocar `/marcas`.

[api-7yaz6r4tpq-uc.a.run.app/marcas](api-7yaz6r4tpq-uc.a.run.app/marcas "api-7yaz6r4tpq-uc.a.run.app/marcas")

    [
      {
        "codigo": "1",
        "nome": "Acura"
      },
      {
        "codigo": "2",
        "nome": "Agrale"
      }, ...

Cada requisição retorna um campo ***codigo*** e* **nome***, o código será utilizado para identificar nas próximas requsições.

#### GET Veiculos

Retornar os veículos de uma marca específica é simples, basta colocar o código da marca, seguindo este padrão: `marcas/(codigo marca)/veiculos`
[https://api-7yaz6r4tpq-uc.a.run.app/marcas/1/veiculos](https://api-7yaz6r4tpq-uc.a.run.app/marcas/1/veiculos "https://api-7yaz6r4tpq-uc.a.run.app/marcas/1/veiculos")

    [
      {
        "codigo": "1",
        "nome": "Integra GS 1.8"
      },
      {
        "codigo": "2",
        "nome": "Legend 3.2/3.5"
      }, ...
#### GET anos/modelos
Seguindo o padrão anterior, você irá colocar assim `marcas/(codigo marca/veiculos/(codigo veiculo)/anos`
https://api-7yaz6r4tpq-uc.a.run.app/marcas/1/veiculos/2/anos

    [
      {
        "codigo": "1998-1",
        "nome": "1998 Gasolina"
      },
      {
        "codigo": "1997-1",
        "nome": "1997 Gasolina"
      }, ...
