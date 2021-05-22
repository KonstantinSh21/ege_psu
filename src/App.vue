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
                    <!--                    //Биология              bio 39-->
                    <!--                    //Математика            mat 39-->
                    <!--                    //Геогрфия              geo 40-->
                    <!--                    //Русский язык          rus 40-->
                    <!--                    //Химия                 che 39-->
                    <!--                    //Обществознание        obs 45-->
                    <!--                    //Информатика и ИКТ     inf 44-->
                    <!--                    //Английский            eng 30-->
                    <!--                    //Физика                phy 39-->
                    <!--                    //История               ist 35-->
                    <!--                    //Иностранный язык      iny 30-->
                    <!--                    //Литература            lit 40-->
                    <!--                    //Немецкий язык         ger 30-->
                    <!--                    //Французский язык      fre 30-->
                    <!--                    //Творческая работа     tvo 50-->
                    <!--                    //Рисунок               ris 50-->
                    <input @click="Click('rus', !isRus)" v-model="isRus" type="checkbox"/>
                    <span>Русский язык</span>
                  </div>

                  <div class="wrapper__cb-item">
                    <input @click="Click('mat', !isMat)" v-model="isMat" type="checkbox"/>
                    <span>Математика (проф.ур.)</span>
                  </div>

                  <div class="wrapper__cb-item">
                    <input @click="Click('inf', !isInf)" v-model="isInf" type="checkbox"/>
                    <span>Информатика и ИКТ</span>
                  </div>

                  <div class="wrapper__cb-item">
                    <input @click="Click('phy', !isPhy)" v-model="isPhy" type="checkbox"/>
                    <span>Физика</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('geo', !isGeo)" v-model="isGeo" type="checkbox"/>
                    <span>География</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('eng', !isEng)" v-model="isEng" type="checkbox"/>
                    <span>Английский язык</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('fre', !isFre)" v-model="isFre" type="checkbox"/>
                    <span>Французский язык</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('lit', !isLit)" v-model="isLit" type="checkbox"/>
                    <span>Литература</span>
                  </div>
                </div>
                <div class="wrapper__cb-items">
                  <div class="wrapper__cb-item">
                    <input @click="Click('ist', !isIst)" v-model="isIst" type="checkbox"/>
                    <span>История</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('obs', !isObs)" v-model="isObs" type="checkbox"/>
                    <span>Обществознание</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('che', !isChe)" v-model="isChe" type="checkbox"/>
                    <span>Химия</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('bio', !isBio)" v-model="isBio" type="checkbox"/>
                    <span>Биология</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('ger', !isGer)" v-model="isGer" type="checkbox"/>
                    <span>Немецкий язык</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('ris', !isRis)" v-model="isRis" type="checkbox"/>
                    <span>Рисунок</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('tvo', !isTvo)" v-model="isTvo" type="checkbox"/>
                    <span>Творческое задание</span>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('iny', !isIny)" v-model="isIny" type="checkbox"/>
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
                    <div :key="item.id" v-for="item in finallyFilterArr">
                      <strong><a
                          v-bind:href="'http://' + item.url"
                          target="_blank"><em>{{item.name}}</em></a></strong>
                      <div class="text">
                        Очная форма обучения
                        <div>
                          {{item.desc_scope}}
                        </div>
                      </div><br>
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
      selectObj: [],
      filterArr: [],
      finallyFilterArr: [],
      open: false,
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
    Click(name, isValue) {
      this.open = false;
      this.filterArr = [];
      this.finallyFilterArr = [];
      //проверяю, чтобы переведен чекбокс в true или false
      if (isValue) {
        this.selectObj.push(name)
      } else {
        let i = this.selectObj.indexOf(name)
        let firstArr = this.selectObj.splice(0, i);
        let secondArr = this.selectObj.splice(i++);
        this.selectObj = [...firstArr, ...secondArr]
      }

      //нет смысла искать элемент когда меньше 3 предметов
      if (this.selectObj.length < 3) {
        this.filterArr = [];
        return false;
      }

      //сложная херовнина, но я бегу по всем элементам главного массива и собираю данные по валидному имени
      //но при добовлениями новых пунктов докидывались новые и дублировались
      for (let i = 0; i < this.myData.description.length; i++) {
        let countObj = 0;
        countObj = 0
        //тут я смотрю какие предеметы выбраны и буду искать какие есть у него
        for (let b = 0; b < this.selectObj.length; b++) {

          for (let key in this.myData.description[i].obj) {
            if (key === this.selectObj[b]) {
              countObj++
            }
            if (countObj === 3) {
              this.filterArr.push(this.myData.description[i])
              this.open = true;
            }
          }
        }
      }
      this.finallyFilterArr = this.filterArr.filter((item, index) => {
        return this.filterArr.indexOf(item) === index;
      });
    },
  }
  ,
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

  .wrapper__header--img {
    width: 100%;
    background-size: 100%;
    background-repeat: no-repeat;
    background-image: url(https://www.jotform.com/uploads/guest_201110705335035/form_files/logo_pgniu.5eb3f33f7392b5.32949480.png);
    display: inline-block;
    height: 100px;
  }
}

</style>
