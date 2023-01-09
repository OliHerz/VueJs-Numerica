<template>
  <div>
    <div class="title center">
      Td01 - Les directives
    </div>
    <hr>

    <h4> syntaxe simple data-biding (lecture seule)</h4>
    <div> Résultat : {{ msg1 }}</div>
    <hr>

    <h4> v-bind </h4>
    <div v-bind:title='msg2'> 
      Résultat :  Passer votre souris sur moi pendant quelques secondes pour voir le titre 
    </div>
    <hr>

    <h4> v-html </h4>
    <span> Pas d'interpretation de HTML : {{msg3}}</span>
    <br>
    <p> utilise v-html : <span v-html='msg3'></span> </p>
    <hr>

    <h4> v-on et expression Javascript </h4>
    <button v-on:click='ok = true'> Oui </button>
    <button v-on:click='ok = false'> Non </button>
    <p> {{ ok ? 'Oui' : 'Non' }}</p>
    <hr>

    <h4> v-model </h4>
    <input type="text" v-model='saisie'>
    <br>
    <p>
      Message : {{  saisie }}
    </p>
    <hr>

    
    <h4> v-show </h4>
    <!-- show = permet de cacher la chose  -->
      <button v-on:click='seen =!seen'> valeur : {{ seen }} </button>
    <div v-if='seen'>
      Résultat : Vous me voyez lorque seen == true
    </div>
    <hr>



    <h4> v-if / v-else </h4> 
  <!-- if = n'existe plus  -->
      <input type="text" v-model='saisie'>
      <br>
    <span v-if='saisie' >
      Message saisi : a que coucou
    </span>
    <p v-else>
      <i> Pas de message </i>
    </p>
    <hr>

    <h4> v-for </h4>
    <!-- Parcours d'un tableau -->
    <ol> Liste
      <li v-for ='el in liste' v-bind:key='el'> {{ el.text }} </li>
    </ol>

    <h4> v-for avec index </h4>
    <!-- Parcours d'un tableau avec un index -->
    <ul> Liste
      <li v-for ='(element,index) in liste' v-bind:key='index'> {{ index }} - {{ element.text }} </li>
    </ul>

  <h4> methode / fonction </h4>
  <div>
    <p> {{ msg4 }} </p>
    <button v-on:click='affiche'> Message affiché</button>
  </div>
  <hr>

  <h4> methode / fonction </h4>
  <div> reverseMessage()
    <p> {{ msg4 }} </p>
    <button v-on:click='reverseMessage'> Message retourné </button>
  </div>

  </div>

 

</template>

<script>
export default {
  data(){
    return{
      // Définition des données 
      msg1: 'hello Vuejs !',
      msg2: 'Vous avez affiché le message le ' + new Date().toLocaleString(),
      msg3: '<span style="color:red"> Ceci est en rouge </span>',
      ok: false,
      saisie:'',
      seen: true,
      liste :[
        {text: 'Apprendre Javascript'},
        {text: 'Apprendre Vue'},
        {text: 'Créer quelque chose'},
      ],
      msg4:'Hello MMI',
    }
  
  },
  methods:{
      // Definition des fonctions
      affiche: function(){
        alert('Affichage de ' +this.msg4)
      },
      
      reverseMessage:function(){
        this.msg4 = this.msg4
        .split('') // Récupère chaque caractère dans un tableau
        .reverse() // Inverse le tableau
        .join('') // recrée une chaine de caractère avec chaque éléments du tableau
      }
    }
}
</script>


<style scoped>
  .center{
    text-align: center;
  }
  .title{
    font-size: 1.4rem;
    font-weight: 500;
    margin-bottom: 0.4rem;
    color: #34495e;
  }
  h4{
    font-weight: bold;
  }
</style>

<!-- <template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style> -->
