<template>
    <button class="btn">
        <slot></slot>
    </button>
</template>

<script>

export default {
    name: "my-button"
}
</script>

<style scored>
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

.btn:hover {
    background-color: red;
}

.btn:active {
    background-color: darkred;
    transform: translateY(1px);
}
</style>