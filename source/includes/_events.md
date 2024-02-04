
# Evènements

## GET Evènements

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event?order=created.asc&filter=past", Method.Get);
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

fetch("https://localhost:7117/event?order=created.asc&filter=past", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "page_size": 10,
    "page_number": 64,
    "data": [
        {
            "id": "eve_017a53af50274115a5121ac00b4063fd",
            "created": 1703677492610,
            "updated": 1703677492650,
            "title": "experiences",
            "start_utc": "2024-01-04T13:00:00Z",
            "end_utc": "2024-01-04T13:30:00Z",
            "duration": 30,
            "capacity": 15,
            "available": 15,
            "fill_rate": 0,
            "state_changed": 1703677492610,
            "max_booking_per_person": 3,
            "use_owner_infos_for_additional_bookings": true,
            "lock_expiry": 0,
            "form_required_fields": [
                "email"
            ],
            "accept_client_message": false,
            "cancellation_dead_line": 60,
            "cancellation_count": 0
        },
        // more items
    ],
    "count": 10,
    "total": 644,
    "total_page": 64
}
```

Point de terminaison pour retirer tous les évènements.

### Requête Http

`GET https://api.openreza.com/event`

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`order` | created.desc | Trie les résultats par date de création. | created.desc, created.asc
`filter`| futur | Retourne les résultats dans le futur par rapport à la date courante UTC. | futur, past, all, title (exemple title-arch)

*Le filtre* **title** *doit contenir* **-**, *la partie droite représentant la chaîne de charactère à trouver.*

### Réponse

Code | Description 
---- | -----------
`200` | OK

## GET Evènement

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/eve_308065c0693549e6aa3684c8fd1873f9?embed=bookings", Method.Get);
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

fetch("https://localhost:7117/event/eve_308065c0693549e6aa3684c8fd1873f9?embed=bookings", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "eve_308065c0693549e6aa3684c8fd1873f9",
    "created": 1703677403550,
    "updated": 1703677403570,
    "title": "paradigms",
    "start_utc": "2024-01-06T17:00:00Z",
    "end_utc": "2024-01-06T18:30:00Z",
    "duration": 90,
    "capacity": 15,
    "available": 15,
    "fill_rate": 0,
    "state_changed": 1703677403550,
    "max_booking_per_person": 3,
    "use_owner_infos_for_additional_bookings": true,
    "lock_expiry": 0,
    "form_required_fields": [
        "email"
    ],
    "accept_client_message": false,
    "cancellation_dead_line": 60,
    "cancellation_count": 0
}
```

Point de terminaison pour retirer un évènement.

### Requête Http

`GET https://api.openreza.com/<id>`

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`embed` |  | propriétés de l'objet | products, products_images, survey, logs, bookings, place, files, waiting_list

### Réponse

Code | Description 
---- | -----------
`200` | OK

## POST Evènement

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event", Method.Post);
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
var body = "{
    "title": "metrics",
    "start_utc": "2024-01-21T14:00:00.000Z",
    "duration": 75,
    "capacity": 15,
    "max_booking_per_person": 3,
    "accept_client_message": false,
    "use_owner_infos_for_additional_bookings": true
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

var raw = "{
    "title": "metrics",
    "start_utc": "2024-01-21T14:00:00.000Z",
    "duration": 75,
    "capacity": 15,
    "max_booking_per_person": 3,
    "accept_client_message": false,
    "use_owner_infos_for_additional_bookings": true
}";

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/event", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "eve_2d8b00a423cf4d97b4aa05699580c89d",
    "created": 1703691369030,
    "updated": 1703691369286,
    "title": "metrics",
    "start_utc": "2024-01-21T14:00:00Z",
    "end_utc": "2024-01-21T15:15:00Z",
    "duration": 75,
    "capacity": 15,
    "available": 15,
    "fill_rate": 0,
    "state_changed": 1703691369030,
    "max_booking_per_person": 3,
    "use_owner_infos_for_additional_bookings": true,
    "lock_expiry": 0,
    "form_required_fields": [
        "email"
    ],
    "accept_client_message": false,
    "cancellation_dead_line": 60,
    "cancellation_count": 0
}
```

Point de terminaison pour ajouter un évènement.

### Requête Http

`POST https://api.openreza.com/`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`title` | string  | Le titre de l'évènement | oui |
`start_utc` | datetime | L'heure de début | oui | 
`duration` | integer | La durée en minutes | oui |
`capacity` | integer | Le nombre de place / réservation que l'évènement peut contenir. | oui | 1
`max_booking_per_person` | integer | Le nombre de personne qu'une personne peut inscrire à l'évènement. Minimum 1. | non | La valeur définie dans vos préférences de réservation, par défault 1.
`accept_client_message` | boolean | Est-ce que les personnes qui réservent peuvent completer leur réservation avec un message personnalisé ? | non | La valeur définie dans vos préférences de réservation, par défault oui
`use_owner_infos_for_additional_bookings` | boolean | Utiliser les informations fournis par le créateur de la réservation pour les réservations supplémentaires ? | non | La valeur définie dans vos préférences de réservation, par défault non
`products` | string[] | Les identifiants des produits que vous souhaitez ajoutés à l'évènement. | non
`form` | string | L'identifiant du formulaire. Le formulaire doit être valide, c'est à dire qu'il comporte au moins 1 question | non
`place` | string | L'identifiant du lieu | non
`files` | string[] | Les identifiants des médias. | non
`waiting_list` | integer | La capacité de la liste d'attente à ajouter. | non

### Réponse

Code | Description 
---- | -----------
`201` | Evènement crée.

## PUT Evènement Ajout Produit

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/product", Method.Put);
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
var body = @"{
    "product": "pro_f023b7a1466f425a9bbdedea1e673f05",
    "event" : "eve_e9088d199f274054b61058c0dc027021"
}";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```


```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");

var raw = JSON.stringify({
  "product": "pro_f023b7a1466f425a9bbdedea1e673f05",
  "event": "eve_e9088d199f274054b61058c0dc027021"
});

var requestOptions = {
  method: 'PUT',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/event/product", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "event": "eve_e9088d199f274054b61058c0dc027021",
    "product": "pro_f023b7a1466f425a9bbdedea1e673f05"
}
```

Point de terminaison pour ajouter un produit à un évènement.

### Requête Http

`PUT https://api.openreza.com/event/product`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`event` | string  | L'identifiant de l'évènement | oui |
`product` | string | L'identifiant du produit  | oui | 

### Réponse

Code | Description 
---- | -----------
`201` | Produit ajouté à l'évènement.


## PUT Evènement Ajout Formulaire

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/survey", Method.Put);
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
var body = @"{
    "event": "eve_e9088d199f274054b61058c0dc027021",
    "survey": "sur_cee07f596a2b49c6b312be403dd1aa07"
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
  "event": "eve_e9088d199f274054b61058c0dc027021",
  "survey": "sur_cee07f596a2b49c6b312be403dd1aa07"
});

var requestOptions = {
  method: 'PUT',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/event/survey", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "event": "eve_e9088d199f274054b61058c0dc027021",
    "survey": "sur_cee07f596a2b49c6b312be403dd1aa07"
}
```

Point de terminaison pour ajouter un Formulaire à un évènement.

### Requête Http

`PUT https://api.openreza.com/event/survey`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`event` | string  | L'identifiant de l'évènement | oui |
`survey` | string | L'identifiant du formulaire  | oui | 

### Réponse

Code | Description 
---- | -----------
`201` | Formulaire ajouté à l'évènement.


## PUT Evènement Ajout Place

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/place", Method.Put);
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
var body = @"{
    "event": "eve_e9088d199f274054b61058c0dc027021",
    "place": "pla_7f8d81e81dd04c628f99153f5893d05d"
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
  "event": "eve_e9088d199f274054b61058c0dc027021",
  "place": "pla_7f8d81e81dd04c628f99153f5893d05d"
});

var requestOptions = {
  method: 'PUT',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/event/place", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "event": "eve_e9088d199f274054b61058c0dc027021",
    "place": "pla_7f8d81e81dd04c628f99153f5893d05d"
}
```

Point de terminaison pour ajouter un Formulaire à un évènement.

### Requête Http

`PUT https://api.openreza.com/event/place`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`event` | string  | L'identifiant de l'évènement | oui |
`place` | string | L'identifiant du lieu  | oui | 

### Réponse

Code | Description 
---- | -----------
`201` | Lieu ajouté à l'évènement.

## PUT Evènement Ajout File

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/file", Method.Put);
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
var body = @"{
    "event":"eve_8691f2a993a7415b801648f13e168e40",
    "file": "med_f51ad1db2c164e1880bdaa4ff3d488ad"
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
  "event": "eve_8691f2a993a7415b801648f13e168e40",
  "file": "med_f51ad1db2c164e1880bdaa4ff3d488ad"
});

var requestOptions = {
  method: 'PUT',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/event/file", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "event":"eve_8691f2a993a7415b801648f13e168e40",
    "file": "med_f51ad1db2c164e1880bdaa4ff3d488ad"
}
```

Point de terminaison pour ajouter un fichier à un évènement.

### Requête Http

`PUT https://api.openreza.com/event/file`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`event` | string  | L'identifiant de l'évènement | oui |
`file` | string | L'identifiant du fichier  | oui | 

### Réponse

Code | Description 
---- | -----------
`201` | Lieu ajouté à l'évènement.

## PUT Evènement Ajout Waiting List

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/waitinglist", Method.Put);
request.AddHeader("X-ULTIM-ORIGIN", "{{origin}}");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("x-api-key", "KS-T6EBI45KSQeceuEoOOCRlZd4B-Dvu5YmA3B0t6MOotMO3PWhb4Gkr5RVPbgmP");
var body = @"{
    "event" : "eve_e9088d199f274054b61058c0dc027021",
    "capacity": 2
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
  "event": "eve_e9088d199f274054b61058c0dc027021",
  "capacity": 2
});

var requestOptions = {
  method: 'PUT',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/event/waitinglist", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "wli_1016b79a7d2d426abec24554cf682e00",
    "event": "eve_e9088d199f274054b61058c0dc027021",
    "created": 1703698869833,
    "updated": 1703698869836,
    "capacity": 2,
    "fill_rate": 0
}
```

Point de terminaison pour ajouter un fichier à un évènement.

### Requête Http

`PUT https://api.openreza.com/event/waitinglist`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`event` | string  | L'identifiant de l'évènement | oui |
`capacity` | integer | Capacité de la liste d'attente  | oui | 

### Réponse

Code | Description 
---- | -----------
`201` | Liste d'attente ajoutée à l'évènement.

## DELETE Evènement

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/eve_236d67adbd17489f9f2aa034d7f8df5e", Method.Delete);
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

fetch("https://localhost:7117/event/eve_236d67adbd17489f9f2aa034d7f8df5e", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour supprimer un évènement.

### Requête Http

`DELETE https://api.openreza.com/<id>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`id` | string | l'identifiant de l'évènement | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.


## GET Log Evènements

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/logs/eve_e9088d199f274054b61058c0dc027021", Method.Get);
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

fetch("https://localhost:7117/event/logs/eve_e9088d199f274054b61058c0dc027021", requestOptions)
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

`GET https://api.openreza.com/event/logs/<id>`

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

## GET Modèles d'evènements

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/template", Method.Get);
request.AddHeader("X-API-KEY", "OPR-TbqZzAJnut3WRj6wRhO1OCnOp2K4ADChXvvaVF2XAraFbKXO1NujVX9TjxgQ");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-API-KEY", "OPR-TbqZzAJnut3WRj6wRhO1OCnOp2K4ADChXvvaVF2XAraFbKXO1NujVX9TjxgQ");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/event/template", requestOptions)
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
            "id": "evt_b4e914e2de3f4d6c9a912b16fc26c6c2",
            "created": 1705488947896,
            "updated": 1705488947900,
            "title": "mindshare",
            "capacity": 1
        },
      // plus de résultats
    ],
    "count": 6,
    "total": 6,
    "total_page": 1
}
```

Point de terminaison pour retirer tous les modèle d'évènements.

### Requête Http

`GET https://api.openreza.com/event/template`

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`order` | created.desc | Trie les résultats par date de création. | created.desc, created.asc
`filter`| futur | Retourne les résultats suivant le filtre appliqué | title

*Le filtre* **title** *doit contenir* **-**, *la partie droite représentant la chaîne de charactère à trouver.*

### Réponse

Code | Description 
---- | -----------
`200` | OK

## GET Modèle d'evènement

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/template/evt_89870b9a2e5546459a0b432b7ed952b6?embed=form;room;place", Method.Get);
request.AddHeader("X-API-KEY", "OPR-TbqZzAJnut3WRj6wRhO1OCnOp2K4ADChXvvaVF2XAraFbKXO1NujVX9TjxgQ");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("X-API-KEY", "OPR-TbqZzAJnut3WRj6wRhO1OCnOp2K4ADChXvvaVF2XAraFbKXO1NujVX9TjxgQ");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://localhost:7117/event/template/evt_89870b9a2e5546459a0b432b7ed952b6?embed=form;room;place", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "evt_89870b9a2e5546459a0b432b7ed952b6",
    "created": 1705501293806,
    "updated": 1705501293810,
    "title": "ROI",
    "capacity": 15
}
```

Point de terminaison pour retirer un modèle d'évènement.

### Requête Http

`GET https://api.openreza.com/event/template<id>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`id` | string | l'identifiant du modèle d'évènement | oui

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`embed` |  | propriétés de l'objet | form, room, place

### Réponse

Code | Description 
---- | -----------
`200` | OK

## POST Modèle Evènement

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/template", Method.Post);
request.AddHeader("Content-Type", "application/json");
request.AddHeader("X-API-KEY", "OPR-TbqZzAJnut3WRj6wRhO1OCnOp2K4ADChXvvaVF2XAraFbKXO1NujVX9TjxgQ");
var body = @"{
" + "\n" +
@"    ""event"" : ""eve_065eb5d11205416fb607d431f48dad3d""
" + "\n" +
@"}";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("X-API-KEY", "OPR-TbqZzAJnut3WRj6wRhO1OCnOp2K4ADChXvvaVF2XAraFbKXO1NujVX9TjxgQ");

var raw = JSON.stringify({
  "event": "eve_065eb5d11205416fb607d431f48dad3d"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://localhost:7117/event/template", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "id": "evt_89870b9a2e5546459a0b432b7ed952b6",
    "created": 1705501293806,
    "updated": 1705501293810,
    "title": "ROI",
    "capacity": 15
}
```

Point de terminaison pour ajouter un modèle d'évènement.

### Requête Http

`POST https://api.openreza.com/event/template`

### Parametres

Parametre | Type | Description | Requis | Defaut
--------- | ---- | ----------- | ------ | ------
`event` | string  | L'identifiant de l'évènement | oui |
`title` | string  | Le titre du modèle. Si nul le modèle prendra le nom de l'évènement | non |

### Réponse

Code | Description 
---- | -----------
`201` | Modèle d'évènement crée.

## DELETE Modèle Evènement

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/event/template/evt_89870b9a2e5546459a0b432b7ed952b6", Method.Delete);
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

fetch("https://localhost:7117/event/template/evt_89870b9a2e5546459a0b432b7ed952b6", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Point de terminaison pour supprimer un modèle d'évènement.

### Requête Http

`DELETE https://api.openreza.com/event/template/<id>`

### Parametres d'Url

Parametre | Type | Description | Requis 
--------- | ---- | ----------- | ------
`id` | string | l'identifiant de l'évènement | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée.
