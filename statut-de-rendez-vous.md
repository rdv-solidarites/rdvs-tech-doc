# États de rendez-vous

L’état des rendez-vous permet de suivre l’évolution d’un rendez-vous, et de connaître les rendez-vous honorés ou ratés\_: les fameux «\_lapins\_».

## _Status_ en base et dans les APIs

* `unknown` : Indéterminé. Le rendez-vous a été posé, mais on ne sait pas encore s’il sera ou s’il a été honoré.
* `waiting`: L’usager est présent en salle d’attente. C’est en principe un état transitoire avant `seen`.
* `excused` : Le rendez-vous a été annulé à l’avance, à l’initiative de l’usager. \(L’annulation a pu être faite par un agent, mais sur demande de l’usager.\)
* `revoked` : Le rendez-vous a été annulé, à l’initiative du service, par exemple pour raison administrative.
* `noshow` : Le rendez-vous est passé, mais l’usager ne c’est pas présenté.
* `seen` : L’usager a bien été vu en rendez-vous.

    **Note : changements du 10 août 2021**

    * Le status`revoked`a été ajouté. Précédemment, on ne faisait pas de différence entre une annulation à l’initiative de l’usager ou du service.
    * Le status `noshow` était auparavant intitulé `notexcused`.

    Ces changements sont visibles dans les APIs de requêtes et de notifications \(webhooks\). Un mode de compatibilité est temporairement disponible si besoin.

## Comportement dans l’interface

Les agents peuvent modifier l’état d’un rendez-vous avant ou après son jour prévu, mais tous les états ne sont pas disponibles. Concrètement: 

* avant le jour du rendez-vous, il n’est possible que d’annuler le rendez-vous. \(`excused` ou `revoked`\)
* à partir du jour du rendez-vous, il est toujours possible de l’annuler, mais aussi de le marquer comme honoré ou raté. \(`excused`, `revoked`,`seen`, `noshow` \)
  * le jour même du rendez-vous, il est aussi possible d’indiquer que l’usager est en salle d’attente. \(`waiting`\)

Par ailleurs, l’état `unknown` apparait différemment avant ou après le rendez-vous. Avant le rendez-vous, il est indiqué « Rendez-vous à venir ». Après le rendez-vous, il est indiqué « À renseigner ».

![Avant un rendez-vous](../.gitbook/assets/capture-de-cran-2021-08-25-a-11.23.40.png)

![Apr&#xE8;s un rendez-vous](../.gitbook/assets/capture-de-cran-2021-08-25-a-11.23.04.png)

