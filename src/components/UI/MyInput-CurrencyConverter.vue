<template>
    <input 
        type="number"
        :class="this.isResult ? 'result' : 'input'"
        :placeholder=Placeholder
        :value="modelValue"
        @input="updateInput"
        :readonly="ReadOnly"
    >
</template>

<script>
export default {
    name: "my-input",
    props: {
        modelValue: [String, Number],
        Placeholder: {
            type: String,
            required: true
        },
        ReadOnly: {
            type: Boolean,
            default: false
        },
        isResult: {
            type: Boolean,
            default: false
        }
    },
    methods: {
        updateInput(event) {
            this.$emit('update:modelValue', event.target.value)
        }
    },
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