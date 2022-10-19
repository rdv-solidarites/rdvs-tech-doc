---
description: Consultation des agents membres des organisations de l’agent connecté
---

# Agents

### Index

**`GET /api/v1/agents`**

#### Paramètres

* `organisation_id` INTEGER - _optionnel_ : filtre les agents retournés pour une seule organisation

#### Réponse en cas de succès

* `agents` : ARRAY\[AGENTS\]

#### Exemple de requête

{% tabs %}
{% tab title="httpie" %}
```bash
http 'https://www.rdv-solidarites.fr/api/v1/agents?organisation_id=1' \
 access-token:FLXP6G2hIEYhmGe5MpHKfg \
 client:fySY0UMlNzgbhE8QYhXdkw \
 uid:'martine@demo.rdv-solidarites.fr'
```
{% endtab %}

{% tab title="curl" %}
```bash
curl --verbose \
  --header 'access-token: FLXP6G2hIEYhmGe5MpHKfg' \
  --header 'client: fySY0UMlNzgbhE8QYhXdkw' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  'https://www.rdv-solidarites.fr/api/v1/absences?organisation_id=1'
```
{% endtab %}
{% endtabs %}

#### Exemple de réponse

```bash
HTTP/1.1 200 OK
...

{
    "agents": [
        {
            "email": "martine@demo.rdv-solidarites.fr",
            "first_name": "Martine",
            "id": 1,
            "last_name": "VALIDAY"
        },
        {
            "email": "marco@demo.rdv-solidarites.fr",
            "first_name": "Marco",
            "id": 2,
            "last_name": "DURAND"
        },
        {
            "email": "polo@demo.rdv-solidarites.fr",
            "first_name": "Polo",
            "id": 3,
            "last_name": "DURANT"
        }
    ],
    "meta": {
        "current_page": 1,
        "total_count": 3,
        "total_pages": 1
    }

}
```

### 

