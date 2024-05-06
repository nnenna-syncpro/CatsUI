<template>
  
  <v-container
    class="fill-height"
    fluid
    
  >
    <v-fade-transition mode="out-in">
      <v-row>
        <v-col cols="6">
          <v-card v-for="(item, i) in cats" :key="item.id">
            <v-img id="image"
              class="bg-grey-lighten-2"
              height="125"
              :src="item.url"
            ></v-img>
            <v-card-title class="text-h6">
              Cat id is {{ item.id }}
            </v-card-title>
            <v-card-text >
              Cat url is 
              <a :href="item.url">{{ item.url }}</a>
            </v-card-text>
          </v-card>
        </v-col>

      </v-row>
    </v-fade-transition>
  </v-container>

  <!-- <v-row>
    <v-col cols="12" md="4">
      <v-card title="Card title" text="...">
        <v-card-item>
          <v-img
             
              height="125"
              src="https://picsum.photos/350/165?random"
            ></v-img>
        </v-card-item>
      </v-card>
    </v-col>
  </v-row> -->
</template>

<script>
export default {
  name: 'IndexPage',
  data(){
    return{
      cats: [
      // {
      //     "id": "J2PmlIizw",
      //     "url": "https://cdn2.thecatapi.com/images/J2PmlIizw.jpg",
      //     "width": 1080,
      //     "height": 1350,
      //     "breeds":[{
      //       "id": "beng",
      //       "name": "Bengal"
      //     }]
      //   },
      //   {
      //     "id": "GAmy2bg8G",
      //     "url": "https://cdn2.thecatapi.com/images/GAmy2bg8G.jpg",
      //     "width": 750,
      //     "height": 750,
      //     "breeds":[{
      //       "id": "beng",
      //       "name": "Bengal"
      //     }]
      //   }
      ]
    }
  },

  async fetch(){
    this.cats = await fetch("http://localhost:3001/cats").then(response => response.json()).catch(function(error){console.log("Error: " + error)});
  },
 
}
</script>
