<template>
    <v-app id="bodyblue">
    <header id="header">
      <div class="container" id="home">
        <div class="col-12 text-center">
          <div class="tm-page-header">
          <i class="fas fa-4x fa-chart-bar mr-4"></i>
          <h1 class="d-inline-block text-uppercase">DSCVER</h1>
          </div>
        </div>
      </div>
    </header>

    <!-- Video Banner -->

    <div class="mt-5 pt-5" id="bienvenidausuario">
      <div>
       <form class="text-center offset-lg-5 offset-3 col-lg-2 col-6" v-on:submit.prevent>
        <div class="form-group">
            <label>Cómo es tu nombre, queride fan de la música</label>
            <input class="form-control" type ="text" v-model="nombre"/>
          </div>
          <div class="form-group">
            <label>Cuál es tu genero musical favorito?</label>
            <input class="form-control" type ="text" v-model="generomusical" @keyup.13="agregar"/>
          </div>
				</form>
        <p class="bienvenidauser text-center">{{texto}} {{ nombre }}, fan de la música {{generomusical}}</p>

        </div>

    <section class="tm-banner-section" id="tmVideoSection">
      <div class="container tm-banner-text-container">
        <div class="row">
          <div class="col-12">
            <header>
              <h2 class="tm-banner-title">Dscver nuevos sonidos<br/> que te inspiren.</h2>
              <p class="mx-auto tm-banner-subtitle">
                Encontrá nuevos artistas y musicalizá tu día con las mejores canciones del momento!
              </p>
            </header>
          </div>
        </div>
      </div>

      <!-- Video -->
      <video id="hero-vid" autoplay="" loop="" muted>
        <source src="videos/city-night-blur-01.mp4" type="video/mp4" />
        Your browser does not support the video tag.
      </video>
    </section>


    </div>
    

  <section class="anotador text-center my-4 col-md-8 offset-md-2">
	<div>
    <h2>Anotador personal</h2>
    <p>Anota los artistas o canciones que tenés que escuchar para que no se te olviden</p>
    <p>Recuerda clickear los que ya escuchaste para identificar cuales te faltan</p>
		<form v-on:submit.prevent>
        <v-text-field
        label="Ingresa artista o canción aquí"
        v-model="mensaje"
        hide-details="auto"
        @keyup.13="agregar"
        class="mx-auto d-inline"
      ></v-text-field>
		</form>
		<div class="error" :class="verificar ? 'classBien' : 'classError'">
			<p>No puede quedar vacío</p> 
		</div>
			
		<ul> 
			<li v-for="(item, index) in lista" :key="index" :class="item.css" >
					<span @click="toggle(index)">{{item.mensaje}}</span>
          <button class="float-right mr-4" @click="borrar(index)">Borrar</button>
    </li>
		</ul>
	
		<p> Total de artistas anotados: {{total}}</p>
		<p> Artistas que ya escuché : {{sumarTerminadas}}</p>
	</div>
  </section>
    
    <section class="container mt-5 pt-5" id="recogenero">    

    <v-parallax
      dark
      src="img/collage.jpg"
      height="300"
          >
      <div class="negrotransparente d-flex flex-grow-1">
      <v-row
        align="center"
        justify="center"
      >
        <v-col
          class="text-center"
          cols="12"
        >

            <h2>Recomendaciones por género</h2>
            <p>Clickea el género que estés buscando y empezá tu búsqueda del tesoro</p>
        </v-col>
      </v-row>
      </div>
    </v-parallax>

      <div id="contenedor" v-cloak class="row mt-4">

        <div class="col-12 text-center checkboxes">
          <label :class="booleanos.jbooleano ? 'text-success' : 'text-secondary'">Jazz
            <input type="checkbox" v-model="booleanos.jbooleano" />
          </label>
          <label :class="booleanos.fbooleano ? 'text-success' : 'text-secondary'">Funk
            <input type="checkbox" v-model="booleanos.fbooleano" />
          </label>
          <label :class="booleanos.rbooleano ? 'text-success' : 'text-secondary'">Rock
            <input type="checkbox" v-model="booleanos.rbooleano" />
          </label>
          <label :class="booleanos.pbooleano ? 'text-success' : 'text-secondary'">Pop
            <input type="checkbox" v-model="booleanos.pbooleano" />
          </label>
          <label :class="booleanos.ibooleano ? 'text-success' : 'text-secondary'">Indie
            <input type="checkbox" v-model="booleanos.ibooleano" />
          </label>
          <label :class="booleanos.ebooleano ? 'text-success' : 'text-secondary'">EDM
            <input type="checkbox" v-model="booleanos.ebooleano" />
          </label>
          <label :class="booleanos.hbooleano ? 'text-success' : 'text-secondary'">Hip-Hop
            <input type="checkbox" v-model="booleanos.hbooleano" />
          </label>
        </div>

        <div class="col-lg-10 offset-lg-1 text-light">

          <div v-if="booleanos.jbooleano" class="row justify-content-around">
          <h2 class="d-flex col-12 justify-content-center py-3">Jazz</h2>
          <div v-bind:key=item.alt v-for="item of jazz" class="tm-activity-block col-md-3 justify-content-center">
            <div class="row">
            <div class="col-8 offset-2 justify-content-center py-3">
              <img class="img-fluid" v-bind:src="item.portada" alt="item.alt"/>
            </div>
               
                <h3 class="tm-text-blue row justify-content-center mt-3">{{item.nombre}}</h3>
                <p class="mb-3 mt-5 mx-5">
                  Canciones:
                </p>                  
                <ul v-bind:key=x v-for="x of item.canciones" class="list-unstyled justify-content-between mx-3"> 
                  <li class="d-inline">{{x.cancion}} </li>
                  <a class="d-inline ml-2" v-bind:href="x.cancionlink" target="_blank"><img src="img/youtube.png"></a>
                </ul>             
            </div>                
            </div>
          </div>

          <div v-if="booleanos.fbooleano" class="row justify-content-around">
          <h2 class="d-flex col-12 justify-content-center py-3">Funk</h2>
          <div v-bind:key=item.alt v-for="item of funk" class="tm-activity-block col-md-3 justify-content-center">
            <div class="row">
            <div class="col-8 offset-2 justify-content-center py-3">
              <img class="img-fluid" v-bind:src="item.portada" alt="item.alt"/>
            </div>
               
                <h3 class="tm-text-blue row justify-content-center mt-3">{{item.nombre}}</h3>
                <p class="mb-3 mt-5 mx-5">
                  Canciones:
                </p>                  
                <ul v-bind:key=x v-for="x of item.canciones" class="list-unstyled justify-content-between mx-3"> 
                  <li class="d-inline">{{x.cancion}} </li>
                  <a class="d-inline ml-2" v-bind:href="x.cancionlink" target="_blank"><img src="img/youtube.png"></a>
                </ul>             
            </div>                
            </div>
          </div>

          <div v-if="booleanos.rbooleano" class="row justify-content-around">
          <h2 class="d-flex col-12 justify-content-center py-3">Rock</h2>
          <div v-bind:key=item.alt v-for="item of rock" class="tm-activity-block col-md-3 justify-content-center">
            <div class="row">
            <div class="col-8 offset-2 justify-content-center py-3">
              <img class="img-fluid" v-bind:src="item.portada" alt="item.alt"/>
            </div>
               
                <h3 class="tm-text-blue row justify-content-center mt-3">{{item.nombre}}</h3>
                <p class="mb-3 mt-5 mx-5">
                  Canciones:
                </p>                  
                <ul v-bind:key=x v-for="x of item.canciones" class="list-unstyled justify-content-between mx-3"> 
                  <li class="d-inline">{{x.cancion}} </li>
                  <a class="d-inline ml-2" v-bind:href="x.cancionlink" target="_blank"><img src="img/youtube.png"></a>
                </ul>             
            </div>                
            </div>
          </div>

          <div v-if="booleanos.pbooleano" class="row justify-content-around">
          <h2 class="d-flex col-12 justify-content-center py-3">Pop</h2>
          <div v-bind:key=item.alt v-for="item of pop" class="tm-activity-block col-md-3 justify-content-center">
            <div class="row">
            <div class="col-8 offset-2 justify-content-center py-3">
              <img class="img-fluid" v-bind:src="item.portada" alt="item.alt"/>
            </div>
               
                <h3 class="tm-text-blue row justify-content-center mt-3">{{item.nombre}}</h3>
                <p class="mb-3 mt-5 mx-5">
                  Canciones:
                </p>                  
                <ul v-bind:key=x v-for="x of item.canciones" class="list-unstyled justify-content-between mx-3"> 
                  <li class="d-inline">{{x.cancion}} </li>
                  <a class="d-inline ml-2" v-bind:href="x.cancionlink" target="_blank"><img src="img/youtube.png"></a>
                </ul>             
            </div>                
            </div>
          </div>

          <div v-if="booleanos.ibooleano" class="row justify-content-around">
          <h2 class="d-flex col-12 justify-content-center py-3">Indie</h2>
          <div v-bind:key=item.alt v-for="item of indie" class="tm-activity-block col-md-3 justify-content-center">
            <div class="row">
            <div class="col-8 offset-2 justify-content-center py-3">
              <img class="img-fluid" v-bind:src="item.portada" alt="item.alt"/>
            </div>
               
                <h3 class="tm-text-blue row justify-content-center mt-3">{{item.nombre}}</h3>
                <p class="mb-3 mt-5 mx-5">
                  Canciones:
                </p>                  
                <ul v-bind:key=x v-for="x of item.canciones" class="list-unstyled justify-content-between mx-3"> 
                  <li class="d-inline">{{x.cancion}} </li>
                  <a class="d-inline ml-2" v-bind:href="x.cancionlink" target="_blank"><img src="img/youtube.png"></a>
                </ul>             
            </div>                
            </div>
          </div>

          <div v-if="booleanos.ebooleano" class="row justify-content-around">
          <h2 class="d-flex col-12 justify-content-center py-3">EDM</h2>
          <div v-bind:key=item.alt v-for="item of edm" class="tm-activity-block col-md-3 justify-content-center">
            <div class="row">
            <div class="col-8 offset-2 justify-content-center py-3">
              <img class="img-fluid" v-bind:src="item.portada" alt="item.alt"/>
            </div>
               
                <h3 class="tm-text-blue row justify-content-center mt-3">{{item.nombre}}</h3>
                <p class="mb-3 mt-5 mx-5">
                  Canciones:
                </p>                  
                <ul v-bind:key=x v-for="x of item.canciones" class="list-unstyled justify-content-between mx-3"> 
                  <li class="d-inline">{{x.cancion}} </li>
                  <a class="d-inline ml-2" v-bind:href="x.cancionlink" target="_blank"><img src="img/youtube.png"></a>
                </ul>             
            </div>                
            </div>
          </div>

          <div v-if="booleanos.hbooleano" class="row justify-content-around">
          <h2 class="d-flex col-12 justify-content-center py-3">Hip-Hop</h2>
          <div v-bind:key=item.alt v-for="item of hiphop" class="tm-activity-block col-md-3 justify-content-center">
            <div class="row">
            <div class="col-8 offset-2 justify-content-center py-3">
              <img class="img-fluid" v-bind:src="item.portada" alt="item.alt"/>
            </div>
               
                <h3 class="tm-text-blue row justify-content-center mt-3">{{item.nombre}}</h3>
                <p class="mb-3 mt-5 mx-5">
                  Canciones:
                </p>                  
                <ul v-bind:key=x v-for="x of item.canciones" class="list-unstyled justify-content-between mx-3"> 
                  <li class="d-inline">{{x.cancion}} </li>
                  <a class="d-inline ml-2" v-bind:href="x.cancionlink" target="_blank"><img src="img/youtube.png"></a>
                </ul>             
            </div>                
            </div>
          </div>

      </div>
    </div>
  </section>
  </v-app>
</template>

<script>
export default {
    name: 'HelloWorld',
    data: function() {
return {
			mensaje:"",
			lista:[],	
			verificar:true,
			total:0,
			sumarTerminadas:0,
      nombre: "user",
      texto:"Bienvenide",
      generomusical:"",
      booleanos: [
        {jbooleano: false},
        {fbooleano: false},
        {rbooleano: false},
        {pbooleano: false},
        {ibooleano: false},
        {ebooleano: false},
        {hbooleano: false},
        ],
		jazz:[
				{nombre: "Jacob Collier", actividad: "2011 - Actualidad", portada:"img/JacobCollier.png", alt:"Jacob tocando el piano",
				canciones:[ 
					{cancion:"Human Nature", cancionlink: "https://www.youtube.com/watch?v=kIjExHdnx2E&ab_channel=QuincyJones"},
					{cancion: "Hideaway", cancionlink: "https://www.youtube.com/watch?v=4v3zyPEy-Po&ab_channel=JacobCollier"},
          {cancion: "You and I", cancionlink: "https://www.youtube.com/watch?v=cAoqM6YICMM&ab_channel=TavisSmiley"},                   
					]
				},

                {nombre: "Esperanza Spalding", actividad: "2011 - Actualidad", portada:"img/EsperanzaSpalding.png", alt:"Esperanza tocando el contrabajo",
				canciones:[ 
					{cancion:" On The Sunny Side Of The Street", cancionlink: "https://www.youtube.com/watch?v=kIjExHdnx2E&ab_channel=QuincyJones"},
					{cancion: "The Blues", cancionlink: "https://www.youtube.com/watch?v=p6ORkLQkaSk&ab_channel=RobertGlasper"},
                    {cancion: "Tiny Desk Concert", cancionlink: "https://www.youtube.com/watch?v=sBZa7-2bG2I&ab_channel=muzlinemuzline"},                   
					]
				},

                {nombre: "Snarky Puppies", actividad: "2011 - Actualidad", portada:"img/SnarkyPuppies.png", alt:"Esperanza tocando el contrabajo",
				canciones:[ 
					{cancion:"Lingus (We Like It Here)", cancionlink: "https://www.youtube.com/watch?v=L_XJ_s5IsQc&ab_channel=GroundUPMusicNYC"},
					{cancion: "Bad Kids to The Back", cancionlink: "https://www.youtube.com/watch?v=fEHpq-BxFm4&ab_channel=GroundUPMusicNYC"},
                    {cancion: "Tio Macaco", cancionlink: "https://www.youtube.com/watch?v=y0bcTSDFScg&ab_channel=GroundUPMusicNYC"},                   
					]
				},

			],

            funk:[
				{nombre: "Vulfpeck", actividad: "2011 - Actualidad", portada:"img/Vulfpeck.png", alt:"Jacob tocando el piano",
				canciones:[ 
					{cancion:"1612", cancionlink: "https://www.youtube.com/watch?v=jRHQPG1xd9o&ab_channel=GroundUPMusicNYCGroundUPMusicNYC"},
					{cancion: "Cory Wong", cancionlink: "https://www.youtube.com/watch?v=AWBUnr0F3Zo"},
                    {cancion: "Dean Town", cancionlink: "https://www.youtube.com/watch?v=le0BLAEO93g&ab_channel=Vulf"},                   
					]
				},

                {nombre: "Scary Pockets", actividad: "2011 - Actualidad", portada:"img/ScaryPockets.png", alt:"Esperanza tocando el contrabajo",
				canciones:[ 
					{cancion:"I Want It That Way", cancionlink: "https://www.youtube.com/watch?v=VZAJMBFq85s&ab_channel=ScaryPockets"},
					{cancion: "Wonderwall", cancionlink: "https://www.youtube.com/watch?v=jftpg_6SUYk&ab_channel=ScaryPockets"},
                    {cancion: "Hey Jude", cancionlink: "https://www.youtube.com/watch?v=HSSO_mqPBCI&ab_channel=ScaryPockets"},                   
					]
				},

                {nombre: "Lettuce", actividad: "2011 - Actualidad", portada:"img/Lettuce.png", alt:"Esperanza tocando el contrabajo",
				canciones:[ 
					{cancion:"Phyllis", cancionlink: "https://www.youtube.com/watch?v=iZaPW_L21WU&ab_channel=WorldCafe"},
					{cancion: "The Force", cancionlink: "https://www.youtube.com/watch?v=EbAHpA-H17w&ab_channel=Lettuce"},
                    {cancion: "Royal Higness", cancionlink: "https://www.youtube.com/watch?v=AG3K6cgNKtg&ab_channel=Lettuce"},                   
					]
				},

			],

            rock:[
				{nombre: "Parcels", actividad: "2014 - Actualidad", portada:"img/Parcels.png", alt:"Jacob tocando el piano",
				canciones:[ 
					{cancion:"Overnight", cancionlink: "https://www.youtube.com/watch?v=BTdBc2Ba8ts"},
					{cancion: "Gamesofluck", cancionlink: "https://www.youtube.com/watch?v=O8mqObs7gv0&ab_channel=ParcelsParcelsCanaloficialdelartista"},
                    {cancion: "Lightenup", cancionlink: "https://www.youtube.com/watch?v=JQz5l55qtsY&ab_channel=ParcelsParcelsCanaloficialdelartista"},                   
					]
				},

                {nombre: "Sam Fender", actividad: "2011 - Actualidad", portada:"img/SamFender.png", alt:"Esperanza tocando el contrabajo",
				canciones:[ 
					{cancion:"Will We Talk?", cancionlink: "https://www.youtube.com/watch?v=b_0oCxfL9cM&ab_channel=SamFenderSamFenderCanaloficialdelartista"},
					{cancion: "Hypersonic Missiles", cancionlink: "https://www.youtube.com/watch?v=CDsFKOrLWhU&ab_channel=SamFenderSamFenderCanaloficialdelartista"},
                    {cancion: "The Borders", cancionlink: "https://www.youtube.com/watch?v=j2EKkWl7K1A&ab_channel=SamFenderSamFenderCanaloficialdelartista"},                   
					]
				},

                {nombre: "Foo Fighters", actividad: "1994 - Actualidad", portada:"img/FooFighters.png", alt:"Esperanza tocando el contrabajo",
				canciones:[ 
					{cancion:"The Pretender", cancionlink: "https://www.youtube.com/watch?v=SBjQ9tuuTJQ&ab_channel=FooFightersFooFightersVerificada"},
					{cancion: "Learn To Fly", cancionlink: "https://www.youtube.com/watch?v=1VQ_3sBZEm0&ab_channel=FooFightersFooFightersCanaloficialdelartista"},
                    {cancion: "Big Me", cancionlink: "https://www.youtube.com/watch?v=pLdJQFTnZfA&ab_channel=FooFightersFooFightersCanaloficialdelartista"},                   
					]
				},

			],
			pop:[
				{nombre:"Pol Granch", actividad:"2018 - Actualidad", portada:"img/PolGranch.png", alt:"Pol Granch",
				canciones:[ 
					{cancion:"Chocolatito", cancionlink:"https://youtu.be/dt3YXEmrb2c"},
					{cancion:"Late", cancionlink:"https://youtu.be/pOFMP1Ub6ic"},
                    {cancion:"Héroïne", cancionlink:"https://youtu.be/idZCrMRHnh8"},                   
					]
				},
				{nombre:"FINNEAS", actividad:"2016 - Actualidad", portada:"img/FINNEAS.png", alt:"FINNEAS",
				canciones:[ 
					{cancion:"Angel", cancionlink:"https://youtu.be/rEJtaPBITZw"},
					{cancion:"Hollywood Forever", cancionlink:"https://youtu.be/26c0iCROJvk"},
                    {cancion:"College", cancionlink:"https://youtu.be/rjaovl0zrqM"},                   
					]
				},
				{nombre:"Harry Styles", actividad: "2017 - Actualidad", portada:"img/HarryStyles.png", alt:"Harry Styles",
				canciones:[ 
					{cancion:"She", cancionlink:"https://youtu.be/zQ3PeDGswz4"},
					{cancion:"Sign of the Times", cancionlink:"https://youtu.be/qN4ooNx77u0"},
                    {cancion:"Only Angel", cancionlink:"https://youtu.be/QbShJru2WFc"},                   
					]
				},
			],
			indie:[
				{nombre:"Wallows", actividad: "2017 - Actualidad", portada:"img/Wallows.png", alt:"Wallows",
				canciones:[ 
					{cancion:"Are You Bored Yet?", cancionlink:"https://youtu.be/wIgmyE5Juzw"},
					{cancion:"Remember When", cancionlink:"https://youtu.be/lom6I3EgynY"},
                    {cancion:"These Days", cancionlink:"https://youtu.be/pgWZQr7r0l0"},                   
					]
				},
				{nombre:"Dayglow", actividad:"2018 - Actualidad", portada:"img/Dayglow.png", alt:"Dayglow",
				canciones:[ 
					{cancion:"Can I Call You Tonight?", cancionlink:"https://youtu.be/hh1WeQxfCX0"},
					{cancion:"Hot Rod", cancionlink:"https://youtu.be/tsJXoqvmgzM"},
                    {cancion:"Close to You", cancionlink:"https://youtu.be/otPB54Wxf5c"},                   
					]
				},
				{nombre:"Seafret", actividad:"2017 - Actualidad", portada:"img/Seafret.png", alt:"Seafret",
				canciones:[ 
					{cancion:"Oceans", cancionlink:"https://youtu.be/aqsL0QQaSP4"},
					{cancion:"Atlantis", cancionlink:"https://youtu.be/gVAy3IZiL0s"},
                    {cancion:"Wildfire", cancionlink:"https://youtu.be/cTfHUbffjr0"},                   
					]
				},
			],
			edm:[
				{nombre:"Skrillex", actividad: "2004 - Actualidad", portada:"img/Skrillex.png", alt:"Skrillex",
				canciones:[ 
					{cancion:"Would You Ever", cancionlink:"https://youtu.be/r-SurvChGFk"},
					{cancion:"Ease My Mind", cancionlink:"https://youtu.be/hwsXo6fsmso"},
                    {cancion:"Red Lips", cancionlink:"https://youtu.be/qI1ondD4FGU"},                   
					]
				},
				{nombre:"Don Diablo", actividad:"1997 - Actualidad", portada:"img/DonDiablo.png", alt:"Don Diablo",
				canciones:[ 
					{cancion:"Cutting Shapes", cancionlink: "https://youtu.be/Oy9V_4im0wg"},
					{cancion:"On My Mind", cancionlink:"https://youtu.be/r6E3J4GPpjc"},
                    {cancion:"Bad", cancionlink:"https://youtu.be/gYJg2ISYMbc"},                   
					]
				},
				{nombre:"Alesso", actividad:"2010 - Actualidad", portada:"img/Alesso.png", alt:"Alesso",
				canciones:[ 
					{cancion:"I Wanna Know", cancionlink:"https://youtu.be/TnSfwONWlk8"},
					{cancion:"REMEDY", cancionlink:"https://youtu.be/vB67ddBhO1c"},
                    {cancion:"Heroes", cancionlink:"https://youtu.be/a7SouU3ECpU"},                   
					]
				},
			],
			hiphop:[
				{nombre:"Travis Scott", actividad: "2012 - Actualidad", portada:"img/TravisScott.png", alt:"Travis Scott",
				canciones:[ 
					{cancion:"HIGHEST IN THE ROOM", cancionlink:"https://youtu.be/tfSS1e3kYeo"},
					{cancion:"goosebumps", cancionlink:"https://youtu.be/Dst9gZkq1a8"},
                    {cancion:"SICKO MODE", cancionlink:"https://youtu.be/6ONRf7h3Mdk"},                   
					]
				},
				{nombre:"J. Cole", actividad:"2007 - Actualidad", portada:"img/JCole.png", alt:"J. Cole",
				canciones:[ 
					{cancion:"No Role Modelz", cancionlink: "https://youtu.be/LR6ybr-BQYY"},
					{cancion:"MIDDLE CHILD", cancionlink:"https://youtu.be/WILNIXZr2oc"},
                    {cancion:"Wet Dreamz", cancionlink:"https://youtu.be/eCGV26aj-mM"},                   
					]
				},
				{nombre:"Joey Badass", actividad:"2010 - Actualidad", portada:"img/JoeyBadass.png", alt:"Joey Badass",
				canciones:[ 
					{cancion:'"Land of the Free"', cancionlink:"https://youtu.be/TeQW-9Cg8qs"},
					{cancion:"Christ Conscious", cancionlink:"https://youtu.be/yRfQGXFRr30"},
                    {cancion:'"Devastated"', cancionlink:"https://youtu.be/RLnA25dVzrQ"},                   
					]
				}
      ]
};
},
	methods:{
			agregar:function(){
				if(this.mensaje ==""){
					this.verificar = false
				}else{
					this.verificar = true
				this.lista.push({
					mensaje: this.mensaje,
          css: 'pendientes',
				});
				this.mensaje="";
				this.total= this.lista.length;
				}
			},
			toggle:function(index){
				if(this.lista[index].css == "pendientes"){
					this.sumarTerminadas ++;
          this.lista[index].css = 'escuchados'
          }else{
          this.sumarTerminadas --;
          this.lista[index].css = 'pendientes'
          }
      },
      borrar:function(index){
				if(this.lista[index].css == 'escuchados'){
					this.sumarTerminadas --;
				}
				this.lista.splice(index,1)
				this.total --;
			},
}}
</script>