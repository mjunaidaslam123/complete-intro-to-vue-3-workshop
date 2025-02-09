<template>
    <h3>hello click to change name</h3>
    <button @click="handleClick">
        <slot name="button">
            Welcome Home
        </slot>
    </button>
    <button @click="handleClick">
        <slot name="but">Nope</slot>
    </button>
</template>
<script>
export default {
    emits: ['hello-world'],
    methods: {
        handleClick() {
            this.$emit('hello-world')
        }
    }
}
</script>