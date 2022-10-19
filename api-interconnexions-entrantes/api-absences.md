---
description: >-
  Lecture, création, modification, suppression d‘absences via l’API de
  RDV-Solidarités.
---

# Absences

### Index

**`GET /api/v1/absences`**

#### Paramètres

* `organisation_id` INTEGER - _optionnel_ : filtre les absences retournées pour une seule organisation

#### Réponse en cas de succès

* `absences` : ARRAY\[ABSENCE\]

#### Exemple de requête

{% tabs %}
{% tab title="httpie" %}
```bash
http 'https://www.rdv-solidarites.fr/api/v1/absences' \
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
  'https://www.rdv-solidarites.fr/api/v1/absences'
```
{% endtab %}
{% endtabs %}

#### Exemple de réponse

```bash
HTTP/1.1 200 OK
...

{
    "absences": [
        {
            "agent": {
                "email": "martine@demo.rdv-solidarites.fr",
                "first_name": "Martine",
                "id": 1,
                "last_name": "VALIDAY"
            },
            "end_day": "2021-01-05",
            "end_time": "08:00:00",
            "first_day": "2020-12-23",
            "ical_uid": "absence_14@RDV Solidarités",
            "id": 14,
            "organisation": {
                "departement": "75",
                "id": 1,
                "name": "MDS Paris Nord"
            },
            "start_time": "08:00:00",
            "title": "Vacances de Noël"
        },
        {
            ...
        }
    ],
    "meta": {
        ...
    }
}
```

### Consultation

**`GET /api/v1/absences/:id`**

#### Paramètres

* `id`: identifiant de l’absence \(requis\)

#### Réponse en cas de succès

* `absence`: ABSENCE

#### Exemple de requête

{% tabs %}
{% tab title="httpie" %}
```bash
http 'https://www.rdv-solidarites.fr/api/v1/absences/14' \
 access-token:FLXP6G2hIEYhmGe5MpHKfg \
 client:fySY0UMlNzgbhE8QYhXdkw \
 uid:'martine@demo.rdv-solidarites.fr'
```
{% endtab %}

{% tab title="curl" %}
```
curl --verbose \
  --header 'access-token: FLXP6G2hIEYhmGe5MpHKfg' \
  --header 'client: fySY0UMlNzgbhE8QYhXdkw' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  'https://www.rdv-solidarites.fr/api/v1/absences/14'
```
{% endtab %}
{% endtabs %}

#### Exemple de réponse

```bash
HTTP/1.1 200 OK
...

{
    "absence": {
        "agent": {
            "email": "martine@demo.rdv-solidarites.fr",
            "first_name": "Martine",
            "id": 1,
            "last_name": "VALIDAY"
        },
        "end_day": "2021-01-05",
        "end_time": "08:00:00",
        "first_day": "2020-12-23",
        "ical_uid": "absence_14@RDV Solidarités",
        "id": 14,
        "organisation": {
            "departement": "75",
            "id": 1,
            "name": "MDS Paris Nord"
        },
        "start_time": "08:00:00",
        "title": "Vacances de Noël"
    }
}
```

### Création

**`POST /api/v1/absences`**

#### Paramètres

* `organisation_id` INTEGER : l'identifiant de l'organisation dans laquelle créer une absence
* `agent_id` INTEGER : l'identifiant de l'agent absent
* `agent_email` EMAIL: l’email de l’agent absent. `agent_email`ou `agent_id` doit être spécifié; si les deux sont présents, `agent_id` est utilisé.
* `title` TEXT : le titre de l’absence
* `first_day` DATE : le jour de début de l'absence
* `start_time` TIME : l'heure de début de l'absence
* `end_day` DATE : le jour de fin de l'absence
* `end_time` TIME : l'heure de fin de l'absence

{% hint style="warning" %}
L’API de création d'absence ne permet pour l'instant pas de créer des absences récurrentes.
{% endhint %}

#### Réponse

* `absence` : ABSENCE : uniquement présent quand l'absence a été créée avec succès. Contient l'absence qui vient d'être créée.

#### Exemple de requête

{% tabs %}
{% tab title="httpie" %}
```bash
http --json POST https://www.rdv-solidarites.fr/api/v1/absences \
  access-token:FLXP6G2hIEYhmGe5MpHKfg \
  client:fySY0UMlNzgbhE8QYhXdkw \
  uid:martine@demo.rdv-solidarites.fr \
  organisation_id=1 \
  agent_id=1 \
  title="Congé parental" \
  first_day="2020-11-20" \
  start_time="08:00" \
  end_day="2020-11-20" \
  end_time="18:00"
```
{% endtab %}

{% tab title="curl" %}
```bash
curl --verbose --request 'POST' \
  --header 'access-token: FLXP6G2hIEYhmGe5MpHKfg' \
  --header 'client: fySY0UMlNzgbhE8QYhXdkw' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  --header 'Content-Type: application/json' \
  --data '{"agent_id":"1","end_day":"2020-11-20","end_time":"18:00","first_day": "2020-11-20","organisation_id":"1","start_time":"08:00","title":"Congé parental"}' \
  'https://www.rdv-solidarites.fr/api/v1/absences'
```
{% endtab %}
{% endtabs %}

#### Exemple de réponse

```bash
HTTP/1.1 200 OK
...

{
    "absence": {
        "agent": {
            "email": "martine@demo.rdv-solidarites.fr",
            "first_name": "Martine",
            "id": 1,
            "last_name": "VALIDAY"
        },
        "end_day": "2020-11-20",
        "end_time": "18:00:00",
        "first_day": "2020-11-20",
        "ical_uid": "absence_10@RDV Solidarités",
        "id": 10,
        "organisation": {
            "departement": "75",
            "id": 1,
            "name": "MDS Paris Nord"
        },
        "start_time": "08:00:00",
        "title": "Congé parental"
    }
}
```

### Modification

**`PUT /api/v1/absences/:id`**

**`PATCH /api/v1/absences/:id`**

#### Paramètres

* `id`: l’identifiant de l’absence
* `title` TEXT : le titre de l’absence
* `first_day` DATE : le jour de début de l'absence
* `start_time` TIME : l'heure de début de l'absence
* `end_day` DATE : le jour de fin de l'absence
* `end_time` TIME : l'heure de fin de l'absence

#### Réponse

* `absence` : ABSENCE. L’absence modifiée.

#### Exemple de requête

{% tabs %}
{% tab title="httpie" %}
```bash
http --json PATCH https://www.rdv-solidarites.fr/api/v1/absences/10 \
  access-token:FLXP6G2hIEYhmGe5MpHKfg \
  client:fySY0UMlNzgbhE8QYhXdkw \
  uid:martine@demo.rdv-solidarites.fr \
  title="Congé maladie"
```
{% endtab %}

{% tab title="curl" %}
```bash
curl --verbose --request 'PATCH' \
  --header 'access-token: FLXP6G2hIEYhmGe5MpHKfg' \
  --header 'client: fySY0UMlNzgbhE8QYhXdkw' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  --header 'Content-Type: application/json' \
  --data '{"title":"Congé maladie"}' \
  'https://www.rdv-solidarites.fr/api/v1/absences/10'
```
{% endtab %}
{% endtabs %}

#### Exemple de réponse

```bash
HTTP/1.1 200 OK
...

{
    "absence": {
        "agent": {
            "email": "martine@demo.rdv-solidarites.fr",
            "first_name": "Martine",
            "id": 1,
            "last_name": "VALIDAY"
        },
        "end_day": "2020-11-20",
        "end_time": "18:00:00",
        "first_day": "2020-11-20",
        "ical_uid": "absence_10@RDV Solidarités",
        "id": 10,
        "organisation": {
            "departement": "75",
            "id": 1,
            "name": "MDS Paris Nord"
        },
        "start_time": "08:00:00",
        "title": "Congé maladie"
    }
}
```

### Suppression

**`DELETE /api/v1/absences/:id`**

#### Paramètres

* `id`: l’identifiant de l’absence

**Réponse**

* Réponse vide en cas de succès.

#### Exemple de requête

{% tabs %}
{% tab title="httpie" %}
```bash
http DELETE https://www.rdv-solidarites.fr/api/v1/absences/10 \
  access-token:FLXP6G2hIEYhmGe5MpHKfg \
  client:fySY0UMlNzgbhE8QYhXdkw \
  uid:martine@demo.rdv-solidarites.fr
```
{% endtab %}

{% tab title="curl" %}
```
curl --verbose --request 'DELETE' \
  --header 'access-token: FLXP6G2hIEYhmGe5MpHKfg' \
  --header 'client: fySY0UMlNzgbhE8QYhXdkw' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  --header 'Content-Type: application/json' \
  'https://www.rdv-solidarites.fr/api/v1/absences/10'
```
{% endtab %}
{% endtabs %}

#### Exemple de réponse

```text
HTTP/1.1 204 No Content
...
```



