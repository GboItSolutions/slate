
# Lieux

## GET Lieux

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/place", Method.Get);
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "{{origin}}");
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/place", requestOptions)
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
            "id": "pla_ee59e8e58967408497886bc0af97038e",
            "created": 1703930128960,
            "updated": 1703930128963,
            "designation": "Sterling Club"
        },
        // more items
    ],
    "count": 10,
    "total": 15,
    "total_page": 2
}
```

Point de terminaison pour retirer tous les lieux.

### Requête Http

`GET https://api.openreza.com/place`

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`order` | created.desc | Trie les résultats par date de création. | created.desc, created.asc
`filter`|  | Retourne les résultats filtrés suivant le paramètre. | designation

*Le filtre* **designation** *doit contenir* **-**, *la partie droite représentant la chaîne de charactère à trouver.*

### Réponse

Code | Description 
---- | -----------
`200` | OK

## GET Lieu

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/place/pla_7f8d81e81dd04c628f99153f5893d05d", Method.Get);
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "{{origin}}");
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/place/pla_7f8d81e81dd04c628f99153f5893d05d", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "pla_7f8d81e81dd04c628f99153f5893d05d",
    "created": 1703698576070,
    "updated": 1703698576073,
    "designation": "Narciso Mountain"
}
```

Point de terminaison pour retirer un lieu.

### Requête Http

`GET https://api.openreza.com/place/<id>`

### Parametres de l'Url

Parametre | type | Description | Requis
--------- | ---- | ----------- | ------
`id` | string | Identifiant du lieu | oui

### Parametres de la Requête

Parametre | type | Description | Valeurs | Defaut
--------- | ---- | ----------- | ------- | ------
`embed` | string | Propriétés de l'objet | `room` | 

### Réponse

Code | Description 
---- | -----------
`200` | OK

## POST Lieu

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/place", Method.Post);
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
var body = @"{
    "designation": "Iliana Dale"
}";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "{{origin}}");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var raw = JSON.stringify({
  "designation": "Tiana Well"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/place", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "pla_08745d18451c4e898da967a2ae3adf1f",
    "created": 1703842024003,
    "updated": 1703842024003,
    "designation": "Iliana Dale"
}
```

Point de terminaison pour ajouter un lieu.

### Requête Http

`POST https://api.openreza.com/place`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`designation` | string  | La designation du lieu | oui |
`description` | string | La description du lieu | non | 
`latitude` | decimal | La latitude du lieu | non | 
`longitude` | decimal | La longitude du lieu | non | 


### Réponse

Code | Description 
---- | -----------
`201` | Evènement crée.

## PUT Lieu Ajout d'une Salle 

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/place/room", Method.Put);
request.AddHeader("Content-Type", "application/json");
request.AddHeader("X-API-KEY", "OPR-TbqZzAJnut3WRj6wRhO1OCnOp2K4ADChXvvaVF2XAraFbKXO1NujVX9TjxgQ");

var body = @"{
"place": "pla_cf48fee1df5e4b7d8106785024713cf4",
"room": "roo_6cc381d508ba4a9ba928edd46cd1d7b4"
}";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("X-API-KEY", "OPR-TbqZzAJnut3WRj6wRhO1OCnOp2K4ADChXvvaVF2XAraFbKXO1NujVX9TjxgQ");

var raw = JSON.stringify({
  "place": "pla_cf48fee1df5e4b7d8106785024713cf4",
  "room": "roo_6cc381d508ba4a9ba928edd46cd1d7b4"
});

var requestOptions = {
  method: 'PUT',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/place/room", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "place": "pla_cf48fee1df5e4b7d8106785024713cf4",
    "room": "roo_6cc381d508ba4a9ba928edd46cd1d7b4"
}
```

Point de terminaison pour ajouter un lieu.

### Requête Http

`PUT https://api.openreza.com/place`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`place` | string  | L'identifiant du lieu | oui |
`room` | string | L'identifiant de la salle | non | 

### Réponse

Code | Description 
---- | -----------
`201` | Salle associée au lieu.

## DELETE Lieu

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/place/pla_6313c56e040b441189f56636e9bdab93", Method.Delete);
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "{{origin}}");
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/place/pla_6313c56e040b441189f56636e9bdab93", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour supprimer un lieu.

### Requête Http

`DELETE https://api.openreza.com/place/<id>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`id` | string | l'identifiant du lieu | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.

## DELETE Salle d'un lieu 

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/place/pla_cf48fee1df5e4b7d8106785024713cf4/room/roo_6cc381d508ba4a9ba928edd46cd1d7b4", Method.Delete);
request.AddHeader("X-API-KEY", "OPR-TbqZzAJnut3WRj6wRhO1OCnOp2K4ADChXvvaVF2XAraFbKXO1NujVX9TjxgQ");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-API-KEY", "OPR-TbqZzAJnut3WRj6wRhO1OCnOp2K4ADChXvvaVF2XAraFbKXO1NujVX9TjxgQ");
var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/place/pla_cf48fee1df5e4b7d8106785024713cf4/room/roo_6cc381d508ba4a9ba928edd46cd1d7b4", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour supprimer un lieu.

### Requête Http

`DELETE https://api.openreza.com/place/<placeId>/room/<roomId>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`placeId` | string | l'identifiant du lieu | oui
`roomId` | string | l'identifiant de la salle | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.
