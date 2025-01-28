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

export default {
    components: { MySelectCurrencyConverter, MyButtonCurrencyConverter, MyInputCurrencyConverter },
    data() {
        return {
            summ: 0,
            fromCurrency: 'RUB',
            toCurrency: 'USD',
            rates: {
                USD: 0.010,
                EUR: 0.0096,
                RUB: 1
            },
            resultText: 0
        }
    },
    methods: {
        convert() {
            this.resultText = (this.summ * this.rates[this.toCurrency]).toFixed(2)
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