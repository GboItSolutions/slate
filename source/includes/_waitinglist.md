
# Liste d'Attente

## GET Listes d'Attente

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/waitinglist", Method.Get);
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

fetch("https://localhost:7117/waitinglist", requestOptions)
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
            "id": "wli_9c055168d72c483b83d9cb9f26cdeb9b",
            "event": "eve_150c404aeda04433ad5e16c000ebbed4",
            "created": 1704019235923,
            "updated": 1704019235926,
            "capacity": 2,
            "fill_rate": 0
        }
    ],
    "count": 1,
    "total": 1,
    "total_page": 1
}
```

Point de terminaison pour retirer tous les Form.

### Requête Http

`GET https://api.openreza.com/waitinglist`

### Parametres de Requête

Parametre | Default | Description | Valeurs | defaut
--------- | ------- | ----------- | ------- | ------
`order` | created.desc | Trie les résultats par date de création. | created.desc, created.asc
`filter`|  | Retourne les résultats filtrés suivant le paramètre. | all, past, futur, capacity, fill_rate | futur

### Réponse

Code | Description 
---- | -----------
`200` | OK

## GET Liste d'Attente

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/waitinglist/wli_0f79b98710e242dab209d0f907bd50be?embed=clients", Method.Get);
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

fetch("https://localhost:7117/waitinglist/wli_0f79b98710e242dab209d0f907bd50be?embed=clients", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "wli_0f79b98710e242dab209d0f907bd50be",
    "event": "eve_56c2c413458e4dd292168f4e44e4cf5b",
    "created": 1704019636810,
    "updated": 1704020466260,
    "capacity": 10,
    "fill_rate": 40,
    "clients": [
        {
            "id": "cli_3d7c9e7961b74127a3e7fa43765560ec",
            "created": 1704020389353,
            "updated": 1704020389353,
            "first_name": "Octavia",
            "last_name": "ROGAHN",
            "created_source": "API",
            "updated_source": "API",
            "email": "octavia.rogahn@rezasport.testinator.com"
        },
        {
            "id": "cli_a7323b48f5ad4ee39bd91c9d9ceb4f35",
            "created": 1704020388906,
            "updated": 1704020388906,
            "first_name": "Kristy",
            "last_name": "GAYLORD",
            "created_source": "API",
            "updated_source": "API",
            "email": "kristy.gaylord@rezasport.testinator.com"
        },
        {
            "id": "cli_c910be11b9d0460db613036a48439af8",
            "created": 1704020389810,
            "updated": 1704020389810,
            "first_name": "Lukas",
            "last_name": "GRAHAM",
            "created_source": "API",
            "updated_source": "API",
            "email": "lukas.graham@rezasport.testinator.com"
        },
        {
            "id": "cli_e80bec04f603442b9d98b63675323b23",
            "created": 1704020388383,
            "updated": 1704020388383,
            "first_name": "Cortney",
            "last_name": "BAUMBACH",
            "created_source": "API",
            "updated_source": "API",
            "email": "cortney.baumbach@rezasport.testinator.com"
        }
    ]
}
```

Point de terminaison pour retirer un Liste d'Attente.

### Requête Http

`GET https://api.openreza.com/waitinglist/<id>`

### Parametres de l'Url

Parametre | type | Description | Requis
--------- | ---- | ----------- | ------
`id` | string | Identifiant de la Liste d'Attente | oui

### Parametres de la Requête

Parametre | type | Description | Requis | Valeur
--------- | ---- | ----------- | ------ | ------
`embed` | string | Propriétés de l'objet | non | clients

### Réponse

Code | Description 
---- | -----------
`200` | OK

## POST Ajout Client

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/waitinglist/client", Method.Post);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");
var body = "{
    "waiting_list": "wli_0f79b98710e242dab209d0f907bd50be",
    "client": "cli_4ff02733cf004600aeba4f287bf977ae"
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
  "waiting_list": "wli_0f79b98710e242dab209d0f907bd50be",
  "client": "cli_4ff02733cf004600aeba4f287bf977ae"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/waitinglist/client", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "client": "cli_3d7c9e7961b74127a3e7fa43765560ec",
    "created": 1704033620770
}
```

Point de terminaison pour ajouter un client dans une liste d'attente.

### Requête Http

`POST https://api.openreza.com/form`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`waiting_list` | string  | L'identifiant de la Liste D'attente | oui 
`client` | string  | L'identifiant du client | oui 

### Réponse

Code | Description 
---- | -----------
`201` | Client ajouté à la liste d'attente.

## PUT Move Client From WL to Bookings

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/waitinglist/wli_0f79b98710e242dab209d0f907bd50be/move/cli_4ff02733cf004600aeba4f287bf977ae", Method.Put);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var settings = {
  "url": "https://localhost:7117/waitinglist/wli_0f79b98710e242dab209d0f907bd50be/move/cli_4ff02733cf004600aeba4f287bf977ae",
  "method": "PUT",
  "timeout": 0,
  "headers": {
    "X-ULTIM-ORIGIN": "API",
    "x-api-key": "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp"
  },
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "boo_69e21f34777f4d6aa2a494a7d03ef7b3",
    "public_booking_id": "f996baa53c784172947bb3e056824f22",
    "created": 1704033784380,
    "updated": 1704033784086,
    "source": "API",
    "clients": [
        {
            "id": "boc_3268cc05bc0a4ade99ce620ee3ea3225",
            "show": false,
            "debit_formula": false,
            "paid": "NONE",
            "client": {
                "id": "cli_4ff02733cf004600aeba4f287bf977ae",
                "created": 1704020386910,
                "updated": 1704020386910,
                "first_name": "Shemar",
                "last_name": "LYNCH",
                "created_source": "API",
                "updated_source": "API",
                "email": "shemar.lynch@rezasport.testinator.com",
                "bookings": []
            },
            "state": "ACCEPTED"
        }
    ],
    "password": "F6AB5",
    "owner": {
        "id": "cli_4ff02733cf004600aeba4f287bf977ae",
        "first_name": "Shemar",
        "last_name": "LYNCH",
        "email": "SHEMAR.LYNCH@REZASPORT.TESTINATOR.COM"
    }
}
```

Point de terminaison pour ajouter un client dans une liste d'attente.

### Requête Http

`PUT https://api.openreza.com/waitinglist/<waitinglistId>/move/<clientId>`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`waitinglistId` | string  | L'identifiant de la Liste d'attente | oui 
`clientId` | string  | L'identifiant du client | oui 

### Réponse

Code | Description 
---- | -----------
`200` | Ok, Client ajouté au booking et retiré de la liste d'attente.


## DELETE Liste d'Attente

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

Point de terminaison pour supprimer un Liste d'Attente.

### Requête Http

`DELETE https://api.openreza.com/form/<id>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`id` | string | l'identifiant du Liste d'Attente | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.

## DELETE Client de Liste d'Attente

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/waitinglist/wli_0f79b98710e242dab209d0f907bd50be/client/cli_3d7c9e7961b74127a3e7fa43765560ec", Method.Delete);
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
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/waitinglist/wli_0f79b98710e242dab209d0f907bd50be/client/cli_3d7c9e7961b74127a3e7fa43765560ec", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour supprimer un client d'une liste d'Attente.

### Requête Http

`DELETE https://api.openreza.com/waitinglist/<waitinglistId>/client/<clientId>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`waitinglistId` | string | l'identifiant du Liste d'Attente | oui
`clientId` | string | l'identifiant du client | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.
