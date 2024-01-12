
# Produits

## GET Produits

```csharp
var options = new RestProduitOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var Produit = new RestProduit(options);
var request = new RestRequest("/Produit?order=d.asc", Method.Get);
request.AddHeader("Accept-Language", "fr-FR");
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
RestResponse response = await Produit.ExecuteAsync(request);
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

fetch("https://localhost:7117/Produit?order=d.asc", requestOptions)
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
            "id": "pro_9f68f3aed97d45eca7030814ea5b7b73",
            "created": 1703930331686,
            "updated": 1703930331686,
            "designation": "Handcrafted Wooden Ball",
            "duration": 5,
            "price": 306,
            "capacity_min": 1,
            "capacity_max": 1
        },
        // more items
    ],
    "count": 10,
    "total": 15,
    "total_page": 2
}
```

Point de terminaison pour retirer tous les Produits.

### Requête Http

`GET https://api.openreza.com/Produit`

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`order` | created.desc | Trie les résultats par date de création. | created.desc, created.asc
`filter`|  | Retourne les résultats filtrés. | designation, duration, price, capacity_max, capacity_min

*Les filtres doivent contenir* **-**, *la partie droite représentant la chaîne de charactère à trouver.*
<br />
*Pour les filtres* **duration, price,capacity_max, capacity_min** *il est possible d'appliquer un opérateur suivant le format:*
<br />
[filter]-[operator].[value]
*exemple:* duration->=.60
<br />
Les opérateurs possibles sont :

* >=
* >
* <=
* <
* =

### Réponse

Code | Description 
---- | -----------
`200` | OK

## GET Produit

```csharp
var options = new RestProduitOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var Produit = new RestProduit(options);
var request = new RestRequest("/Produit/cli_fc2671a2bfce4b97ad15ad432a385035?embed=bookings", Method.Get);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
RestResponse response = await Produit.ExecuteAsync(request);
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

fetch("https://localhost:7117/Produit/cli_fc2671a2bfce4b97ad15ad432a385035?embed=bookings", requestOptions)
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

Point de terminaison pour retirer un Produit.

### Requête Http

`GET https://api.openreza.com/Produit/<id>`

### Parametres de l'Url

Parametre | type | Description | requis
--------- | ---- | ----------- | -------
`id` | string | identifiant du Produit | oui

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`embed` |  | propriétés de l'objet | images

### Réponse

Code | Description 
---- | -----------
`200` | OK

## POST Produit

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/product", Method.Post);
request.AddHeader("X-ULTIM-ORIGIN", "API");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
var body = @"{
    "Designation": "Tasty Rubber Pizza",
    "Duration": 120,
    "Price":"531"
}";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("X-ULTIM-ORIGIN", "API");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var raw = JSON.stringify({
  "Designation": "Licensed Wooden Bacon",
  "Duration": 120,
  "Price": "572"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/product", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "pro_14aef566a5a74fdc8245b794973f23e7",
    "created": 1703858007452,
    "updated": 1703858007452,
    "designation": "Tasty Rubber Pizza",
    "duration": 120,
    "price": 531,
    "capacity_min": 1,
    "capacity_max": 1
}
```

Point de terminaison pour ajouter un produit.

### Requête Http

`POST https://api.openreza.com/product`

### Parametres

Parametre | Type | Description | Requis | Defaut | values
--------- | ---- | ----------- | ------ | ------ | ------
`designation` | string  | Le nom du Produit | oui | |
`duration` | integer | La durée du Produit en minutes | oui | | La valeur doit être >= 5 et représenter une durée multiple de 5.
`price` | integer | Le prix du produit exprimé sans virgule | oui | | La valeur doit être >= 0. **attention** pour un prix de 55 euros il faut que `price` soit 5500
`capacity_min` | integer | La capacité minimale du produit | non | 1 | 
`capacity_max` | integer | La capacité maximale du produit | non | 1 | 

### Réponse

Code | Description 
---- | -----------
`201` | Produit crée.

## PUT Ajout Image à un Produit

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/product/image", Method.Put);
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");
var body = @"{
  "media": "med_145e551103bb4ea49b5d55993085d44c",
  "product": "pro_f824c3c34f6c49dcb9dc1f592201ae57"
}";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "KS-cNVTD-XNY-nq6bmsVyhq_6l5IzW4MIsib_r3iZp8fAWNZqGDFTnIh3TcSa0wp");

var raw = JSON.stringify({
  "media": "med_145e551103bb4ea49b5d55993085d44c",
  "product": "pro_f824c3c34f6c49dcb9dc1f592201ae57"
});

var requestOptions = {
  method: 'PUT',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/product/image", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "product": "pro_f824c3c34f6c49dcb9dc1f592201ae57",
    "media": "med_145e551103bb4ea49b5d55993085d44c"
}
```

Point de terminaison pour ajouter une image à une produit.

### Requête Http

`POST https://api.openreza.com/product/image`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`product` | string  | L'identifiant du produi | oui 
`media` | string | L'identifiant du média | oui

### Réponse

Code | Description 
---- | -----------
`201` | Image Produit crée.

## DELETE Supprimer Image d'un Produit

```csharp

```

```javascript

```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json

```

Point de terminaison pour ajouter une image à une produit.

### Requête Http

`DELETE https://api.openreza.com/product/<product>/image/<media>`

### Parametres de l'Url

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`product` | string  | L'identifiant du produit | oui 
`media` | string | L'identifiant du média | oui

### Réponse

Code | Description 
---- | -----------
`204` | Image Produit supprimée.

## DELETE Produit

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

Point de terminaison pour supprimer un Produit.

### Requête Http

`DELETE https://api.openreza.com/Product/<id>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`id` | string | l'identifiant du Produit | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.

