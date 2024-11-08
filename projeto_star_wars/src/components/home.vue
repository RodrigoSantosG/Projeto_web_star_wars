<template>
    <div class="home">
        <v-main>
            <v-container>
                <v-row>
                    <v-col>
                        <v-card flat class="border mb-4">
                            <div style="display: flex; justify-content: space-between; align-items: center;">
                                <v-card-text>
                                    <v-text-field v-model="searchQuery" :loading="loading" density="compact"
                                        label="Pesquisa algum personagem" variant="solo" hide-details single-line
                                        @keydown.enter="onSearchInput">
                                    </v-text-field>
                                    <br>
                                    <!-- Botão de pesquisa -->

                                    <v-btn @click="onSearchInput" color="grey" :loading="loading" class="">
                                        Pesquisar
                                    </v-btn>

                                    <!-- Apagar pesquisa -->

                                    <v-btn @click="clearSearch">
                                        Apagar
                                    </v-btn>

                                </v-card-text>
                            </div>
                            <!-- Exibir mensagem caso nenhum personagem tinha sido encontrado -->

                            <v-alert v-if="noResultsFound" type="error" class="mt-4">
                                Nenhum personagem encontrado. Tente novamente.
                            </v-alert>
                        </v-card>
                    </v-col>
                </v-row>
                <v-row>

                    <!-- Tela do Luke Skywalker -->

                    <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
                        <v-card>
                            <v-img src="../assets/imagem_star_wars/personagem/Luke.jpeg" style="height: 545px"
                                class="align-end text-white">
                            </v-img>
                            <v-card-title class="pt-4" style="border-bottom: 2px solid white">Luke
                                Skywalker</v-card-title>
                            <v-card-title class="pt-2" style="font-size: 18px">Feitos:</v-card-title>
                            <v-card-text>
                                Luke Skywalker é um herói central em Star Wars, conhecido por
                                destruir a Estrela da Morte com a ajuda da Força e redimir seu
                                pai, Darth Vader, que derrotou o Imperador. Treinado por Yoda,
                                ele se tornou um Jedi poderoso, resgatou Han Solo e enfrentou
                                Jabba, o Hutt. Em "Os Últimos Jedi", Luke se sacrificou para
                                salvar a Resistência, usando uma projeção de si mesmo. Após sua
                                morte, ele guiou Rey, transmitindo seus ensinamentos e cumprindo
                                o legado Jedi, trazendo paz à galáxia.
                            </v-card-text>
                            <v-card-actions>

                                <!-- Ativador do diálogo -->

                                <v-dialog v-model="lukeDialogActive" max-width="500">
                                    <template v-slot:activator="{ props }">
                                        <v-btn v-bind="props" color="white" text="Ver Mais" variant="flat">
                                        </v-btn>
                                        <v-icon class="mdi mdi-fencing"></v-icon>
                                    </template>

                                    <!-- Conteúdo do diálogo -->

                                    <v-card title="Luke Skywalker">
                                        <v-img
                                            src="../assets/imagem_star_wars/personagem_segundo_plano/Luke Skywalker.jpeg"
                                            class="align-end text-white" style="height: 700px"></v-img>
                                        <v-card-title class="pt-2" style="font-size: 18px">Historia:</v-card-title>
                                        <v-card-text>
                                            A história de Luke Skywalker começa em Tatooine, onde ele
                                            vive com seus tios, sem saber de seu verdadeiro legado.
                                            Sua vida muda quando ele encontra a mensagem de Leia e
                                            conhece o Jedi Obi-Wan Kenobi. Juntos, eles se unem à
                                            Aliança Rebelde para derrotar o Império Galáctico. Luke
                                            destrói a Estrela da Morte com a ajuda da Força, se
                                            tornando um herói. Luke então busca treinamento com o
                                            mestre Jedi Yoda, mas interrompe o aprendizado para salvar
                                            seus amigos. Em O Império Contra-Ataca, ele descobre que
                                            Darth Vader é seu pai, um choque profundo. Mesmo assim,
                                            Luke não desiste e, em O Retorno de Jedi, ele confronta
                                            Vader e o Imperador, acreditando na redenção de seu pai.
                                            Vader se redime, destrói o Imperador e traz fim ao
                                            Império. Mais tarde, Luke tenta reconstruir a Ordem Jedi,
                                            mas se sacrifica para salvar a Resistência em "Os Últimos
                                            Jedi". Sua jornada inspira Rey, que continua seu legado
                                            Jedi. Ao longo de sua vida, Luke passa de um fazendeiro
                                            ingênuo a um dos maiores heróis da galáxia, cumprindo a
                                            profecia e trazendo equilíbrio à Força.
                                        </v-card-text>
                                        <v-card-actions>
                                            <v-spacer></v-spacer>
                                            <!-- Botão de fechar o diálogo -->
                                            <v-btn text="Fechar" @click="lukeDialogActive = false"></v-btn>
                                        </v-card-actions>
                                    </v-card>
                                </v-dialog>
                            </v-card-actions>
                        </v-card>
                    </v-col>

                    <!-- Tela do C-3PO -->

                    <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
                        <v-card>
                            <v-img src="../assets/imagem_star_wars/personagem/C-3PO.jpeg" style="height: 525px"
                                class="align-end text-white">
                            </v-img>
                            <v-card-title class="pt-4" style="border-bottom: 2px solid white">C-3PO</v-card-title>
                            <v-card-title class="pt-2" style="font-size: 18px">Feitos:</v-card-title>
                            <v-card-text>
                                C-3PO é um droide de protocolo criado por Anakin Skywalker,
                                especializado em tradução de mais de 6 milhões de idiomas. Ao
                                longo da saga Star Wars, ele se torna essencial para a Rebelião,
                                ajudando Leia a entregar os planos da Estrela da Morte e
                                desempenhando papéis chave em várias missões. Apesar de seu
                                comportamento medroso e pessimista, sua lealdade e inteligência
                                o tornam indispensável, ajudando a derrotar o Império e a
                                Primeira Ordem. Ele também salva Leia em várias ocasiões e
                                lidera outros droides em missões importantes.
                            </v-card-text>

                            <!-- Ativador do diálogo -->

                            <v-card-actions>
                                <v-dialog v-model="c3poDialogActive" max-width="500">
                                    <template v-slot:activator="{ props }">
                                        <v-btn v-bind="props" color="white" text="Ver Mais" variant="flat">
                                        </v-btn>
                                        <v-icon class="mdi mdi-robot-outline"></v-icon>
                                    </template>

                                    <!-- Conteúdo do diálogo -->

                                    <v-card title="C-3PO">
                                        <v-img src="../assets/imagem_star_wars/personagem_segundo_plano/C-3PO.jpeg"
                                            class="align-end text-white"></v-img>
                                        <v-card-title class="pt-2" style="font-size: 18px">Historia:</v-card-title>
                                        <v-card-text>
                                            C-3PO é um droide de protocolo criado por Anakin Skywalker
                                            em Tatooine, especializado em tradução e comunicação entre
                                            espécies. Ele começa sua jornada ajudando Anakin e sua
                                            mãe, e depois se junta a Padmé Amidala e aos heróis da
                                            Rebelião. Ao longo da saga, C-3PO desempenha papéis
                                            cruciais, como entregar os planos da Estrela da Morte e
                                            ajudar os heróis a derrotar o Império e a Primeira Ordem.
                                            Apesar de seu comportamento medroso e cômico, C-3PO é leal
                                            e indispensável, sendo vital em diversas missões, como
                                            salvar Leia Organa, liderar droides em Endor e decifrar
                                            códigos importantes. Ele é uma figura fundamental na luta
                                            pela liberdade da galáxia, sempre ao lado de R2-D2 e dos
                                            heróis, até a vitória final da Resistência.
                                        </v-card-text>
                                        <v-card-actions>
                                            <v-spacer></v-spacer>

                                            <!-- Botão de fechar o diálogo -->

                                            <v-btn text="Fechar" @click="c3poDialogActive = false"></v-btn>
                                        </v-card-actions>
                                    </v-card>
                                </v-dialog>
                            </v-card-actions>
                        </v-card>
                    </v-col>

                    <!-- Tela do R2-D2 -->

                    <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
                        <v-card>
                            <v-img src="../assets/imagem_star_wars/personagem/r2-d2.jpeg" style="height: 566px"
                                class="align-end text-white">
                            </v-img>
                            <v-card-title class="pt-4" style="border-bottom: 2px solid white">R2-D2</v-card-title>
                            <v-card-title class="pt-2" style="font-size: 18px">Feitos:</v-card-title>
                            <v-card-text>
                                R2-D2 é um astromech droid criado por Anakin Skywalker e
                                desempenha papéis essenciais ao longo da saga Star Wars. Ele
                                entrega os planos da Estrela da Morte a Leia Organa, ajuda Luke
                                Skywalker a encontrar Yoda e resgata Han Solo em "O Retorno de
                                Jedi". Ao lado de C-3PO, ele continua a ajudar a Resistência a
                                derrotar o Império e a Primeira Ordem, provando ser um dos
                                droides mais valiosos e leais da galáxia.
                            </v-card-text>

                            <!-- Ativador do diálogo -->

                            <v-card-actions>
                                <v-dialog v-model="r2d2DialogActive" max-width="500">
                                    <template v-slot:activator="{ props }">
                                        <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                                        <v-icon class="mdi mdi-robot-outline"></v-icon>
                                    </template>

                                    <!-- Conteúdo do diálogo -->

                                    <v-card title="R2-D2">
                                        <v-img src="../assets/imagem_star_wars/personagem_segundo_plano/r2-d2.jpeg"
                                            class="alingn-end text-white"></v-img>
                                        <v-card-title class="pt-2" style="font-size: 18px">Historia:</v-card-title>
                                        <v-card-text>
                                            R2-D2 é um astromech droid criado por Anakin Skywalker e
                                            se torna uma figura essencial em Star Wars. Ele começa sua
                                            jornada ajudando Padmé Amidala e transportando os planos
                                            da Estrela da Morte para Leia Organa em "Uma Nova
                                            Esperança". Ao longo da saga, R2 é crucial em várias
                                            missões, como ajudar Luke Skywalker a encontrar Yoda em "O
                                            Império Contra-Ataca" e resgatar Han Solo de Jabba the
                                            Hutt em "O Retorno de Jedi". R2 também acompanha os heróis
                                            durante a Guerra dos Clones e é vital na luta contra o
                                            Império e a Primeira Ordem. Em "A Ascensão Skywalker", ele
                                            ajuda a Resistência a derrotar o mal, provando ser um dos
                                            droides mais leais e corajosos da galáxia.
                                        </v-card-text>

                                        <!-- Botão de Fechar o dialogo -->

                                        <v-card-actions>
                                            <v-spacer></v-spacer>
                                            <v-btn text="Fechar" @click="r2d2DialogActive = false"></v-btn>
                                        </v-card-actions>
                                    </v-card>
                                </v-dialog>
                            </v-card-actions>
                        </v-card>
                    </v-col>

                    <!-- Tela do Darth Vader -->

                    <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
                        <v-card>
                            <v-img src="../assets/imagem_star_wars/personagem/Darth Vader.jpeg" style="height: 568px"
                                class="aling-end text-white"></v-img>
                            <v-card-title class="pt-4" style="border-bottom: 2px solid white">Darth Vader</v-card-title>
                            <v-card-title class="pt-2" style="font-size: 18px">Feitos:</v-card-title>
                            <v-card-text>
                                Darth Vader, originalmente Anakin Skywalker, foi fundamental na
                                destruição da Ordem Jedi e na ascensão do Império. Como Vader,
                                ele caçou os rebeldes e travou batalhas decisivas, como contra
                                Obi-Wan Kenobi e na Batalha de Hoth. Sua maior ação foi, no
                                entanto, sua redenção: ao salvar seu filho, Luke Skywalker, ele
                                destruiu o Imperador Palpatine e trouxe equilíbrio à galáxia,
                                sacrificando sua própria vida.
                            </v-card-text>

                            <!-- Ativador do Diálogo -->

                            <v-card-actions>
                                <v-dialog v-model="darthDialogActive" max-width="500">
                                    <template v-slot:activator="{ props }">
                                        <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                                        <v-icon class="mdi mdi-fencing"></v-icon>
                                    </template>

                                    <!-- Conteúdo do diálogo -->

                                    <v-card title="Darth Vader">
                                        <v-img
                                            src="../assets/imagem_star_wars/personagem_segundo_plano/Darth Vader.jpeg"
                                            class="alingn-end text-white"></v-img>
                                        <v-card-title class="pt-2" style="font-size: 18">Historia:</v-card-title>
                                        <v-card-text>
                                            Darth Vader, originalmente Anakin Skywalker, nasceu no
                                            planeta Tatooine e foi treinado como Jedi por Obi-Wan
                                            Kenobi. Possuía grande potencial, mas seus medos e a perda
                                            de Padmé Amidala o levaram a ser manipulado pelo Sith
                                            Darth Sidious. Ele se virou contra os Jedi, ajudou a
                                            exterminá-los e se tornou Darth Vader, um agente do
                                            Império. Após uma luta fatal com Obi-Wan, Anakin foi
                                            gravemente ferido e reconstruído com uma armadura negra,
                                            tornando-se o temido Vader. No entanto, ao descobrir que
                                            tinha um filho, Luke Skywalker, Vader passou a se
                                            questionar. No final de O Retorno de Jedi, ele se redimiu
                                            ao salvar Luke e matar o Imperador, sacrificando sua vida.
                                            Assim, cumpriu seu destino de trazer equilíbrio à Força,
                                            encontrando a paz antes de morrer.
                                        </v-card-text>

                                        <!-- Botão de Fechar o dialogo -->

                                        <v-card-actions>
                                            <v-spacer></v-spacer>
                                            <v-btn text="Fechar" @click="darthDialogActive = false"></v-btn>
                                        </v-card-actions>
                                    </v-card>
                                </v-dialog>
                            </v-card-actions>
                        </v-card>
                    </v-col>

                    <!-- Tela da Leia Organa -->
                    <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
                        <v-card>
                            <v-img src="../assets/imagem_star_wars/personagem/leia.jpeg" style="height: 430px"
                                class="aling-end text-white"></v-img>
                            <v-card-title class="pt-4" style="border-bottom: 2px solid white">Leia Organa</v-card-title>
                            <v-card-title class="pt-2" style="font-size: 18px">Feitos:</v-card-title>
                            <v-card-text>
                                Leia Organa é uma líder corajosa e estratégica que, como
                                princesa e membro da Rebelião, desempenha um papel crucial na
                                luta contra o Império e, mais tarde, contra a Primeira Ordem.
                                Ela se destaca por sua habilidade em resgatar aliados, liderar
                                batalhas e tomar decisões difíceis, como quando salva Han Solo
                                de Jabba, o Hutt. Embora não seja uma Jedi treinada, ela possui
                                habilidades com a Força e, ao longo da saga, se torna um símbolo
                                de resistência e esperança, além de ser fundamental para a
                                redenção de seu pai, Darth Vader.
                            </v-card-text>

                            <!-- Ativador do Diálogo -->

                            <v-card-actions>
                                <v-dialog v-model="leiaDialogActive" max-width="500">
                                    <template v-slot:activator="{ props }">
                                        <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                                        <v-icon class="mdi mdi-fencing"></v-icon>
                                    </template>

                                    <!-- Contéudo do diálogo -->

                                    <v-card title="Leia Organa">
                                        <v-img
                                            src="../assets/imagem_star_wars/personagem_segundo_plano/Leia Organa.jpeg"
                                            class="alingn-end text-white"></v-img>
                                        <v-card-title class="pt-2" style="font-size: 18">Historia:</v-card-title>
                                        <v-card-text>
                                            Leia Organa é filha de Anakin Skywalker (Darth Vader) e
                                            Padmé Amidala, mas é criada como filha adotiva de Bail
                                            Organa, governante de Alderaan. Durante a era do Império,
                                            ela se torna uma líder chave na Rebelião contra o Império
                                            Galáctico. Em Uma Nova Esperança, ela envia os planos da
                                            Estrela da Morte para os rebeldes e, depois de ser
                                            capturada, é resgatada por Luke Skywalker e Han Solo,
                                            ajudando na destruição da superarma imperial. Ela continua
                                            a lutar contra o Império em O Império Contra-Ataca e O
                                            Retorno de Jedi, onde lidera missões importantes e
                                            desempenha um papel fundamental na queda de Darth Vader e
                                            do Imperador. Após a queda do Império, Leia se torna uma
                                            líder na nova República, mas, em O Despertar da Força, ela
                                            lidera a Resistência contra a Primeira Ordem. Ela também
                                            lida com a perda de seu filho, Ben Solo (Kylo Ren), e
                                            tenta trazê-lo de volta ao lado da luz. Embora não seja
                                            uma Jedi treinada, Leia possui habilidades com a Força,
                                            herdadas de seu pai. Sua jornada é uma história de
                                            coragem, liderança e redenção, tornando-se um símbolo de
                                            esperança para toda a galáxia.
                                        </v-card-text>

                                        <!-- Botão de fechar o dialogo -->

                                        <v-card-actions>
                                            <v-spacer></v-spacer>
                                            <v-btn text="Fechar" @click="leiaDialogActive = false"></v-btn>
                                        </v-card-actions>
                                    </v-card>
                                </v-dialog>
                            </v-card-actions>
                        </v-card>
                    </v-col>

                    <!-- Tela do Owen Lars -->

                    <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
                        <v-card>
                            <v-img src="../assets/imagem_star_wars/personagem/Owen Lars.jpeg" style="height: 433px"
                                class="aling-end text-white"></v-img>
                            <v-card-title class="pt-4" style="border-bottom: 2px solid white">Owen Lars</v-card-title>
                            <v-card-title class="pt-2" style="font-size: 18px">Feitos:</v-card-title>
                            <v-card-text>
                                Owen Lars é o tio adotivo de Luke Skywalker e o responsável por
                                sua criação em Tatooine. Ele cuida de Luke após a morte de seus
                                pais, mantendo o garoto seguro e escondido do Império,
                                especialmente de Darth Vader, sem saber que é seu pai. Owen
                                tenta dissuadir Luke de seguir o caminho dos Jedi e ficar na
                                fazenda, priorizando a segurança e o bem-estar do sobrinho.
                                Embora não tenha grandes feitos de combate, ele desempenha um
                                papel crucial na proteção de Luke, permitindo que o jovem
                                crescesse em segurança até o momento certo de se envolver na
                                luta contra o Império.
                            </v-card-text>

                            <!-- Ativador do Diálogo -->

                            <v-card-actions>
                                <v-dialog v-model="owenDialogActive" max-width="500">
                                    <template v-slot:activator="{ props }">
                                        <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                                        <v-icon class="mdi mdi-fencing"></v-icon>
                                    </template>

                                    <!-- Contéudo do diálogo -->

                                    <v-card title="Owen Lars">
                                        <v-img src="../assets/imagem_star_wars/personagem_segundo_plano/Owen Lars.jpeg"
                                            class="alingn-end text-white"></v-img>
                                        <v-card-title class="pt-2" style="font-size: 18">Historia:</v-card-title>
                                        <v-card-text>
                                            Owen Lars é o tio adotivo de Luke Skywalker, e sua
                                            história é marcada pela proteção e cuidado com o sobrinho.
                                            Após a morte de seus pais, Owen e sua esposa Beru assumem
                                            a responsabilidade de criar Luke em Tatooine, mantendo sua
                                            identidade e origem em segredo para protegê-lo do Império.
                                            Owen é cético em relação à ideia de Luke se tornar um Jedi
                                            e tenta dissuadi-lo de seguir o caminho dos Jedi,
                                            priorizando sua segurança e uma vida simples na fazenda.
                                            Sua vida termina tragicamente quando a fazenda dos Lars é
                                            atacada pelos Stormtroopers do Império, que procuram os
                                            droides R2-D2 e C-3PO. Owen e Beru são mortos no ataque, o
                                            que impulsiona Luke a partir para a Rebelião e seguir seu
                                            destino como Jedi. Embora não tenha grandes feitos de
                                            batalha, Owen desempenha um papel crucial ao proteger Luke
                                            durante sua infância e ajudá-lo a sobreviver até o momento
                                            certo de se envolver na luta contra o Império.
                                        </v-card-text>

                                        <!-- Botão de fechar o dialogo -->

                                        <v-card-actions>
                                            <v-spacer></v-spacer>
                                            <v-btn text="Fechar" @click="owenDialogActive = false"></v-btn>
                                        </v-card-actions>
                                    </v-card>
                                </v-dialog>
                            </v-card-actions>
                        </v-card>
                    </v-col>

                    <!-- Tela da Beru Whitesun lars -->

                    <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
                        <v-card>
                            <v-img src="../assets/imagem_star_wars/personagem/Beru Whitesun lars.jpeg"
                                style="height: 436px" class="aling-end text-white"></v-img>
                            <v-card-title class="pt-4" style="border-bottom: 2px solid white">Beru Whitesun
                                lars</v-card-title>
                            <v-card-title class="pt-2" style="font-size: 18px">Feitos:</v-card-title>
                            <v-card-text>
                                Beru Whitesun Lars, esposa de Owen Lars, é a tia adotiva de Luke
                                Skywalker. Ela cuida de Luke em Tatooine após a morte de seus
                                pais, mantendo sua identidade em segredo para protegê-lo do
                                Império. Beru e Owen oferecem um lar seguro e acolhedor para
                                Luke, longe dos perigos da galáxia. Sua história termina
                                tragicamente quando ela e Owen são mortos no ataque dos
                                Stormtroopers à sua fazenda, o que impulsiona Luke a seguir seu
                                destino como Jedi. Embora discreta, Beru desempenha um papel
                                crucial na formação de Luke e em sua infância.
                            </v-card-text>

                            <!-- Ativador do Diálogo -->

                            <v-card-actions>
                                <v-dialog v-model="beruDialogActive" max-width="500">
                                    <template v-slot:activator="{ props }">
                                        <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                                        <v-icon class="mdi mdi-fencing"></v-icon>
                                    </template>

                                    <!-- Contéudo do Diálogo -->

                                    <v-card title="Beru Whitesun lars">
                                        <v-img
                                            src="../assets/imagem_star_wars/personagem_segundo_plano/Beru Whitesun lars.jpeg"
                                            class="alingn-end text-white"></v-img>
                                        <v-card-title class="pt-2" style="font-size: 18">Historia:</v-card-title>
                                        <v-card-text>
                                            Beru Whitesun Lars é a tia adotiva de Luke Skywalker,
                                            casada com Owen Lars. Após a morte dos pais de Luke, ela e
                                            Owen o criam em Tatooine, mantendo sua identidade secreta
                                            para protegê-lo do Império e de Darth Vader. Beru é uma
                                            figura maternal que oferece a Luke um lar seguro e
                                            acolhedor durante sua infância, longe das ameaças
                                            externas. Sua história termina tragicamente quando ela e
                                            Owen são mortos no ataque dos Stormtroopers à sua fazenda,
                                            após a chegada dos droides R2-D2 e C-3PO. Seu papel,
                                            embora discreto, é crucial na formação e proteção de Luke
                                            até que ele parta para sua jornada como Jedi.
                                        </v-card-text>

                                        <!-- Botão de fechar o dialogo -->

                                        <v-card-actions>
                                            <v-spacer></v-spacer>
                                            <v-btn text="Fechar" @click="beruDialogActive = false"></v-btn>
                                        </v-card-actions>
                                    </v-card>
                                </v-dialog>
                            </v-card-actions>
                        </v-card>
                    </v-col>

                    <!-- Tela do R5-D4 -->

                    <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
                        <v-card>
                            <v-img src="../assets/imagem_star_wars/personagem/r5-d4.jpeg" style="height: 437px"
                                class="aling-end text-white"></v-img>
                            <v-card-title class="pt-4" style="border-bottom: 2px solid white">R5-D4</v-card-title>
                            <v-card-title class="pt-2" style="font-size: 18px">Feitos:</v-card-title>
                            <v-card-text>
                                R5-D4 é um droide astromech que aparece brevemente em Star Wars:
                                Uma Nova Esperança. Inicialmente, ele é escolhido pelos Lars
                                para ser comprado, mas sabota a si mesmo de forma intencional,
                                causando um defeito em seu sistema. Isso leva Luke e Owen a
                                escolherem R2-D2, o que acaba sendo crucial, já que R2-D2
                                carrega os planos da Estrela da Morte e desempenha um papel
                                fundamental na vitória da Rebelião. O feito de R5-D4, embora
                                pequeno, é sua autossabotagem para garantir que R2-D2 seguisse
                                sua missão importante, o que contribui para a derrota do
                                Império.
                            </v-card-text>

                            <!-- Ativador do Diálogo -->

                            <v-card-actions>
                                <v-dialog v-model="r5d4DialogActive" max-width="500">
                                    <template v-slot:activator="{ props }">
                                        <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                                        <v-icon class="mdi mdi-robot-outline"></v-icon>
                                    </template>

                                    <!-- Contéudo do Diálogo -->

                                    <v-card title="R5-D4">
                                        <v-img src="../assets/imagem_star_wars/personagem_segundo_plano/R5-D4.jpeg"
                                            class="alingn-end text-white"></v-img>
                                        <v-card-title class="pt-2" style="font-size: 18">Historia:</v-card-title>
                                        <v-card-text>
                                            R5-D4 é um droide astromech que aparece brevemente em Star
                                            Wars: Uma Nova Esperança. Ele é levado para ser comprado
                                            por Owen Lars, que precisava de um droide para ajudar na
                                            manutenção de sua nave. Quando ativado, R5-D4 apresenta um
                                            defeito técnico, o que faz com que Owen e Luke optem por
                                            comprar R2-D2 em seu lugar. No entanto, essa falha não é
                                            acidental — R5-D4 sabota a si mesmo de forma intencional.
                                            Essa ação é interpretada como parte de uma estratégia para
                                            garantir que R2-D2, que carrega os planos da Estrela da
                                            Morte, fosse escolhido para seguir a missão crucial. Em
                                            outras palavras, R5-D4, ao falhar de propósito, facilita o
                                            destino de R2-D2, que mais tarde desempenha um papel
                                            essencial na derrota do Império. Portanto, embora R5-D4
                                            não tenha grandes feitos de combate ou aventuras, sua
                                            sabotagem deliberada teve um impacto significativo na
                                            trajetória que levou à destruição da Estrela da Morte e à
                                            vitória da Rebelião.
                                        </v-card-text>

                                        <!-- Botão de fechar o dialogo -->

                                        <v-card-actions>
                                            <v-spacer></v-spacer>
                                            <v-btn text="Fechar" @click="r5d4DialogActive = false"></v-btn>
                                        </v-card-actions>
                                    </v-card>
                                </v-dialog>
                            </v-card-actions>
                        </v-card>
                    </v-col>

                    <!-- Tela do Biggs Darklighter -->

                    <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
                        <v-card>
                            <v-img src="../assets/imagem_star_wars/personagem/Biggs Darklighter.jpeg"
                                class="aling-end text-white"></v-img>
                            <v-card-title class="pt-4" style="border-bottom: 2px solid white">Biggs
                                Darklighter</v-card-title>
                            <v-card-title class="pt-2" style="font-size: 18px">Feitos:</v-card-title>
                            <v-card-text>
                                Biggs Darklighter é um amigo de infância de Luke Skywalker em
                                Tatooine, com quem compartilhou o sonho de se tornar piloto. Ele
                                se junta à Rebelião contra o Império e se torna um piloto de
                                elite. Sua maior contribuição ocorre na Batalha de Yavin, onde
                                participa da missão para destruir a Estrela da Morte. Durante o
                                combate, Biggs combate ao lado de Luke e é abatido pelos TIE
                                Fighters do Império, morrendo heroicamente enquanto tenta ajudar
                                Luke a completar a missão. Sua morte é um golpe significativo
                                para a Rebelião e para Luke, reforçando o custo da luta contra o
                                Império. Embora tenha pouco tempo de tela, Biggs é lembrado como
                                um herói e amigo leal de Luke.
                            </v-card-text>

                            <!-- Ativador do Diálogo -->

                            <v-card-actions>
                                <v-dialog v-model="biggsDialogActive" max-width="500">
                                    <template v-slot:activator="{ props }">
                                        <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                                        <v-icon class="mdi mdi-rocket-launch-outline"></v-icon>
                                    </template>

                                    <!-- Contéudo do Diálogo -->

                                    <v-card title="Biggs Darklighter">
                                        <v-img
                                            src="../assets/imagem_star_wars/personagem_segundo_plano/Biggs Darklighter.jpeg"
                                            class="alingn-end text-white"></v-img>
                                        <v-card-title class="pt-2" style="font-size: 18">Historia:</v-card-title>
                                        <v-card-text>
                                            Biggs Darklighter é um piloto da Rebelião e amigo de
                                            infância de Luke Skywalker em Tatooine. Os dois cresceram
                                            juntos e sonhavam em se tornar pilotos, mas Biggs se
                                            alista na Rebelião, enquanto Luke fica na fazenda com seus
                                            tios. Quando Biggs retorna a Tatooine e se reencontra com
                                            Luke, ele já é um piloto experiente da Rebelião. Biggs
                                            participa da Batalha de Yavin, em Star Wars: Uma Nova
                                            Esperança, onde luta ao lado de Luke na missão para
                                            destruir a Estrela da Morte. Durante a batalha, Biggs é
                                            abatido por caças TIE do Império, mas não antes de tentar
                                            ajudar Luke, mostrando coragem e lealdade. Sua morte é um
                                            momento de grande impacto emocional, especialmente para
                                            Luke, que perde um amigo próximo e um aliado importante na
                                            luta contra o Império. Embora Biggs tenha uma presença
                                            curta na trama, sua amizade com Luke e seu sacrifício na
                                            batalha são importantes, lembrando o alto custo da guerra
                                            e a bravura dos heróis da Rebelião.
                                        </v-card-text>

                                        <!-- Botão de fechar o dialogo -->

                                        <v-card-actions>
                                            <v-spacer></v-spacer>
                                            <v-btn text="Fechar" @click="biggsDialogActive = false"></v-btn>
                                        </v-card-actions>
                                    </v-card>
                                </v-dialog>
                            </v-card-actions>
                        </v-card>
                    </v-col>

                    <!-- Tela do Obi-Wan Kenobi -->

                    <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
                        <v-card>
                            <v-img src="../assets/imagem_star_wars/personagem/Obi-Wan Kenobi.jpeg" style="height: 412px"
                                class="aling-end text-white"></v-img>
                            <v-card-title class="pt-4" style="border-bottom: 2px solid white">Obi-Wan
                                Kenobi</v-card-title>
                            <v-card-title class="pt-2" style="font-size: 18px">Feitos:</v-card-title>
                            <v-card-text>
                                Obi-Wan Kenobi é um dos Jedi mais importantes de Star Wars. Como
                                mestre de Anakin Skywalker, treinou o jovem Jedi até que ele
                                caísse para o Lado Sombrio e se tornasse Darth Vader. Obi-Wan
                                derrotou o Sith Darth Maul, ajudou a derrotar o general Grievous
                                na Guerra dos Clones e, em A Vingança dos Sith, enfrentou Anakin
                                em Mustafar, deixando-o gravemente ferido, mas sem matá-lo.
                                Exilado em Tatooine, Obi-Wan protegeu Luke Skywalker, filho de
                                Anakin, e, ao se sacrificar para permitir que Luke escapasse do
                                Império, tornou-se um espírito da Força, continuando a guiá-lo.
                                Sua história é marcada por coragem, sabedoria e lealdade à Ordem
                                Jedi.
                            </v-card-text>

                            <!-- Ativandor do Diálogo -->

                            <v-card-actions>
                                <v-dialog v-model="obiDialogActive" max-width="500">
                                    <template v-slot:activator="{ props }">
                                        <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                                        <v-icon class="mdi mdi-fencing"></v-icon>
                                    </template>

                                    <!-- Contúdo do diálogo -->

                                    <v-card title="Obi-Wan Kenobi">
                                        <v-img
                                            src="../assets/imagem_star_wars/personagem_segundo_plano/Obi-Wan Kenobi.jpeg"
                                            class="alingn-end text-white"></v-img>
                                        <v-card-title class="pt-2" style="font-size: 18">Historia:</v-card-title>
                                        <v-card-text>
                                            Obi-Wan Kenobi nasceu em Stewjon e foi treinado como Jedi
                                            desde jovem. Seu mestre foi Qui-Gon Jinn, e juntos
                                            enfrentaram o Sith Darth Maul em Naboo, onde Qui-Gon
                                            morreu, deixando Obi-Wan para derrotar Maul. Após isso,
                                            Obi-Wan assumiu a responsabilidade de treinar Anakin
                                            Skywalker, que se mostrou um Jedi talentoso, mas
                                            impulsivo. Durante as Guerras Clônicas, Obi-Wan se
                                            destacou como líder militar, mas sua relação com Anakin
                                            começou a se deteriorar à medida que o jovem Jedi se
                                            tornava cada vez mais difícil de controlar. Em A Vingança
                                            dos Sith, Anakin se vira para o Lado Sombrio, se tornando
                                            Darth Vader, e Obi-Wan é forçado a lutar contra ele em
                                            Mustafar, deixando-o gravemente ferido. Após a queda da
                                            Ordem Jedi, Obi-Wan se exila em Tatooine, onde passa a
                                            vigiar e proteger Luke Skywalker, filho de Anakin. Em Uma
                                            Nova Esperança, Obi-Wan se sacrifica ao confrontar Darth
                                            Vader na Estrela da Morte, permitindo que Luke e seus
                                            amigos escapem. Ele se torna um espírito da Força, guiando
                                            Luke na luta contra o Império. O legado de Obi-Wan é de
                                            sabedoria, sacrifício e dedicação à Força, sendo uma das
                                            figuras mais importantes na luta contra o mal na galáxia.
                                        </v-card-text>

                                        <!-- Botão de fechar o dialogo -->

                                        <v-card-actions>
                                            <v-spacer></v-spacer>
                                            <v-btn text="Fechar" @click="obiDialogActive = false"></v-btn>
                                        </v-card-actions>
                                    </v-card>
                                </v-dialog>
                            </v-card-actions>
                        </v-card>
                    </v-col>
                </v-row>
            </v-container>
        </v-main>
    </div>
</template>

<script setup>

// Controla os diálogos

import { ref } from "vue";
// import { tr } from "vuetify/locale";
const lukeDialogActive = ref(false);
const c3poDialogActive = ref(false);
const r2d2DialogActive = ref(false);
const darthDialogActive = ref(false);
const leiaDialogActive = ref(false);
const owenDialogActive = ref(false);
const beruDialogActive = ref(false);
const r5d4DialogActive = ref(false);
const biggsDialogActive = ref(false);
const obiDialogActive = ref(false);

// Variável de pesquisa
const searchQuery = ref(""); // Armazena o que o usuário está digitando
const loading = ref(false); // Controle de loading
const noResultsFound = ref(false);

// função para limpar a pesquisa
const clearSearch = () => {
    searchQuery.value = ""; // limpa a pesquisa
    noResultsFound.value = false; // reseta o alerta de "não encontrado"
}


// Função de pesquisa
const onSearchInput = () => {
    const query = searchQuery.value.trim().toLocaleLowerCase(); // Remover espaços e tornar tudo minúsculo

    // Fechar todos os diálogos antes de abrir o correto
    lukeDialogActive.value = false;
    c3poDialogActive.value = false;
    r2d2DialogActive.value = false;
    darthDialogActive.value = false;
    leiaDialogActive.value = false;
    owenDialogActive.value = false;
    beruDialogActive.value = false;
    r5d4DialogActive.value = false;
    biggsDialogActive.value = false;
    obiDialogActive.value = false;

    // Verificar qual personagem foi pesquisado e abrir o diálogo correspondente
    if (query === 'luke skywalker') {
        lukeDialogActive.value = true;
    } else if (query === 'c-3po') {
        c3poDialogActive.value = true;
    } else if (query === 'r2-d2') {
        r2d2DialogActive.value = true;
    } else if (query === 'darth vader') {
        darthDialogActive.value = true;
    } else if (query === 'leia organa') {
        leiaDialogActive.value = true;
    } else if (query === 'owen lars') {
        owenDialogActive.value = true;
    } else if (query === 'beru whitesun lars') {
        beruDialogActive.value = true;
    } else if (query === 'r5-d4') {
        r5d4DialogActive.value = true;
    } else if (query === 'biggs darklighter') {
        biggsDialogActive.value = true;
    } else if (query === 'obi-wan kenobi') {
        obiDialogActive.value = true;
    } else {
        // Se o termo não corresponder a nenhum personagem, definir a variável para true
        noResultsFound.value = true;

        setTimeout(() => {
            noResultsFound.value = false;
        }, 3000); // 3000 milissegundos = 3 segundos
    }

    loading.value = false

};

</script>