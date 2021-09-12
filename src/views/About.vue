<template>
  <div class="about">
    <h1 class="text">Currency Calculator</h1>

    <div class="container dropdawn_container" v-if="dataCur.Valute">

      <div class="drdwn1">
        <p class="text">Выберите валюту из который надо перевести </p>
        <div class="dropdown">
          <button class="dropbtn">{{selecteValueBefore}}</button>
          <div class="dropdown-content">
            <a href="#/about" @click="selecteValueBefore = dataCur.Valute.USD.Name, selecteValueBeforeChar = dataCur.Valute.USD.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)" >{{dataCur.Valute.USD.Name}}</a>
            <a href="#/about" @click="selecteValueBefore = dataCur.Valute.EUR.Name, selecteValueBeforeChar = dataCur.Valute.EUR.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">{{dataCur.Valute.EUR.Name}}</a>
            <a href="#/about" @click="selecteValueBefore = dataCur.Valute.BYN.Name, selecteValueBeforeChar = dataCur.Valute.BYN.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">{{dataCur.Valute.BYN.Name}}</a>
            <a href="#/about" @click="selecteValueBefore = dataCur.Valute.UAH.Name, selecteValueBeforeChar = dataCur.Valute.UAH.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">{{dataCur.Valute.UAH.Name}}</a>
            <a href="#/about" @click="selecteValueBefore = dataCur.Valute.GBP.Name, selecteValueBeforeChar = dataCur.Valute.GBP.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">{{dataCur.Valute.GBP.Name}}</a>
            <a href="#/about" @click="selecteValueBefore = dataCur.Valute.CZK.Name, selecteValueBeforeChar = dataCur.Valute.CZK.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">{{dataCur.Valute.CZK.Name}}</a>
            <a href="#/about" @click="selecteValueBefore = 'Российский Рубль', selecteValueBeforeChar = 'RUB', countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">Российский Рубль</a>
          </div>
        </div>

      </div>

      <div class="drdwn1">
        <p class="text">Выберите валюту в которую надо перевести </p>
        <div class="dropdown">
          <button class="dropbtn">{{selecteValueAfter}}</button>
          <div class="dropdown-content">
            <a href="#/about" @click="selecteValueAfter = dataCur.Valute.USD.Name, selecteValueAfterChar = dataCur.Valute.USD.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)" >{{dataCur.Valute.USD.Name}}</a>
            <a href="#/about" @click="selecteValueAfter = dataCur.Valute.EUR.Name, selecteValueAfterChar = dataCur.Valute.EUR.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">{{dataCur.Valute.EUR.Name}}</a>
            <a href="#/about" @click="selecteValueAfter = dataCur.Valute.BYN.Name, selecteValueAfterChar = dataCur.Valute.BYN.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">{{dataCur.Valute.BYN.Name}}</a>
            <a href="#/about" @click="selecteValueAfter = dataCur.Valute.UAH.Name, selecteValueAfterChar = dataCur.Valute.UAH.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">{{dataCur.Valute.UAH.Name}}</a>
            <a href="#/about" @click="selecteValueAfter = dataCur.Valute.GBP.Name, selecteValueAfterChar = dataCur.Valute.GBP.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">{{dataCur.Valute.GBP.Name}}</a>
            <a href="#/about" @click="selecteValueAfter = dataCur.Valute.CZK.Name, selecteValueAfterChar = dataCur.Valute.CZK.CharCode, countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">{{dataCur.Valute.CZK.Name}}</a>
            <a href="#/about" @click="selecteValueAfter = 'Российский Рубль', selecteValueAfterChar = 'RUB', countValuteCourse(selecteValueBeforeChar, selecteValueBeforeChar, countValute)">Российский Рубль</a>
          </div>
        </div>

      </div>

    </div>

    <div class="container" v-else>
      <h2 class="text">
        Сбой сбора информации о валюте
      </h2>
    </div>

    <div class="container output_container">
        <input type="text" placeholder="10" v-model="countValute" @keydown="countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)" @change="countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)" @keyup.enter="countValuteCourse(selecteValueBeforeChar, selecteValueAfterChar, countValute)">

        <p class="text out_p">{{selecteValueBefore}} {{countValute}} = {{selecteValueAfter}} {{answerValute.toFixed(1)}}</p>

    </div>

  </div>
</template>

<script>
import {url} from '../data/data.js'

export default {
  data () {
    return {
      URL: url,
      dataCur: [],
      selecteValueBefore: 'Долар США',
      selecteValueAfter: 'Российский Рубль',
      selecteValueBeforeChar: 'USD',
      selecteValueAfterChar: 'RUB',
      answerValute: 0,
      countValute: 0,
    }
  },
  methods: {
    async getDataCurrency (url) {
      let respData = await fetch(url);
      let answer = await respData.json()
      this.dataCur = answer
      console.log(answer);
    },
    countValuteCourse (BeforeChar, AfterChar, countValute) {
      if (BeforeChar == 'RUB') {
        console.log(0);
        let after = 'this.dataCur.Valute.'+AfterChar+'.Value'
        let valueValuteAfter = eval(after)
        if (AfterChar == 'UAH') {
          this.answerValute = countValute / (valueValuteAfter/10)
        } else {
          console.log(valueValuteAfter);
          this.answerValute = countValute / valueValuteAfter
        }
        
      } 


      let before = 'this.dataCur.Valute.'+BeforeChar+'.Value'
      let valueValuteBefore = eval(before)
      console.log(BeforeChar, AfterChar);
      // console.log(valueValuteBefore);

      if (AfterChar == 'RUB') {
        console.log(1);
        if (BeforeChar == 'UAH') {
          this.answerValute = (valueValuteBefore/10) * countValute 
        } else {
          this.answerValute = valueValuteBefore * countValute
        }
      }
      else {
        console.log(2);
        let after = 'this.dataCur.Valute.'+AfterChar+'.Value'
        let valueValuteAfter = eval(after)
        console.log(valueValuteBefore);
        console.log(valueValuteAfter);

        let intermediate_answer = 0
        if (valueValuteBefore == "UAH") {
          intermediate_answer = (valueValuteBefore/10) * countValute
          console.log(intermediate_answer);
          console.log(intermediate_answer/valueValuteAfter);

          this.answerValute = intermediate_answer / valueValuteAfter
        } else {
          intermediate_answer = valueValuteBefore * countValute
          console.log(intermediate_answer);
          console.log(intermediate_answer/valueValuteAfter);

          this.answerValute = intermediate_answer / valueValuteAfter
        }
        
      }
      
    },
  },
  beforeMount(){
    this.getDataCurrency(this.URL)
  },
}
</script>

<style lang="stylus" scoped>
  .about
    padding-top 70px
  h1
    margin 0 auto
    min-width 300px

  .dropdawn_container
    display flex
    justify-content space-between
  
  .drdwn1
    max-width 350px
    width 100%

    display flex
    justify-content space-between
    align-items center
    text-align center

    margin-top 40px

  .dropbtn {
    width 100%
    max-width 150px
    min-width 150px
    background-color: #4CAF50;
    color: white;
    padding: 16px;
    font-size: 16px;
    border: none;
  }
  /* The container <div> - needed to position the dropdown content */
  .dropdown {
    position: relative;
    display: inline-block;
    // margin-top 40px
  }

  /* Dropdown Content (Hidden by Default) */
  .dropdown-content {
      display: none;
      position: absolute;
      background-color: #f1f1f1;
      min-width: 160px;
      box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
      z-index: 1;
  }

  /* Links inside the dropdown */
  .dropdown-content a {
      color: black;
      padding: 12px 16px;
      text-decoration: none;
      display: block;
  }

  /* Change color of dropdown links on hover */
  .dropdown-content a:hover {background-color: #ddd;}

  /* Show the dropdown menu on hover */
  .dropdown:hover .dropdown-content {display: block;}

  /* Change the background color of the dropdown button when the dropdown content is shown */
  .dropdown:hover .dropbtn {background-color: #3e8e41;}

  .output_container
    display flex
    justify-content space-between

    
    margin-top 20px

  input
    font-size:18px;
    color #EEEEEE
    padding:10px 10px 10px 5px;
    display:block;
    width:300px;
    border:none;
    border-bottom:1px solid #757575;
    background none
  input:focus     { outline:none; }

  @media (max-width: 768px) 
    h1
      font-size 24px
    p
      font-size 16px
    input
      margin-left auto
      margin-right auto

    .dropdawn_container
      display block
    .output_container
      display block
      text-align center

    .out_p
      margin-left auto
      margin-right auto
</style>