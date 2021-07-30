<template>
  <div id="task">
    <div class="grupo">
      <form @submit.prevent="addItem"><input
          type="text"
          placeholder="Tarefa de hoje?"
          v-model="tarefa"
        >
        <button type="submit">Adicionar</button>
      </form>

      <Item :lista="tarefas" />

      <span v-show="tarefas.length > 0">
        Voce tem <strong :class="{pend: pendente}">{{tarefas.length}}</strong> tarefas pendentes.
      </span>

    </div>
  </div>
</template>

<script>
import Item from './Item'
export default {
  name: 'Task',
  components: {
    Item
  },
  data () {
    return {
      tarefa: '',
      tarefas: [],
      pendente: false,
    }

  },
  methods: {
    addItem () {
      if (this.tarefa !== '') {
        this.tarefas.push({
          text: this.tarefa,
          key: Date.now(),
        })
      } else {
        alert('Digite alguma tarefa!')
        return;
      }
      this.tarefa = '';
    }
  },
  watch: {
    tarefas () {
      localStorage.setItem('tasks', JSON.stringify(this.tarefas))
      this.tarefas.length > 4 ? this.pendente = true : this.pendente = false
    }
  },
  created () {
    const json = localStorage.getItem('tasks');
    this.tarefas = JSON.parse(json) || []
  },

}

</script>

<style scoped>
#task {
  display: flex;
  width: 100%;
  justify-content: center;
}
.grupo {
  width: 700px;
  background: #fff;
  border-radius: 4px;
  padding: 20px;
  margin: 20px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
}
form {
  margin-top: 30px;
  display: flex;
  flex-direction: row;
}
form button {
  cursor: pointer;
  background: #0f5959;
  border-radius: 4px;
  margin-left: 10px;
  padding: 0 15px;
  justify-content: center;
  align-items: center;
  color: white;
}

input {
  flex: 1;
  border: 1px solid #eee;
  padding: 6px 10px;
  border-radius: 4px;
  font-size: 14px;
  outline: none;
}
.pend {
  color: red;
}
</style>