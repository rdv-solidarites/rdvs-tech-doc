# Motifs

Lecture de Motifs via l’API de RDV-Solidarités.

### Index

**`GET /api/v1/organisations/:organisation_id/motifs`**

**Paramètres**

* `:organisation_id` INT - _requis_ : Liste de l'organisation pour laquelle on souhaite récupérer les motifs
* `:active` BOOL - _optionnel_ : permet de ne retourner que les motifs actifs
* `:reservable_online` BOOL - _optionnel_ : permet de ne retourner que les motifs réservables en ligne

**Réponse en cas de succès**

* `motifs` : ARRAY\[MOTIF\]

#### Exemple de requête

```bash
http 'https://www.rdv-solidarites.fr/api/v1/organisations/3/motifs' \
 access-token:FLXP6G2hIEYhmGe5MpHKfg \
 client:fySY0UMlNzgbhE8QYhXdkw \
 uid:'martine@demo.rdv-solidarites.fr'
```

```bash
curl --verbose \
  --header 'access-token: FLXP6G2hIEYhmGe5MpHKfg' \
  --header 'client: fySY0UMlNzgbhE8QYhXdkw' \
  --header 'uid: martine@demo.rdv-solidarites.fr' \
  'https://www.rdv-solidarites.fr/api/v1/absences'
```

#### Exemple de réponse

```bash
HTTP/1.1 200 OK
...

{
    "motifs": [
        {
            "id": 1,
            "location_type": "phone",
            "name": "Être rappelé par la PMI"
        },
        {
            "id": 2,
            "location_type": "phone",
            "name": "Consultation gynécologie / contraception"
        },
        {
            "id": 3,
            "location_type": "public_office",
            "name": "Consultation prénatale"
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

### 

