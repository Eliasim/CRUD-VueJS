<template>
  <form class="flex justify-center text-center pt-5">
      <div class="bg-gray-400 m-10 p-3 rounded-md">
        <label class="text-4xl font-mono text-white" for="Nombre" id="Nombre">Nombre</label><br><br>
        <input class="bg-gray-100" type="text" id="inNombre" name="inNombre" v-model="nombre" onkeypress="return event.charCode != 32">
      </div>
    
      <div class="bg-gray-400 m-10 p-3 rounded-md">
        <label class="text-4xl font-mono text-white" for="Fecha" id="Fecha">Fecha de Nacimiento</label><br><br>
        <input class="bg-gray-100" type="date" id="inFecha" name="inFecha" v-model="fecha">
      </div>
    
      <div class="bg-gray-400 m-10 p-3 rounded-md">
        <label class="text-4xl font-mono text-white" for="Telefono" id="Telefono">Telefono</label><br><br>
        <input class="bg-gray-100" type="text" maxlength="10" id="inTelefono" name="inTelefono" v-model="telefono" onkeypress="return (event.charCode >= 48 && event.charCode <= 57)" >
      </div>
    
      <div class="bg-gray-400 m-10 p-3 rounded-md">
        <label class="text-4xl font-mono text-white" for="Edad" id="Edad">Edad</label><br><br>
        <input class="bg-gray-100" type="text" maxlength="2" id="inEdad" name="inEdad" v-model="edad" onkeypress="return (event.charCode >= 48 && event.charCode <= 57)">
      </div>
    
      <div class="bg-gray-400 m-10 p-3 rounded-md">
        <label class="text-4xl font-mono text-white" for="Trabajo" id="Trabajo">Trabajo</label><br><br>
        <select class="bg-gray-100" name="inTrabajo" id="inTrabajo" v-model="trabajo">
          <option value="Front-end">Front-end</option>
          <option value="Back-end">Back-end</option>
          <option value="Full Stack">Full Stack</option>
          <option value="Scrum Master">Scrum Master</option>
          <option value="Data Base Admin">Data Base Admin</option>
          <option value="UI">UI</option>
          <option value="UX">UX</option>
        </select>
    </div> 
  </form>

  <div class="flex justify-center pt-4">
    <button class="font-mono rounded-md bg-gray-300 p-1 mb-6" @click="guardar()">Guardar</button>
  </div>

  <div class="flex justify-center" name="tabla">
    <table id="Listado" class="table-auto  m-5">
      <thead>
        <tr>
          <th class="text-xl font-mono bg-gray-300 m-5 p-5 rounded-tl-lg rounded-bl-lg " for="Nombre">Nombre</th>   
                    <th class="text-xl font-mono bg-gray-300 m-5 p-5" for="Fecha">Fecha de Nacimiento</th>  
                    <th class="text-xl font-mono bg-gray-300 m-5 p-5" for="Telefono">Telefono</th>    
                    <th class="text-xl font-mono bg-gray-300 m-5 p-5" for="Edad">Edad</th>    
                    <th class="text-xl font-mono bg-gray-300 m-5 p-5" for="Trabajo">Trabajo</th>            
                    <th class="text-xl font-mono bg-gray-300 m-5 p-5 rounded-tr-lg rounded-br-lg" for="Acciones">Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr class="text-center border border-gray-200 mb-4 uppercase" v-for="(persona, index) in listaPersonas" :key="persona.nombre">
          <td>{{persona.nombre}}</td>
          <td>{{persona.fecha}}</td>
          <td>{{persona.telefono}}</td>
          <td>{{persona.edad}}</td>
          <td>{{persona.trabajo}}</td>
          <td>
            <button class="rounded-md bg-gray-300 p-1 mx-2 my-1" @click="editar(index)">Editar</button>
            <button class="rounded-md bg-gray-300 p-1 mx-2 my-1" @click="eliminar(index)">Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>


export default {
name: 'HomeView',
components: {
},
data(){
  return{
    indice: -1,
    nombre: '',
    fecha: '',
    telefono: '',
    edad: '',
    trabajo: '',
    listaPersonas:[],
    
  }
},
methods:{
  limpiar(){
    this.nombre = '',
    this.fecha = '',
    this.edad = '',
    this.telefono = '',
    this.trabajo = ''
  },
  guardar(){
    var persona = {
      nombre:this.nombre, 
      fecha:this.fecha, 
      telefono:this.telefono, 
      edad:this.edad, 
      trabajo:this.trabajo
    }
    if(this.indice == -1){
    
    this.listaPersonas.push(persona)
    }
    else
    {
      this.listaPersonas[this.indice] = persona
    }
    this.limpiar()
    console.log(this.listaPersonas);
  },
  eliminar(index){
    this.listaPersonas.splice(index,1)
    console.log(this.listaPersonas);
  },
  editar(index){
    var persona = this.listaPersonas[index]
    this.indice = index
    this.nombre = persona.nombre
    this.fecha = persona.fecha
    this.edad = persona.edad
    this.telefono = persona.telefono
    this.trabajo = persona.trabajo
  }
},

  
}
</script>
