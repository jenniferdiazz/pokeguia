<template>
<div>
  <h1>PokeGuia</h1>
  <img src="img\descarga.jpg" alt="">
  <form action="">
      <label>Ingrese nombre de personaje: </label>
      <input type="text" v-model="personaje.name">
      <input type="submit" value="Buscar" @click.prevent="fetchCharacter">
  </form>
  <section>
      
      <img :src="image" alt="no hay imagen">
      
      
      <hr>
      <h3>Habilidades</h3>
      <ul>
          <li v-for="abiliti in abilities" :key="abiliti">
              {{abiliti}}
          </li>
      </ul>
      <hr>
      <h3>Movimientos</h3>
      <ul>
          <li v-for="move in moves" :key="move">
              {{move}}
          </li>
      </ul>
  </section>
</div>
</template>

<script>
  export default {
      //name:'rickMorty-component',
      name:'pokemon-component',
    data() {
      return {
        personaje:{
            name:"pikachu",
            sprites:{
                front_default:""
                },
            image:"",
        }
      }
    },
    computed:{
        image(){
            return this.personaje.sprites.front_default;
        },
        nombre(){
            return this.personaje.name;
        },
      
        abilities(){
            
            
            /*let cont= this.personaje.abilities.length;
            console.log(cont);*/
            let newAbilities = []
            for(let i=0; i<this.personaje.abilities.length; i++){
                newAbilities.push(""+this.personaje.abilities[i].ability.name)
            }
            console.log(newAbilities);
            return newAbilities;
        },
       moves(){
            
        
            /*let cont= this.personaje.moves.length;
            console.log(cont);*/
            let newMoves = []
            for(let i=0; i<this.personaje.moves.length; i++){
                newMoves.push(""+this.personaje.moves[i].move.name)
            }
            console.log(newMoves);
            return newMoves;
        }
    },
    methods:{
        fetchCharacter() {
            fetch(`https://pokeapi.co/api/v2/pokemon/${this.personaje.name}`)
            .then(response => response.json())
            .then(json=>{
                
                this.addCharacter(json);
            })
            .catch(error=>{
                console.log(error)
                alert("No encontrado");
            })
        
    },
    addCharacter(json){
        console.log("hola");
       console.log(json)
        if(json===undefined){
            alert("no encontrado");
            return;
        }
        this.personaje = json;
      
    }
  },
  created(){
      this.fetchCharacter();
  }
  }
</script>

<style scoped>
  div{
      text-align: center;
  }
  ul> li{
      list-style: none;
  }
</style>