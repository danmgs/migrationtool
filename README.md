# FAQ de migration Sonar

### Contexte

Sonar de l'équipe ITSREL (entité Engie GEMS) va être migré vers Sonar de l'équipe WALNUT (entité Engie Digital).

L'objectif est d'avoir un Sonar au sein du groupe. Il faut déterminer les étapes pour y arriver.

### Etats des lieux (simplifié)

- Il y a 285 projets dans le portal Sonar ITSREL.

- Une communication sera envoyé aux équipes pour les sensibiliser. Cette communication contiendra un lien vers une FAQ confluence (contenu listé ci-dessous).
La communication guidera les équipes GEMS (FAQ) et mentionnera les points suivant:

- Concrétement et certainement, tout ne pourra pas être migré car il y a des projets qui ne sont plus buildé chez Engie GEMS depuis un moment. 

- Cela permettra de faire un ménage naturellement de projets dépréciés.
Il y a des projets "POC" avec 0 lignes de code (CF le report  excel de Daniel)

- Plusieurs équipes doivent certainement ne pas se rendre compte que leurs pipelines de builds "Sonar" ne fonctionnent plus car elles n'ont pas été mis à jour (maintenance non faite forçant de faire usage d'un service connection de type https, ou build non lancé sur ce projet depuis un bail car mise en prod depuis des lustres, sans besoin de fix).

- Chaque équipe se verra facturée à terme en fonction du nombre de ligne de codes qu'elles envoient. Cela les sensibilisera et portera leur attention sur le fait qu'on peut exclure des types de fichiers dans leurs analyses Sonar (builds plus rapide et moins couteux en terme de lignes et donc de cout). Il est donc temps de ne plus envoyer du code dans Sonar simplement pour envoyer, il faut vraiment en avoir utilité !


### Définitions:

- **Quality profile**:

ensemble de règles de codage sur divers et nombreux langages C#, java, salesforce, python, html.. (exemple: ne jamais définir une variable non utilisée, ne jamais renvoyé une liste null) qu'on active ou pas).
Il y a la quality profile "Sonar Way" de base. 

On peut en créer d'autres qui sont des déclinaisons de la Sonar Way, en
- conservant l'héritage des règles (si des règles de la quality profile SOnar way est modifiée , alors ce sera répercuté sur les quality profiles enfants), 
- ou bien sans conserver (la quality profile demande un effort à être maintenue par les équipes propriétaires)

- **Quality Gates**:

ensemble de règle macro comme "% de code à couvrir en terme de test, vis à vis du nouveau code introduit", "% de code non sécurisé introduit", etc
Il y a la quality gates "Sonar Way" de base. On peut créer des quality gates customisées.

### Use cases:

- En tant que développeur d'une équipe Engie GEMS, je veux migrer mon projet de Sonar ITSREL vers Sonar WALNUT.
Comment faire ?

1. <lien vers le portal walnut pour faire un ticket de demande d'accès>
2. <lien vers le portal walnut pour faire un ticket de création du projet dans le Sonar WALNUT> (création d'un service connection dans Azure Devops par exemple, etc)
3. <bonus: lien vers la page confluence WALNUT de documentations pour les pratiques Sonar>


- En tant que développeur d'une équipe Engie GEMS, j'aimerais savoir si je peux conserver l'historique de mes analyse sonar pour mes projets.


2 cas possibles qu'on pourra gérer.

1. Non (cas le plus simple, celui que ITSREL devrait privilégier pour faciliter la migration au maximum)
2. Oui. Il faut que les instances Sonar Walnut et GEMS soit identiques en version. On exporte d'un côté et on importe de l'autre, cela fonctionne si les quality gates et profiles du projet à migrer existent au préalable. Ceci dit, à voir pour le cas 2: il faut étudier la faisabilité , simuler ce cas de figure enrte les 2 Sonar.


- En tant que développeur d'une équipe Engie GEMS, j'aimerais conserver mes quality profiles et/ou quality gates
  
1. Sonar Walnut permet d'avoir  d'entrée une quality profile et quality gates propre à chaque projet (cas simple de base).

Cas compliqué: Mais il sera possible de les récupérer à l'identique des quality profiles et/ou quality gates qu'il y avait chez Sonar ITSREL.

Comment: Il faut exporter le profile ou gate en XML et le reimporter.
Par défaut, suite à la mgration, ce sera les quality profile et gates de base "Sonar Way"
Sinon, pour toute personalisation , les équipes intéréssées devront contacter WALNUT (cas par cas de customisation à la demande)

- Quelle est la date limite pour faire la migration ? Jusqu'à quand le portal Sonar ITSREL sera dispo ?


1. On renouvelle pas la license SOnar ITSREL qui périme le XXX 2024. 
Chaque équipe chez GEMS doivent migrer. A défaut, elles devront désactiver les étapes Sonar dans leur pipeline de build **pour ne pas être bloquer** dans les builds. (Dans ce cas de figure, elles risquent simplement de cumuler de la dette technique)
2. On veut bien prolonger la license encore 1 an le temps de migrer afin que les équipes puissent avoir une référence entre le Sonar WALNUT et le Sonar ITSREL, parfaire leur configuration etc

- En tant que développeur d'une équipe Engie GEMS, je n'ai pas eu le temps de migrer mon projet. ça fait longtemps que je n'ai pas eu besoin de le builder et j'ai besoin de faire un build pour un fix/une release en PROD. Ma build est bloqué car elle échoue aux étapes Sonar. Que faire ?


Les équipes devront désactiver les étapes Sonar dans leur pipeline de build **pour ne pas être bloquer** dans les builds (Dans ce cas de figure, elles risquent simplement de cumuler de la dette technique)

- En tant que développeur d'une équipe Engie GEMS, j'ai des soucis pour configurer ma pipeline de build pour  faire les analyse et les pousser des analyses vers le Sonar WALNUT. Je crois que ma machine de build n'est pas correctement configuré. A qui dois je m'adresser ?

<TBD pour l'assistance aux équipes: ITSREL ou WALNUT ?>

- Je suis le manageur d'une équipe Engie GEMS. Avant ITSREL payait tout pour toutes les équipes d'engie GEMS. Maintenant, si je passe chez Sonar WALNUT: combien ça me coute tout ça ?
  
Chaque projet sonarisé chez WALNUT porte une clé identifiant. ce projet est déclarée et le cout se fait comme indiqué dans cette page <mettre le lien de la page ici>




