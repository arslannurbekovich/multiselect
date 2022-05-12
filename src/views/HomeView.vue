<template>
  <div class="container mt-5">
        <div class="row">
      <div class="col form-inline">
        <b-form-input v-model="newTask" placeholder="Добавить таск" @keyup.enter="add"></b-form-input>
        <br>
        <b-button class="ml-2" variant="primary" @click="add" >Добавить</b-button>
      </div>
    </div> 
    <div class="row mt-3">
      <div class="col-md-3">
        <div class="p-2 alert alert-secondary">
          <h3>BackLog</h3>
            <draggable class="list-group kanban" :list="arrBackLog" group="tasks">
              <div class="list-group-item" v-for="element in arrBackLog" :key="element.name">
                {{element.name}}
              </div>
            </draggable>
        </div>
      </div>

       <div class="col-md-3">
        <div class="p-2 alert alert-primary">
          <h3>Prosses</h3>
            <draggable class="list-group kanban" :list="arrInProsses" group="tasks">
              <div class="list-group-item" v-for="element in arrInProsses" :key="element.name">
                {{element.name}}
              </div>
            </draggable>
        </div>
      </div>

       <div class="col-md-3">
        <div class="p-2 alert alert-warning">
          <h3>Test</h3>
            <draggable class="list-group kanban" :list="arrTested" group="tasks">
              <div class="list-group-item" v-for="element in arrTested" :key="element.name">
                {{element.name}}
              </div>
            </draggable>
        </div>
      </div>

       <div class="col-md-3">
        <div class="p-2 alert alert-success">
          <h3>Done</h3>
            <draggable class="list-group kanban" :list="arrDone" group="tasks">
              <div class="list-group-item" v-for="element in arrDone" :key="element.name">
                {{element.name}}
              </div>
            </draggable>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
export default {
    name:"HomeView",
  components: {
    draggable
  },
    data () {
       return {
      newTask: "",
      arrBackLog: [
        {name: 'Реализовать FrontEnd'},
        {name: 'Реализовать BackEnd'},
        {name: 'Реализовать Sigm In'},
        {name: 'Создать таблицу в Postgres'},
      ],
      arrInProsses: [],
      arrTested: [],
      arrDone: [],
    };
    },
  methods: {
    add() {
      if(this.newTask) {
        this.arrBackLog.push({name:this.newTask});
        this.newTask="";
      }
    }
  }
}
</script>

<style scoped>
.kanban {
  min-height: 300px;
}
</style>
