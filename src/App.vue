<template>
    <div id="app">
        <div class="wrapper">
          <!--<EasterEgg v-show="openItem"/>-->
          <!--<div @dblclick="easterEgg()" class="wrapper__item"></div>-->
            <div class="wrapper__main-body">
                <a href="http://www.psu.ru">
                    <div class="wrapper__header--img"></div>
                </a>
                <div class="wrapper__body">
                    <div class="wrapper__body-header">
                        <h1 class="wrapper__body-header--strong text" align=center>
                            Навигатор ЕГЭ в ПГНИУ
                        </h1>
                        <div class="wrapper__body-header--desc text">
                            Выбери предметы, которые ты сдаешь в форме ЕГЭ. Ниже под формой ты увидишь направления
                            ПГНИУ, куда можешь
                            подать документы в 2022 году, и минимальные баллы.
                        </div>
                        <div class="wrapper__body-header--desc_sub text">
                            * - внутренние экзамены ПГНИУ
                        </div>
                    </div>
                    <div class="wrapper__body-cb">
            <div class="wrapper__body-header">
              <div class="wrapper__cb">
                <div class="wrapper__cb-items">
                  <div class="wrapper__cb-item">
                    <input @click="Click('eng', !isEng)" v-model="isEng" type="checkbox" id="eng"/>
                    <label for="eng">Английский язык <b>(30)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('bio', !isBio)" v-model="isBio" type="checkbox" id="bio"/>
                    <label for="bio">Биология <b>(39)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('geo', !isGeo)" v-model="isGeo" type="checkbox" id="geo"/>
                    <label for="geo">География <b>(40)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('iny', !isIny)" v-model="isIny" type="checkbox" id="iny"/>
                    <label for="iny">Другой иностранный язык <b>(30)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('inf', !isInf)" v-model="isInf" type="checkbox" id="inf"/>
                    <label for="inf">Информатика и ИКТ <b>(44)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('ist', !isIst)" v-model="isIst" type="checkbox" id="ist"/>
                    <label for="ist">История <b>(35)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('lit', !isLit)" v-model="isLit" type="checkbox" id="lit"/>
                    <label for="lit">Литература <b>(40)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('mat', !isMat)" v-model="isMat" type="checkbox" id="mat"/>
                    <label for="mat">Математика <b>(39)</b></label>
                  </div>
                </div>
                <div class="wrapper__cb-items">
                  <div class="wrapper__cb-item">
                    <input @click="Click('ger', !isGer)" v-model="isGer" type="checkbox" id="ger"/>
                    <label for="ger">Немецкий язык <b>(30)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('obs', !isObs)" v-model="isObs" type="checkbox" id="obs"/>
                    <label for="obs">Обществознание <b>(45)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('ris', !isRis)" v-model="isRis" type="checkbox" id="ris"/>
                    <label for="ris">Рисунок* <b>(50)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('rus', !isRus)" v-model="isRus" type="checkbox" id="rus"/>
                    <label for="rus">Русский язык <b>(40)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('tvo', !isTvo)" v-model="isTvo" type="checkbox" id="tvo"/>
                    <label for="tvo">Творческая работа* <b>(50)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('phy', !isPhy)" v-model="isPhy" type="checkbox" id="phy"/>
                    <label for="phy">Физика <b>(39)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('fre', !isFre)" v-model="isFre" type="checkbox" id="fre"/>
                    <label for="fre">Французский язык <b>(30)</b></label>
                  </div>
                  <div class="wrapper__cb-item">
                    <input @click="Click('che', !isChe)" v-model="isChe" type="checkbox" id="che"/>
                    <label for="che">Химия <b>(39)</b></label>
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
                                        <div :key="item.id + index" v-for="(item, index) in finallyFilterArr">
                                            <strong><a
                                              v-bind:href="'http://' + item.url"
                                              target="_blank"><em>{{ item.name }}</em></a></strong>
                                            <div class="text">
                                                <i>{{ item.desc }}</i><br>
                                                Профили обучения: <i>{{ item.prof }}</i><br>
                                                Форма обучения: <i>{{ item.form }}</i><br>
                                                <div>
                                                    <ul>
                                                        <li>{{ item.scope1 }}</li>
                                                        <li>{{ item.scope2 }}</li>
                                                        <li>{{ item.scope3 }}</li>
                                                    </ul>
                                                </div>
                                            </div>
                                            <br>
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
//import EasterEgg from "./EasterEgg";
export default {
    name: 'App',
    data() {
        return {
            myData: '',
            selectObj: [],
            filterArr: [],
            finallyFilterArr: [],
            open: false,
            openItem: false,
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
//    components: {
//      EasterEgg
//    },
    methods: {
        Click(name, isValue) {
            this.open = false;
            this.filterArr = [];
            this.finallyFilterArr = [];
            //проверяю, чтобы переведен чекбокс в true или false
            if (isValue) {
                this.selectObj.push(name)
            } else {
                let i = 0;
                while (i < this.selectObj.length) {
                    if (this.selectObj[i] === name) {
                        this.selectObj.splice(i, 1);
                    } else {
                        ++i;
                    }
                }
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

            this.filterArr.reduce((acc, n) => {
                const i = acc.findIndex(m => m.id === n.id);
                if (!~i || !acc[i].id) {
                    acc.push(n);
                    if (~i) {
                        acc.splice(i, 1);
                    }
                }
                this.finallyFilterArr = acc;
                return acc;
            }, [])
        },

      easterEgg() {
        this.openItem = !this.openItem;
      }
    },
}
</script>
<style>
* {
    padding: 0;
    margin: 0;
    font-family: Lucida Grande, sans-serif;
}

.wrapper__item {
  opacity: 0;
  height: 20px;
  width: 20px;
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
    width: 80%;
    margin-bottom: 10%;
    margin-left: 10%;
    background-size: 100% 160px;
    background-repeat: no-repeat;
    background-image: url(http://www.psu.ru/templates/xhtml/images/company.png);
    display: inline-block;
    height: 160px;
}

.wrapper__body {
    background-color: #fff;
    box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.4);
}

.wrapper__body-header {
    padding: 35px;
}

.wrapper__body-header--desc {
    text-align: justify;
    font-size: 20px;
    line-height: 1.5em;
    font-style: normal;
    margin: 3px 0 0;
}

.wrapper__body-header--desc_sub {
    text-align: justify;
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
    cursor: pointer;
}

.wrapper__cb-item label {
    font-size: 18px;
    font-family: Arial;
    padding-left: 25px;
    cursor: pointer;
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
a:link {
    color: #C62E3E; /* Цвет ссылок */   
}
a:active{   
    color: #C62E3E; /* Цвет активной ссылки */   
}
a:visited{   
    color: #C62E3E; /* Цвет посещенной ссылки */   
}

@media screen and (max-width: 1600px) {
    .wrapper__main-body {
        width: 70%;
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

    .wrapper__header--img {
        width: 80%;
        margin-top: 10%;
        margin-left: 10%;
        background-size: 100% 100px;
        background-repeat: no-repeat;
        background-image: url(http://www.psu.ru/templates/xhtml/images/company.png);
        display: inline-block;
        height: 120px;
    }
}
</style>