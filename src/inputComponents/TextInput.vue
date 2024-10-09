<template>
    <div>
        <input type="text" v-model="inputText" @input="emitTheChange">
    </div>
</template>

<script>
export default {
    data () {
        return {
            inputText: ""
        }
    },
    methods: {
        emitTheChange () {
            this.$emit('updateValue', this.inputText, "input")
        }
    }
}
</script>
