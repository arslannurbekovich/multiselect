<template>
<div>
  <div>
    <vue-multi-select
      v-model="values"
      emptyTabText="Роли не найдено"
      search
      searchPlaceholder="Поиск"
      :filters="filters"
      :options="optionss"
      :selectOptions="roles"/>
  </div>
  <div>
  <section>
    <ul class="page"> 
      <a href="#page">
        <li>
          Назад
        </li>
      </a>
      <a href="#page">
        <li>
          1
        </li>
      </a>
       <a href="#page" class="active">
        <li>
          2
        </li>
      </a>
       <a href="#page">
        <li>
          Вперед
        </li>
      </a>
    </ul>
  </section>
  </div>
  <div class="multiselect">
    <div class="selectBox">
      <select v-on:click="show=!show">
        <option>Select an opition</option>
      </select>
      <div class="overSelect"></div>
      <div id="checkboxes" v-show="show">
        <label for="one"><input type="checkbox" id="one"/> First checkboxes</label>
        <label for="two"><input type="checkbox" id="two"/>Second checkboxes</label>
        <label for="three"><input type="checkbox" id="three"/>Thrid checkboxes</label>
        <label for="four"><input type="checkbox" id="four"/>Four checkboxes</label>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
import vueMultiSelect from 'vue-multi-select';
import 'vue-multi-select/dist/lib/vue-multi-select.css';

export default {
  data() {
    return {
      values: [],
      roles: [{
        title: 'Выберите роли',
        elements: ['Администратор', 'Менеджер', 'Конструктор', 'Опрашиваемый пользователь'],
      }],
      filters: [{
        nameAll: 'Выбрать все',
        nameNotAll: 'Убрать все',
        func() {
          return true;
        },
      }],
      optionss: {
        multi: true,
        groups: true,
        labelList: 'elements',
        groupName: 'title',
        cssSelected: option => (option.selected ? { 'background-color': 'hotpink' } : ''),
      },
      radio: '1',
      show:false
    };
  },
  methods: {

  },
  components: {
    vueMultiSelect
  },
};
</script>
<style scoped>
section {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
.page {
  list-style: none;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  padding: 0.75rem 1rem;
  border-radius: 0.5rem;
  background-color: #E1E1E1 ;
}
.page li {
  margin: 0.25rem;
  padding: 0.75rem;
  border-radius: 0.5rem;
  color: #323232 ;
}
.page a li {
  background-color: #F2EEED ;
  border: 1px solid#ECEBEB;
}
.page a:hover li {
  border-color: hotpink;
  color: hotpink;
}
.page a.active li {
  background-color: hotpink;
  color: white;
  border-color: hotpink;
  font-weight: 600;
  box-shadow: 0 0.5rem 1rem #ff52f136;
}
a {
    text-decoration: none;
}
/* 
.multiselect {
  width: 200px;
}
.selectBox select {
  width: 100%;
  font-weight: bold;
}
.overSelect {
  position: absolute;
  left: 0; right: 0; top: 0; bottom: 0;
}
#checkboxes {
  display: none;
  border: 1px #dadada solid;
}
#checkboxes label {
  display: block;
}
#checkboxes label:hover{
  background-color: #1e90ff;
} */
</style> 