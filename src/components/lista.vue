<template>
    <ul class="lista">
        <li 
            :title="'n-não clique em mim por favor'" 
            @mouseover="aumenta()" 
            @click="alerta('b-baka!!')" 
            v-for="(item, index, key) in array"
            :key="key">
            {{ key }} Esse é meu index: {{ index }} e esse é meu conteúdo: {{ item }}, mas você passou o mouse em cima {{ contador }} vezes
        </li>
    </ul>
</template>

<script>
    export default {
        name: 'lista',
        props: ['array'],
        data: function(){
                return {
                    contador: 0
                };
            },
        methods:{
            alerta(msg){
                alert(msg);
            },
            log(msg){
                console.log(msg);
            },
            aumenta(){
                this.log(`mouse passou em cima ${++this.contador} vezes`);
                this.$emit('contador', this.contador);
            }
        }
    }
</script>