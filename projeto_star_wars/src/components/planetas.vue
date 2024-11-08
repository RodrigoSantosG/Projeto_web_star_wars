<template>
  <div class="home">
    <!-- Pesquisa -->

    <v-row>
      <v-col>
        <v-card flat class="border mb-4">
          <v-card-text>
            <v-text-field v-model="searchQuery" :loading="loading" density="compact" label="Pesquisa algum personagem"
              variant="solo" hide-details single-line @keydown.enter="onSearchInput">
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

          <!-- Exibir mensagem caso nenhum palenta tenha sido encontrado -->

          <v-alert v-if="noResultsFound" type="error" class="mt-4">
            Nenhum planeta encontrado. Tente novamente.
          </v-alert>
        </v-card>
      </v-col>
    </v-row>

    <v-row>
      <!-- Tela do Coruscant -->

      <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
        <v-card>
          <v-img src="../assets/imagem_star_wars/planetas/Coruscant _ Star Wars Planet, Shiny Man.jpeg"
            style="height: 545px" class="align-end text-white">
          </v-img>
          <v-card-title class="pt-4" style="border-bottom: 2px solid white">Coruscant</v-card-title>
          <v-card-title class="pt-2" style="font-size: 18px">Sobre o Planeta:</v-card-title>
          <v-card-text>
            Antiguidade: Coruscant é um dos planetas mais antigos e históricos
            da galáxia. Sua importância remonta aos tempos da República Antiga e
            até mesmo da Ordem Jedi primitiva. A cidade foi construída sobre as
            ruínas de civilizações antigas, e há muito conhecimento e história
            escondidos nas profundezas de seus níveis inferiores. Queda da
            República e Ascensão do Império: Com a manipulação de Palpatine e a
            execução da Ordem 66, que resultou na extinção quase completa dos
            Jedi, Coruscant passou de um símbolo de esperança para um centro de
            opressão sob o Império. A resistência foi uma constante, com grupos
            como a Aliança Rebelde buscando lutar contra o regime imperial.
            Pós-Império: Após a queda do Império Galáctico e a ascensão da Nova
            República, Coruscant continuou sendo um símbolo de poder, ainda que
            agora com um novo governo e uma tentativa de reconstrução das
            instituições galácticas.
          </v-card-text>
          <v-card-actions>
            <!-- Ativador do diálogo -->

            <v-dialog v-model="CoruDialogActive" max-width="500">
              <template v-slot:activator="{ props }">
                <v-btn v-bind="props" color="white" text="Ver Mais" variant="flat">
                </v-btn>
                <v-icon class="mdi mdi-death-star-variant"></v-icon>
              </template>

              <!-- Conteúdo do diálogo -->

              <v-card title="Coruscant">
                <v-img src="../assets/imagem_star_wars/planetas_segundo_plano/coruscant_segundo.jpeg"
                  class="align-end text-white" style="height: 700px"></v-img>
                <v-card-title class="pt-2" style="font-size: 18px">Impacto:</v-card-title>
                <v-card-text>
                  Centro de Poder e Corrupção Política:
                  <br /><br />
                  Coruscant é o epicentro da política galáctica, onde as grandes
                  mudanças de poder ocorrem. Na República Galáctica, é o local
                  do Senado e das decisões políticas, mas também reflete a
                  crescente corrupção que facilita a ascensão de Palpatine ao
                  poder e a transformação da República em Império. O planeta
                  simboliza como as instituições democráticas podem ser
                  corrompidas por ambição e manipulação.
                  <br /><br />
                  Impacto no Destino de Anakin Skywalker:
                  <br /><br />
                  O planeta é crucial para o arco de Anakin Skywalker, cuja
                  jornada é moldada pelas intrigas políticas em Coruscant. A
                  cidade abriga o Conselho Jedi, onde Anakin sofre suas maiores
                  crises pessoais e é manipulado por Palpatine, o que leva à sua
                  transformação em Darth Vader.
                  <br /><br />
                  Reflexo da Sociedade Galáctica:
                  <br /><br />
                  Coruscant também representa a divisão entre as classes
                  sociais, com suas camadas superiores repletas de poderosos e
                  suas camadas inferiores, o submundo, sendo um cenário de
                  corrupção, crime e desigualdade. Esse contraste ajuda a
                  ilustrar as tensões sociais e a decadência da galáxia.
                  <br /><br />
                  Símbolo de Queda e Esperança:
                  <br /><br />
                  Ao longo da trama, Coruscant passa de um símbolo de unidade e
                  democracia para um centro de opressão, com a queda do Senado e
                  a destruição da Ordem Jedi. Após a queda do Império, o planeta
                  ainda serve como campo de batalha político, refletindo a luta
                  pela recuperação da liberdade.
                </v-card-text>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <!-- Botão de fechar o diálogo -->
                  <v-btn text="Fechar" @click="CoruDialogActive = false"></v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-card-actions>
        </v-card>
      </v-col>

      <!-- Tela do Dagobah -->

      <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
        <v-card>
          <v-img
            src="../assets/imagem_star_wars/planetas/Dagobah, where Luke met Yoda in The Empire Strikes Back (8_900 km, Star Wars).jpeg"
            style="height: 525px" class="align-end text-white">
          </v-img>
          <v-card-title class="pt-4" style="border-bottom: 2px solid white">Dagobah</v-card-title>
          <v-card-title class="pt-2" style="font-size: 18px">Sobre o Planeta:</v-card-title>
          <v-card-text>
            Dagobah é um planeta remoto e isolado, com um ecossistema de
            pântanos, florestas densas e uma atmosfera úmida. Por ser
            praticamente desabitado e de difícil acesso, o planeta se tornou o
            local de exílio de Yoda após a Queda da República Galáctica e a
            execução da Ordem 66, que resultou na extinção quase total da Ordem
            Jedi. Yoda se refugiou ali, longe das forças do Império Galáctico
            que caçavam os Jedi sobreviventes. Anos depois, durante a Guerra
            Civil Galáctica, Luke Skywalker viaja até Dagobah, onde encontra
            Yoda, que o treina como Jedi. Durante seu tempo em Dagobah, Luke
            enfrenta seu maior teste: em uma caverna chamada Vale Sombrio, ele
            confronta uma versão de Darth Vader e é forçado a confrontar seus
            próprios medos e a tentação do Lado Sombrio da Força. Yoda também o
            ensina sobre a importância de não ceder à pressa e ao medo, lições
            que são fundamentais para o crescimento de Luke como Jedi.
          </v-card-text>

          <!-- Ativador do diálogo -->

          <v-card-actions>
            <v-dialog v-model="dagoDialogActive" max-width="500">
              <template v-slot:activator="{ props }">
                <v-btn v-bind="props" color="white" text="Ver Mais" variant="flat">
                </v-btn>
                <v-icon class="mdi mdi-death-star-variant"></v-icon>
              </template>

              <!-- Conteúdo do diálogo -->

              <v-card title="Dagobah">
                <v-img src="../assets/imagem_star_wars/planetas_segundo_plano/Dagobah_segundo.jpeg"
                  class="align-end text-white"></v-img>
                <v-card-title class="pt-2" style="font-size: 18px">impacto:</v-card-title>
                <v-card-text>
                  solamento e Reflexão:
                  <br /><br />
                  O impacto de Dagobah na obra de Star Wars é principalmente
                  simbólico. O planeta, isolado e selvagem, representa o refúgio
                  e a reflexão, essencial para o crescimento dos Jedi. Para
                  Yoda, é um lugar onde ele pode sobreviver após a destruição da
                  Ordem Jedi e refletir sobre o fracasso da galáxia. Para Luke,
                  Dagobah é onde ele enfrenta seus medos, aprende as lições mais
                  profundas da Força e dá passos decisivos para se tornar um
                  Jedi.
                  <br /><br />
                  Treinamento de Luke Skywalker:
                  <br /><br />
                  O planeta é crucial para o desenvolvimento de Luke. Em
                  Dagobah, ele recebe o treinamento espiritual e físico
                  necessário para se tornar um Jedi. As lições de paciência,
                  controle emocional e disciplina de Yoda são fundamentais para
                  a vitória de Luke sobre o Lado Sombrio da Força e seu
                  enfrentamento com Darth Vader. O Vale Sombrio, onde Luke
                  enfrenta sua visão de Vader, simboliza o confronto interno de
                  qualquer Jedi com os medos e tentações da Força.
                  <br /><br />
                  Símbolo de Esperança e Resiliência:
                  <br /><br />
                  Mesmo sendo um lugar isolado e selvagem, Dagobah simboliza
                  resiliência e esperança. A presença de Yoda ali, longe dos
                  olhos do Império, é uma metáfora para a sabedoria escondida, e
                  o planeta representa o último reduto da Ordem Jedi, aguardando
                  o momento em que um novo herói surgiria para restaurar o
                  equilíbrio na galáxia.
                </v-card-text>
                <v-card-actions>
                  <v-spacer></v-spacer>

                  <!-- Botão de fechar o diálogo -->

                  <v-btn text="Fechar" @click="dagoDialogActive = false"></v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-card-actions>
        </v-card>
      </v-col>

      <!-- Tela do Death Star -->

      <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
        <v-card>
          <v-img src="../assets/imagem_star_wars/planetas/Death star sphere.jpeg" style="height: 566px"
            class="align-end text-white">
          </v-img>
          <v-card-title class="pt-4" style="border-bottom: 2px solid white">Death Star</v-card-title>
          <v-card-title class="pt-2" style="font-size: 18px">Sobre o Planeta:</v-card-title>
          <v-card-text>
            A Primeira Estrela da Morte aparece em Star Wars: Episódio IV - Uma
            Nova Esperança (1977). Esta estação, construída pelo Império
            Galáctico, foi projetada para ser a arma definitiva, capaz de
            destruir planetas inteiros com um único disparo de seu superlaser.
            Ela era alimentada por uma gigantesca usina de energia e possuía uma
            superfície planetária cheia de infraestruturas internas, incluindo
            uma estação de batalha, portos de navegação, e até uma base militar.
            Destruição de Alderaan: No filme, a Primeira Estrela da Morte é
            usada para destruir o planeta Alderaan, um bastião da Aliança
            Rebelde, como demonstração de sua potência. A destruição de Alderaan
            é um momento crucial, mostrando a brutalidade do Império Galáctico e
            estabelecendo a ameaça imediata da Estrela da Morte. Destruição da
            Estrela da Morte: A estação é destruída durante a Batalha de Yavin,
            quando Luke Skywalker, com a ajuda da Aliança Rebelde, consegue
            disparar um tiro preciso no ponto fraco da estação, que foi deixado
            propositalmente para garantir sua vulnerabilidade. Esse ato heroico
            foi um dos maiores momentos de resistência contra o Império e a
            primeira grande vitória dos Rebeldes.
          </v-card-text>

          <!-- Ativador do diálogo -->

          <v-card-actions>
            <v-dialog v-model="deathDialogActive" max-width="500">
              <template v-slot:activator="{ props }">
                <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                <v-icon class="mdi mdi-death-star-variant"></v-icon>
              </template>

              <!-- Conteúdo do diálogo -->

              <v-card title="Death Star">
                <v-img src="../assets/imagem_star_wars/planetas_segundo_plano/Death_Star_segundo.jpeg"
                  style="height: 600px" class="alingn-end text-white"></v-img>
                <v-card-title class="pt-2" style="font-size: 18px">Impacto:</v-card-title>
                <v-card-text>
                  A Estrela da Morte tem um impacto significativo na narrativa
                  de Star Wars e nas temáticas da saga. Ela não é apenas uma
                  arma de destruição em massa, mas um símbolo do poder absoluto
                  do Império Galáctico, da opressão e da resistência. Aqui estão
                  os principais pontos de impacto:
                  <br /><br />
                  Símbolo do Poder e da Tirania:
                  <br /><br />
                  A Estrela da Morte representa o poder absoluto do Império. A
                  capacidade de destruir planetas inteiros de uma vez simboliza
                  a opressão extrema e o controle tirânico do Império sobre a
                  galáxia. Ao usá-la para destruir Alderaan, o Império envia uma
                  mensagem de intimidação e controle. Essa ameaça de destruição
                  em larga escala cria um clima de medo que domina a galáxia.
                  <br /><br />
                  Catalisador da Rebelião:
                  <br /><br />
                  A existência da Estrela da Morte é, paradoxalmente, um dos
                  maiores impulsores da resistência contra o Império. A
                  destruição de Alderaan por parte da Estrela da Morte leva à
                  mobilização da Aliança Rebelde, que começa a lutar ativamente
                  contra o regime imperial. Em Uma Nova Esperança, os planos
                  roubados da Estrela da Morte se tornam a chave para sua
                  destruição, enquanto os Rebeldes buscam maneiras de derrotar
                  essa arma de destruição maciça.
                  <br /><br />
                  O Ponto Fraco e a Vitória Rebelde:
                  <br /><br />
                  O conceito de que a Estrela da Morte tinha um ponto fraco foi
                  crucial para a narrativa de Star Wars. A vulnerabilidade que
                  foi deliberadamente deixada na estação permitiu aos Rebeldes
                  uma chance de derrotá-la. A destruição da Primeira Estrela da
                  Morte, com o tiro preciso de Luke Skywalker (guiado pela
                  Força), foi um momento central para a vitória dos Rebeldes e
                  um marco na luta contra o Império.
                </v-card-text>

                <!-- Botão de Fechar o dialogo -->

                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn text="Fechar" @click="deathDialogActive = false"></v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-card-actions>
        </v-card>
      </v-col>

      <!-- Tela do Endor -->

      <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
        <v-card>
          <v-img src="../assets/imagem_star_wars/planetas/Endor.jpeg" style="height: 568px"
            class="aling-end text-white"></v-img>
          <v-card-title class="pt-4" style="border-bottom: 2px solid white">Endor</v-card-title>
          <v-card-title class="pt-2" style="font-size: 18px">Sobre o Planeta:</v-card-title>
          <v-card-text>
            Endor é um planeta na Região do Borda Exterior, conhecido por sua
            vegetação densa, florestas exuberantes, e um ecossistema
            particularmente habitado por Ewoks – pequenas criaturas nativas com
            aparência de ursos e um comportamento primitivo, mas astuto. Endor
            não é um planeta grandioso ou impressionante do ponto de vista
            geopolítico, mas sua importância é monumental devido aos eventos que
            ocorreram em torno dele.
          </v-card-text>

          <!-- Ativador do Diálogo -->

          <v-card-actions>
            <v-dialog v-model="endorDialogActive" max-width="500">
              <template v-slot:activator="{ props }">
                <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                <v-icon class="mdi mdi-death-star-variant"></v-icon>
              </template>

              <!-- Conteúdo do diálogo -->

              <v-card title="Endor">
                <v-img src="../assets/imagem_star_wars/planetas_segundo_plano/Endor_segundo.jpeg"
                  class="alingn-end text-white"></v-img>
                <v-card-title class="pt-2" style="font-size: 18">impacto:</v-card-title>
                <v-card-text>
                  O Fim do Império:
                  <br /><br />
                  A Batalha de Endor marca o fim do Império Galáctico. Com a
                  destruição da Segunda Estrela da Morte, o Império sofre uma
                  derrota catastrófica que leva à queda do imperador Palpatine e
                  à libertação da galáxia da tirania imperial. A aliança entre a
                  Aliança Rebelde e os Ewoks ajuda a solidificar a vitória e o
                  fim da guerra civil galáctica.
                  <br /><br />
                  A União entre Espécies e Culturas:
                  <br /><br />
                  Endor simboliza a união de espécies diferentes e a
                  solidariedade entre culturas aparentemente muito distantes. A
                  aliança entre os rebeldes humanos e os Ewoks (uma raça
                  primitiva e aparentemente ingênua) reflete a ideia de que a
                  força da união pode derrubar até os maiores impérios. Esse
                  tema de aliança universal é um dos pilares do ethos de Star
                  Wars.
                  <br /><br />
                  Temas de Simplicidade e Coragem:
                  <br /><br />
                  Os Ewoks, como personagens, são um grande contraste com as
                  complexas máquinas de guerra do Império, como as TIE fighters,
                  AT-ATs e, claro, a Estrela da Morte. Sua vitória demonstra a
                  ideia de que até os mais simples e desprezados têm um papel
                  essencial na luta contra o mal. Eles também simbolizam o poder
                  da coragem simples e da resistência, independentemente das
                  odds aparentemente descomunais.
                  <br /><br />
                  A Conexão com a Força:
                  <br /><br />
                  Enquanto Luke Skywalker e Leia Organa estão em uma jornada
                  pessoal para confrontar seu destino, Endor serve como o
                  cenário para o confronto final entre Luke e Palpatine, onde o
                  jovem Jedi enfrenta a tentação do Lado Sombrio da Força e a
                  possibilidade de cair nas garras de seu próprio pai, Darth
                  Vader. A redenção de Vader e a morte do Imperador são aspectos
                  centrais dessa parte da história, e Endor serve como o local
                  onde a Força se manifesta no confronto final.
                </v-card-text>

                <!-- Botão de Fechar o dialogo -->

                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn text="Fechar" @click="endorDialogActive = false"></v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-card-actions>
        </v-card>
      </v-col>

      <!-- Tela do Hoth -->

      <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
        <v-card>
          <v-img src="../assets/imagem_star_wars/planetas/Hoth.jpeg" style="height: 430px"
            class="aling-end text-white"></v-img>
          <v-card-title class="pt-4" style="border-bottom: 2px solid white">Hoth</v-card-title>
          <v-card-title class="pt-2" style="font-size: 18px">Sobre o Planeta:</v-card-title>
          <v-card-text>
            Hoth é um planeta remoto localizado na Região do Borda Exterior, a
            vasta parte da galáxia onde muitos dos eventos da Guerra Civil
            Galáctica ocorrem. As características mais marcantes de Hoth são seu
            clima gelado e superfície coberta por neve e gelo, com vastas
            planícies e montanhas cobertas de gelo, além de uma atmosfera fria e
            inóspita. Sua fauna inclui criaturas perigosas, como o Wampa, uma
            grande besta predadora, e o Tauntaun, um animal usado pelos rebeldes
            para viajar pelo deserto de gelo.
          </v-card-text>

          <!-- Ativador do Diálogo -->

          <v-card-actions>
            <v-dialog v-model="hothDialogActive" max-width="500">
              <template v-slot:activator="{ props }">
                <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                <v-icon class="mdi mdi-death-star-variant"></v-icon>
              </template>

              <!-- Contéudo do diálogo -->

              <v-card title="Hoth">
                <v-img src="../assets/imagem_star_wars/planetas_segundo_plano/Hoth_segundo.jpeg" style="height: 600px"
                  class="alingn-end text-white"></v-img>
                <v-card-title class="pt-2" style="font-size: 18">Impacto:</v-card-title>
                <v-card-text>
                  O impacto de Hoth em Star Wars é imenso e vai além do simples
                  cenário de uma batalha. Ele é um ponto de virada na saga, que
                  tem implicações tanto para os personagens quanto para o enredo
                  da trilogia original.
                  <br /><br />
                  A Primeira Grande Derrota dos Rebeldes:
                  <br /><br />
                  A Batalha de Hoth é a primeira vez que os Rebeldes enfrentam
                  uma grande derrota militar nas mãos do Império. Embora a
                  resistência tenha sido feroz, o ataque imperial mostra o poder
                  imenso do Império, com suas forças esmagadoras e tecnologia
                  superior. Esse contraste entre a força bruta do Império e a
                  determinação dos Rebeldes é um tema central da saga.
                  <br /><br />
                  O Desenvolvimento de Personagens:
                  <br /><br />
                  Luke Skywalker começa a ser mais desafiado em sua jornada
                  Jedi. Em Hoth, ele é obrigado a tomar decisões difíceis, como
                  ir para o planeta Dagobah para continuar seu treinamento com
                  Yoda, após receber uma visão. Este momento marca o início de
                  sua jornada de autoconhecimento e aprendizado sobre o Lado
                  Luminoso da Força. Para Han Solo e Leia Organa, Hoth
                  representa o início de sua relação romântica, mas também um
                  momento de perda e sacrifício, já que a base é destruída e
                  muitos membros da Aliança Rebelde são mortos ou capturados.
                  Eles também enfrentam a ameaça crescente do Império, que os
                  persegue durante o filme.
                  <br /><br />
                  O Papel do Império:
                  <br /><br />
                  Hoth também demonstra a eficiência militar do Império
                  Galáctico. A aparição dos AT-ATs e a chegada da frota imperial
                  em Hoth são marcos do poder militar do Império, algo que
                  coloca os Rebeldes em grande desvantagem. Esse contraste de
                  poder continua a ser um tema importante em toda a saga.
                </v-card-text>

                <!-- Botão de fechar o dialogo -->

                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn text="Fechar" @click="hothDialogActive = false"></v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-card-actions>
        </v-card>
      </v-col>

      <!-- Tela do Naboo -->

      <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
        <v-card>
          <v-img
            src="../assets/imagem_star_wars/planetas/Naboo is a planet in the fictional Star Wars universe with a mostly green terrain and which is the homeworld of two societies_ the Gungans who dwell in underwater cities and the humans who live in colonies on the surface_.jpeg"
            style="height: 433px" class="aling-end text-white"></v-img>
          <v-card-title class="pt-4" style="border-bottom: 2px solid white">Naboo</v-card-title>
          <v-card-title class="pt-2" style="font-size: 18px">Sobre o Planeta:</v-card-title>
          <v-card-text>
            Naboo é um planeta localizado na Região Central da galáxia, e é
            conhecido por suas paisagens deslumbrantes, que incluem lagoas
            serenas, florestas luxuriantes e grandes planícies verdejantes. A
            arquitetura do planeta é igualmente notável, com palácios
            imponentes, cidades subaquáticas e grandes templos. As cidades
            principais são construídas tanto no nível da superfície quanto
            debaixo d'água, sendo Theed a capital e a maior cidade do planeta.
          </v-card-text>

          <!-- Ativador do Diálogo -->

          <v-card-actions>
            <v-dialog v-model="nabooDialogActive" max-width="500">
              <template v-slot:activator="{ props }">
                <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                <v-icon class="mdi mdi-death-star-variant"></v-icon>
              </template>

              <!-- Contéudo do diálogo -->

              <v-card title="Naboo">
                <v-img src="../assets/imagem_star_wars/planetas_segundo_plano/Naboo_segundo.gif"
                  class="alingn-end text-white"></v-img>
                <v-card-title class="pt-2" style="font-size: 18">Impacto:</v-card-title>
                <v-card-text>
                  Naboo tem um impacto significativo no universo de Star Wars,
                  tanto em termos de sua influência política quanto na
                  construção dos personagens principais e das relações entre
                  eles. Vamos destacar alguns pontos importantes sobre seu
                  impacto:
                  <br /><br />
                  O Cenário para a Ascensão e Queda de Palpatine:
                  <br /><br />
                  Naboo desempenha um papel fundamental na trama política de
                  Star Wars, pois é o planeta natal de Palpatine, que
                  eventualmente se torna o Imperador e mestre do Lado Sombrio da
                  Força. O fato de Palpatine ser de Naboo liga o planeta
                  diretamente ao plot político central da saga. Sua ascensão ao
                  poder no Senado Galáctico começa com suas origens em Naboo, e
                  ele manipula sua terra natal para criar uma crise que ajudará
                  a justificar sua transformação em ditador.
                  <br /><br />
                  A invasão de Naboo em A Ameaça Fantasma é parte do seu plano
                  maior de manipular a política da República Galáctica para
                  garantir sua própria ascensão ao poder. O conflito sobre Naboo
                  serve como um exemplo de como ele usa as crises e divisões
                  para ganhar controle sobre a galáxia.
                  <br /><br />
                  O Papel de Padmé Amidala e a Política Galáctica:
                  <br /><br />
                  Padmé Amidala é uma das figuras mais influentes de Naboo e se
                  torna uma das personagens centrais no que diz respeito à luta
                  contra a corrupção e ao crescimento da ameaça separatista. Sua
                  liderança como Rainha e depois como Senadora coloca Naboo no
                  centro da resistência contra o crescente autoritarismo da
                  República e a manipulação de Palpatine.
                  <br /><br />
                  Ela é uma das poucas figuras que se opõem ao Senador Palpatine
                  no Senado Galáctico, e sua visão idealista de paz e justiça
                  entra em conflito com os planos secretos do Império, o que a
                  coloca em uma posição vulnerável durante as Guerras Clônicas.
                  <br /><br />
                  A Relação entre Naboo e os Jedi:
                  <br /><br />
                  Naboo também é importante para a ordem Jedi. Em A Ameaça
                  Fantasma, Qui-Gon Jinn e Obi-Wan Kenobi visitam Naboo para
                  resolver a crise com a Federação do Comércio e, eventualmente,
                  descobrem o potencial de Anakin Skywalker, que se tornaria o
                  escolhido para trazer equilíbrio à Força, embora sua jornada
                  tragicamente acabe em sua queda para o Lado Sombrio. A relação
                  entre os Jedi e Naboo é central para o início da preparação de
                  Anakin para se tornar um Jedi, mas também para as tensões que
                  surgem entre a ordem Jedi e o crescente poder do Senado,
                  manipulada por Palpatine.
                </v-card-text>

                <!-- Botão de fechar o dialogo -->

                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn text="Fechar" @click="nabooDialogActive = false"></v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-card-actions>
        </v-card>
      </v-col>

      <!-- Tela do Tatooine-->

      <v-col style="color: black" cols="12" sm="6" md="4" lg="3">
        <v-card>
          <v-img src="../assets/imagem_star_wars/planetas/Tatooine.jpeg" style="height: 436px"
            class="aling-end text-white"></v-img>
          <v-card-title class="pt-4" style="border-bottom: 2px solid white">Tatooine</v-card-title>
          <v-card-title class="pt-2" style="font-size: 18px">Sobre o Planeta:</v-card-title>
          <v-card-text>
            Tatooine é um planeta desértico, localizado na Borda Externa da
            galáxia. Sua superfície é coberta por vastos desertos, e seu clima
            quente e árido faz com que seja um local inóspito para a maioria das
            formas de vida. No entanto, o planeta se tornou um ponto de comércio
            devido à sua posição estratégica, embora a população seja
            predominantemente pobre e composta por forasteiros e nômades.
          </v-card-text>

          <!-- Ativador do Diálogo -->

          <v-card-actions>
            <v-dialog v-model="tatooineDialogActive" max-width="500">
              <template v-slot:activator="{ props }">
                <v-btn v-bind="props" color="white" text="Ver mais" variant="flat"></v-btn>
                <v-icon class="mdi mdi-death-star-variant"></v-icon>
              </template>

              <!-- Contéudo do Diálogo -->

              <v-card title="Tatooine">
                <v-img src="../assets/imagem_star_wars/planetas_segundo_plano/Tatooine_segundo.jpeg"
                  class="alingn-end text-white"></v-img>
                <v-card-title class="pt-2" style="font-size: 18">Impacto:</v-card-title>
                <v-card-text>
                  O Início da Jornada de Luke Skywalker:
                  <br /><br />
                  Tatooine é o ponto de partida da jornada de Luke Skywalker.
                  Ele começa sua história como um simples fazendeiro no planeta
                  desértico, sem saber de sua verdadeira origem ou destino. A
                  partir de Tatooine, ele é levado para o Caminho Jedi e se
                  torna a chave para derrotar o Império e restaurar a Paz na
                  Galáxia. O planeta simboliza o começo da aventura e o
                  despertar do herói.
                  <br /><br />
                  Transformação de Anakin Skywalker:
                  <br /><br />
                  Tatooine é onde Anakin Skywalker nasce e cresce, e onde ocorre
                  a tragédia de sua mãe, Shmi Skywalker, que morre em suas mãos.
                  Esses eventos influenciam profundamente sua jornada e são
                  essenciais para sua transformação de Jedi promissor para o
                  Lado Sombrio como Darth Vader. Portanto, Tatooine é crucial
                  para a origem do maior vilão da saga.
                  <br /><br />
                  A Conexão com a Força:
                  <br /><br />
                  Tatooine também simboliza a força do destino e a ideia de que
                  grandes eventos podem começar em lugares humildes. O encontro
                  de Qui-Gon Jinn com Anakin em A Ameaça Fantasma e o início da
                  jornada de Luke em Uma Nova Esperança mostram que os maiores
                  heróis e vilões podem emergir dos lugares mais inesperados.
                </v-card-text>

                <!-- Botão de fechar o dialogo -->

                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn text="Fechar" @click="tatooineDialogActive = false"></v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script setup>
const showDetails = () => { };

// Controla os diálogos

import { ref } from "vue";
const CoruDialogActive = ref(false);
const dagoDialogActive = ref(false);
const deathDialogActive = ref(false);
const endorDialogActive = ref(false);
const hothDialogActive = ref(false);
const nabooDialogActive = ref(false);
const tatooineDialogActive = ref(false);

// Variáveis de pesquisa

const searchQuery = ref(""); // A variável que armazena o que o usuário está digitando
const loading = ref(false); // Para controle de loading
const noResultsFound = ref(false); // Variável para controlar se o resultado foi encontrado


// função para limpar a pesquisa
const clearSearch = () => {
  searchQuery.value = ""; // limpa a pesquisa
  noResultsFound.value = false; // reseta o alerta de "não encontrado"
}

// Função para executar a pesquisa quando presionar "Enter"

const onSearchInput = () => {
  const query = searchQuery.value.trim().toLowerCase(); // Converte para minúsculas para garantir que a busca seja case-insensitive

  // Fechar todos os diálogos primeiro (garante que apenas o correto será aberto)

  CoruDialogActive.value = false;
  dagoDialogActive.value = false;
  deathDialogActive.value = false;
  endorDialogActive.value = false;
  hothDialogActive.value = false;
  nabooDialogActive.value = false;
  tatooineDialogActive.value = false;

  // Verificar qual planeta foi pesquisado e abrir o diálogo correspondente

  if (query === "coruscant") {
    CoruDialogActive.value = true;
  } else if (query === "dagobah") {
    dagoDialogActive.value = true;
  } else if (query === "death star") {
    deathDialogActive.value = true;
  } else if (query === "endor") {
    endorDialogActive.value = true;
  } else if (query === "hoth") {
    hothDialogActive.value = true;
  } else if (query === "naboo") {
    nabooDialogActive.value = true;
  } else if (query === "tatooine") {
    tatooineDialogActive.value = true;
  } else {
    // Se o termo não corresponder a nenhum planeta, definir a variável para true
    noResultsFound.value = true;

    setTimeout(() => {
      noResultsFound.value = false;
    }, 3000); // 3000 milissegundos = 3 segundos
  }

  loading.value = false

};
</script>
