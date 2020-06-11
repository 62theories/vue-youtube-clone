<template>
    <div>
        <input @input="handleInput" />
    </div>
</template>

<script>
export default {
    name: "SearchBar",
    props: {
        onSearchInputChanged: Function,
    },
    methods: {
        handleInput: function({ target: { value } }) {
            this.onSearchInputChanged(value)
        },
    },
}
</script>

<style scoped>
div {
    text-align: center;
    margin: 20px;
}
input {
    width: 75%;
}
</style>
