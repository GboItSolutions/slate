
# Formulaire

## GET Formulaires

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/form", Method.Get);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "API");
myHeaders.append("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/form", requestOptions)
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
      "id": "for_1b435e65e8c64105abf15c9802c695ff",
      "name": "Awesome Frozen Towels",
      "created": 1703960910180,
      "updated": 1703963507930,
      "updated_by": "8de30c59-d20b-46d3-ae60-a8e236e37f84"
    },
    // more items
  ],
  "count": 2,
  "total": 2,
  "total_page": 1
}
```

Point de terminaison pour retirer tous les Form.

### Requête Http

`GET https://api.openreza.com/form`

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`order` | created.desc | Trie les résultats par date de création. | created.desc, created.asc
`filter`|  | Retourne les résultats filtrés suivant le paramètre. | name

*Le filtre* **name** *doit contenir* **-**, *la partie droite représentant la chaîne de charactère à trouver.*

### Réponse

Code | Description 
---- | -----------
`200` | OK

## GET Formulaire

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/form/for_1b435e65e8c64105abf15c9802c695ff?embed=questions", Method.Get);
request.AddHeader("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/form/for_1b435e65e8c64105abf15c9802c695ff?embed=questions", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "for_1b435e65e8c64105abf15c9802c695ff",
    "name": "Awesome Frozen Towels",
    "created": 1703960910180,
    "updated": 1703963507930,
    "updated_by": "8de30c59-d20b-46d3-ae60-a8e236e37f84",
    "questions": [
        {
            "id": "que_8b5cd2d9196b4440848366e61b8f2a62",
            "created": 1703958190583,
            "updated": 1703958190583,
            "order": 1
        },
        {
            "id": "que_74fb40060bf346078c74f33a0edfe0f9",
            "created": 1703958187940,
            "updated": 1703958187940,
            "order": 2
        },
        {
            "id": "que_171339ce9e7f4afdbe495a3e4dc3e122",
            "created": 1703958195573,
            "updated": 1703958195573,
            "order": 3
        },
        {
            "id": "que_0af6ccbbf38f42769db25b884c3bc1a9",
            "created": 1703958193010,
            "updated": 1703958193010,
            "order": 4
        }
    ]
}
```

Point de terminaison pour retirer un Formulaire.

### Requête Http

`GET https://api.openreza.com/form/<id>`

### Parametres de l'Url

Parametre | type | Description | Requis
--------- | ---- | ----------- | ------
`id` | string | Identifiant du Formulaire | oui

### Parametres de la Requête

Parametre | type | Description | Requis | Valeur
--------- | ---- | ----------- | ------ | ------
`embed` | string | Propriétés de l'objet | non | questions,questions_translations,questions_response

### Réponse

Code | Description 
---- | -----------
`200` | OK

## POST Formulaire

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/form", Method.Post);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");
var body = @"{
" + "\n" +
@"    ""name"": ""Generic Rubber Bike""
" + "\n" +
@"}";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "API");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");

var raw = JSON.stringify({
  "name": "Generic Soft Hat"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/form", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "for_7568ce5c02c04629a6d902f2bf9cb1d9",
    "name": "Sleek Rubber Bacon",
    "created": 1704015534840,
    "updated": 1704015534840,
    "updated_by": "8de30c59-d20b-46d3-ae60-a8e236e37f84"
}
```

Point de terminaison pour ajouter un Formulaire.

### Requête Http

`POST https://api.openreza.com/form`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`name` | string  | Le nom Formulaire | oui |

### Réponse

Code | Description 
---- | -----------
`201` | Formulaire crée.

## POST Questions

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/form/questions", Method.Post);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");
var body = @"{
    "form": "for_5bef7115c0694eb0a95ff85a27e69c0a",
    "questions": [
        {
            "id": "que_0af6ccbbf38f42769db25b884c3bc1a9",
            "order": 1
        },
        {
            "id": "que_171339ce9e7f4afdbe495a3e4dc3e122",
            "order": 2
        }
    ]
}";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "API");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");

var raw = JSON.stringify({
  "form": "for_5bef7115c0694eb0a95ff85a27e69c0a",
  "questions": [
    {
      "id": "que_0af6ccbbf38f42769db25b884c3bc1a9",
      "order": 1
    },
    {
      "id": "que_171339ce9e7f4afdbe495a3e4dc3e122",
      "order": 2
    }
  ]
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/form/questions", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "for_5bef7115c0694eb0a95ff85a27e69c0a",
    "name": "Handmade Plastic Chicken",
    "created": 1704015637036,
    "updated": 1704015757526,
    "updated_by": "8de30c59-d20b-46d3-ae60-a8e236e37f84",
    "questions": [
        {
            "id": "que_0af6ccbbf38f42769db25b884c3bc1a9",
            "created": 1703958193010,
            "updated": 1703958193010,
            "order": 1
        },
        {
            "id": "que_171339ce9e7f4afdbe495a3e4dc3e122",
            "created": 1703958195573,
            "updated": 1703958195573,
            "order": 2
        }
    ]
}
```

Point de terminaison pour ajouter un Formulaire.

### Requête Http

`POST https://api.openreza.com/form/questions`

### Parametres

Parametre | Type | Description | Requis
--------- | ---- | ----------- | ------
`form` | string  | L'identifiant du formualre | oui
`questions` | [question]  | Tableau de question | oui

### Parametres Object Question

Parametre | Type | Description | Requis
--------- | ---- | ----------- | ------
`id` | string  | L'identifiant de de la question | oui
`order` | integer  | L'ordre de la question dans le formulaure | oui

### Réponse

Code | Description 
---- | -----------
`201` | Questions ajoutées au formualire.


## DELETE Formulaire

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/form/for_7568ce5c02c04629a6d902f2bf9cb1d9", Method.Delete);
request.AddHeader("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/form/for_7568ce5c02c04629a6d902f2bf9cb1d9", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour supprimer un Formulaire.

### Requête Http

`DELETE https://api.openreza.com/form/<id>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`id` | string | l'identifiant du Formulaire | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.

## DELETE Question 

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/form/for_5bef7115c0694eb0a95ff85a27e69c0a/question/que_0af6ccbbf38f42769db25b884c3bc1a9", Method.Delete);
request.AddHeader("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/form/for_5bef7115c0694eb0a95ff85a27e69c0a/question/que_0af6ccbbf38f42769db25b884c3bc1a9", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour supprimer une question d'un formulaire.

### Requête Http

`DELETE https://api.openreza.com/form/<formId>/question/<questionId>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`formId` | string | l'identifiant du Formulaire | oui
`questionId` | string | l'identifiant de la question | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.

