<template>
    <div class="container-maior">
        <div class="container">
                <div class="itens">
                    <div class="form-container"> <!-- Campos de inserção - todos ligados com a diretiva v-model -->
                        <!-- Título -->
                        <input type="text" class="titulo" placeholder="Título da atividade" v-model="titulo">
                        <!-- Descrição -->
                        <input type="text" class="descricao" placeholder="Descrição" v-model="descricao">
                        <!-- Periodicidade -->
                        <div style="display: flex; justify-content: center;">
                            <label for="diariamente">Repetir diariamente</label>
                            <input style="width: 1.5em;" type="checkbox" name="diariamente" v-model="diariamente">
                        </div>
                        <!-- Dia da atividade -->
                        <!-- OBS: Note que os elementos abaixo possuem a diretiva v-show -->
                        <!-- Isto ocorre porque, se o usuário indicou periodicidade diária da atividade -->
                        <!-- não é conveniente solicitar a ele a inserção de um dia específico para atividade -->
                        <label v-show="!diariamente" for="diasemana">Dia da semana:</label>
                        <select v-show="!diariamente" name="diasemana" id="" v-model="dia">
                            <option value="1">Segunda-feira</option>
                            <option value="2">Terça-feira</option>
                            <option value="3">Quarta-feira</option>
                            <option value="4">Quinta-feira</option>
                            <option value="5">Sexta-feira</option>
                        </select>
                        <!-- Horário inicial -->
                        <label>Horário inicial</label>
                        <input type="time" class="horainicio" v-model="inicio">
                        <!-- Horário final -->
                        <label>Horário final</label>
                        <input type="time" class="horafim" v-model="fim">
                        <!-- Cadastro da atividade -->
                        <button class="botao" @click="adicionar">Cadastrar</button>
                    </div>
                </div>

                <!-- Quadro de status da carga horária -->
                <div style="display: flex; gap: 2em; font-size: 1em; border-radius: 1em; border: 2px black solid;" class="contagem">
                    <!-- Carga horária devida provém de um dado salvo no localStorage do navegador do usuário -->
                    <!-- Essa informação é carregada previamente na seção de dados do componente -->
                    <p>Carga horária devida: {{ cargaDevida }}</p>
                    <!-- O campo abaixo é atualizado dinamicamente pela função "contarCarga", cujo nome explica sua função -->
                    <p>Carga horária cumprida: {{ contarCarga() }}</p>
                    <!-- Os campos abaixo possuem a diretiva v-show para estabelecer condições para as diferentes situações -->
                    <!-- de cumprimento de carga horária -->
                    <p style="color: green;" v-show="cargaDevida == contarCarga()">Situação: Ok.</p>
                    <!-- Condição nº 1: Situação ok: a carga devida é igual à contagem total das atividades exercidas -->
                    <p style="color: red;" v-show="cargaDevida < contarCarga()">Situação: Carga excedente de {{ contarCarga() - cargaDevida }} horas.</p>
                    <!-- Condição nº 2: Situação excedente: a carga cumprida excede o valor da carga devida -->
                    <p style="color: red;" v-show="cargaDevida > contarCarga()">Situação: Carga insuficiente: cumpra mais {{ cargaDevida - contarCarga() }} horas.</p>
                    <!-- Condição nº 3: Situação insuficiente: a carga cumprida não atinge o valor da carga devida -->
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

                        <!-- Abaixo se encontram os espaços para atividade. -->
                        <!-- Cada um possui a função abrirModal, que funciona caso o elemento possua -->
                        <!-- a classe "preenchido" -->

                        <!-- Ao inserirmos atividades no quadro, os espaços preenchidos -->
                        <!-- possuirão uma classe identificadora da atividade, -->
                        <!-- que possibilitará a associação entre os dados e a interface do quadro -->
                        <!-- Dica: imagine esta identificação como se fosse uma "chave estrangeira" -->
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

        <!-- Modal de visualização, edição e exclusão de atividades -->
        <div id="modal-timeline" class="modal">
            <div id="modal-container">
                <!-- Título da atividade -->
                <h3></h3>
                <!-- Descrição da atividade -->
                <p></p>
                <h4>Editar</h4>
                <!-- Campo para novo título -->
                <label for="titulo">Título</label>
                <input type="text" name="titulo">
                <!-- Campo para nova descrição -->
                <label for="descricao">Descrição</label>
                <textarea name="descricao" cols="30" rows="10"></textarea>
                <!-- Botões relacionados ao CRUD -->
                <div class="botoes">
                    <!-- Edição -->
                    <button @click="editar">Salvar</button>
                    <!-- Cancelamento (ou desistência) da operação -->
                    <button @click="sumir">Fechar</button>
                    <!-- Exclusão -->
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
                    /* ------------------------------------------------------------------------ */
                    /* Dados provenientes dos campos do formulário */
                    titulo: "",
                    descricao: "",
                    dia: "1",
                    inicio: "",
                    fim: "",
                    diariamente: "",
                    /* ------------------------------------------------------------------------ */
                    /* Indicação da atividade sendo manipulada (este dado é utilizado, como exemplo,
                    nas operações de edição exclusão. Dessa forma, o sistema sabe qual atividade manipular) */
                    atividadeSelecionada: "",
                    /* Lista de atividades: provavelmente o elemento mais importante para o funcionamento do
                    sistema */
                    listaAtividades: [],
                    /* Auto incremento: controla o valor do ID da atividade */
                    autoIncremento: 0,
                    /* Carga devida: carregamento da carga horária do usuário, proveniente do dado
                    salvo em localStorage no momento do cadastro */
                    cargaDevida: localStorage['cargahoraria'],
                    /* Horários possíveis para o início de uma atividade: lista utilizada para verificação 
                    da validade dos horários inseridos nos campos de cadastro de atividade */
                    horariosPossiveisInicio: [
                        730, 815, 900, 1000, 1045, 1330, 1415, 1500, 1600, 1645, 1900, 1950, 2050, 2140
                    ],
                    /* Horários possíveis para o fim de uma atividade: lista utilizada para verificação 
                    da validade dos horários inseridos nos campos de cadastro de atividade */
                    horariosPossiveisFim: [
                        815, 900, 945, 1045, 1130, 1415, 1500, 1545, 1645, 1730, 1950, 2040, 2140, 2230
                    ]
                }
            },       

            /* Referente ao ciclo de vida do componente, antes de carregar a página, o sistema verifica
            se o usuário possui o cadastro. Isso é necessário, pois o sistema precisa ter a informação
            da carga horária do usuário */
            beforeMount () {
                if (localStorage.getItem('cargahoraria') == undefined) {
                    alert('ATENÇÃO! Realize seu cadastro antes de acessar o quadro.');
                    window.location.href = '/subscribe';
                }
            },

            methods: {
                /* adicionar: Método para adicionar atividade ao quadro */
                /* Funções: Verificar validade dos campos enviados, adição da atividade
                na lista de atividades e chamada da função para "desenhar" atividade no quadro */
                adicionar() {
                    if (!(this.dia) || !(this.titulo) || !(this.descricao)) { 
                        /* Verificação de campos obrigatórios */
                        alert('Olá parceiro!! Infelizmente você deve inserir todos os itens para que o sistema funcione :)');
                        return;
                    }

                    if (parseInt(this.inicio.replace(':', '')) > parseInt(this.fim.replace(':', ''))) { 
                        /* Garantia de que o horário de fim não antecede o horário de início */
                        alert('Ei amigo!!!!! Você está invertendo a ordem de seus horários. Verifique os dados e INTRODUZA novamente.');
                        return;
                    }

                    if (!(this.horariosPossiveisInicio.includes(parseInt(this.inicio.replace(':', ''))) || this.horariosPossiveisFim.includes(parseInt(this.fim.replace(':', ''))))) {
                        /* Garantia de que os horários de início e fim são válidos perante as regras de negócio do sistema */
                        /* Exemplo de horário de início válido: 07:30 */
                        /* Exemplo de horário de início inválido: 07:00 */
                        alert('ATENÇÃO! Horário não permitido.');
                        return;
                    }

                

                let atividadesDoDia;

                if (!this.diariamente) {
                    /* Filtro da lista de atividades, filtrando apenas atividades correspondentes
                    ao dia em que se deseja inserir uma atividade */
                    atividadesDoDia = this.listaAtividades.filter((atividade) => atividade.dia == this.dia);
                } else {
                    /* Verificação deve ocorrer entre todas as atividades, afinal, a atividade
                    ocupará todos os dias */
                    atividadesDoDia = this.listaAtividades;
                }
                
                /* A verificação de interseção de horário de atividades se dá por meio da lógica de conjuntos:
                Uma atividade A possui um horário inicial e um horário final.
                Entre um horário inicial e um horário final, existem diversos minutos que uma atividade ocupa.
                Sendo assim, essa função gera, a partir da lista de atividades do dia, o conjunto de minutos
                que cada atividade ocupa.
                Para verificar interseção de horários de atividades, basta comparar o conjunto de minutos
                da atividade da inserção com o conjunto de minutos das atividades do dia, verificando se
                existe qualquer igualdade de minutos */

                /* --------------------------------------------------- */
                /* Geração de minutos das atividades JÁ CADASTRADAS */

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

                /* --------------------------------------------------- */

                /* --------------------------------------------------- */
                /* Geração de minutos da atividade A SER INSERIDA */

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

                /* --------------------------------------------------- */

                /* Abaixo está a lógica para verificação de interseção */

                for (let minuto of minutosDaAtividade) { /* Para cada minuto da atividade a ser inserida */
                    for (let minutos of minutosDeCadaAtividadeDoDia) { /* Para cada lista de minutos das atividades do dia */
                        if (minutos.includes(minuto)) { /* Verificar se o minuto está na lista */
                            alert('Ei amigo!!!!! Você está intercedendo a ordem de seus horários. Verifique os dados e introduza novamente.');
                            return;
                        }
                    }
                }

                /* A partir desta linha, a atividade já considerada válida. Portanto, abaixo, atualizamos
                a variável de auto incremento que controla a atribuição de identificadores para as atividades */

                this.autoIncremento++;

                /* Inserção da atividade na lista de atividades: */

                this.listaAtividades.push({
                    id: this.autoIncremento,
                    titulo: this.titulo,
                    descricao: this.descricao,
                    dia: this.dia,
                    inicio: this.inicio,
                    fim: this.fim,
                    diariamente: this.diariamente
                });

                /* Chamada da função para desenhar na interface do quadro de horários: */

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
                    elemento.classList.add(`atividade-${idAtividade}`); // Atribuição de identificador
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
                } // Faz o contrário da função desenhar
            },
            abrirModal(evento) {
                let elementoClicado = evento.srcElement; // Caminho para identificação do elemento

                let classe = elementoClicado.classList.value.split(' ').find(c => (/^atividade-/).test(c)); // Extração de explicar

                if (classe == undefined) { // Verificação de atividade preenchida com classe de associação atividade-interface
                    return;
                }

                let idAtividade = classe.replace(/^atividade-(\d+)$/, "$1"); // Extrai da classe o número identificador

                this.atividadeSelecionada = idAtividade;

                document.querySelector('.modal').style.display = 'flex'; // Aparecer
                document.querySelector('.modal h3').textContent = 'Título: ' + this.listaAtividades.find(a => a != undefined && a.id == idAtividade).titulo; // Inserção do título na interface de visualização
                document.querySelector('.modal p').textContent = 'Descrição: ' + this.listaAtividades.find(a => a != undefined && a.id == idAtividade).descricao; // Inserção da descrição na interface de visualização
            },
            sumir() {
                document.querySelector('.modal').style.display = 'none';
            },
            editar() {
                let atividade = this.listaAtividades.find(a => a != undefined && a.id == this.atividadeSelecionada);
                atividade.titulo = document.getElementsByName('titulo')[0].value;
                atividade.descricao = document.getElementsByName('descricao')[0].value;
                document.getElementsByName('titulo')[0].value = ""; // Limpar valores dos campos
                document.getElementsByName('descricao')[0].value = ""; // Limpar valores dos campos
                this.sumir();
                this.desenhar(this.atividadeSelecionada);
            },
            excluir() {
                if (!(confirm('O (a) senhor(a) tem certeza que deseja excluir a atividade?'))){
                    return;
                }

                this.sumir();
                this.apagar(this.atividadeSelecionada); // Apagar da interface

                // Apagar da lista
                delete this.listaAtividades[this.listaAtividades.indexOf(this.listaAtividades.find(a => a != undefined && a.id == this.atividadeSelecionada))];
            },
            contarCarga() {
                let horasCumpridasSemanalmente = 0;

                this.listaAtividades.forEach(atividade => {
                    let [horaInicio, minutoInicio] = atividade.inicio.split(':').map(n => parseInt(n));
                    let [horaFim, minutoFim] = atividade.fim.split(':').map(n => parseInt(n));

                    let minutosInicio = horaInicio * 60 + minutoInicio;
                    let minutosFim = horaFim * 60 + minutoFim;

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