<template>

 <v-app>
    <v-navigation-drawer
      v-model="drawer"
        app>
      <v-list>
        <v-list-item links 
          v-for="item in items"
          :key="item.titulo"
          :to="item.path">
          <v-list-item-action>
            <v-icon>mdi-{{item.icono }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title> {{ item.titulo }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    
    <v-app-bar class="primary" app>
     <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>DSCVR</v-toolbar-title>
    </v-app-bar>
    <v-main>
      <v-container fluid>        
      
         <transition mode="out-in" enter-active-class="animate__animated animate__fadeInLeft">
          <router-view></router-view>
        </transition>

      </v-container>

    </v-main> 

  </v-app>

</template>

<script>


export default {
  name: 'App',
 

  data: () => ({
     items:[
        {
         titulo: 'Home',
         icono: 'home',
         path:'/'
       },
         {
         titulo: 'Agregar Favoritos',
         icono:'heart',
         path:'/Favs'
       },
         {
          titulo:'Recomendaciones',
          icono:'format-list-checkbox',
          path:'/Reco'
        }
        ],
    juegos:[],

    drawer: null,
    group: null,
    
  }),

  mounted(){
      fetch("http://vueprueba.000webhostapp.com/api/api.php")
          .then(response => response.json())
          .then(response => {
            this.juegos = response;
            console.log(response)
          localStorage.setItem("dato",JSON.stringify(this.juegos))
          })
          .catch( err => console.error(err));


  }
};
</script>
