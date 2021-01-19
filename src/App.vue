<template>
  <div id="app">
    <button @click="Click">
      найти
    </button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      myData: '',
      mySql: ['math', 'phys', 'pus'],
      filterArr: [],
      finallyFilterArr: []
    }
  },
  mounted() {
    //обработал JSON падают ошибки буду думать
    const userData = require('./data.json');
    this.myData = userData;
    this.myData = JSON.parse(JSON.stringify(this.myData))
  },
  methods: {
    Click() {
      //пока сделал на 3 клика потом будет на кол-во кликов
      for (let i = 0; i < this.myData.description.length; i++) {
        for (let b = 0; b < 3; b++) {
          for (let key in this.myData.description[i].obj) {
            if (key === this.mySql[b]) {
              this.filterArr.push(this.myData.description[i]);
              if (this.filterArr.length > 2) {
                this.filterArr = []
                this.finallyFilterArr.push(this.myData.description[i])
              }
            }
          }
        }
      }
    },
  },
}

</script>

<style>
</style>
