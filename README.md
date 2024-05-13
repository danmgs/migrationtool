# FAQ de migration Sonar

### Définitions:

- **Quality profile**: ensemble de règles de codage sur divers et nombreux langages C#, java, salesforce, python, html.. (exemple: ne jamais définir une variable non utilisée, ne jamais renvoyé une liste null) qu'on active ou pas).
Il y a la quality profile "Sonar Way" de base. 
On peut en créer d'autres qui sont des déclinaisons de la Sonar Way, en
- conservant l'héritage des règles (si des règles de la quality profile SOnar way est modifiée , alors ce sera répercuté sur les quality profiles enfants), 
- ou bien sans conserver (la quality profile demande un effort à être maintenue par les équipes propriétaires)

- **Quality Gates**: ensemble de règle macro comme "% de code à couvrir en terme de test, vis à vis du nouveau code introduit", "% de code non sécurisé introduit" etc
Il y a la quality gates "Sonar Way" de base. On peut en créer des custom.

### Use cases:

- En tant que développeur d'une équipe Engie GEMS, je veux migrer mon projet de Sonar ITSREL vers Sonar WALNUT.
Comment faire ?

1. <lien vers le portal walnut pour faire un ticket de demande d'accès>
2. <lien vers le portal walnut pour faire un ticket de création du projet dans le Sonar WALNUT> (création d'un service connection dans Azure Devops par exemple, etc)
3. <bonus: lien vers la page confluence WALNUT de documentations pour les pratiques Sonar>


- En tant que développeur d'une équipe Engie GEMS, j'aimerais savoir si je peux conserver l'historique de mes analyse sonar pour mes projets.


2 cas possibles qu'on pourra gérer.

1. Non (cas simple, celui que ITSREL devrait cadrer pour simplifier la migration)
2. Oui. Il faut que les instances Sonar Walnut et GEMS soit identiques en version. On export d'un côté et on import de l'autre, cela fonctionne si les quality gates et profiles existent.
   à voir pour le cas 2. il faut étudier la faisabilité , simuler ce cas de figure enrte les 2 Sonar.


- En tant que développeur d'une équipe Engie GEMS, j'aimerais conserver mes quality profiles et/ou quality gates
  
1. Sonar Walnut permet d'avoir une quality profil et quality gates dédiée à chaque projet qui sont sonarisés. Mais il est possible de les récupérer à l'identique des quality profiles et/ou quality gates qu'il y avait chez Sonar ITSREL.
Il faut exporter le profile ou gate en XML et le reimporter.
Par défaut, suite à la mgration, ce sera les quality profile et gates de base "Sonar Way"
Sinon, pour toute personalisation , les équipes intéréssées devront contacter WALNUT (cas par cas de customisation à la demande)

- Quelle est la date limite pour faire la migration ? Jusqu'à quand le portal Sonar ITSREL sera dispo ?
1. On renouvelle pas la license SOnar ITSREL qui périme le XXX 2024. 
Chaque équipe chez GEMS doivent migrer. A défaut, elles devront désactiver les étapes Sonar dans leur pipeline de build **pour ne pas être bloquer** dans les builds. (Dans ce cas de figure, elles risquent simplement de cumuler de la dette technique)
2. On décide de la renouveller encore 1 an le temps de migrer afin que les équipes puissent avoir une référence entre le Sonar WALNUT et le Sonar ITSREL.

- En tant que développeur d'une équipe Engie GEMS, je n'ai pas eu le temps de migrer mon projet. ça fait longtemps que je n'ai pas eu besoin de le builder et j'ai besoin de faire un build pour un fix/une release en PROD.
Les équipes devront désactiver les étapes Sonar dans leur pipeline de build **pour ne pas être bloquer** dans les builds. (Dans ce cas de figure, elles risquent simplement de cumuler de la dette technique)

- En tant que développeur d'une équipe Engie GEMS, j'ai des soucis pour configurer ma pipeline de build pour pousser dans le Sonar WALNUT. Je crois que ma machine de build n'est pas correctement configuré. A qui dois je m'adresser ?




