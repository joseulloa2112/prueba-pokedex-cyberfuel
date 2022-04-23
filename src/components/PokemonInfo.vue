<template>
    <div>
      <div class="static">
            <v-container>
      <v-row justify="space-around">
        <v-card>
          <v-img
            class="banner-pk"
            height="200px"
            src="https://cdnb.artstation.com/p/assets/images/images/021/500/833/large/mario-aceituno-carcasa-pokedex-completa.jpg?1571920182"
          >
             
          </v-img>
  
          <v-card-text>
            <div class="font-weight-bold ml-8 mb-2">
              Abilities
            </div>
  
            <v-timeline
              align-top
              dense
            >
              <v-timeline-item
                v-for="(pokemon, i) in pokemon_info.abilities"
                :key="i"
                color="green"
                small
              >
                <div>
                  <div class="font-weight-normal pointer" @click="$emit('send_url',pokemon.ability.url)">
                    <strong>{{ pokemon.ability.name }}</strong>
                  </div>
              
                </div>
              </v-timeline-item>
            </v-timeline>
          </v-card-text>
        </v-card>
      </v-row>
    </v-container>
      </div>
      
    </div>
</template>



<script>
export default{
    props: {
        pokemon_info: [],
    },

    data(){
        return{
       
        }
    }
}


</script>



<style scoped>
.static{
    position: fixed;
}
.pointer{
    cursor: pointer;
}
.banner-pk{
    
}
</style>