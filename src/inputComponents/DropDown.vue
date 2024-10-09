<template>
    <div>
        <select v-model="dropdownValue">
            <option value="selection 1">selection 1</option>
            <option value="selection 2">selection 2</option>
            <option value="selection 3">selection 3</option>
        </select>
    </div>
</template>

<script>
export default {
    data () {
        return {
            dropdownValue: ""
        }
    },
    watch: {
        dropdownValue () {
            this.$emit('updateValue', this.dropdownValue, "dropdown")
        }
    }
}
</script>
