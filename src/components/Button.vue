<template>
    <button :style="{background: color}" class="btn">{{ text }}</button>
</template>

<script>
export default {
    name: 'Button-Comp',
    props: {
        text: String,
        color: String,
    },
    methods: {
    }
}
</script>