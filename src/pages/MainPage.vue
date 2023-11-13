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
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                        </tr>

                        <tr>
                            <td class="corzinha"> Ter</td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                        </tr>

                        <tr>
                            <td class="corzinha">Qua</td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                        </tr>

                        <tr>
                            <td class="corzinha">Qui</td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                        </tr>

                        <tr>
                            <td class="corzinha">Sex</td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                            <td class="espaco" @click="editar($event)"></td>
                        </tr>
                    </tbody>
                </table>
            </div>

        </div>
    </div>

    <div id="modal-timeline" class="modal">
        <div id="modal-container">
            <h3></h3>
            <p></p>
            <button id="close-modal" @click="sumir">Fechar</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "MainPage",
        data() {
            return {
                titulo: "getulho vargas",
                descricao: "pai dos pobres",
                dia: "1",
                inicio: "07:30",
                fim: "08:15",
                listaAtividades: [],
                autoIncremento: 0,
                horariosPossiveisInicio: [
                    730, 815, 900, 1000, 1045, 1330, 1415, 1500, 1600, 1645, 1900, 1950, 2050, 2140
                ],
                horariosPossiveisFim: [
                    815, 900, 945, 1045, 1130, 1415, 1500, 1545, 1645, 1730, 1950, 2040, 2140, 2230
                ]
            }
        },       
        
        mounted() {
            console.log(this.listaAtividades);
        },

        methods: {
            adicionar() {
                if (!(this.dia) || !(this.titulo) || !(this.descricao)) { // if (condição não fake)
                    alert('Olá parceiro!! Infelizmente você deve inserir todos os itens para que o sistema funcione :)');
                    return;
                }

                if (parseInt(this.inicio.replace(':', '')) > parseInt(this.fim.replace(':', ''))) {
                    alert('Ei amigo!!!!! Você está invertendo a ordem de seus horários. Verifique os dados e INTRODUZA novamente.');
                    return;
                }

                if (!(this.horariosPossiveisInicio.includes(parseInt(this.inicio.replace(':', ''))) || this.horariosPossiveisFim.includes(parseInt(this.fim.replace(':', ''))))) {
                    alert('ATENÇÃO! Horário não permitido.');
                    return;
                }

                let atividadesDoDia = this.listaAtividades.filter((atividade) => atividade.dia == this.dia);
                let minutosDeCadaAtividadeDoDia = atividadesDoDia.map((atividade) => {
                    let minutoInicial = parseInt(atividade.inicio.replace(':', ''));
                    let minutoFinal = parseInt(atividade.fim.replace(':', ''));
                    
                    let listaMinutos = [];

                    for (
                        let minuto = minutoInicial;
                        minuto < minutoFinal;
                        minuto++
                        ) {
                            listaMinutos.push(minuto);
                    }

                    return listaMinutos;
                });

                let minutosDaAtividade = []

                let minutoInicial = parseInt(this.inicio.replace(':', ''));
                let minutoFinal = parseInt(this.fim.replace(':', ''));

                for (
                    let minuto = minutoInicial;
                    minuto < minutoFinal;
                    minuto++
                ) {
                    minutosDaAtividade.push(minuto);
                }

                for (let minuto of minutosDaAtividade) {
                    for (let minutos of minutosDeCadaAtividadeDoDia) {
                        if (minutos.includes(minuto)) {
                            alert('Ei amigo!!!!! Você está intercedendo a ordem de seus horários. Verifique os dados e introduza novamente.');
                            return;
                        }
                    }
                }

                this.autoIncremento++;

                this.listaAtividades.push({
                    id: this.autoIncremento,
                    titulo: this.titulo,
                    descricao: this.descricao,
                    dia: this.dia,
                    inicio: this.inicio,
                    fim: this.fim
                });

                this.desenhar(this.autoIncremento);
            },
            desenhar(idAtividade) {
                let atividade = this.listaAtividades.find(a => a.id == idAtividade)

                let indexInicio = this.horariosPossiveisInicio.indexOf(parseInt(atividade.inicio.replace(':', ''))) + 2;
                let indexFim = this.horariosPossiveisFim.indexOf(parseInt(atividade.fim.replace(':', ''))) + 2;
                let indexes = [];

                for (let i = indexInicio; i <= indexFim; i++) {
                    indexes.push(i);
                }

                let elementos = []

                indexes.forEach(e => {
                    elementos.push(document.querySelector(`table tbody tr:nth-child(${atividade.dia}) td:nth-child(${e})`));
                });

                for (let elemento of elementos) {
                    elemento.textContent = atividade.titulo;
                    elemento.classList.add('preenchido');
                    elemento.classList.add(`atividade-${idAtividade}`);
                }
            },
            editar(evento) {
                let elementoClicado = evento.srcElement;

                let classe = elementoClicado.classList.value.split(' ').find(c => (/^atividade-/).test(c));

                if (classe == undefined) {
                    return;
                }

                let idAtividade = classe.replace(/^atividade-(\d+)$/, "$1");

                document.querySelector('.modal').style.display = 'flex';
                document.querySelector('.modal h3').textContent = this.listaAtividades.find(a => a.id == idAtividade).titulo;
                document.querySelector('.modal p').textContent = this.listaAtividades.find(a => a.id == idAtividade).descricao;
            },
            sumir() {
                document.querySelector('.modal').style.display = 'none';
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

    .espaco {
        font-size: 0.5em;
    }

    .preenchido {
        background-color: rgb(213, 213, 213);
        cursor: pointer;
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

    #modal-timeline {
        position: fixed;
        top: 0;
        left: 0;
        z-index: 50;
        right: 0;
        bottom: 0;
        background-color: rgba(128, 128, 128, 0.5);
        transition: .3s;
        width: 100%;
        height: 100%;
        align-items: center;
        justify-content: center;
        display: none;
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