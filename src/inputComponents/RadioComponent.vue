<template>
    <div>
        <div>
            <input v-model="radioValue" type="radio" value="option 1">
            option 1
        </div>
        <div>
            <input v-model="radioValue" type="radio" value="option 2">
            option 2
        </div>
        <div>
            <input v-model="radioValue" type="radio" value="option 3">
            option 3
        </div>
    </div>
</template>

<script>
export default {
    data () {
        return {
            radioValue: ""
        }
    },
    watch: {
        radioValue () {
            this.$emit('updateValue', this.radioValue, "radio")
        }
    }
}
</script>
