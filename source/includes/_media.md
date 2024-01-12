
# Media

## GET Medias

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/media", Method.Get);
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

fetch("https://localhost:7117/media", requestOptions)
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
      "id": "med_692e67a203d2471cb280c1a3eb7913b5",
      "created": 1703707282270,
      "updated": 1703707282273,
      "name": "UserDelete.csv",
      "validation_state": "ACCEPTED",
      "short": "https://localhost:7117/dwl/452bf49d"
    },
    {
      "id": "med_eeee8dbbefaf4bc28011cb07a1c22c46",
      "created": 1703707261260,
      "updated": 1703707261263,
      "name": "38126.pdf",
      "validation_state": "ACCEPTED",
      "short": "https://localhost:7117/dwl/32a24f05"
    }
  ],
  "count": 2,
  "total": 2,
  "total_page": 1
}
```

Point de terminaison pour retirer tous les médias.

### Requête Http

`GET https://api.openreza.com/media`

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`order` | created.desc | Trie les résultats par date de création. | created.desc, created.asc
`filter`|  | Retourne les résultats selon le filtre. | name, description, validation_state

*Les filtres doivent contenir* **-**, *la partie droite représentant la chaîne de charactère à trouver, et être séparés par **;**.*
*Exemple :* `name-38;validation_state-accepted`

### Réponse

Code | Description 
---- | -----------
`200` | OK

## GET Media

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/media/med_12defe4e7cc14c87a72ba598a742a8df", Method.Get);
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/media/med_12defe4e7cc14c87a72ba598a742a8df", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "med_12defe4e7cc14c87a72ba598a742a8df",
    "created": 1703776515223,
    "updated": 1703776515226,
    "name": "38126.pdf",
    "validation_state": "PENDING",
    "short": "https://localhost:7117/dwl/d98cb96d"
}
```

Point de terminaison pour retirer un Média.

### Requête Http

`GET https://api.openreza.com/media/<id>`

### Parametres de l'Url

Parametre | type | Description | Requis
--------- | -----| ----------- | -------
`id` | string | L'identifiant du média | oui

### Réponse

Code | Description 
---- | -----------
`200` | OK


## GET Download Media File

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/media/dwl/med_12defe4e7cc14c87a72ba598a742a8df", Method.Get);
request.AddHeader("X-ULTIM-ORIGIN", "WEBCOMP");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "WEBCOMP");
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/media/dwl/med_12defe4e7cc14c87a72ba598a742a8df", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour retirer un Média.

### Requête Http

`GET https://api.openreza.com/media/dwl/<id>`

### Parametres de l'Url

Parametre | type | Description | Requis
--------- | -----| ----------- | -------
`id` | string | L'identifiant du média | oui

### Réponse

Code | Description 
---- | -----------
`200` | OK


## GET Container Size

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/media/size", Method.Get);
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

fetch("https://localhost:7117/media/size", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "o": 1431598,
    "ko": "1398.04",
    "mo": "1.37"
}
```


Point de terminaison qui retourne l'utilisation du conteneur de stockage.

### Requête Http

`GET https://api.openreza.com/media/size`

### Réponse

Code | Description 
---- | -----------
`200` | Ok


## POST Media

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/media", Method.Post);
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
request.AlwaysMultipartFormData = true;
request.AddFile("file", "/C:/Users/bapti/Downloads/dqjx2fqs.png");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "{{origin}}");
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var formdata = new FormData();
formdata.append("file", fileInput.files[0], "/C:/Users/bapti/Downloads/dqjx2fqs.png");

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: formdata,
  redirect: 'follow'
};

fetch("https://localhost:7117/media", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "med_612021d847fe4859982da6840c91a70e",
    "created": 1703755920886,
    "updated": 1703755920886,
    "name": "dqjx2fqs.png",
    "validation_state": "ACCEPTED",
    "short": "https://localhost:7117/dwl/91def77e"
}
```

Point de terminaison pour ajouter un média. La taille maximale authorisée est 256 MB.

### Requête Http

`POST https://api.openreza.com/media`

### Réponse

Code | Description 
---- | -----------
`201` | Fichier uploadé.

## DELETE Media

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/media/a4f7334a", Method.Delete);
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

fetch("https://localhost:7117/media/a4f7334a", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour supprimer un média.

### Requête Http

`DELETE https://api.openreza.com/media/<id>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`id` | string | l'identifiant du média | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.
