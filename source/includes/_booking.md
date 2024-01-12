
# Booking

## GET Bookings

```csharp
var options = new RestClientOptions("https://api.openreza.com")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/booking?order=created.desc", Method.Get);
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```shell
curl --location 'https://api.openreza.com/booking?order=created.desc' \
--header 'X-ULTIM-ORIGIN: null' \
--header 'x-api-key: <YOUR_API_KEY>' \
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "page_size": 10,
    "page_number": 1,
    "data": [
        {
            "id": "boo_19a9ca0b67694d1f85f9ee5cc60ce4fe",
            "public_booking_id": "581b82dcce91454785c047aab39d5be6",
            "event": {
                "id": "eve_e9f3fb56ddfa40e4ae7ca7998a7907bb",
                "created": 1703670020290,
                "updated": 1703670449433,
                "title": "supply-chains",
                "start_utc": "2024-01-24T12:00:00Z",
                "end_utc": "2024-01-24T13:15:00Z",
                "duration": 75,
                "capacity": 15,
                "available": 14,
                "fill_rate": 6,
                "state_changed": 1703670020290,
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
            "created": 1703670409126,
            "updated": 1703670409120,
            "source": "API",
            "password": "D30DB"
        },
        // more items
    ],
    "count": 10,
    "total": 13,
    "total_page": 1
}
```

Enpoint pour retirer toutes les réservations. Par défaut retourne les réservations dans le futur par rapport à la date courante UTC.

### HTTP Request

`GET https://api.openreza.com/booking`

### Parametres de Requête

Parametre | Default | Description | Valeurs
--------- | ------- | ----------- | -------
`order` | created.desc | Trie les résultats par date de création. | created.desc, created.asc
`filter`| futur | Retourne les résultats suivant que les évènements auxquels ils sont rattachés sont dans le futur ou pas. | futur, past, all, title (exemple title-arch)

*Le filtre* **title** *doit contenir* **-**, *la partie droite représentant la chaîne de charactère à trouver.*

### Réponse

Code | Description 
---- | -----------
`200` | Ok

## GET Booking 

```csharp
var options = new RestClientOptions("https://api.openreza.com")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/booking/<Id>?embed=clients;event", Method.Get);
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "<YOUR_API_KEY>");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.openreza.com/booking/<Id>?embed=clients;event", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "Id": "boo_c85168381818438b92c80cf950a7e56c",
    "public_booking_Id": "922e27f5b43745448f186da3bec40859",
    "event": {
        "Id": "eve_c328acec159144439830b9e94a9bb5d3",
        "created": 1703432325220,
        "updated": 1703433479736,
        "title": "paradigms",
        "start_utc": "2023-12-27T07:00:00Z",
        "end_utc": "2023-12-27T10:00:00Z",
        "duration": 180,
        "capacity": 2,
        "available": -1,
        "fill_rate": 150,
        "state_changed": 1703432325220,
        "max_booking_per_person": 1,
        "use_owner_infos_for_additional_bookings": true,
        "lock_expiry": 0,
        "form_required_fields": [
            "email"
        ],
        "accept_client_message": false,
        "cancellation_dead_line": 60,
        "cancellation_count": 2
    },
    "created": 1703433479720,
    "updated": 1703433479716,
    "source": "API",
    "clients": [
        {
            "Id": "boc_e339bf23fe074797b1ee7fdef9611b8d",
            "show": false,
            "debit_formula": false,
            "paId": "NONE",
            "client": {
                "Id": "cli_19ec213360804bdf8ed4ffa8646a1ba3",
                "created": 1703431771633,
                "updated": 1703431771633,
                "first_name": "Beth",
                "last_name": "LIND",
                "created_source": "DASHBOARD",
                "updated_source": "DASHBOARD",
                "email": "beth.lind@rezasport.testinator.com"
            },
            "state": "ACCEPTED"
        }
    ],
    "password": "6E86A",
    "owner": {
        "Id": "cli_19ec213360804bdf8ed4ffa8646a1ba3",
        "first_name": "Beth",
        "last_name": "LIND",
        "email": "BETH.LIND@REZASPORT.TESTINATOR.COM"
    }
}
```

Ce point de terminaison retourne un Booking spécifique.


### HTTP Request

`GET https://api.openreza.com/booking/<Id>`

### Paramètres d'URL

Parameter | Obligatoire | Description
--------- | ----------- | -----------
Id | oui | L'Id du booking

### Parametres de Requète

Parameter | Obligatoire | Description | Valeur
--------- | ----------- | ----------- | ------
`embed` | non | propriétés de l'objet | clients, event

### Réponse

Code | Description 
---- | -----------
`200` | Ok

## POST Booking.

```csharp
var options = new RestClientOptions("https://api.openreza.com")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/booking", Method.Post);
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
var body = "{
    "event": "eve_0a6627ac09e74d54bf28a116e01fed0f",
    "owner_in_reservation": true,
    "owner": {
        "first_name": "Lillian",
        "last_name": "Nicolas",
        "email": "Lillian.Nicolas@rezasport.testinator.com"
    },
    "clients": [
        {
            "first_name": "Norbert",
            "last_name": "Rodriguez",
            "email": "Norbert.Rodriguez@rezasport.testinator.com"
        }
    ]
}";
request.AddStringBody(body, DataFormat.Json);
RestResponse response = await client.ExecuteAsync(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "<YOUR_API_KEY>");

var raw = JSON.stringify({
    "event": "eve_0a6627ac09e74d54bf28a116e01fed0f",
    "owner_in_reservation": true,
    "owner": {
        "first_name": "Lillian",
        "last_name": "Nicolas",
        "email": "Lillian.Nicolas@rezasport.testinator.com"
    },
    "clients": [
        {
            "first_name": "Norbert",
            "last_name": "Rodriguez",
            "email": "Norbert.Rodriguez@rezasport.testinator.com"
        }
    ]
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.openreza.com/booking", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> La commande ci-dessus retourne un fichier JSON structuré comme suit :

```json
{
    "Id": "boo_e56e0d2a56ce4a1d8bca4bc47423db17",
    "public_booking_Id": "31d142de62a145dfa63a2ad0304701d4",
    "created": 1703617945776,
    "updated": 1703617945773,
    "source": "API",
    "password": "27E8E",
    "owner": {
        "Id": "cli_b87d1cf022f24dd1a6cac7a3e7803841",
        "first_name": "Lillian",
        "last_name": "NICOLAS",
        "email": "LILLIAN.NICOLAS@REZASPORT.TESTINATOR.COM"
    }
}
```

Ce point de terminaison ajoute un Booking. 
L'owner est le propriétaire de la réservation, c'est celui qui effectue la réservation. Ce champs est obligatoire.

### HTTP Request

`POST https://api.openreza.com/booking`

### Parametres

Parameter | Type | Description | Requis
--------- | ---- | ----------- | ------
`event` | string | L'identifiant de l'évènement concerné par la réservation | oui
`owner_in_reservation` | boolean | Determine si le propriétaire de la réservation fait parti des réservants. | oui
`owner` | `client` | La personne qui effectue la réservation | oui.
`clients` | [`client`] | Liste des personnes de la réservation. | oui si `owner_in_reservation` est false autrement non.

### Parametres Client
Parameter | type | Description | Requis
--------- | ---- | ----------- | ------
`email` | string | L'email de la personne | oui
`first_name` | string | Un prénom | non
`last_name` | string | Un nom | non.

### Réponse

Code | Description 
---- | -----------
`201` | Ajout effectué.

## DELETE Booking

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/booking/boo_f27b790e38f34f16a4846832a14ed07d", Method.Delete);
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

fetch("https://localhost:7117/booking/boo_f27b790e38f34f16a4846832a14ed07d", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Ce point de terminaison supprime un Booking. 

### HTTP Request

`DELETE https://api.openreza.com/booking/<Id>`

<aside class="warning">
    Supprimer une réservation n'entraîne pas la réservation automatique d'un client en liste d'attente. Pour faire monter automatiquement un client de liste d'attente aux réservations il faut annuler une réservation et non la supprimer.
</aside>

### Parametres d'Url

Parameter | type | Description | Requis
--------- | ---- | ----------- | ------
`id` | string | L'identifiant de booking | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée

## DELETE Booking Client

```csharp
var options = new RestClientOptions("https://localhost:7117")
{
  MaxTimeout = -1,
};
var client = new RestClient(options);
var request = new RestRequest("/booking/client/boc_b81cd2cecd564a82a175a8e06f676f2a", Method.Delete);
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

fetch("https://localhost:7117/booking/client/boc_b81cd2cecd564a82a175a8e06f676f2a", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Ce point de terminaison supprime le Booking d'un client spécifiquement. 

### HTTP Request

`DELETE https://api.openreza.com/booking/client/<Id>`

<aside class="warning">
    Supprimer la réservation d'un client spécifiquement n'entraîne pas la réservation automatique d'un client en liste d'attente. Pour faire monter automatiquement un client de liste d'attente aux réservations il faut annuler une réservations et non la supprimer.
</aside>

### Parametres d'Url

Parameter | type | Description | Requis
--------- | ---- | ----------- | ------
`id` | string | L'identifiant de booking client | oui

### Réponse

Code | Description 
---- | -----------
`204` | Supression effectuée
