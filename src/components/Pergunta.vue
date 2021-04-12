<template>
    <div>
        <b><span v-html="perguntaAtual.pergunta"></span></b><br />

        <div v-for="(item, indice) in perguntaAtual.respostas" :key="`resposta-${indice}`">
            <md-button v-html="item" v-on:click="responder(indice)"></md-button><br />
        </div>
    </div>
</template>

<style scoped>

</style>

<script>
export default {
    name: 'Pergunta',
    props: ['perguntas'],
    created: function() {
        console.log('Perguntas', this.perguntas);
    },
    computed: {
        perguntaAtual: function() {
            return this.perguntas[0];
        }
    },
    methods: {
        responder(indice) {
            if (indice === this.perguntaAtual.correta - 1) {
                alert(this.perguntaAtual.textoCerto ?? "Parabéns, é exatamente isso.");
            } else {
                alert(this.perguntaAtual.textoErrado ?? "Humm, Infelizmente você errou.");
            }
        }
    }
}
</script>