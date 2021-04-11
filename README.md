# API Superhero

Projeto API de super-heróis

Trata-se de de uma API que busca dados de super-heróis de uma outra API.


Busca de herói

Esta rota nos permitire buscar um herói não só pelo nome, mas por qualquer informação que esteja escrita em qualquer um dos seus atributos de texto.
- Rota GET /search que recebe um único atributo (via url) "q" - exemplo: "/search?q=hair"
- Se o valor de "q" tiver menos de 3 caracteres, retornar um erro com status 400
- A busca confere se a informação buscada está presente em alguns dos atributos do super-herói (name, tudo em appearance, biography e work), ignorando maiuscula e minúsculas (case insensitive)
- Se nenhum super herói for encontrado, status 204 é retornado
- Os que forem encontratos, retornam em um array de heróis
- Se no post vier um header "case-sensitive" com valor "true", buscar levando em consideração o case, se "case-sensitive" for "false" ou não for informado, achar independente de maiuscula e minúsculas

Detalhe de herói
- Rota GET /hero/{slug}, que irá obter o herói em questão pelo atributo slug
- Se o herói existir, retornar apenas ele com status 200
- Se o herói não existir, retornar 404

Cache local
- A sua API só deve obter dados da superhero-api uma única vez, quando ela receber a primeira requisição (seja de busca ou detalhe)
- Na primeira busca ou detalhe, se não houver nenhum registro local, obter os dados de /all.json e salvar na memoria (todos os heróis)
- Tanto a busca quando o detalhe irão consultar apenas os dados da memória
