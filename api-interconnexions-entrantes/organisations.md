---
description: Consultation des organisations auxquelles appartient l‘agent connecté
---

# Organisations

### Index

**`GET /api/v1/organisations`**

#### Paramètres

\(Aucun\)

#### Réponse en cas de succès

* `organisations` : ARRAY\[ORGANISATION\]

#### Exemple de requête

{% tabs %}
{% tab title="httpie" %}
```bash
http 'https://www.rdv-solidarites.fr/api/v1/organisations' \
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
  'https://www.rdv-solidarites.fr/api/v1/organisations'
```
{% endtab %}
{% endtabs %}

#### Exemple de réponse

```bash
HTTP/1.1 200 OK
...

{
    "organisations": [
        {
            "id": 1,
            "name": "MDS Paris Nord"
        },
        {
            "id": 2,
            "name": "MDS Paris sud"
        }
    ],
    "meta": {
        "current_page": 1,
        "total_count": 2,
        "total_pages": 1
    }
}
```

### 

