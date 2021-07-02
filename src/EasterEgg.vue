<template>
  <div class="wrapper">
    <h1>
      Данный сайт сделали эти люди
    </h1>
    <div v-show="false">
      Специально не скрыл из консоли, дам подсказку двойной клик и ты это увидишь)))
    </div>
    <div class="wrapper-link">
      <a href="https://vk.com/shikhov_21" target="_blank">Костя</a>
      <a href="https://vk.com/lb627" target="_blank">Дима</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "EasterEgg"
}
</script>

<style scoped>
.wrapper {
  padding: 16px;
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translateX(-50%) translateY(-50%);
  width: 300px;
  height: 250px;
  background: hsla(0, 0%, 97.3%, .4);
  text-align: center;
  border-radius: 16px;
  z-index: 100;
  backdrop-filter: blur(4px);
  box-shadow: 0px 0px 20px 1px rgba(34, 60, 80, 0.2);
}

.wrapper-link {
  display: flex;
  flex-direction: column;
  font-size: 25px;
  text-align: center;
  /*height: 100%;*/
  margin-top: 16px;
  align-items: center;
}

.wrapper-link a {
  color: #000000;
  text-decoration: none;
}

</style>