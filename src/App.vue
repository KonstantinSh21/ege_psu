<template>
  <div id="app">
    <div class="wrapper">
      <div class="wrapper__main-body">
        <div class="wrapper__header--img"></div>
        <div class="wrapper__body">
          <div class="wrapper__body-header">
            <h1 class="wrapper__body-header--strong text">
              Навигатор ЕГЭ в ПГНИУ
            </h1>
            <div class="wrapper__body-header--desc text">
              Выбери предметы, которые ты сдаешь в форме ЕГЭ. Ниже под формой ты увидишь направления ПГНИУ, куда можешь
              подать документы в 2021 году, и минимальные баллы.
            </div>
          </div>
          <div class="wrapper__body-cb">
            <div class="wrapper__body-header">
              <div class="wrapper__cb">
                <div class="wrapper__cb-items">
                  <div class="wrapper__cb-item">
                    <input v-model="isRus" type="checkbox"/>
                    <span>Русский язык</span>
                  </div>

                  <div class="wrapper__cb-item">
                    <input v-model="isMat" type="checkbox"/>
                    <span>Математика (проф.ур.)</span>
                  </div>

                  <div class="wrapper__cb-item">
                    <input v-model="isInf" type="checkbox"/>
                    <span>Информатика и ИКТ</span>
                  </div>

                  <div class="wrapper__cb-item">
                    <input v-model="isPhy" type="checkbox"/>
                    <span>Физика</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input  v-model="isGeo" type="checkbox"/>
                    <span>География</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input v-model="isEng" type="checkbox"/>
                    <span>Английский язык</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input  v-model="isFre" type="checkbox"/>
                    <span>Французский язык</span>
                  </div>
                </div>
                <div class="wrapper__cb-items">
                  <div class="wrapper__cb-item">
                    <input v-model="isLit" type="checkbox"/>
                    <span>Литература</span>
                  </div>

                  <div class="wrapper__cb-item">
                    <input v-model="isIst" type="checkbox"/>
                    <span>История</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input v-model="isObs" type="checkbox"/>
                    <span>Обществознание</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input v-model="isChe" type="checkbox"/>
                    <span>Химия</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input v-model="isBio" type="checkbox"/>
                    <span>Биология</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input v-model="isGer" type="checkbox"/>
                    <span>Немецкий язык</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input v-model="isIny" type="checkbox"/>
                    <span>Другой иностранный язык</span>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="wrapper__footer--full">
            <div :class="open ? 'wrapper__footer--padding' :'wrapper__footer--padding-none'">
              <div class="wrapper__footer-items">
                <div :class="open ? 'wrapper__footer-text--opacity' :'wrapper__footer-text--none'">
                  <div class="footer__footer">
                    <strong><a
                        href="http://www.psu.ru/fakultety/geograficheskij-fakultet/napravleniya-obrazovatelnoj-deyatelnosti/napravlenie-geodeziya-i-distantsionnoe-zondirovanie-bakalavriat"
                        target="_blank" rel="nofollow">Геодезия и дистанционное зондирование</a></strong>
                    <br>
                    <div class="text">
                      <em class="">Профиль: Дистанционное зондирование</em>
                      <br>Очная форма обучения<br>
                      <strong>Минимальные баллы:</strong> <br>
                      Математика – 39<br>
                      Информатика и ИКТ – 42<br>
                      Русский язык – 40
                    </div>

                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      myData: '',
      mySql: ['bio', 'mat', 'geo','rus','che','obs','inf','eng','phy','ist','iny','lit','ger','fre','tvo','ris'],
      filterArr: [],
      finallyFilterArr: [],
      isBio: false,
      isMat: false,
      isGeo: false,
      isRus: false,
      isChe: false,
      isObs: false,
      isInf: false,
      isEng: false,
      isPhy: false,
      isIst: false,
      isIny: false,
      isLit: false,
      isGer: false,
      isFre: false,
      isTvo: false,
      isRis: false
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
* {
  padding: 0;
  margin: 0;
  font-family: Lucida Grande, sans-serif;
}

.wrapper {
  width: 100%;
}

.wrapper__main-body {
  width: 30%;
  padding: 60px 0;
  margin: 0 auto;
}


.wrapper__header--img {
  width: 100%;
  background-size: 100% 129px;
  background-repeat: no-repeat;
  background-image: url(https://www.jotform.com/uploads/guest_201110705335035/form_files/logo_pgniu.5eb3f33f7392b5.32949480.png);
  display: inline-block;
  height: 129px;
}

.wrapper__body {
  background-color: #fff;
  box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.4);
}

.wrapper__body-header {
  padding: 35px;
}

.wrapper__body-header--desc {
  font-size: 14px;
  line-height: 1.5em;
  font-style: normal;
  margin: 3px 0 0;
}

.text {
  color: #555;
  font-family: Arial;
}

.wrapper__body-cb {
  border-top: 2px #e6e6e6 solid;
}

.wrapper__cb {
  max-width: 100%;
  height: 100%;
  display: flex;
  position: relative;
}

.wrapper__cb-item {
  position: relative;
  flex: 1 1 100%;
  padding-bottom: 5px;
}

.wrapper__cb-items {
  min-width: 50%;
  max-width: 50%;
}

.wrapper__cb-item input {
  position: absolute;
  top: -2.5px;
  height: 100%;
}

.wrapper__cb-item span {
  font-size: 14px;
  font-family: Arial;
  padding-left: 25px;
}

.wrapper__footer--none {
  transition: 0.5s;
  height: 0;
}

.wrapper__footer--padding {
  padding: 35px;
  transition: 0.5s;
}

.wrapper__footer--padding-none {
  padding: 0;
  transition: 0.5s;
}

.wrapper__footer-text--opacity {
  height: 150px;
  opacity: 1;
  transition: 0.5s;
}

.wrapper__footer-text--none {
  height: 0;
  opacity: 0;
  transition: 0.5s;
}

.footer__footer {
  font-size: 14px;
  line-height: 20px;
}

@media screen and (max-width: 1600px) {
  .wrapper__main-body {
    width: 50%;
  }
}

@media screen and (max-width: 1000px) {
  .wrapper__main-body {
    width: 70%;
  }
}

@media screen and (max-width: 650px) {
  .wrapper__main-body {
    width: 100%;
  }
}

@media screen and (max-width: 650px) {
  .wrapper__main-body {
    width: 100%;
  }
}

@media screen and (max-width: 500px) {
  .wrapper__cb {
    flex-wrap: wrap;
  }

  .wrapper__cb-items {
    min-width: 100%;
    max-width: 100%;
  }

  .wrapper__footer--padding {
    height: 170px;
  }
  .wrapper__header--img{
    width: 100%;
    background-size: 100%;
    background-repeat: no-repeat;
    background-image: url(https://www.jotform.com/uploads/guest_201110705335035/form_files/logo_pgniu.5eb3f33f7392b5.32949480.png);
    display: inline-block;
    height: 100px;
  }
}

</style>
