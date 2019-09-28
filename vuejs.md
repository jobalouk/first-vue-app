Vue vs React

Différences fondamentales
Je vais surtout faire le tour de l'API
Et j'ai une connaissance naive du framework


Part 1 : Point communs

Titre : Points communs

Les utilisent un DOM VIRTUEL
Fournissent des composants de vue réactifs et composables
Restent concentrés sur le cœur de la bibliothèque en déléguant le routage et la gestion d’état à des bibliothèques connexes(???)

__Le DOM de vuejs__
Un peu de détail sur le dom virtuel de vuejs

__La réactivité dans Vue.js__
Un peu de détail sur la réactivé dans vuejs

Gestion de l'état dans Vue et React

React
`this.state` ou state 'functionnel' avec les hooks

Vue.js
La single source of truth d'un composant dans Vue est la prop `data`

`data` quand on fait `new Vue()`

`data` est une fonction quand on crée un composant monofichier...
La propriété du composant `data` doit être une fonction, afin que chaque instance puisse conserver une copie indépendante de l’objet retourné

Questions :
Un composant monofichier est un composant fonctionnel?


Part 2 : Optimisation

React

Avec React, quand l’état d’un composant change, cela enclenche de nouveau le rendu de tous ses sous-composants,
en partant de ce composant comme racine

`PureComponent`
`ShouldComponentUpdate`

Mais utiliser ces  méthodes présupposent que le rendu d'un composant soit déterminé par les props


Vue

Au rendu les dépendances d'un composant sont trackées, il sait quels componsants ont besoin d'être
mise à jour. Chaque composant peut être considéré comme ayant déjà `shouldComponentUpdate`(??)


Part 3 : JSX vs template

React, JSX

Utiliser du javascript dans les vues.
Les linter et les outils d'autocompletion plus avancés que les templates de Vues


Vue, template

Vue possède des fonctions de rendus et un support pour le JSX.
Par défaut :
- Template basé sur du html
- La doc nous dit que les dév sont plus productifs avec du html
- Plus simple à migrer
- Plus simple pour les designer et les dév avec moins d'éxpérience
- Et on peut utiliser des préprocesseurs


Part 4 : CSS à portée limitée au composant

React

Limiter la portée du css Dans React est souvent fait par des solutions
CSS-IN-JS.
Trade-off: un bundle plus lourd mais une expérience de dév bien meilleur.


Vue

La méthode de style par défaut de Vue est plus familière avec l’utilisation d’une balise <style>
dans un composant monofichier

`<style scoped>
  @media (min-width: 250px) {
    .list-container:hover {
      background: orange;
    }
  }
</style>
`

`scoped` encapsule automatiquement ce CSS dans votre composant en ajoutant un unique attribut.


Part 5 : Utilisation avancée

Redux avec Vue

Vuex avec Vue (inspiré par Elm(?)), apparement offre une expérience de dév supérieur


Vue

Les state manager accompagnant Vue et les lib de routage sont toutes officiellements supportées et
mises à jour avec le coeur de la bibliothèque.


React

React laisse cette partie à la communauté, créant un écosystème plus fragmenté.
Mais l’écosystème de React est considérablement plus riche que celui de Vue (c'est la doc de Vue qui le dit)
[Sidenote : React sera de toute façon plus mature que Vue pour l'écosysteme]


CLI

Vue et React ont un outil de génération de projet en CLI avec quelques particularités
que je ne vais pas lister parce que pas encore testées.

`vue init webpack app-name`


Snippets

Création d'un composant
`Vue.component('button-counter', {
  data: function () {
    return {
      count: 0
    }
  },
  template: '<button v-on:click="count++">Vous m\'avez cliqué {{ count }} fois.</button>'
})`


Fonction de rendu
`Vue.component('anchored-heading', {
  render: function (createElement) {
    return createElement(
      'h' + this.level,   // nom de balise
      this.$slots.default // tableau des enfants $slots.default -> prop d'instance
    )
  },
  props: {
    level: {
      type: Number,
      required: true
    }
  }
})
`

Des props dans un composant
`Vue.component('blog-post', {
  // camelCase en JavaScript
  props: ['postTitle'],
  template: '<h3>{{ postTitle }}</h3>'
})

<blog-post post-title="Hello !"></blog-post>
`


Passer des events à un composant
`<div id="example-1">
  <button v-on:click="counter += 1">Add 1</button>
  <p>Le bouton ci-dessus a été cliqué {{ counter }} fois.</p>
</div>
`

`var example1 = new Vue({
  el: '#example-1',
  data: {
    counter: 0
  }
})
`
