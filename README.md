# Schwartz-Sophie
Mémoire SF

18/12/2014
----------
Je suis Sophie SCHWARTZ étudiante sage-femme en dernière année à l'école de Strasbourg. Je suis actuellement en train de réaliser mon mémoire de fin d'étude. 

Mme Basso, sage-femme enseignante qui suit mon travail de mémoire s'est permis de me transmettre les coordonnées du SAV, suite au cours de statistique quantitative que vous avez récemment dispensé aux 4ème années ! En effet, je suis un peu perdue dans le vaste monde des statistiques... Et j'aimerais savoir si vous pourriez m'aider ou si vous pouviez me conseiller une personne disponible à cet effet.

Mon mémoire consiste en la réalisation d'une étude quantitative rétrospective dont la question de recherche est la suivante :

« Existe-t-il une différence de prise en charge du travail et de l'accouchement des femmes à bas risque obstétrical, entre une maternité de niveau I et une maternité de niveau III ? »

Afin de réaliser cette étude rétrospective, je vais consulter les dossiers obstétricaux de femmes considérées à bas risque obstétrical ayant accouché dans une maternité de niveau I ou de niveau III. Je vais ainsi réaliser une comparaison des pratiques de médicalisation en salle de naissance dans ces deux types de maternités, ainsi qu'une évaluation du devenir post-natal immédiat maternel et néonatal. 

J'ai déterminé :
- les critères d'inclusion
- les critères d'exclusion
- les données à étudier pour l'étude (c'est-à-dire les critères de médicalisation et du devenir post-natal)

Je pense utiliser le logiciel R pour le traitement des données. Cependant j'aimerais être sûre de créer un tableur excel correct afin de simplifier l'analyse statistique. 


En espérant que vous pourrez m'aider, je me tiens à votre disposition pour plus d'informations sur ce travail. 

réponse:

Bonjour madame Schwartz,

tout à fait d'accord sur le principe avec une petite restriction, je serai absent à partir de demain et jusqu'au 5 janvier 2015.
Pouvez-vous m'adresser la liste des données à étudier avec le plus de détails possibles ?
Le logiciel R est un bon choix mais les données doivent être présentées en respectant certaines contraintes pour pouvoir être exploitées rapidement. Je joins le diaporama que j'ai utilisé à l'école de SF. Les Diapos 10 à 22 sont plus particulièrement consacrées à l'utilisation d'un tableur en vue d'une exploitation avec R.

+ diaporama sur les données

23/12/2014
----------

Tout d'abord merci beaucoup pour votre réponse rapide et votre diaporama ! 

Je vous envoie un document pdf avec plus de détails sur mon sujet de mémoire. J'ai commencé à rédiger de manière synthétique la partie "Matériels et Méthodes". Ce n'est pour l'instant qu'une ébauche... Je vous envoie également la liste des critères que je veux étudier. La liste est conséquente et il y a plusieurs critères "alternatifs", comme par exemple : Y a-t-il eu une pose de péridurale ? Si oui à quelle dilatation ? 
Certaines réponses sont OUI/NON, d'autres sont des chiffres (durée des efforts expulsifs par exemple) ou encore des propositions (couleur du liquide amniotique) ce qui risque de compliquer les choses ! 

Je suis pour ma part en période de révisions en vue des examens les 8 et 9 janvier, je reste cependant à votre disposition pour plus d'informations. A partir du 12 janvier je serai en stage, mais je serai disponible l'après-midi.

Je vous souhaite de bonnes fêtes,

24/12/2014
------------

Bonjour,

C'est un projet très ambitieux au regard du nombre d'items à recueillir pour un dossier, mais le résultat promet d'être très intéressant en particulier dans le cadre d'une recherche reproductible. R se prête bien à ce type de travail notamment si on l'utilise via une surcouche appelée RStudio (http://www.rstudio.com/products/rstudio/download/ installation facile) qui simplifie l'utilisation de R et permet de produire des documents très élaborés.

J'ai parcouru le document 'feuille de recueil' et aucun item ne présente de difficulté de recueil dans un tableur. Quelques conseils:
- établir une dictionnaire ou lexique des données. C'est un peu fastidieux mais cela rendra beaucoup de services par la suite. Si vous utilisez un tableur (Excel, libre office, google drive...):
  - ce sont des classeurs où l'on peut ouvrir plusieurs pages (onglets du bas), chaque page constituant une grille de saisie.
  - la première feuille est réservée à la saisie des données. C'est la page principale.
  - la feuille 2 contient le dictionnaire, constitué par l'ensemble des items que l'on veut recueillir disposés de la façon suivante:
    - un item par ligne
    - colonne 1: intitulé complet de l'item
    - colonne 2: abréviation de l'item, à la fois succinte et explicite. ex. APD = analgésie péridurale. L'abréviation de devrait pas dépasser 10 caractères. Si on utilise des mots composés, les séparer par un point '.' ou  un underscore '_', jamais par un espace. N'utiliser que des lettres majuscules et jamais d'accents. Ces abréviation serviront à identifier les colonnes de la feuille de saisie (feuille 1).
    - colonne 3: pour chaque item, détailler les réponses possibles sous la forme 'abréviation' = 'réponse en clair. Par ex. pour le liquide amniotique (LA) on aurait LAC = liquide amniotique clair, LAT = liquide teinté, LAM = liquide méconial (?). Il est possible voire souhaitable de réserver une ligne par réponse.
    - colonne 4: unités utilisées pour chaque item. Ex: taille en cm, date = AAAA-MM-JJ (format ISO), heure = HH:MM:SS, score APGAR = 0 à 10, etc. Cela permet de mettre en place des contôle de cohérence.
   
Pour le feuillet saisie (page 1 du classeur)

- Une ligne par observation (patiente) et une colonne par variable (ce que l'on mesure)
- on peut mélanger sans problème des variables numériques (poids, IMC...) et catégorielles (couleur du liquide amniotique) à condition de respecter la règle suivante: une colonne ne peut contenir q'un type de donnée et un seul. Une colonne de poids ne peut contenir que des chiffres, une colonne de mots (aspect du liquide amniotique) ne doit contenir que les abréviations présentes dans le dictionnaire pour cet item.
- les variables catégorielles (aspect du liquide) sont très bien gérée par R. Utiliser les abréviations LAC, LAT ou LAM pour le décrire. C'est plus facile à comprendre pour vous et pour R! De la même manière pour les variables dichotomiques, utilisez OUI ou NON. ATTENTION: R est sensibleà la casse (majuscule/minuscule) c'est à dire que pour R, OUI et oui ou Oui sont 3 réponses différentes. En pratique, choisir une ortographe et s'y tenir pour toutes les observations.
- pour les items du type 'peridurale' OUI/NON, 'si OUI à quelle dilatation du col', prévoir 2 colonnes:
  - colonne 1: APD = OUI ou NON
  - colonne 2: APD_OUI = dilatation du col en cm si APD = OUI, et NA si APD = NON. NA (not avalaible ou non applicable) est un symbole conventionnel qui peut être utilisé dans une colonne de chiffres et qui indique à R qu'il faut ignorer cette valeur. D'une manière générale, NA est à utiliser chaque fois qu'une donnée est manquante, quel que soit la valeur de cette donnée (numérique ou catégorielle).

Quelques réflexions qui me sont venues en passant:

- Origine ethnique: je pense que c'est un élément intéressant pour toutes sortes de raisons, mais que la CNIL n'autorisait pas en France le recueil de cette information ? Dans la mesure où le questionnaire reste anonyme, je pense que cela reste possible. C'est une variable catégorielle couramment utilisée aux USA (on peut utiliser leur classification)

- position: je pense que le nombre de positions pour un accouchement est dénombrable, ce qui permet de proposer une liste finie de positions ?

- quelques items que je n'ai pas trouvé:

- sexe de l'enfant (l'Y est fragile...). Je ne sais pas si c'est pertinent, mais c'est une info facile à récupérer et évite de retourner aux dossiers...
- gemellité ?
- prématurité (critère d'exclusion ?)

Je suis actuellement au Canada et en congé jusqu'au 5 janvier. Internet rest un bon moyen d'échange dans l'immédiat.

Je vous souhaite de bonnes fêtes de fin d'année et du couragepour vos révisions !

1/02/2015
---------

Tout d'abord merci beaucoup pour votre réponse rapide et surtout désolée pour tout ce temps sans nouvelles de ma part... J'ai enfin réalisé le tableur grâce à vos consignes. J'ai utilisé OpenOffice dans sa dernière version (4.1.1).

Je vous transmets ce tableur ainsi que la grille de recueil que j'ai modifiée grâce à vos idées et à ce que j'ai pu trouver d'intéressant dans les dossiers :

- J'ai enlevé la partie "origine ethnique" et "niveau d'étude" puisque cet item est très peu rempli dans les dossiers et que je ne sais pas vraiment ce que j'aurais fait de ces informations dans les résultats...
- Certains éléments seront difficilement analysables de manière statistique.. Mais j'ai laissé ces items pour m'en servir éventuellement dans la discussion. (les positions lors du travail qui sont effectivement très variées, l'attitude de l'équipe à l'arrivée d'une femme en début de travail qui est généralement standardisée dans l'établissement pour toutes les sages-femmes,...)
- Le sexe de l'enfant a bien entendu été ajouté, j'avais oublié que l'Y était si important !
- Pour ce qui est de la gémellité et des prématurés il s'agit en fait de critères d'exclusion de la population considérée à bas risque obstétrical qui est étudiée.

J'ai quelques questions suite à réalisation de ce tableur : 

- Faut-il indiquer NA dans "réponses possibles" sur la page du dictionnaire ou est-ce que R reconnait automatiquement NA comme une absence de réponse ?
- Faut-il prévoir une feuille de saisie pour chaque lieu puisque je vais comparer Thann et Mulhouse ?
- Comment indiquer plusieurs réponses possibles ? Par exemple pour le dernier item "interventions médicales lors du travail et de l'accouchement" il est possible que le gynécologue, le pédiatre et l'anesthésiste soient tous intervenus...


Je pense qu'il y a des choses à corriger avant de commencer à saisir les données... Je suis malheureusement coincée en stage à Mulhouse pour encore une semaine et je n'ai pas accès à internet là bas, hormis sur mon téléphone. Je peux donc recevoir les mails mais je ne pourrai pas vous renvoyer un document d'ici là... Mais j'attends vos remarques et suggestions avec plaisir ! 

Vu que je suis prise par le temps, je ne pourrai inclure qu’environ 50 dossiers dans chaque maternité... Ce nombre sera bien entendu insuffisant pour obtenir des résultats significatifs, mais je suppose que même avec le double de dossiers ce ne serait tout de même pas significatif... Il faudra mettre en avant la démarche réalisée plutôt que le résultat en tant que tel et la possibilité de reproduire cette étude pour aller plus loin !

La semaine prochaine je suis en stage à Strasbourg, ce qui pourra me permettre d'être plus disponible. Est-ce que vous seriez d'accord pour m'aider à boucler la partie statistique de cette étude ? 


En vous remerciant du temps que vous m'accorder, 

2/02/2014
----------

ok pour continuer la partie statistique du travail. Je suis disponible la semaine prochaine lundi  en fin de matinée et mardi matin. Le dictionnaire est très complet et le tableur très bien présenté. Je vais le tester avec de données fictives mais à ce stade tous le pièges ont été évités. Pour NA (not available) pas de pb, R connait et sait faire des opérations avec NA ( 1 + NA = 1 na.rm [oter les NA = na remove], etc).
