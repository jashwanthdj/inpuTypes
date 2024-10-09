<template>
    <div>
        <div>{{ componentsValue.input }}</div>
        <div>{{ componentsValue.dropdown }}</div>
        <div>{{ componentsValue.radio }}</div>
    </div>
</template>
<script>
export default {
    props: {
        componentsValue: {
            type: Object,
            required: false
        }
    }
}
</script>
