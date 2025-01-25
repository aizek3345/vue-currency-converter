<template>
    <input 
        type="number"
        class="input"
        placeholder="Введите сумму"
        :value="modelValue"
        @input="updateInput"
    >
</template>

<script>
export default {
    name: "my-input",
    props: {
        modelValue: [String, Number],
    },
    methods: {
        updateInput(event) {
            this.$emit('update:modelValue', event.target.value)
        }
    }
}
</script>

<style>
.input{
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