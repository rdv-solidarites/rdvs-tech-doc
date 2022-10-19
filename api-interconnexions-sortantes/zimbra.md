# Interconnexion par email et icalendar

En plus des webhooks, RDV-solidarités peut envoyer des emails aux agents après qu’un rendez-vous a été posé ou modifié, ou lorsqu’une plage d’ouverture est créée ou modifiée. De la même façon, un email est envoyé aux usagers concernés par un rendez-vous.

Ces emails contiennent les informations de l’_évènement_, c’est-à-dire le rendez-vous, la plage d’ouverture ou l’absence, au format icalendar. Elles sont incluses dans le mail en double: une fois en pièce jointe sous forme d’un fichier .ics, une fois en _part_ `text/calendar`. Ce sont les mêmes informations, dupliquées: le but est d’assurer une meilleure compatibilité avec les différents logiciels de calendrier. N’hésitez pas à nous contacter si quelque chose ne fonctionne pas parfaitement chez vous.

En images, le comportement sur Zimbra de l’ajout manuel d’une plage d’ouverture créée dans RDV-solidarités:

![](../../.gitbook/assets/76201480-9e5c0780-61f3-11ea-921a-2de6f5884518.png)

![](../../.gitbook/assets/76201596-c9465b80-61f3-11ea-9c43-4c600ccb99c2.png)

![](../../.gitbook/assets/76201489-a1ef8e80-61f3-11ea-96c4-7eb48ee221ca.png)

