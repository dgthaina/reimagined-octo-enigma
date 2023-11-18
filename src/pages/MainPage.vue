<template>
    <div class="container-maior">
        <div class="container">
                <div class="itens">
                    <div class="form-container">
                        <input type="text" class="titulo" placeholder="Título da atividade" v-model="titulo">
                        <input type="text" class="descricao" placeholder="Descrição" v-model="descricao">
                        <div style="display: flex; justify-content: center;">
                            <label for="diariamente">Repetir diariamente</label>
                            <input style="width: 1.5em;" type="checkbox" name="diariamente" v-model="diariamente">
                        </div>
                        <label v-show="!diariamente" for="diasemana">Dia da semana:</label>
                        <select v-show="!diariamente" name="diasemana" id="" v-model="dia">
                            <option value="1">Segunda-feira</option>
                            <option value="2">Terça-feira</option>
                            <option value="3">Quarta-feira</option>
                            <option value="4">Quinta-feira</option>
                            <option value="5">Sexta-feira</option>
                        </select>
                        <label>Horário inicial</label>
                        <input type="time" class="horainicio" v-model="inicio">
                        <label>Horário final</label>
                        <input type="time" class="horafim" v-model="fim">
                        <button class="botao" @click="adicionar">Cadastrar</button>
                    </div>
                </div>

                <div style="display: flex; gap: 2em; font-size: 1em; border-radius: 1em; border: 2px black solid;" class="contagem">
                    <p>Carga horária devida: {{ cargaDevida }}</p>
                    <p>Carga horária cumprida: {{ contarCarga() }}</p>
                    <p style="color: green;" v-show="cargaDevida == contarCarga()">Situação: Ok.</p>
                    <p style="color: red;" v-show="cargaDevida < contarCarga()">Situação: Carga excedente de {{ contarCarga() - cargaDevida }} horas.</p>
                    <p style="color: red;" v-show="cargaDevida > contarCarga()">Situação: Carga insuficiente: cumpra mais {{ cargaDevida - contarCarga() }} horas.</p>
                </div>

                <div class="quadro">
                    <table>
                        <thead>
                            <tr>
                                <th>Dia</th>
                                <th>1 <br><span class="hora">7:30 - 8:15</span></th>
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
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                            </tr>

                            <tr>
                                <td class="corzinha"> Ter</td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                            </tr>

                            <tr>
                                <td class="corzinha">Qua</td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                            </tr>

                            <tr>
                                <td class="corzinha">Qui</td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                            </tr>

                            <tr>
                                <td class="corzinha">Sex</td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
                                <td class="espaco" @click="abrirModal($event)"></td>
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
                <h4>Editar</h4>
                <label for="titulo">Título</label>
                <input type="text" name="titulo">
                <label for="descricao">Descrição</label>
                <textarea name="descricao" cols="30" rows="10"></textarea>
                <div class="botoes">
                    <button @click="editar">Salvar</button>
                    <button @click="sumir">Fechar</button>
                    <button @click="excluir">Excluir</button>
                </div>
            </div>
        </div>
    </template>

    <script>
        export default {
            name: "MainPage",
            data() {
                return {
                    titulo: "",
                    descricao: "",
                    dia: "1",
                    inicio: "",
                    fim: "",
                    diariamente: "",
                    atividadeSelecionada: "",
                    listaAtividades: [],
                    autoIncremento: 0,
                    cargaDevida: localStorage['cargahoraria'],
                    horariosPossiveisInicio: [
                        730, 815, 900, 1000, 1045, 1330, 1415, 1500, 1600, 1645, 1900, 1950, 2050, 2140
                    ],
                    horariosPossiveisFim: [
                        815, 900, 945, 1045, 1130, 1415, 1500, 1545, 1645, 1730, 1950, 2040, 2140, 2230
                    ]
                }
            },       

            beforeMount () {
                if (localStorage.getItem('cargahoraria') == undefined) {
                    alert('ATENÇÃO! Realize seu cadastro antes de acessar o quadro.');
                    window.location.href = '/subscribe';
                }
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
                    fim: this.fim,
                    diariamente: this.diariamente
                });

                this.desenhar(this.autoIncremento);
            },
            desenhar(idAtividade) {
                let atividade = this.listaAtividades.find(a => a != undefined && a.id == idAtividade);

                let indexInicio = this.horariosPossiveisInicio.indexOf(parseInt(atividade.inicio.replace(':', ''))) + 2;
                let indexFim = this.horariosPossiveisFim.indexOf(parseInt(atividade.fim.replace(':', ''))) + 2;
                let indexes = [];

                for (let i = indexInicio; i <= indexFim; i++) {
                    indexes.push(i);
                }

                let elementos = []

                if (atividade.diariamente) {
                    for (let dia = 1; dia <= 5; dia++) {
                        indexes.forEach(e => {
                            elementos.push(document.querySelector(`table tbody tr:nth-child(${dia}) td:nth-child(${e})`));
                        });
                    }
                } else {
                    indexes.forEach(e => {
                        elementos.push(document.querySelector(`table tbody tr:nth-child(${atividade.dia}) td:nth-child(${e})`));
                    });
                }
                

                for (let elemento of elementos) {
                    elemento.textContent = atividade.titulo;
                    elemento.classList.add('preenchido');
                    elemento.classList.add(`atividade-${idAtividade}`);
                }
            },
            apagar(idAtividade) {
                let atividade = this.listaAtividades.find(a => a != undefined && a.id == idAtividade);

                let indexInicio = this.horariosPossiveisInicio.indexOf(parseInt(atividade.inicio.replace(':', ''))) + 2;
                let indexFim = this.horariosPossiveisFim.indexOf(parseInt(atividade.fim.replace(':', ''))) + 2;
                let indexes = [];

                for (let i = indexInicio; i <= indexFim; i++) {
                    indexes.push(i);
                }

                let elementos = []

                if (atividade.diariamente) {
                    for (let dia = 1; dia <= 5; dia++) {
                        indexes.forEach(e => {
                            elementos.push(document.querySelector(`table tbody tr:nth-child(${dia}) td:nth-child(${e})`));
                        });
                    }
                } else {
                    indexes.forEach(e => {
                        elementos.push(document.querySelector(`table tbody tr:nth-child(${atividade.dia}) td:nth-child(${e})`));
                    });
                }

                for (let elemento of elementos) {
                    elemento.textContent = "";
                    elemento.classList.remove('preenchido');
                    elemento.classList.remove(`atividade-${idAtividade}`);
                }
            },
            abrirModal(evento) {
                let elementoClicado = evento.srcElement;

                let classe = elementoClicado.classList.value.split(' ').find(c => (/^atividade-/).test(c));

                if (classe == undefined) {
                    return;
                }

                let idAtividade = classe.replace(/^atividade-(\d+)$/, "$1");

                this.atividadeSelecionada = idAtividade;

                document.querySelector('.modal').style.display = 'flex';
                document.querySelector('.modal h3').textContent = 'Título: ' + this.listaAtividades.find(a => a != undefined && a.id == idAtividade).titulo;
                document.querySelector('.modal p').textContent = 'Descrição: ' + this.listaAtividades.find(a => a != undefined && a.id == idAtividade).descricao;
            },
            sumir() {
                document.querySelector('.modal').style.display = 'none';
            },
            editar() {
                let atividade = this.listaAtividades.find(a => a != undefined && a.id == this.atividadeSelecionada);
                atividade.titulo = document.getElementsByName('titulo')[0].value;
                atividade.descricao = document.getElementsByName('descricao')[0].value;
                document.getElementsByName('titulo')[0].value = "";
                document.getElementsByName('descricao')[0].value = "";
                this.sumir();
                this.desenhar(this.atividadeSelecionada);
            },
            excluir() {
                if (!(confirm('O (a) senhor(a) tem certeza que deseja excluir a atividade?'))){
                    return;
                }

                this.sumir();
                this.apagar(this.atividadeSelecionada);

                delete this.listaAtividades[this.listaAtividades.indexOf(this.listaAtividades.find(a => a != undefined && a.id == this.atividadeSelecionada))];
            },
            contarCarga() {

                let horasCumpridasSemanalmente = 0;

                this.listaAtividades.forEach(atividade => {
                    // let inicio = parseInt(atividade.inicio.replace(':', ''));
                    // let fim = parseInt(atividade.fim.replace(':', ''));

                    let [horaInicio, minutoInicio] = atividade.inicio.split(':').map(n => parseInt(n));
                    let [horaFim, minutoFim] = atividade.fim.split(':').map(n => parseInt(n));

                    let minutosInicio = horaInicio * 60 + minutoInicio;
                    let minutosFim = horaFim * 60 + minutoFim;

                    console.log(minutosInicio);
                    console.log(minutosFim);

                    horasCumpridasSemanalmente += (minutosFim - minutosInicio) / 60;
                });

                return horasCumpridasSemanalmente;
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

    #modal-timeline #modal-container .botoes {
        display: flex;
        justify-content: center;
        gap: 0.2em;
    }

    #modal-timeline #modal-container .botoes button:first-child {
        background-color: #a70000;
        color: white;
    }

    #modal-timeline #modal-container button {
        border: 0.1em black solid;
        border-radius: 1em;
        background-color: rgb(230, 230, 230);
        padding: 0.5em;
        margin-top: 1.5em;
    }

    .contagem {
        position: absolute;
        top: 0;
        left: 0;
        background-color: white;
        margin-top: 1em;
        padding-block: 0.2em;
        padding-inline: 2em; 
    }

</style>