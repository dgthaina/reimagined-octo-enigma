<template>
    <div id="modal-timeline">
        <div id="modal-container">
            <h3>Título: {{ titulo }}</h3>
            <p></p>
            <button id="close-modal">Fechar</button>
        </div>
    </div>

</template>

<script>
    export default {
        name: "MainPage",
        data() {
            return {
                titulo: "Aula de artes 2f"
            }
        }
    }
</script>

<style>
    #modal-timeline {
        position: fixed;
        top: 0;
        left: 0;
        z-index: 50;
        right: 0;
        bottom: 0;
        background-color: rgba(128, 128, 128, 0.5);
        display: flex;
        opacity: 0;
        display: none;
        transition: .3s;
        width: 100%;
        height: 100%;
        align-items: center;
        justify-content: center;
    }
    #modal-timeline #modal-container {
        top: 50%;
        left: 50%;
        background-color: white;
        margin: 2em 15em;
        padding: 0.5em;    
        border: 0.5em #a70000 solid;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
    }
    #modal-timeline #modal-container p {
        text-align: justify;
        text-indent: 0.5em;
        font-size: 0.9em;
    }
    #modal-timeline #modal-container button {
        border: 0.1em black solid;
        border-radius: 1em;
        background-color: rgb(230, 230, 230);
        padding: 0.5em;
        margin-top: 1.5em;
    }
</style>