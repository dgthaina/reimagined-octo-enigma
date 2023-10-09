<template>
    <div class="container">
        <div class="frase">
            <h1>oiiiiiiiiiiiiiii bem vindo</h1>
        </div>
        <div class="itens">
            <div class="form-container">
                <input type="text" class="nome" placeholder="Nome Completo">
                <input type="text" class="siape" placeholder="SIAPE">
                <input type="text" class="senha" placeholder="Senha">
                <input type="text" class="carga" placeholder="Carga Horária">
                <input type="text" class="email" placeholder="E-mail">
                <button>Enviar</button>
            </div>
            <div class="foto">
                <img src="../assets/img/socorro.jpg" alt="">
            </div>
        </div>
    </div>
</template>

<script>


</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Autour+One&display=swap');
    body {
        background-color: #a70000;
        background-image: radial-gradient(#ffffff 0.5px, transparent 0.5px), radial-gradient(#ffffff 0.5px, #a70000 0.5px);
        background-size: 20px 20px;
        background-position: 0 0, 10px 10px;
        font-family: 'Autour One', cursive;
        width: 100%;
        height: 100vh;
    }

    .container {
        background-color: white;
        border: 2px black solid;
        border-radius: 1em;
    }

    .frase {
        display: flex;
        justify-content: center;
    }

    .form-container {
        display: flex;
        flex-direction: column;
    }
</style>