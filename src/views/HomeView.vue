<template>
  <div>
     <div class="center">
  
      <img src="https://archives.bulbagarden.net/media/upload/4/4b/Pok%C3%A9dex_logo.png" >
  </div>
    <div class="content">

      <div class="flex">
        <div class="flex-col">


    <div v-for="(data, index) in pokemons" :key="index" class="justify-center">
  
    <v-app id="inspire" class="size">
    <v-card
      class="mx-auto w-100"
    >
      <!-- max-width="aut" -->
      <v-img
      class="pointer"
        :src="data.url"
        height="200px"
        @click="send_info(data)"
      ></v-img>
  
      <v-card-title class="w-100 p-5 m-5" style="min-width: 200px"> {{data.name}} </v-card-title>
  
      <!-- <v-card-subtitle> -->
        <!-- 1,000 miles of wonder -->
      <!-- </v-card-subtitle> -->
  
      <!-- <v-card-actions>
        <v-btn
          color="orange lighten-2"
          text
        >
          Explore
        </v-btn>
  
        <v-spacer></v-spacer>
  
        <v-btn
          icon
          @click="show = !show"
        >
          <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
        </v-btn>
      </v-card-actions> -->
  
      <!-- <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>
  
          <v-card-text>
            I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
          </v-card-text>
        </div>
      </v-expand-transition> -->
    </v-card>
  </v-app>

</div>
        </div>
        <div class="flex-col">
         <PokemonInfo :pokemon_info="selected_pokemon" @send_url="recieve_url" ></PokemonInfo>
        </div>

      </div>

    </div>

  </div>
</template>



<script>

import axios from 'axios';
import PokemonInfo from '../components/PokemonInfo.vue';


 export default {

   components:{PokemonInfo},


    data(){
      return{
       show:false,
       pokemons:[],
       selected_pokemon:[], 
       };

    },
    created(){
      let instance = this;
  
  for(let i = 0; i <= 10; i++) {


      axios
      .get(`https://pokeapi.co/api/v2/pokemon/${i+1}`)
      .then(response => {
       console.log(response)
        let pokemon = {
         abilities: response.data.abilities, 
         name: response.data.name, 
         url: response.data.sprites.front_default,
       };

      instance.pokemons.push(pokemon);
      })
      .catch(err =>{
        console.log(err);
      });

    }

      console.log(this.pokemons);
    },
    methods:{
      send_info(pokemon_info){
      this.selected_pokemon = pokemon_info
      },
      recieve_url(url){
       window.location.replace(url)
      }
    }
  
  };
</script>



<style scoped>
.center{
  text-align: center;
  margin-top: 1%;
}
.size{
  height: 550px;
  
}
.pointer{
  cursor: pointer;
}
.flex{
  display: flex;
}
.flex-col{
  flex: 1;
  background-color: red;
}
</style>