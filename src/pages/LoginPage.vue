<template>
    <div class="container-maior">
        <div class="container">
            <div class="frase">
                <h1>oiiiiiiiiiiiiiii bem vindo</h1>
            </div>
            <div class="itens">
                <div class="form-container">
                    <input type="text" class="siape" placeholder="SIAPE">
                    <input type="text" class="senha" placeholder="Senha">
                    <button class="botao" @click='logar'>Enviar</button>
                </div>
                <div class="foto">
                    <img src="../assets/img/socorro.jpg" alt="" class="fotoperfil">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
            name: "LoginPage",
            methods: {
                logar() {
                    window.location.href = "/";
                    /* Redirecionar usuário para página do quadro de horários */
                }
            }
        }

</script>

<style scoped>
    @import url('https://fonts.googleapis.com/css2?family=Autour+One&display=swap');

    .container {
        background-color: white;
        border: 2px black solid;
        border-radius: 1em;
        width: 50%;
        height: 45%;
    }

    .container-maior {
        display: flex;
        justify-content: center;
        height: 100vh;
        align-items: center;
    }

    .frase {
        display: flex;
        justify-content: center;
    }

    .form-container {
        display: flex;
        flex-direction: column;
        gap: 0.8em;
    }

    .form-container > * {
        border-radius: 0.5em;
        border: #444444 1px solid;
        padding: 0.3em;
    }

    .fotoperfil {
        width: 12em;
        border-radius: 50%;
        border: 1px rgb(0, 0, 0) solid;
    }

    .itens {
        display: flex;
        justify-content: center;
        gap: 5em;
        align-items: center;
    }

    .botao:active {
        background-color: #ff7b7b;
    }

</style>