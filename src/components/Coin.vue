<template>
    <div>
        <input :placeholder="name" :value="value" v-on:input="(evt) => { this.$emit('valueChange', parseInt(evt.target.value)) }" />
    </div>
</template>

<script>
export default {
    name: 'Coin',
    props: {
        name: String,
        value: Number
    }
};
</script>

<style>

</style>
