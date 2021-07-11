<template>
  <h1>{{title}}</h1>
  <div class="form">
    <div class="form-group">
      <label>Título</label>
      <input class="form-control" type="text" v-model="nota.title">
    </div>
    <div class="form-group">
      <label>Descripción</label>
      <textarea class="form-control" type="text" v-model="nota.description"></textarea>
    </div>
    <div class="form-group">
      <label>Fecha</label>
      <input class="form-control" type="date" v-model="nota.date">
    </div>

    <button class="btn btn-primary" @click="addNota">Guardar</button>
    
  </div>

  <div class="col-sm-">
    <div class="col-sm-4 nota" :key="key" v-for=" (nota,key) in notas">
      <div class="card">
        <div class="card-block">
          <div class="card-title">{{nota.title}}</div>
          <div class="card-subtitle mb-2 text-muted">{{nota.date}}</div>
          <p class="card-text"> {{nota.description}}</p>
        </div>
        <button class="close" @click="deleteNota(key)">&times;</button>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      title: 'Gestión de Notas',
      nota:{
        title:'',
        description:'',
        date: ''
      },
      notas:[
        {
          title: 'Ir al cine',
          description: 'Examinar las películas de estreno',
          date: new Date(Date.now()).toLocaleDateString()
        }
      ]
      
    }
  },
  methods:{
    addNota(){
      let {title, description, date} = this.nota;
      this.notas.push({
        title,
        description,
        date
      });

      this.clearInput();
    },
    clearInput(){
      this.nota.title='';
      this.nota.description='';
      this.nota.date='';
    },
    deleteNota(index){
      this.notas.splice(index,1);
    }
  }
}
</script>

<style>
  .form{
    text-align: left;
  }

  .card{
    text-align: left;
    border: 1px solid #2c3e50;
    border-radius: 4px;
    padding-left: 4px;
    padding-right: 8px;
  }

  .nota{
    padding: 5px;
  }
</style>
