
# Clients

## GET Clients

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/client?order=d.asc", Method.Get);
request.AddHeader("Accept-Language", "fr-FR");
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Accept-Language", "fr-FR");
myHeaders.append("X-ULTIM-ORIGIN", "{{origin}}");
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/client?order=d.asc", requestOptions)
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
            "id": "cli_8822ee5e0a9a48b19690a0759df24ab2",
            "created": 1703929714243,
            "updated": 1703929714243,
            "first_name": "Edgar",
            "last_name": "HEANEY",
            "created_source": "API",
            "updated_source": "API",
            "email": "edgar.heaney@rezasport.testinator.com"
        },
        {
            "id": "cli_b3643680d5f34cf0b552aac185de0e13",
            "created": 1703929713150,
            "updated": 1703929713150,
            "first_name": "Nelle",
            "last_name": "SCHNEIDER",
            "created_source": "API",
            "updated_source": "API",
            "email": "nelle.schneider@rezasport.testinator.com"
        },
        {
            "id": "cli_b42b50126aa94a908cc64c3bd999297e",
            "created": 1703929711993,
            "updated": 1703929711993,
            "first_name": "Myrl",
            "last_name": "NICOLAS",
            "created_source": "API",
            "updated_source": "API",
            "email": "myrl.nicolas@rezasport.testinator.com"
        },
        {
            "id": "cli_640129c884944d96954a803b11e2915c",
            "created": 1703929710640,
            "updated": 1703929710640,
            "first_name": "Keanu",
            "last_name": "HETTINGER",
            "created_source": "API",
            "updated_source": "API",
            "email": "keanu.hettinger@rezasport.testinator.com"
        },
        {
            "id": "cli_3e6f8362754e49f8b7940dfdc1bd6feb",
            "created": 1703866155296,
            "updated": 1703866155296,
            "first_name": "Justyn",
            "last_name": "MURRAY",
            "created_source": "API",
            "updated_source": "API",
            "email": "justyn.murray@rezasport.testinator.com"
        }
    ],
    "count": 5,
    "total": 5,
    "total_page": 1
}
```

Point de terminaison pour retirer tous les clients.

### Requête Http

`GET https://api.openreza.com/client`

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`order` | created.desc | Trie les résultats par date de création. | created.desc, created.asc
`filter`|  | Retourne les résultats filtrés. | first_name, last_name, email

*Les filtres doivent contenir* **-**, *la partie droite représentant la chaîne de charactère à trouver.*

### Réponse

Code | Description 
---- | -----------
`200` | OK

## GET Client

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/client/cli_fc2671a2bfce4b97ad15ad432a385035?embed=bookings", Method.Get);
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
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/client/cli_fc2671a2bfce4b97ad15ad432a385035?embed=bookings", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "cli_fc2671a2bfce4b97ad15ad432a385035",
    "created": 1703844385450,
    "updated": 1703844385450,
    "first_name": "Korbin",
    "last_name": "O'HARA",
    "created_source": "API",
    "updated_source": "API",
    "email": "korbin.o'hara@rezasport.testinator.com",
    "bookings": [
        {
            "id": "boc_caa18b5159d34928a51c9c1931b5e08a",
            "show": false,
            "debit_formula": false,
            "paid": "NONE",
            "state": "ACCEPTED"
        }
    ]
}
```

Point de terminaison pour retirer un client.

### Requête Http

`GET https://api.openreza.com/client/<id>`

### Parametres de l'Url

Parametre | type | Description | requis
--------- | ---- | ----------- | -------
`id` | string | identifiant du client | oui

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`embed` |  | propriétés de l'objet | bookings

### Réponse

Code | Description 
---- | -----------
`200` | OK

## POST Client

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/client", Method.Post);
request.AddHeader("X-CSRF-TOKEN", "CfDJ8Oac1XiQCJRIvmQ-IvlucHaCMvfoevb2GuQe1FKgpsPe8SZl6QxOWGnVZNaCn0nwxAL7hYOTDY7Z6LH8CMKxKT46j1wzUyDYCz05XXpgjmMHxcq-A3oelIyayIbgr2PXQRQ_qAxwsvnrLa_j6w4WStY");
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
var body = @"{
  "first_name": "Stanley",
  "last_name": "Wilderman"
}
";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("X-CSRF-TOKEN", "CfDJ8Oac1XiQCJRIvmQ-IvlucHaCMvfoevb2GuQe1FKgpsPe8SZl6QxOWGnVZNaCn0nwxAL7hYOTDY7Z6LH8CMKxKT46j1wzUyDYCz05XXpgjmMHxcq-A3oelIyayIbgr2PXQRQ_qAxwsvnrLa_j6w4WStY");
myHeaders.append("X-ULTIM-ORIGIN", "API");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var raw = JSON.stringify({
  "first_name": "{{rezaFirstName}}",
  "last_name": "{{rezaLastName}}"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/client", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "cli_932c39a663904d76b2877237d173ed1f",
    "created": 1703845293433,
    "updated": 1703845293433,
    "first_name": "Stanley",
    "last_name": "WILDERMAN",
    "created_source": "API",
    "updated_source": "API"
}
```

Point de terminaison pour ajouter un évènement.

### Requête Http

`POST https://api.openreza.com/client`

### Parametres

Parametre | Type | Description | Requis | Defaut | values
--------- | ---- | ----------- | ------ | ------ | ------
`first_name` | string  | Le prénom du client | oui | |
`last_name` | string | Le nom du client | oui | |
`email` | string | L'email du client | non | |
`gender` | string | Le genre du client | non | | F (femme), M (homme), O (non déterminé)

### Réponse

Code | Description 
---- | -----------
`201` | Evènement crée.

## DELETE Client

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/client/cli_95448e2a970c407190c991faa50e1b58", Method.Delete);
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/client/cli_95448e2a970c407190c991faa50e1b58", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour supprimer un client.

### Requête Http

`DELETE https://api.openreza.com/client/<id>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`id` | string | l'identifiant du client | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.

