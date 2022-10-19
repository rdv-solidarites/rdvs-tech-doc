# Généralités

Pour la version prod, les requêtes doivent être adressées à `https://www.rdv-solidarites.fr` et non à `https://rdv-solidarites.fr` Pour la version démo, les requêtes doivent être adressées à `https://demo.rdv-solidarites.fr`

L'API supporte uniquement le format JSON. Toutes les réponses envoyées par l'API contiendront le header `Content-Type: application/json` et leur contenu sera présent dans le body dans un format JSON à désérialiser. 

L'API adhère aux principes REST : 

* requêtes `GET` : lecture sans modification
* requêtes `POST` : création de nouvelle ressource
* requêtes `PUT` : mise à jour d'une ressource existante
* requêtes `DELETE` : suppression d'une ressource

Les paramètres des requêtes `GET` doivent être envoyés via les query string de la requête. 

Les paramètres des requêtes `POST` doivent être transmis dans le corps de la requête sous un format JSON valide, et doivent contenir le header `Content-Type: application/json`

Les paramètres doivent respecter les formats suivants : 

* `DATE` : "YYYY-MM-DD" par exemple : "2021-10-21"
* `TIME` : H:m\[:s\], par exemple : "10:30"

### Codes de retour

Les statuts HTTP des réponses renvoyées par l'API peuvent être les suivants :

* `200` : succès
* `204` : succès, si la réponse ne retourne pas de données \(par exemple pour une suppression\)
* `400` : requête mal formatée. Par exemple si le JSON du body est invalide.
* `401` : requête non authentifiée
* `403` : requête bien authentifiée mais droits insuffisants pour réaliser l'action demandée. Par exemple si un agent non-admin essaie de créer une absence pour un agent d'un autre service.
* `422` : paramètres sains \(JSON valide\) mais incorrects. Par exemple si vous essayez de créer une absence avec une date de fin antérieure à sa date de début.
* `500` : erreur interne. Nous sommes automatiquement prévus de ces erreurs et devrions nous en occuper rapidement. Vous pouvez nous contacter si cela se reproduit.

### Erreurs

En cas d'erreur reconnue par le système \(par exemple erreur 422\), les champs suivants seront présents dans la réponse pour vous informer sur les problèmes :

* `errors` : \[ERREUR\] : liste d'erreurs groupées par attribut problèmatique au format machine
* `error_messages` : \[ERREUR\] : idem mais dans un format plus facilement lisible.

### Pagination

Les requêtes d’index retournent une liste de résultats paginés, par défaut par 100 items.

#### Paramètres

* `per`: le nombre d’items par page
* `page` : l’index de la page demandée

#### Résultats

La réponse contient en outre un objet `meta` qui indique le nombre total de pages et d’items, par exemple:

```text
{
    […]
    "meta": {
        "current_page": 1,
        "total_count": 112,
        "total_pages": 2
    }°
}
```

