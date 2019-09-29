Vuejs

__Exemple de code__
Un peu d'improvisation sur les exemples de la doc de Vue

https://vuejs.org/v2/examples/

Différences fondamentales

Installer le dev tool pour le montrer

Comment les modifications sont tracées :
https://fr.vuejs.org/v2/guide/reactivity.html


__Points communs__
Les utilisent un DOM VIRTUEL
Fournissent des composants de vue réactifs et composables
Restent concentrés sur le cœur de la bibliothèque en déléguant le routage et la gestion d’état à des bibliothèques connexes

__Truc que je peux montrer/parler__
* Montrer le CLI avec ses opts
* Cloner un projet que j'ai fait
* Montrer mon projet

__La réactivité dans Vue.js__
Un peu de détail sur la réactivé dans vuejs

__La base__ une instance de vue avec ses opts
* création local
* création global
* composant mono fichier
* instance de vue


__Détails sur data__
La single source of truth d'un composant dans Vue -> `data`

`data` est une fonction quand on crée un composant monofichier...
La propriété du composant `data` doit être une fonction, afin que chaque instance puisse conserver une copie indépendante de l’objet retourné


### Optimisation

__React__
Utiliser `shouldComponentUpdate()` présupposent que le rendu d'un composant soit déterminé par les props


__Vue__
Au rendu les dépendances d'un composant sont tracées, Vue sait quels sont les composants qui ont besoin d'être update.
Chaque composant peut être considéré comme ayant déjà `shouldComponentUpdate`(??)
* data
* données reactives
* Pk les propriétés doivent être présentent dans l'objet data

:Vue effectue le processus de conversion en accesseur/mutateur lors de l’initialisation de l’instance, une propriété doit être présente dans l’objet data afin que Vue puisse la convertir et la rendre réactive.


### CSS à portée limitée au composant

__React__
Limiter la portée du css Dans React est souvent fait par des solutions
CSS-IN-JS.
Trade-off: un bundle plus lourd mais une expérience de dév bien meilleur.


__Vue__
`scoped` encapsule automatiquement ce CSS dans votre composant en ajoutant un unique attribut.


### CLI

Vue et React ont un outil de génération de projet en CLI avec quelques particularités

`vue init webpack app-name`
