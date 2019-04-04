<template>
    <input type="number" :placeholder="placeholder" v-model="num" @change="fazCoisas(num)">
</template>

<script>
export default {
    name: 'campoTexto',
    props: {
        'placeholder': String
    },
    data: () => {
        return {
            num: undefined
        };
    },
    methods: {
        log(a){
            console.log(a);
        },
        fazCoisas(a){
            this.log(a);
            this.$emit('valor', this.num, this.bits);
        }
    }
};
</script>
