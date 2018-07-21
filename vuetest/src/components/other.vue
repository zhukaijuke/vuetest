<template>
    <div>
        <h1>other template</h1>
        <p>{{ parentMsg }}</p>
        <slot name="a">
            slot-a 默认内容
        </slot>
        <slot name="b">
            slot-b 默认内容
        </slot>
        <slot></slot>
    </div>
</template>

<script>
    export default {
        name: "other",
        props: ['parentMsg'],
        mounted: function () {
            var a = this.$slots.a;
            var b = this.$slots.b;
            var main = this.$slots.default;
            console.info(a);
            console.info(b);
            console.info(main);
        }
    }
</script>

<style scoped>

</style>
