<template>
	<div id="app">
		<img alt="Vue logo" src="./assets/logo.png">
		<!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
		<lista @contador="editaTexto" :array="'oie'"></lista>
		<lista @contador="editaTexto" :array="'oie'"></lista>
		<lista @contador="editaTexto" :array="'oie'"></lista>
		<p>{{ recebido ? recebido : indefinido }}</p>
		<campo-texto @valor="recebeCampo" placeholder="digite um número"></campo-texto>
		<p>{{ campo ? campo : msgCampo }}</p>
	</div>
</template>

<script>
	import HelloWorld from './components/HelloWorld.vue';
	import lista from './components/lista.vue';
	import campoTexto from './components/texto.vue';

	export default {
		name: 'app',
		data: () => {
			return {
				recebido: undefined,
				indefinido: 'você ainda não passou o mouse em cima de algum dos textos acima.',
				campo: '',
				msgCampo: 'você ainda não digitou na caixa de textos.'
			}
		},
		components: {
			HelloWorld,
			lista,
			campoTexto
		},
		methods: {
			editaTexto(e){
				this.recebido = 'o ultimo numero recebido dos filhos foi: ' + e;
			},
			recebeCampo(e){
				this.campo = this.padding(e, 8);
			},
			dec2bin(a){
				return (a === 0) ? 0 : (a % 2 + 10 * this.dec2bin(Math.floor(a / 2)));
			},
			padding(a, b){
				if ((a >= 0) && (b > 0)){
					let r = this.dec2bin(a).toString();
				
					if (r.length <= b){
						let dif = b - r.length;
						let aux = '';

						while (aux.length < dif){
							aux += '0';
						}

						return aux + r;
					}
					else{
						return `Fora do intervalo. min = 0, max = ${Math.pow(2, b) - 1}`;
					}
				}
				else{
					return 'Argumentos incorretos.';
				}
			}
		}
	}
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>
