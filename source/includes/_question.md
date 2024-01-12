
# Questions

## GET Questions

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/question", Method.Get);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("x-api-key", "KS-K1sG3lLTbwj2972BondCdjhb7idspZTeDlOf1BCW2ak0_GEx41pW-wxJjt00A");
request.AddHeader("Cookie", ".AspNetCore.Antiforgery.Svnx1GNBrNo=CfDJ8Oac1XiQCJRIvmQ-IvlucHZX-yxLZQNU9BD2qDirrMOZAjCGjxR2KnyuORGDqsYiGgQkeLVQ8DJABB0VoRk9roiJ5FU0irUWgn5C2IaXOqoRoi0U_Xixy6a9KYF3rW5KSSevIg-Hw4mKoOmqpfDjJP4; XSRF-TOKEN=CfDJ8Oac1XiQCJRIvmQ-IvlucHZXaS3t5-Ds3b90lPwS4y3_f0SquvDbS12bpaVSQs6YGKvYo-A730ltjM8RTbJtzMJ_o_7HOSQV_odfOu1cbic6UGfvf7GKwH3D2B9gpbm4EjkdJf1_FMhGzhgUFMZboJE");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "API");
myHeaders.append("x-api-key", "KS-K1sG3lLTbwj2972BondCdjhb7idspZTeDlOf1BCW2ak0_GEx41pW-wxJjt00A");
myHeaders.append("Cookie", ".AspNetCore.Antiforgery.Svnx1GNBrNo=CfDJ8Oac1XiQCJRIvmQ-IvlucHZX-yxLZQNU9BD2qDirrMOZAjCGjxR2KnyuORGDqsYiGgQkeLVQ8DJABB0VoRk9roiJ5FU0irUWgn5C2IaXOqoRoi0U_Xixy6a9KYF3rW5KSSevIg-Hw4mKoOmqpfDjJP4; XSRF-TOKEN=CfDJ8Oac1XiQCJRIvmQ-IvlucHZXaS3t5-Ds3b90lPwS4y3_f0SquvDbS12bpaVSQs6YGKvYo-A730ltjM8RTbJtzMJ_o_7HOSQV_odfOu1cbic6UGfvf7GKwH3D2B9gpbm4EjkdJf1_FMhGzhgUFMZboJE");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/question", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "page_size": 10,
    "page_number": 1,
    "data": [
        {
            "id": "que_e824b1d8cd7246b2bb4484475ddf6f59",
            "created": 1703880082903,
            "updated": 1703880082903,
            "translations": [
                {
                    "id": "qut_4e660ba746d74a439e70a580473e3061",
                    "text": "Neque nobis quis ut suscipit illum.",
                    "language": "fr"
                },
                {
                    "id": "qut_e2dff25d96044f3a9c9813cceab24ad0",
                    "text": "Blanditiis harum magni.",
                    "language": "es"
                },
                {
                    "id": "qut_fde634f357bc4f9884bb7dad17892a94",
                    "text": "Iste corrupti labore non ducimus et sed esse laudantium.",
                    "language": "en"
                }
            ]
        },
        // more items
    ],
    "count": 10,
    "total": 25,
    "total_page": 3
}
```

Point de terminaison pour retirer tous les Questions.

### Requête Http

`GET https://api.openreza.com/question`

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`order` | created.desc | Trie les résultats par date de création. | created.desc, created.asc
`filter`|  | Retourne les résultats filtrés. | language

*Les filtres doivent contenir* **-**, *la partie droite représentant la chaîne de charactère à trouver.*
<br />
*Pour le filtre* **language** les valeurs possibles sont :

* fr
* en
* es
* de

### Réponse

Code | Description 
---- | -----------
`200` | OK

## GET Question

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/question/que_fb47c569934d42dabc77fdc55783da2b", Method.Get);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("x-api-key", "KS-K1sG3lLTbwj2972BondCdjhb7idspZTeDlOf1BCW2ak0_GEx41pW-wxJjt00A");
request.AddHeader("Cookie", ".AspNetCore.Antiforgery.Svnx1GNBrNo=CfDJ8Oac1XiQCJRIvmQ-IvlucHZX-yxLZQNU9BD2qDirrMOZAjCGjxR2KnyuORGDqsYiGgQkeLVQ8DJABB0VoRk9roiJ5FU0irUWgn5C2IaXOqoRoi0U_Xixy6a9KYF3rW5KSSevIg-Hw4mKoOmqpfDjJP4; XSRF-TOKEN=CfDJ8Oac1XiQCJRIvmQ-IvlucHZXaS3t5-Ds3b90lPwS4y3_f0SquvDbS12bpaVSQs6YGKvYo-A730ltjM8RTbJtzMJ_o_7HOSQV_odfOu1cbic6UGfvf7GKwH3D2B9gpbm4EjkdJf1_FMhGzhgUFMZboJE");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "API");
myHeaders.append("x-api-key", "KS-K1sG3lLTbwj2972BondCdjhb7idspZTeDlOf1BCW2ak0_GEx41pW-wxJjt00A");
myHeaders.append("Cookie", ".AspNetCore.Antiforgery.Svnx1GNBrNo=CfDJ8Oac1XiQCJRIvmQ-IvlucHZX-yxLZQNU9BD2qDirrMOZAjCGjxR2KnyuORGDqsYiGgQkeLVQ8DJABB0VoRk9roiJ5FU0irUWgn5C2IaXOqoRoi0U_Xixy6a9KYF3rW5KSSevIg-Hw4mKoOmqpfDjJP4; XSRF-TOKEN=CfDJ8Oac1XiQCJRIvmQ-IvlucHZXaS3t5-Ds3b90lPwS4y3_f0SquvDbS12bpaVSQs6YGKvYo-A730ltjM8RTbJtzMJ_o_7HOSQV_odfOu1cbic6UGfvf7GKwH3D2B9gpbm4EjkdJf1_FMhGzhgUFMZboJE");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/question/que_fb47c569934d42dabc77fdc55783da2b", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "que_fb47c569934d42dabc77fdc55783da2b",
    "created": 1703861849710,
    "updated": 1703861849710
}
```

Point de terminaison pour retirer une question.

### Requête Http

`GET https://api.openreza.com/question/<id>`

### Parametres de l'Url

Parametre | type | Description | requis
--------- | ---- | ----------- | -------
`id` | string | identifiant de la question | oui

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`embed` |  | propriétés de l'objet | translations, response, response_choices

### Réponse

Code | Description 
---- | -----------
`200` | OK

## POST Question

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/question", Method.Post);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-K1sG3lLTbwj2972BondCdjhb7idspZTeDlOf1BCW2ak0_GEx41pW-wxJjt00A");
var body = @"{
    "text": "Veritatis labore nihil velit illo sit non.",
    "language": "en",
    "response": {
        "type": "CHOICE",
        "choice_type": "CHECK",
        "nb_accepted_response": 2,
        "choices": [
            {
                "text": "Dolore aut qui quia nesciunt maiores laborum."
            },
            {
                "text": "Nihil et et enim eum."
            },
            {
                "text": "Blanditiis vel iure veritatis recusandae et."
            },
            {
                "text": "Vel qui aut qui vitae molestiae eos perferendis."
            }
        ]
    }
}";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "API");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "KS-K1sG3lLTbwj2972BondCdjhb7idspZTeDlOf1BCW2ak0_GEx41pW-wxJjt00A");

var raw = JSON.stringify({
  "text": "Sed voluptatem dolor illo praesentium.",
  "language": "en",
  "response": {
    "type": "CHOICE",
    "choice_type": "CHECK",
    "nb_accepted_response": 2,
    "choices": [
      {
        "text": "Est molestiae maxime quos."
      },
      {
        "text": "At aut harum distinctio non voluptate et itaque."
      },
      {
        "text": "Aut neque magni."
      },
      {
        "text": "Veritatis similique quo."
      }
    ]
  }
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/question", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "que_afd31cc35a864cfb9d919d16f20a1def",
    "created": 1703926508943,
    "updated": 1703926508943,
    "response": {
        "id": "res_dd6f7ae187af471ca4cfaee571a6edb1",
        "type": "CHOICE",
        "choice_type": "CHECK",
        "nb_accepted_response": 2
    }
}
```

Point de terminaison pour ajouter une question.

### Requête Http

`POST https://api.openreza.com/question`

### Parametres

Parametre | Type | Description | Requis | Defaut | values
--------- | ---- | ----------- | ------ | ------ | ------
`text` | string  | Le texte de la question | oui | |
`language` | string | La langue dans laquelle vous rédifez la question | oui | | Pour des raisons techniques les langues authorisées sont **fr**, **en**, **es**, **de**
`response` | object | Les paramètres de réponse que vous attentez pour la question | oui | | 

### Parametres object Response

Parametre | Type | Description | Requis | Defaut | values
--------- | ---- | ----------- | ------ | ------ | ------
`type` | string  | Le type de réponse attendu | oui | | TEXT, CHOICE 
`choice_type` | string | Le type de choix attendu | oui si `type`=CHOICE | | LIST, CHECK
`choices` | object | Les choix que vous souhaitez proposer | oui si `type`=CHOICE | | 

### Parametres object Choice

Parametre | Type | Description | Requis | Defaut | values
--------- | ---- | ----------- | ------ | ------ | ------
`text` | string  | Le texte du choix| oui | |  

### Réponse

Code | Description 
---- | -----------
`201` | Question crée.

## POST Traduction
```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/question", Method.Post);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-K1sG3lLTbwj2972BondCdjhb7idspZTeDlOf1BCW2ak0_GEx41pW-wxJjt00A");
var body = @"{
    "text": "Aperiam sint iusto.",
    "language": "fr",
    "question": "que_f3e195395aac4ba88f3f385dbd2ccc82",
    "response": {
        "type": "CHOICE",
        "choice_type": "LIST",
        "choice_count_response": 1,
        "choices": [
            {
                "text": "Dolore repudiandae eos est facere."
            },
            {
                "text": "Sit eligendi veniam voluptas et labore."
            },
            {
                "text": "Qui quidem vitae dolor iste minus."
            },
            {
                "text": "Consequatur nam temporibus."
            }
        ]
    }
}";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "API");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "KS-K1sG3lLTbwj2972BondCdjhb7idspZTeDlOf1BCW2ak0_GEx41pW-wxJjt00A");

var raw = JSON.stringify({
  "text": "Hic enim amet in dicta nulla earum assumenda.",
  "language": "fr",
  "question": "que_f3e195395aac4ba88f3f385dbd2ccc82",
  "response": {
    "type": "CHOICE",
    "choice_type": "LIST",
    "choice_count_response": 1,
    "choices": [
      {
        "text": "Eum et minima illum rem."
      },
      {
        "text": "Sapiente assumenda vel quibusdam."
      },
      {
        "text": "Voluptatibus est quod ducimus a voluptas magni."
      },
      {
        "text": "Natus error et vero unde perferendis quas."
      }
    ]
  }
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/question", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "que_f3e195395aac4ba88f3f385dbd2ccc82",
    "created": 1703927167586,
    "updated": 1703927167586,
    "response": {
        "id": "res_10e4cb8fe5bc4c169d32b1e9796e8fb8",
        "type": "CHOICE",
        "choice_type": "LIST"
    }
}
```

Point de terminaison pour rajouter une traduction à une question existante.

### Requête Http

`POST https://api.openreza.com/question`

### Parametres

Tous les paramètres sont les mêmes que pour ajouter une question, il convient néamoins d'ajouter le paramètre `question`.

Parametre | Type | Description | Requis |
--------- | ---- | ----------- | ------ |
`question` | string  | L'identifiant de la question à laquelle vous ajoutez une traduction | oui |

### Réponse

Code | Description 
---- | -----------
`201` | Ajout de la traduction effectuée.

## DELETE Question

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/product/pro_1bfad6af07894ceeaabbbfc7221b66d6", Method.Delete);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "API");
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/product/pro_1bfad6af07894ceeaabbbfc7221b66d6", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour supprimer un Question.

### Requête Http

`DELETE https://api.openreza.com/question/<id>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`id` | string | l'identifiant du question | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.

