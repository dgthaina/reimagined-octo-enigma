<template>
    <div class="container-maior">
        <div class="container">
            <div class="itens">
                <div class="form-container">
                    <input type="text" class="titulo" placeholder="Título da atividade" v-model="titulo">
                    <input type="text" class="descricao" placeholder="Descrição" v-model="descricao">
                    <label for="diasemana">Dia da semana:</label>
                    <select name="diasemana" id="" v-model="dia">
                        <option value="1">Segunda-feira</option>
                        <option value="2">Terça-feira</option>
                        <option value="3">Quarta-feira</option>
                        <option value="4">Quinta-feira</option>
                        <option value="5">Sexta-feira</option>
                    </select>
                    <label for="diasemana">Horário inicial</label>
                    <input type="time" class="horainicio" v-model="inicio">
                    <label for="diasemana">Horário final</label>
                    <input type="time" class="horafim" v-model="fim">
                    <button class="botao" @click="adicionar">Cadastrar</button>
                </div>
            </div>

            <div class="quadro">
                <table>
                    <thead>
                        <tr>
                            <th>Dia</th>
                            <th>1 <br> <span class="hora">7:30 - 8:15</span></th>
                            <th>2 <br><span class="hora">8:15 - 9:00</span></th>
                            <th>3 <br><span class="hora">9:00 - 9:45</span></th>
                            <th>4 <br><span class="hora">10:00 - 10:45</span></th>
                            <th>5 <br><span class="hora">10:45 - 11:30</span></th>
                            <th>6 <br><span class="hora">13:30 - 14:15</span></th>
                            <th>7 <br><span class="hora">14:15 - 15:00</span></th>
                            <th>8 <br><span class="hora">15:00 - 15:45</span></th>
                            <th>9 <br><span class="hora">16:00 - 16:45</span></th>
                            <th>10 <br><span class="hora">16:45 - 17:30</span></th>
                            <th>11 <br><span class="hora">19:00 - 19:50</span></th>
                            <th>12 <br><span class="hora">19:50 - 20:40</span></th>
                            <th>13 <br><span class="hora">20:50 - 21:40</span></th>
                            <th>14 <br><span class="hora">21:40 - 22:30</span></th>

                        </tr>
                    </thead>

                    <tbody>
                        <tr>
                            <td class="corzinha">Seg</td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td class="corzinha"> Ter</td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td class="corzinha">Qua</td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td class="corzinha">Qui</td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td class="corzinha">Sex</td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                            <td></td>
                        </tr>

                    </tbody>
                </table>
            </div>

        </div>
    </div>

    <Modal-Atividade />
</template>

<script>
    import ModalAtividade from "../components/ModalAtividade.vue"
    export default {
        name: "MainPage",
        components: {
            ModalAtividade,
            
        },
        data() {
            return {
                titulo: "",
                descricao:"",
                dia:"",
                inicio:"",
                fim:"",
                listaAtividades: []
            }
        },       
        

        methods: {
            adicionar() {
                this.listaAtividades.push({
                    titulo: this.titulo,
                    descricao: this.descricao,
                    dia: this.dia,
                    inicio: this.inicio,
                    fim: this.fim
                });
                console.log(this.listaAtividades)
            }

        }

    }




</script>

<style scoped>
    .container {
        background-color: white;
        border: 2px black solid;
        border-radius: 1em;
        width: 95%;
        height: 80%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .container > * {
        margin: 0 3em;
    }

    .container-maior {
        display: flex;
        justify-content: center;
        height: 100vh;
        align-items: center;
    }

    .form-container {
        display: flex;
        flex-direction: column;
        gap: 0.5em;
    }

    .itens {
        justify-content: center;
        display: flex;
        padding: 1.2em; 
    }

    td, th {
        border: black solid 2px;
        width: 5em;
        height: 5em;
        text-align: center;
    }

    th, .corzinha {
        background-color: rgb(192, 255, 255);
}

    table {
        border-spacing: 0;
        border-collapse: collapse;
        font-size: 1em;
        border-radius: 1em;
    }
    .hora {
        font-size: 0.52em;
    }

</style>