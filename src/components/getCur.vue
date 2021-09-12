<template>
 <h1 class="text">Курсы валют 2021</h1>

  <div class="container" v-if="dataCur.Valute">   
    
    <div class="valute_container">
        <div class="valute_content" >
          <h2 class="text">
            {{dataCur.Valute.USD.Name}}
          </h2>
          <h4 class="text">
            {{dataCur.Valute.USD.Nominal}} {{dataCur.Valute.USD.CharCode}} = {{(dataCur.Valute.USD.Value).toFixed(2)}} RUB

            <span :class="{upCours: dataCur.Valute.USD.Value > dataCur.Valute.USD.Previous, 
              downCours: dataCur.Valute.USD.Value < dataCur.Valute.USD.Previous}">&nbsp;

              ( {{(dataCur.Valute.USD.Value - dataCur.Valute.USD.Previous).toFixed(1)}} ) 

            </span>
          </h4>
        </div>

      <!-- USD -->
      <iframe iframe src="https://www.alta.ru/currency/graph_frame/?min=21&max=21" scrolling="no"></iframe>    
    </div>

    <div class="valute_container">
      <div class="valute_content">
        <h2 class="text">
            {{dataCur.Valute.EUR.Name}}
          </h2>
          <h4 class="text">
            {{dataCur.Valute.EUR.Nominal}} {{dataCur.Valute.EUR.CharCode}} = {{(dataCur.Valute.EUR.Value).toFixed(2)}} RUB

            <span :class="{upCours: dataCur.Valute.EUR.Value > dataCur.Valute.EUR.Previous, 
              downCours: dataCur.Valute.EUR.Value < dataCur.Valute.EUR.Previous}">&nbsp;

              ( {{(dataCur.Valute.EUR.Value - dataCur.Valute.EUR.Previous).toFixed(1)}} ) 

            </span>
          </h4>
      </div>

      <!-- EUR -->
      <iframe src="https://www.alta.ru/currency/graph_frame/?code[]=978&min=2021&max=2021" scrolling="no"></iframe> 
 
    </div>

    <div class="valute_container">
      <div class="valute_content">
        <h2 class="text">
            {{dataCur.Valute.BYN.Name}}
          </h2>
          <h4 class="text">
            {{dataCur.Valute.BYN.Nominal}} {{dataCur.Valute.BYN.CharCode}} = {{(dataCur.Valute.BYN.Value).toFixed(2)}} RUB

            <span :class="{upCours: dataCur.Valute.BYN.Value > dataCur.Valute.BYN.Previous, 
              downCours: dataCur.Valute.BYN.Value < dataCur.Valute.BYN.Previous}">&nbsp;

              ( {{(dataCur.Valute.BYN.Value - dataCur.Valute.BYN.Previous).toFixed(1)}} ) 

            </span>
          </h4>
      </div>

      <!-- Беларусский -->
      <iframe src="https://www.alta.ru/currency/graph_frame/?code[]=933&min=2021&max=2021" scrolling="no"></iframe>

    </div>

    <div class="valute_container">
      <div class="valute_content">
        <h2 class="text">
            {{dataCur.Valute.UAH.Name}}
          </h2>
          <h4 class="text">
            {{dataCur.Valute.UAH.Nominal}} {{dataCur.Valute.UAH.CharCode}} = {{(dataCur.Valute.UAH.Value).toFixed(2)}} RUB

            <span :class="{upCours: dataCur.Valute.UAH.Value > dataCur.Valute.UAH.Previous, 
              downCours: dataCur.Valute.UAH.Value < dataCur.Valute.UAH.Previous}">&nbsp;

              ( {{(dataCur.Valute.UAH.Value - dataCur.Valute.UAH.Previous).toFixed(1)}} ) 

            </span>
          </h4>
      </div>

      <!-- Украиская -->
      <iframe src="https://www.alta.ru/currency/graph_frame/?code[]=980&min=2021&max=2021" scrolling="no"></iframe>
    
    </div>

    <div class="valute_container">
      <div class="valute_content">
        <h2 class="text">
            {{dataCur.Valute.CZK.Name}}
          </h2>
          <h4 class="text">
            {{dataCur.Valute.CZK.Nominal}} {{dataCur.Valute.CZK.CharCode}} = {{(dataCur.Valute.CZK.Value).toFixed(2)}} RUB

            <span :class="{upCours: dataCur.Valute.CZK.Value > dataCur.Valute.CZK.Previous, 
              downCours: dataCur.Valute.CZK.Value < dataCur.Valute.CZK.Previous}">&nbsp;

              ( {{(dataCur.Valute.CZK.Value - dataCur.Valute.CZK.Previous).toFixed(1)}} ) 

            </span>
          </h4>
      </div>

      <!-- Чешская -->
      <iframe src="https://www.alta.ru/currency/graph_frame/?code[]=203&min=2021&max=2021" scrolling="no"></iframe>
    
    </div>

    <div class="valute_container">
      <div class="valute_content">
        <h2 class="text">
            {{dataCur.Valute.GBP.Name}}
        </h2>
          <h4 class="text">
            {{dataCur.Valute.GBP.Nominal}} {{dataCur.Valute.GBP.CharCode}} = {{(dataCur.Valute.GBP.Value).toFixed(2)}} RUB

            <span :class="{upCours: dataCur.Valute.GBP.Value > dataCur.Valute.GBP.Previous, 
              downCours: dataCur.Valute.GBP.Value < dataCur.Valute.GBP.Previous}">&nbsp;

              ( {{(dataCur.Valute.GBP.Value - dataCur.Valute.GBP.Previous).toFixed(1)}} ) 

            </span>
          </h4>
      </div>

      <!-- Фунтстерлингов -->
      <iframe src="https://www.alta.ru/currency/graph_frame/?code[]=826&min=2021&max=2021" scrolling="no"></iframe>

    </div>
  </div>

  <div class="container" v-else>
    <h2 class="text">
      Сбой сбора информации о валюте
    </h2>
  </div>

</template>

<script>
import {url} from '../data/data.js'



export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data () {
    return {
      URL: url,
      dataCur: [],
    }
  },
  methods: {
    async getDataCurrency (url) {
      let respData = await fetch(url);
      let answer = await respData.json()
      this.dataCur = answer
    },

  },
  beforeMount(){
    this.getDataCurrency(this.URL)
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus">
.valute_container
  display flex
  justify-content space-between
  margin-top 70px

h1
  margin-left auto
  margin-right auto

.upCours
  color green
.downCours
  color red

iframe
  max-width 600px
  width 100%
  height 495px
  border none
  overflow hidden

@media (max-width: 768px) 
  .valute_container
    margin-top 50px
    display block
  h1
    font-size 24px
  h2
    font-size 18px
  h4
    font-size 16px
  .valute_content
    text-align center
    align-items center
    width fit-content
    margin 0 auto


</style>