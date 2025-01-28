<template>
    <div class="container">
        <h3 class="title">Конвертер валют</h3>
        <my-input-currency-converter
            v-model="summ"
        />
        <my-select-currency-converter
            v-model="toCurrency"
        />
        <my-button-currency-converter
            @click="convert">
                Конвертировать
        </my-button-currency-converter>
        <my-input-currency-converter
            v-model="resultText"
            :Placeholder="'Результат'"
            ReadOnly
            isResult
        />
    </div>
</template>

<script>
import MyButtonCurrencyConverter from './UI/MyButton-CurrencyConverter'
import MyInputCurrencyConverter from './UI/MyInput-CurrencyConverter'
import MySelectCurrencyConverter from './UI/MySelect-CurrencyConverter'
import axios from 'axios';

export default {
    components: { MySelectCurrencyConverter, MyButtonCurrencyConverter, MyInputCurrencyConverter },
    data() {
        return {
            summ: 0,
            fromCurrency: 'RUB',
            toCurrency: 'USD',
            rates: {},
            resultText: 0,
            dollarCourse: 0
        }
    },
    mounted() {
        axios.get('https://openexchangerates.org/api/latest.json?app_id=1649e65be5514c7a97da7730d65889ca&base=USD&symbols=RUB')
        .then(response => {
            this.dollarCourse = response.data.rates.RUB
        })
        .catch(e => {console.log(e)})
    },
    methods: {
        convert() {
            this.resultText = (this.summ / this.dollarCourse).toFixed(3)
        }
    }
}
</script>

<style scored>
.container{
    max-width: 350px;
    margin: 30px auto;
    padding: 15px;
    background-color: #f4f4f9;
    border-radius: 8px;
    border: 1px solid #ccc;
}

.title {
    text-align: center;
    font-size: 22px;
}
</style>