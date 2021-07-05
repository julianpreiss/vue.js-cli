<template>
    <section id="misfavoritos" class="container mt-5 pt-5 col-md-10 offset-md-1">
      <div class="row">
        <div id="favoritos" v-cloak class="col-lg-12" >

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
          <h2 class="text-center">Agrega a tus artistas favoritos</h2>
        </v-col>
      </v-row>
      </div>
    </v-parallax>

<div class="form mt-5">
		<form  v-on:submit.prevent="guardar" novalidate >

		<div class="form-group">
			<label class="my-2">Artista</label>
			<input type="text" v-model="artista" class="form-control mb-2" placeholder="Ingrese Artista" name="artista" required>
		</div>

		<div class="form-group">
        <label class="my-2">Te gustaría agregar las canciones que te gustan?</label>
        <textarea v-model="canciones" name="canciones" class="form-control" rows="3"></textarea>
        <small id="emailHelp" class="form-text text-muted">(opcional)</small>
    </div>

		<div class="form-group">
		<label class="my-2">Cuál es el género del artista?</label>
		<select v-model="genero" class="form-control mb-2" name="genero">
		<option>Rock</option>
		<option>Pop</option>
    <option>Funk</option>
    <option>Edm</option>
		<option>K-pop</option>
		<option>Rock</option>
    <option>Otro</option>
		</select>
	</div>

		<div class="form-group">
    <label class="my-2">En que año lo conociste?</label>
    <input type="number mb-2" v-model.number="anio" name="anio" class="form-control"  placeholder="1920 - 2021">
    </div>

		<button class="btn btn-primary my-3 text-white"  type="submit">Enviar</button>

		</form>

		<div v-if="submitted === true">
		<div v-if="hayErrores">
		<ul class="list-group">
    <li v-bind:key="x" class="error mt-2 list-group-item" v-for="x in errores" >{{x}}</li>
    </ul>
    </div>
    <div v-else class="enviado mt-4">
              <span class="alert alert-success">Enviado con éxito</span>
        </div>
 </div>

		<div v-if="this.arr.length > 0" >
			<h2 class="mt-5">Mis Artistas</h2>

			<section class="container">
				<div class="row d-flex justify-content-around">
					<ul v-bind:key="item.artista" v-for="item in arr" class="col-lg-3 border pink lighten-4 rounded m-4 list-unstyled">
						<li>Artista: {{item.artista}}</li>
            <li>Canciones: {{item.canciones}}</li> 
						<li>Genero Musical: {{item.genero}}</li>
            <li>Cuando lo descubrí: {{item.anio}}</li>
					</ul>
				</div>
			</section>
	
		</div>
		<div v-else class="classerror">
			<p>No hay datos que mostrar, empezá a cargar tus artistas!</p>
		</div>

	</div>		
	</div>
        </div>
    </section>

</template>

<script>
export default {
    name: 'Favoritos',
	data: function(){
		return {
                artista:null,
				canciones:"",
				genero:"",
				anio:null,						
				arr:[],
				errores:[],
				submitted: false,
                generos: [
                    'Rock',
                    'Pop',
                    'Funk',
                    'K-pop',
                    'Otro',                    
                    ],
		}
    },
	computed : {
    hayErrores: function(){
        return this.errores.length;
    },

    selectErrors () {
      const errors = []
      if (!this.$v.select.$dirty) return errors
      !this.$v.select.required && errors.push('Item is required')
      return errors
    },
    nameErrors () {
      const errors = []
      if (!this.$v.name.$dirty) return errors
      !this.$v.name.maxLength && errors.push('Name must be at most 10 characters long')
      !this.$v.name.required && errors.push('Name is required.')
      return errors
    },
    emailErrors () {
      const errors = []
      if (!this.$v.email.$dirty) return errors
      !this.$v.email.email && errors.push('Must be valid e-mail')
      !this.$v.email.required && errors.push('E-mail is required')
      return errors
    },
},
methods:{
	guardar:function(e){
		console.log(e)
	//validacion
    this.submitted = true;       
	this.errores = [];
        if (!this.artista) {
        this.errores.push('El Artista es obligatorio.');
       
      }
        if(!this.genero[0]){
        this.errores.push('Debe seleccionar un género.');
      }

        if (this.anio > 2021 || this.anio < 1920) {
        this.errores.push('Debes ingresar un año entre 1920 y 2021');    
    } 	
        if(this.errores.length == 0){     	 
        let nuevoObj={canciones: this.canciones,
            artista: this.artista,
            genero: this.genero,
			anio: this.anio,}
			
        if(!localStorage.artist){
			this.arr=[]
		}else{
			this.arr=JSON.parse(localStorage.getItem("artist"))
			}

		this.arr.push(nuevoObj)
		localStorage.setItem("artist",JSON.stringify(this.arr))
   }
}
},
	mounted:function(){
        this.arr=JSON.parse(localStorage.getItem("artist")) || [] 		
	
},
}
</script>




