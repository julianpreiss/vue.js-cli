    <template>

  <v-app id="inspire">
      <h2 class="my-2 text-center">Playlist armadas especialmente para vos!</h2>
    <v-row class="my-2">   
    <v-card
      max-width="400"
      class="mx-auto d-inline-flex my-2"
    >  
      <v-container>
        <v-row dense>
          <v-col cols="12">
            <v-card
              color="#385F73"
              dark
            >
              <v-card-title class="text-h5">
                Recomendaciones K-pop
              </v-card-title>
  
              <v-card-subtitle>A continuación te damos las recomendaciones de k-pop del mes. También tenemos una lista especialmente armada para los fanáticos de este género</v-card-subtitle>
  
              <v-card-actions>
                <v-btn 
                text
                href="https://open.spotify.com/playlist/37i9dQZF1DX1LU4UHKqdtg"
                target="_blank" >
                  Escuchar en Sportify
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
  
          <v-col
            v-for="(item, i) in itemsk"
            :key="i"
            cols="12"
          >
            <v-card
              :color="item.color"
              dark
            >
              <div class="d-flex flex-no-wrap justify-space-between">
                <div>
                  <v-card-title
                    class="text-h5"
                    v-text="item.title"
                  ></v-card-title>
  
                  <v-card-subtitle v-text="item.artist"></v-card-subtitle>
  
                  <v-card-actions>  
                    <v-btn
                      class="ml-2 mt-5"
                      outlined
                      rounded
                      small
                      :href='item.href' 
                      target="_blank"
                    >
                      STREAM NOW
                    </v-btn>
                  </v-card-actions>
                </div>
  
                <v-avatar
                  class="ma-3"
                  size="125"
                  tile
                >
                  <v-img :src="item.src"></v-img>
                </v-avatar>
              </div>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-card>

        <v-card
      max-width="400"
      class="mx-auto d-inline-flex my-2"
    >  
      <v-container>
        <v-row dense>
          <v-col cols="12">
            <v-card
              color="#385F73"
              dark
            >
              <v-card-title class="text-h5">
                Recomendaciones Pop
              </v-card-title>
  
              <v-card-subtitle>Todo lo último del género más escuchado a nivel mundial. Agregá nuestra lista de Spotify y asegurate de no perderte lo último de en trendings.</v-card-subtitle>
  
              <v-card-actions>
                <v-btn 
                text
                href="https://open.spotify.com/playlist/37i9dQZF1DX6aTaZa0K6VA"
                target="_blank">
                Escuchar en Spotify
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
  
          <v-col
            v-for="(item, i) in itemsp"
            :key="i"
            cols="12"
          >
            <v-card
              :color="item.color"
              dark
            >
              <div class="d-flex flex-no-wrap justify-space-between">
                <div>
                  <v-card-title
                    class="text-h5"
                    v-text="item.title"
                  ></v-card-title>
  
                  <v-card-subtitle v-text="item.artist"></v-card-subtitle>
  
                  <v-card-actions>
                    <v-btn
                      v-if="item.artist === 'Ellie Goulding'"
                      class="ml-2 mt-3"
                      fab
                      icon
                      height="40px"
                      right
                      width="40px"
                    >
                      <v-icon>mdi-play</v-icon>
                    </v-btn>
  
                    <v-btn
                      v-else
                      class="ml-2 mt-5"
                      outlined
                      rounded
                      small
                      :href='item.href' 
                      target="_blank"                      
                    >
                      STREAM NOW
                    </v-btn>
                  </v-card-actions>
                </div>
  
                <v-avatar
                  class="ma-3"
                  size="125"
                  tile
                >
                  <v-img :src="item.src"></v-img>
                </v-avatar>
              </div>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-card>

            <v-card
      max-width="400"
      class="mx-auto d-inline-flex my-2"
    >  
      <v-container>
        <v-row dense>
          <v-col cols="12">
            <v-card
              color="#385F73"
              dark
            >
              <v-card-title class="text-h5">
                Recomendaciones Rock
              </v-card-title>
  
              <v-card-subtitle>Lo mejor de este icónico género que ha venido reinventandose desde los '50 hasta la era actual.</v-card-subtitle>
  
              <v-card-actions>
                <v-btn 
                text
                href="https://open.spotify.com/playlist/1UyrGwXUiAZilemyfqA3vj"
                target="_blank"
                >
                  Escuchar en Spotify
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
  
          <v-col
            v-for="(item, i) in itemsr"
            :key="i"
            cols="12"
          >
            <v-card
              :color="item.color"
              dark
            >
              <div class="d-flex flex-no-wrap justify-space-between">
                <div>
                  <v-card-title
                    class="text-h5"
                    v-text="item.title"
                  ></v-card-title>
  
                  <v-card-subtitle v-text="item.artist"></v-card-subtitle>
  
                  <v-card-actions>
                    <v-btn
                      v-if="item.artist === 'Ellie Goulding'"
                      class="ml-2 mt-3"
                      fab
                      icon
                      height="40px"
                      right
                      width="40px"
                    >
                      <v-icon>mdi-play</v-icon>
                    </v-btn>
  
                    <v-btn
                      v-else
                      class="ml-2 mt-5"
                      outlined
                      rounded
                      small
                      :href='item.href' 
                      target="_blank"
                    >
                      STREAM NOW
                    </v-btn>
                  </v-card-actions>
                </div>
  
                <v-avatar
                  class="ma-3"
                  size="125"
                  tile
                >
                  <v-img :src="item.src"></v-img>
                </v-avatar>
              </div>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
    </v-row>

</v-app>

    
</template>

  <script>
export default {
    name: 'Favoritos',
    data: () => ({
    itemsk: [
      {
        color: '#1F7087',
        src: 'img/butter.jpg',
        title: 'Butter',
        artist: 'BTS',
        href: 'https://www.youtube.com/watch?v=gdZLi9oWNZg&ab_channel=HYBELABELSHYBELABELS',
      },
      {
        color: '#952175',
        src: 'img/rose.jpg',
        title: 'On The Ground',
        artist: 'Rosé',
        href:'https://www.youtube.com/watch?v=CKZvWhCqx1s',
      },
        {
        color: '#1F7087',
        src: 'img/bigbang.jpg',
        title: 'On The Ground',
        artist: 'BIGBANG',
        href: 'https://www.youtube.com/watch?v=AAbokV76tkU&ab_channel=BLACKPINKBLACKPINKCanaloficialdelartista',
      },
    ],
    itemsp: [
      {
        color: '#1F7087',
        src: 'img/dualipa.jpg',
        title: 'Levitating',
        artist: 'Dua Lipa ft. DaBaby',
        href: 'https://www.youtube.com/watch?v=TUVcZfQe-Kw&ab_channel=DuaLipaDuaLipaCanaloficialdelartista',
      },
      {
        color: '#952175',
        src: 'img/justin.jpg',
        title: 'Peaches',
        artist: 'Justin Bieber',
        href: 'https://www.youtube.com/watch?v=tQ0yjYUFKAE&ab_channel=JustinBieberVEVO',
      },
        {
        color: '#1F7087',
        src: 'img/olivia.jpg',
        title: 'Good 4 U',
        artist: 'Olivia Rodrigo',
        href: 'https://www.youtube.com/watch?v=gNi_6U5Pm_o&ab_channel=OliviaRodrigoVEVO'
      },
    ],
        itemsr: [
      {
        color: '#1F7087',
        src: 'img/coldplay.jpg',
        title: 'Higher Power',
        artist: 'Coldplay',
        href: 'https://www.youtube.com/watch?v=3lfnR7OhZY8&ab_channel=Coldplay',
      },
      {
        color: '#952175',
        src: 'img/gretavanfleet.jpg',
        title: 'Broken Bells',
        artist: 'Greta Van Fleet',
        href: 'https://www.youtube.com/watch?v=6vjLrCqedXs&ab_channel=GretaVanFleet',
      },
        {
        color: '#1F7087',
        src: 'img/foofighters.jpg',
        title: 'Making A Fire',
        artist: 'Foo Fighters',
        href: 'https://www.youtube.com/watch?v=gfbJCzaEdps&ab_channel=foofightersVEVO'
      },
    ],
  }),
}
</script>