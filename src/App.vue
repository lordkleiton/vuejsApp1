<template>
	<div id="app">
		<img alt="Vue logo" src="./assets/logo.png">
		<lista @contador="editaTexto" :array="'oie'"></lista>
		<lista @contador="editaTexto" :array="'oie'"></lista>
		<lista @contador="editaTexto" :array="'oie'"></lista>
		<p>{{ recebido ? recebido : indefinido }}</p>

		<div>
			<label for="bits">Digite um número maior que zero para a quantidade de bits do número: </label>
			<campo-texto id="bits" @valor="recebeBits" placeholder="Digite um número inteiro"></campo-texto>
		</div>

		<div v-if="bits > 0">
			<label for="num">Digite um número inteiro entre 0 e {{ getMax() }} para ver sua representação em binário: </label>
			<campo-texto id="num" @valor="recebeNum" placeholder="Digite um número inteiro"></campo-texto>
			<p>{{ num ? num : msgCampo }}</p>
			<p>Número em formato estranho? Entenda mais clicando <a href="https://pt.wikipedia.org/wiki/Nota%C3%A7%C3%A3o_cient%C3%ADfica">aqui</a>.</p>
		</div>

	</div>
</template>

<script>
	import lista from './components/lista.vue';
	import campoTexto from './components/texto.vue';

	export default {
		name: 'app',
		data: () => {
			return {
				recebido: undefined,
				indefinido: 'Você ainda não passou o mouse em cima de algum dos textos acima.',
				num: undefined,
				msgCampo: 'Você ainda não digitou na caixa acima.',
				bits: undefined
			}
		},
		components: {
			lista,
			campoTexto
		},
		methods: {
			getMax(){
				return Math.pow(2, this.bits) - 1;
			},
			editaTexto(e){
				this.recebido = 'o ultimo numero recebido dos filhos foi: ' + e;
			},
			recebeBits(e){
				this.bits = e;
			},
			recebeNum(e){
				this.num = this.padding(e, this.bits);
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
