<template>
     
     <div class="container">
  
  <div class="row">
    <div class="col-md-12">
      <div class="border-radius">
     <v-spacer></v-spacer>
      <table class="table text-center">   
        
        <thead>
          <tr>
            <th>Id</th>
            <th>Nombre</th>
            <th>Siglas</th>
            <th>Status</th>
            <th>Editar</th>
            <th>Eliminar</th>
           
          </tr>
        </thead>
        <tbody>
          <tr v-for="(persona, index) in arrayPersonas" :key="persona.id"> 
             <td v-text="persona.id"></td>
            <td v-text="persona.nombre"></td> 
            <td v-text="persona.siglas"></td> 
            <td v-text="persona.status"></td>

            <td><a href="#editar" @click="editar(index)"><i class="material-icons">edit</i></a></td>
            
            <td><a href="#eliminar" @click="eliminar(persona)"><i class="material-icons">delete</i></a></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
 </div>

 <template>
 
  <v-row justify="center">
    <v-dialog
      v-model="dialog"
      persistent
      max-width="600px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
        >
          Crear
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="text-h5"></span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Id*"
                  required
                  v-model="id"
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >

              <v-text-field
                  label="Nombre*"
                  required
                  v-model="nombre"
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >

              <v-text-field
                  label="Siglas*"
                  required
                  v-model="siglas"
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >

              
              <v-text-field
                  label=" Status*"
                  class="number"
                  v-model="status"
                ></v-text-field>
              </v-col>
              <v-col
              cols="12"
                sm="6"
                md="4"
              >  
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog=close"
          >
            Close
          </v-btn>
          
          <v-btn
           color="primary"
           dark
            class="btn btn-success"
            @click="Guardar(persona)" 
          >
            Save
          </v-btn>

         
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>
</div>
   </template>
  
     
  
<script>
export default {
  name: 'app',
  data () {
    return {
      indice: -1,
      arrayPersonas:[],
      id:"",
      nombre : "",
      siglas:"",
      status:"",
      
      
    }
  },
  methods:{
    Guardar(){
      var persona = {id:this.id, nombre:this.nombre, siglas:this.siglas, status:this.status} 
      this.arrayPersonas.push(persona);

      
      this.id = "",
      this.nombre = "";
      this.siglas = "";
      this.status = "";
     
    },
   eliminar(index)
   {
    if(!confirm ('desea eliminar este registro')) return;
    this.arrayPersonas.splice(index, 1)
   },
   editar(index) {
    var persona = this.arrayPersonas[index];
    this.indice = index;
    this.id = persona.id;
    this.nombre = persona.nombre;
    this.siglas = persona.siglas;
    this.status = persona.status;
   }
  }
}
</script>
