
# Salles

## GET Salles

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/room?filter=&order=created.desc", Method.Get);
request.AddHeader("X-ULTIM-ORIGIN", "dashboard");
request.AddHeader("X-API-KEY", "OPR-D6b9kbKIwqB7yAJ5vFQmVGbZZCV9XOcPDDjUJCHDTSiC6HvQyIZJo_SzUmfS");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "dashboard");
myHeaders.append("X-API-KEY", "OPR-D6b9kbKIwqB7yAJ5vFQmVGbZZCV9XOcPDDjUJCHDTSiC6HvQyIZJo_SzUmfS");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/room?filter=&order=created.desc", requestOptions)
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
            "id": "roo_8bd7ef9447854878979c2f2fc3541796",
            "created": 1705076493086,
            "updated": 1705076493090,
            "name": "Unbranded Metal Gloves",
            "capacity": 1000
        },
        {
            "id": "roo_ac8e2de37cea461dbbf30afe710760dd",
            "created": 1705071891633,
            "updated": 1705071891633,
            "name": "Licensed Metal Pants",
            "capacity": 2
        },
        {
            "id": "roo_6cc381d508ba4a9ba928edd46cd1d7b4",
            "created": 1705071872806,
            "updated": 1705071872806,
            "name": "Intelligent Soft Bacon",
            "capacity": 2
        }
    ],
    "count": 3,
    "total": 3,
    "total_page": 1
}
```

Point de terminaison pour retirer toutes les Salles.

### Requête Http

`GET https://api.openreza.com/room`

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

## GET Salle

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/room/roo_61700ac562504e36aa19d0f1b0e403ec", Method.Get);
request.AddHeader("X-ULTIM-ORIGIN", "dashboard");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "dashboard");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/room/roo_61700ac562504e36aa19d0f1b0e403ec", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "roo_61700ac562504e36aa19d0f1b0e403ec",
    "created": 1705072035380,
    "updated": 1705072035383,
    "name": "Awesome Frozen Shirt",
    "capacity": 1000
}
```

Point de terminaison pour retirer une Salle.

### Requête Http

`GET https://api.openreza.com/room/<id>`

### Parametres de l'Url

Parametre | type | Description | Requis
--------- | ---- | ----------- | ------
`id` | string | Identifiant de la Salle | oui

### Réponse

Code | Description 
---- | -----------
`200` | OK

## POST Salle

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/room", Method.Post);
request.AddHeader("X-ULTIM-ORIGIN", "dashboard");
var body = @"{
"name" : "Practical Cotton Soap",
"capacity": 1000
}";
request.AddParameter("text/plain", body,  ParameterType.RequestBody);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "dashboard");

var raw = "{\r\n    \"name\" : \"Generic Rubber Chips\",\r\n    \"capacity\": 1000\r\n}";

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/room", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "roo_8bd7ef9447854878979c2f2fc3541796",
    "created": 1705076493086,
    "updated": 1705076493090,
    "name": "Unbranded Metal Gloves",
    "capacity": 1000
}
```

Point de terminaison pour ajouter une Salle.

### Requête Http

`POST https://api.openreza.com/room`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`name` | string  | La designation du Salle | oui |
`capacity` | string | La description du Salle | non | 1

### Réponse

Code | Description 
---- | -----------
`201` | Evènement crée.

## DELETE Salle

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/room/roo_8bd7ef9447854878979c2f2fc3541796", Method.Delete);
request.AddHeader("X-ULTIM-ORIGIN", "dashboard");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "dashboard");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/room/roo_8bd7ef9447854878979c2f2fc3541796", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour supprimer une Salle.

### Requête Http

`DELETE https://api.openreza.com/room/<id>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`id` | string | l'identifiant de la Salle | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.

