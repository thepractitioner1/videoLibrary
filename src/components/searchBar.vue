<template>
    <div>
        <input v-on:blur ="onInput" type="text"/>
    </div>

</template>

<script>
export default {
    methods:{
        onInput: function(event){
            this.$emit('termChange', event.target.value);
        }
    }
}
</script>

<style scoped>
    input {
        width: 75%;
    }

    div{
        text-align: center;
        margin: 20px;
    }
</style>