<template>
    <select 
        :value="modelValue"
        @change="updateValue"
        class="select-field">
            <option 
                v-for="currency in currencies" 
                :key="currency"
                :value="currency">
                    {{ currency }}
            </option>
    </select>
</template>

<script>

export default {
    name: "my-select",

    data() {
        return {
            currencies: ['USD', 'EUR'],
        }
    },

    props: {
        modelValue:{
            type: String,
            required: true
        },
    },
    methods: {
        updateValue(event){
            this.$emit('update:modelValue', event.target.value)
        }
    }
}
</script>

<style scored>
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
</style>