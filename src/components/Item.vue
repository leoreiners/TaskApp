<template>
  <div id="item">
    <!-- <h1>{{lista}}</h1> -->
    <ul>
      <li
        v-for="(tare, index) in lista"
        :key="index"
      >
        <span>{{tare.text}}</span>

        <button @click="concluir(index)">Concluir</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Item',
  props: ['lista'],

  methods: {
    concluir (a) {
      this.lista.splice(a, 1)
    }
  }
}
</script>

<style scoped>
#item {
  white-space: pre-wrap;
  word-wrap: break-word;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

ul li {
  padding: 18px 0;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}

span {
  color: #0d2636;
}

li:not(:first-child) {
  border-top: 1px solid #eee;
}

ul button {
  cursor: pointer;
  background: #ddd;
  color: #000;
  border: 0;
  padding: 8px 8px;
  outline: none;
  border-radius: 4px;
}
</style>


//   v-for="tare in lista"
//         :key="tare"