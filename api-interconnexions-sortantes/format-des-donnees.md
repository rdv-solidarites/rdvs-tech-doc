# Format des données

La forme du contenu des requêtes est donnée pour les RDV et les plages d'ouvertures :

### RDV

```javascript
{
  "data": {
    "id": 1,
    "address": "",
    "agents": [
      {
        "id": 1,
        "email": "martine@demo.rdv-solidarites.fr",
        "first_name": "Martine",
        "last_name": "VALIDAY"
      }
    ],
    "duration_in_min": 30,
    "motif": {
      "id": 1,
      "location_type": "phone",
      "name": "Être rappelé par la PMI"
    },
    "organisation": {
      "id": 1,
      "departement": "75",
      "name": "MDS Paris Nord"
    },
    "starts_at": "2020-08-07 10:00:00 +0200",
    "status": "noshow",
    "users": [
      {
        "id": 1,
        "address": null,
        "birth_date": "1975-06-20",
        "email": "patricia_duroy@demo.rdv-solidarites.fr",
        "first_name": "Patricia",
        "last_name": "DUROY",
        "phone_number": "01 23 45 67 89",
        "responsible": null
      }
    ],
    "uuid": "966f9fb3-3d9d-4548-b1b8-feaf08548d9e"
  },
  "meta": {
    "model": "Rdv",
    "event": "updated",
    "timestamp": "2020-08-04 10:46:03 +0200"
  }
}
```

### Plage d'ouverture

```javascript
{
  "data": {
    "id": 568,
    "agent": {
      "id": 294,
      "email": "vincent.parfait@pasdecalais.fr",
      "first_name": "Jean",
      "last_name": "Parfait"
    },
    "end_time": "18:00:00",
    "first_day": "2020-07-17",
    "ical": "BEGIN:VCALENDAR\r\nVERSION:2.0\r\nPRODID:RDV Solidarités\r\nCALSCALE:GREGORIAN\r\nMETHOD:REQUEST\r\nBEGIN:VTIMEZONE\r\nTZID:Europe/Paris\r\nBEGIN:DAYLIGHT\r\nDTSTART:20200329T030000\r\nTZOFFSETFROM:+0100\r\nTZOFFSETTO:+0200\r\nRRULE:FREQ=YEARLY;BYDAY=-1SU;BYMONTH=3\r\nTZNAME:CEST\r\nEND:DAYLIGHT\r\nBEGIN:STANDARD\r\nDTSTART:20201025T020000\r\nTZOFFSETFROM:+0200\r\nTZOFFSETTO:+0100\r\nRRULE:FREQ=YEARLY;BYDAY=-1SU;BYMONTH=10\r\nTZNAME:CET\r\nEND:STANDARD\r\nEND:VTIMEZONE\r\nBEGIN:VEVENT\r\nDTSTAMP:20200717T085543Z\r\nUID:plage_ouverture_568@RDV Solidarités\r\nDTSTART;TZID=Europe/Paris:20200717T160000\r\nDTEND;TZID=Europe/Paris:20200717T180000\r\nCLASS:PUBLIC\r\nDESCRIPTION:\r\nLOCATION:Rue du Commandant Lherminier 62700 Bruay-la-Buissière\r\nSUMMARY:RDV Solidarités test vt\r\nATTENDEE:mailto:vincent.parfait@pasdecalais.fr\r\nEND:VEVENT\r\nEND:VCALENDAR\r\n",
    "ical_uid": "plage_ouverture_568@RDV Solidarités",
    "lieu": {
      "id": 10,
      "address": "Rue du Commandant Lherminier 62700 Bruay-la-Buissière",
      "name": "CCAS de Bruay-la-Buissière"
    },
    "motifs": [
      {
        "id": 320,
        "name": "Consultation BCG"
      }
    ],
    "organisation": {
      "id": 1,
      "departement": "62",
      "name": "MDS Lapins"
    },
    "rrule": null,
    "start_time": "16:00:00",
    "title": "test vt"
  },
  "meta": {
    "model": "PlageOuverture",
    "event": "created",
    "timestamp": "2020-07-17 10:55:43 +0200"
  }
}
```



