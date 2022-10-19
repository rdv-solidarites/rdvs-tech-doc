# Usagers

'Consultation, création et invitation d’usagers via l’API de RDV-Solidarités'

### Usagers et Profils

Un Usager désigne le compte unique d'un usager sur la plateforme RDV-Solidarités. Il contient les informations de l'état civil de l'usager \(nom, prénoms, date de naissance...\) ainsi que des informations communes comme les préférences de notifications

Un Profil Usager lie un Usager à une Organisation. La plupart des usagers n'ont un lien qu'avec une seule Organisation, mais une partie interagit avec plusieurs Organisations. Au sein d'une Organisation, seuls les comptes usagers y ayant un profil sont visibles. Ce profil contient aussi quelques informations sur l'usager, indépendantes et non-partagées entre organisations.

### Index

**`GET /api/v1/users`**

#### Paramètres de l'URL

* `:ids` ARRAY\[INT\] - _optionnel_ : Liste des identifiants des usagers que l'on souhaite récupérer

#### Réponse en cas de succès

* ARRAY\[USER\]

#### Exemple de requête

```http
http GET https://www.rdv-solidarites.fr/api/v1/users \
  access-token:FLXP6G2hIEYhmGe5MpHKfg \
  client:fySY0UMlNzgbhE8QYhXdkw \
  uid:martine@demo.rdv-solidarites.fr
```

```bash
curl --verbose \
  --header 'access-token: b-zBRj7TFto9dIJlXg5eyw' \
  --header 'client: jcfNV37BmHusa6S0FFC9FQ' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  'https://www.rdv-solidarites.fr/api/v1/users'
```

#### Exemple de réponse

```javascript
{
    "users": [
        {
            "address": null,
            "affiliation_number": null,
            "birth_date": "1975-06-20",
            "birth_name": null,
            "created_at": "2021-06-28T10:12:41.993+02:00",
            "caisse_affiliation": null,
            "email": "patricia_duroy@demo.rdv-solidarites.fr",
            "family_situation": null,
            "first_name": "Patricia",
            "id": 1,
            "last_name": "DUROY",
            "notify_by_email": true,
            "notify_by_sms": true,
            "number_of_children": null,
            "phone_number": "0101010103",
            "phone_number_formatted": "+33101010103",
            "responsible": null,
            "responsible_id": null,
            "user_profiles": [
                {
                    "logement": "en_accession_propriete",
                    "notes": null,
                    "organisation": {
                        "departement": "75",
                        "id": 1,
                        "name": "MDS Paris Nord"
                    }
                }
            ]
        }
    ]
}
```

**`GET /api/v1/:organisation_id/users`**

#### Paramètres de l'URL

* `:organisation_id` INT - _requis_ : Liste de l'organisation pour laquelle on souhaite récupérer les
* `:ids` ARRAY\[INT\] - _optionnel_ : Liste des identifiants des usagers que l'on souhaite récupérer

#### Réponse en cas de succès

* ARRAY\[USER\]

#### Exemple de requête

```http
http GET https://www.rdv-solidarites.fr/api/v1/3/users \
  access-token:FLXP6G2hIEYhmGe5MpHKfg \
  client:fySY0UMlNzgbhE8QYhXdkw \
  uid:martine@demo.rdv-solidarites.fr
```

```bash
curl --verbose \
  --header 'access-token: b-zBRj7TFto9dIJlXg5eyw' \
  --header 'client: jcfNV37BmHusa6S0FFC9FQ' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  'https://www.rdv-solidarites.fr/api/v1/3/users'
```

#### Exemple de réponse

```javascript
{
    "users": [
        {
            "address": null,
            "affiliation_number": null,
            "birth_date": "1975-06-20",
            "birth_name": null,
            "created_at": "2021-06-28T10:12:41.993+02:00",
            "caisse_affiliation": null,
            "email": "patricia_duroy@demo.rdv-solidarites.fr",
            "family_situation": null,
            "first_name": "Patricia",
            "id": 1,
            "last_name": "DUROY",
            "notify_by_email": true,
            "notify_by_sms": true,
            "number_of_children": null,
            "phone_number": "0101010103",
            "phone_number_formatted": "+33101010103",
            "responsible": null,
            "responsible_id": null,
            "user_profiles": [
                {
                    "logement": "en_accession_propriete",
                    "notes": null,
                    "organisation": {
                        "departement": "75",
                        "id": 1,
                        "name": "MDS Paris Nord"
                    }
                }
            ]
        }
    ]
}
```

### Consultation

**`GET /api/v1/users/:id`**

#### Paramètres de l'URL

* `:id` INT : identifiant unique de l'usager

#### Réponse

* `user` : USER
  * `user_profiles` Profils de l'usager dans les organisations accessibles à l'agent faisant la requête

#### Exemple de requête

```bash
http GET https://www.rdv-solidarites.fr/api/v1/users/102 \
  access-token:FLXP6G2hIEYhmGe5MpHKfg \
  client:fySY0UMlNzgbhE8QYhXdkw \
  uid:martine@demo.rdv-solidarites.fr

```

```bash
curl --verbose \
  --header 'access-token: b-zBRj7TFto9dIJlXg5eyw' \
  --header 'client: jcfNV37BmHusa6S0FFC9FQ' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  'https://www.rdv-solidarites.fr/api/v1/users/1'
```

#### Exemple de réponse

```javascript
{
    "user": {
        "address": null,
        "affiliation_number": null,
        "birth_date": "1975-06-20",
        "birth_name": null,
        "created_at": "2021-06-28T10:12:41.993+02:00",
        "caisse_affiliation": null,
        "email": "patricia_duroy@demo.rdv-solidarites.fr",
        "family_situation": null,
        "first_name": "Patricia",
        "id": 1,
        "last_name": "DUROY",
        "notify_by_email": true,
        "notify_by_sms": true,
        "number_of_children": null,
        "phone_number": "0101010103",
        "phone_number_formatted": "+33101010103",
        "responsible": null,
        "responsible_id": null,
        "user_profiles": [
            {
                "logement": "en_accession_propriete",
                "notes": null,
                "organisation": {
                    "departement": "75",
                    "id": 1,
                    "name": "MDS Paris Nord"
                }
            }
        ]
    }
}
```

### Invitation

**`GET /api/v1/users/:id/invite`**

#### Paramètres de l'URL

* `:id` INT : identifiant unique de l'usager

#### Réponse

* `invitation_url` : lien d'invitation à destination de l'usager pour créer son profil
* `invitation_token` : code d'invitation de 8 caractères à destination de l'usager pour créer son profil en se rendant à l'url `https://www.rdv-solidarites.fr/invitation`

#### Exemple de requête

```bash
http GET https://www.rdv-solidarites.fr/api/v1/users/102/invite \
  access-token:FLXP6G2hIEYhmGe5MpHKfg \
  client:fySY0UMlNzgbhE8QYhXdkw \
  uid:martine@demo.rdv-solidarites.fr

```

```bash
curl --verbose \
  --header 'access-token: b-zBRj7TFto9dIJlXg5eyw' \
  --header 'client: jcfNV37BmHusa6S0FFC9FQ' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  'https://www.rdv-solidarites.fr/api/v1/users/102/invite'
```

#### Exemple de réponse

```javascript
{
    "invitation_token": "TOKENTOKEN",
    "invitation_url": "https://rdv-solidarites.fr/users/invitation/accept?invitation_token=TOKENTOKEN"
}
```

## POST /api/v1/users/:id/invite

### Paramètres de l'URL

* `:id` INT : identifiant unique de l'usager

### Paramètres

* `invite_for` : INT - en secondes, la durée de validité souhaitée du lien d'invitation envoyé à l'usager. \(1 jour = 86 400 secondes\). Si ce paramètre n'est pas renseignée, l'invitation sera valable 4 semaines par défaut.

### Réponse

Si l'utilisateur a une adresse mail :

* `invitation_url` : lien d'invitation à destination de l'usager pour créer son profil

Si l'utilisateur n'a pas d'adresse mail :

* `invitation_token` : code d'invitation à destination de l'usager pour créer son profil en se rendant à l'url `https://www.rdv-solidarites.fr/invitation`

### Création

**`POST /api/v1/users`**

#### Paramètres

* `organisation_ids` : \[INT\] - requis: Identifiants des organisations auxquelles rattacher le nouvel usager
* `first_name`: STRING - requis: Prénom\(s\)
* `last_name`: STRING - requis: Nom d'usage
* `email`: STRING - optionnel: Email de contact \(unique par usager\)
* `birth_name`: STRING - optionnel: Nom de naissance
* `birth_date`: STRING ou DATE - optionnel: Date de naissance
* `address`: STRING - optionnel: Adresse au format texte
* `phone_number`: STRING - optionnel: Numéro de téléphone français, mobile de préférence
* `responsible_id`: INT - optionnel: Identifiant de l'usager responsable 
* `caisse_affiliation`: STRING - optionnel: Caisse d'affiliation, valeurs possibles : `aucune`, `caf` ou `msa`
* `affiliation_number`: STRING - optionnel: Numéro d'affiliation à la caisse
* `family_situation`: STRING - optionnel: Situation familiale, valeurs possibles : `single`, `in_a_relationship` ou `divorced`
* `number_of_children`: INT - optionnel: nombre d'enfants
* `notify_by_sms`: BOOL - optionnel: Tenter d'envoyer des notifications par SMS
* `notify_by_email`: BOOL - optionnel: Tenter d'envoyer des notifications par email

Si vous souhaitez créer un usager proche, remplissez le paramètre `responsible_id`, et notez que seuls les champs `organisation_ids`, `first_name`, `last_name`, `birth_date` et `birth_name` seront pris en compte. Les usagers proches n'ont pas tous les champs d'un usager responsable.

#### Réponse en cas de succès 

* `user` : USER
  * `user_profiles` Profils de l'usager dans les organisations accessibles à l'agent faisant la requête

{% hint style="info" %}
Si vous tentez de créer un usager avec un email déjà utilisé, l'ID de l'usager déjà existant vous sera retourné dans les champs d'erreurs
{% endhint %}

{% hint style="info" %}
Cet endpoint ne déclenche pas l'envoi d'invitations. L'usager ne recevra pas de mail l'invitant à créer son mot de passe et accéder à son compte. Les agents pourront déclencher l'invitation plus tard depuis l'interface web
{% endhint %}

#### Exemple de requête

```bash
http --json POST https://www.rdv-solidarites.fr/api/v1/users \
  access-token:qx9HksCwRWvhQixJoXMlGA \
  client:mfev-k8pv9n8s9VLExXXZQ \
  uid:martine@demo.rdv-solidarites.fr \
  organisation_ids:='[1,2]' \
  first_name=Jean \
  last_name=Jacques \
  email=jean@jacques.fr \
  phone_number="06 60 60 60 60"
```

```bash
curl --verbose --request 'POST' \
  --header 'access-token: qx9HksCwRWvhQixJoXMlGA' \
  --header 'client: mfev-k8pv9n8s9VLExXXZQ' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  --header 'Content-Type: application/json' \
  --data '{"organisation_ids": [1], "first_name": "Jean", "last_name": "Jacques"}' \
  'http://localhost:5000/api/v1/users'
```

#### Exemple de réponse

```javascript
{
    "user": {
        "address": null,
        "affiliation_number": null,
        "birth_date": null,
        "birth_name": null,
        "caisse_affiliation": null,
        "email": "jean2@jacques.fr",
        "family_situation": null,
        "first_name": "Jean",
        "id": 21,
        "last_name": "JACQUES",
        "notify_by_email": true,
        "notify_by_sms": true,
        "number_of_children": null,
        "phone_number": "06 60 60 60 60",
        "responsible": null,
        "responsible_id": null,
        "user_profiles": null
    }
}
```

### Association à une Organisation

**`POST api/v1/user_profiles`**

#### Paramètres

* `organisation_id` : INT - requis: Identifiant de l'organisation
* `user_id` : INT - requis: Identifiant de l'usager
* `logement`: STRING - optionnel : situation de logement, valeurs possibles : `sdf`, `heberge`, `en_accession_propriete`, `proprietaire` ou `autre`
* `notes` : STRING - optionnel : Notes libres à propos l'usager - ne pas y inclure de donneées sensibles ou confidentielles

#### Réponse en cas de succès 

* `user_profile` : USER\_PROFILE
  * `user` : USER
  * `organisation` : ORGANISATION

{% hint style="info" %}
Un usager et une organisation ne peuvent être liées que par un seul et unique Profil. Vous recevrez une erreur si vous tentez de créer un Profil liant un couple organisation-usager déjà existant
{% endhint %}

#### Exemple de requête

```bash
http --json POST https://www.rdv-solidarites.fr/api/v1/user_profiles \
  access-token:qx9HksCwRWvhQixJoXMlGA \
  client:mfev-k8pv9n8s9VLExXXZQ \
  uid:martine@demo.rdv-solidarites.fr \
  organisation_id:=1 \
  user_id:=21 \
  notes="Usager pressé"
```

```bash
curl --verbose --request 'POST' \
  --header 'access-token: qx9HksCwRWvhQixJoXMlGA' \
  --header 'client: mfev-k8pv9n8s9VLExXXZQ' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  --header 'Content-Type: application/json' \
  --data '{"organisation_id": 1, "user_id": 21}' \
  'https://www.rdv-solidarites.fr/api/v1/user_profiles'
```

#### Exemple de réponse

```javascript

{
    "user_profile": {
        "logement": null,
        "notes": "Usager pressé",
        "organisation": {
            "departement": "75",
            "id": 1,
            "name": "MDS Paris Nord"
        },
        "user": {
            "address": null,
            "affiliation_number": null,
            "birth_date": null,
            "birth_name": null,
            "caisse_affiliation": null,
            "email": "jean2@jacques.fr",
            "family_situation": null,
            "first_name": "Jean",
            "id": 21,
            "last_name": "JACQUES",
            "notify_by_email": true,
            "notify_by_sms": true,
            "number_of_children": null,
            "phone_number": "06 60 60 60 60",
            "responsible": null,
            "responsible_id": null
        }
    }
}
```

