<template>
    <div class="container">
        <h3 class="title">Конвертер валют</h3>
        <input 
        type="number"
        placeholder="Введите сумму"
        class="input"
        v-model="summ"
        >
        <select v-model="toCurrency" class="select-field">
            <option 
            v-for="currency in currencies" 
            :key="currency"
            :value="currency">
                {{ currency }}
            </option>
        </select>
        <button 
        @click="convert"
        class="btn">
            Конвертировать
        </button>
        <input 
        type="number"
        class="result"
        placeholder="Результат"
        :value="resultText"
        readonly>
    </div>
</template>

<script>
export default {
    data() {
        return {
            summ: 0,
            fromCurrency: 'RUB',
            toCurrency: 'USD',
            currencies: ['USD', 'EUR'],
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

.input,
.select-field {
    width: 100%;
    padding: 8px;
    margin: 8px 0;
    border-radius: 5px;
    font-size: 16px;
    color: #555;
    box-sizing: border-box;
    border: 1px solid #ccc;
}

.btn {
    width: 100%;
    padding: 10px;
    margin-top: 5px;
    background-color: lightcoral;
    color: white;
    border-radius: 5px;
    font-size: 18px;
    border: 1px solid #ccc;
}

.result {
    width: 100%;
    padding: 8px;
    margin-top: 15px;
    border-radius: 5px;
    font-size: 16px;
    color: #555;
    box-sizing: border-box;
    text-align: center;
    border: 1px solid #ccc;
}
</style>