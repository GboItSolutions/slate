
# Log Evènements

## GET Log Evènements

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/eventlog/eve_e9088d199f274054b61058c0dc027021", Method.Get);
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

fetch("https://localhost:7117/eventlog/eve_e9088d199f274054b61058c0dc027021", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
[
    {
        "id": "evl_2858ea26e18c4577b19eced942f792da",
        "event": "eve_e9088d199f274054b61058c0dc027021",
        "description": "pla_7f8d81e81dd04c628f99153f5893d05d",
        "type": "ADD_PLACE",
        "created": "2023-12-27T18:36:38Z"
    },
    {
        "id": "evl_a57cb345e7c04520812055c04417f694",
        "event": "eve_e9088d199f274054b61058c0dc027021",
        "description": "e-markets",
        "type": "CREATION",
        "created": "2023-12-27T18:27:12Z"
    }
]
```

Point de terminaison pour retirer tous les logs d'un évènement.

### Requête Http

`GET https://api.openreza.com/eventlog/<id>`

### Parametres de l'URL

Parametre | Type | Description 
--------- | ---- | ----------- 
`id` | string | L'identifiant de l'évènement.

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`order` | created.desc | Trie les résultats par date de création. | created.desc, created.asc

### Réponse

Code | Description 
---- | -----------
`200` | OK
