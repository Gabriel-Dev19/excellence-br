<template>
  <div>
    <header>
      <nav class="navbar nav d-lg-none fixed-top" :class="{'pt-30': !NavScroll, 'bg-grafite py-15 shadow': NavScroll}">
        <div class="container">
          <a href="https://excellencedetetives.com.br/">
            <img src="../assets/img/logo-excellence.webp" :class="{'w-130': !NavScroll, 'w-120': NavScroll}" alt="Logo">
          </a>
          <transition enter-active-class="animate__animated animate__fadeIn" leave-active-class="animate__animated animate__fadeOut">
            <div v-show="ShowNav" id="nav-offset" @click.prevent="HideNav" />
          </transition>
          <button class="btn d-flex justify-content-center px-1 py-0 align-items-center btn-vermelho" @click.prevent="ShownNav">
            <ion-icon class="fs-35 text-white" name="menu-outline" />
          </button>
          <transition enter-active-class="animate__animated animate__slideInLeft" leave-active-class="animate__animated animate__slideOutLeft">
            <aside v-show="ShowNav" id="nav-event" class="pt-3 pb-30">
              <div class="d-flex align-items-center mt-2 px-15 justify-content-between">
                <h5 class="text-white d-flex align-content-center">
                  <ion-icon class="fs-26 text-white" name="ellipsis-vertical-outline" />
                  <span style="margin-top: 1px; margin-left: -3px;">Menu</span>
                </h5>
                <button class="btn d-flex justify-content-center px-0 py-0 align-items-center" @click.prevent="HideNav">
                  <ion-icon class="fs-30 text-white" name="return-up-forward-outline" style="margin-top: -2px" />
                </button>
              </div>
              <div class="px-15 mt-50">
                <button class="btn d-flex align-items-center pl-15 bg-white border-radius-25 py-10 border-radius-0-right col-12" @click.prevent="ScrollHome">
                  <ion-icon class="fs-25 text-vermelho" name="home-outline" />
                  <span class="ml-10 fs-19 text-vermelho fw-500">Home</span>
                  <ion-icon class="ml-auto fs-22 text-vermelho" name="arrow-redo-outline" />
                </button>
                <button class="btn d-flex mt-10 align-items-center pl-15 bg-white border-radius-25 py-10 border-radius-0-right col-12" @click.prevent="ScrollSobre">
                  <ion-icon class="fs-25 text-vermelho" name="information-circle-outline" />
                  <span class="ml-10 fs-19 text-vermelho fw-500">Sobre</span>
                  <ion-icon class="ml-auto fs-22 text-vermelho" name="arrow-redo-outline" />
                </button>
                <div class="bg-white border-radius-25">
                  <button v-b-toggle.collapse-servicos class="btn d-flex mt-10 align-items-center pl-15 py-10 border-radius-0-right col-12">
                    <ion-icon class="fs-25 text-vermelho" name="construct-outline" />
                    <span class="ml-10 fs-19 text-vermelho fw-500">Servi??os</span>
                    <ion-icon class="ml-auto rotate-down fs-22 text-vermelho" name="arrow-redo" />
                  </button>
                  <b-collapse id="collapse-servicos" class="pl-20">
                    <div class="pb-15 mt-1">
                      <button class="btn d-flex align-items-center fw-500 px-0 py-0" @click.prevent="TodosOsServicos">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> Todos os servi??os
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="InvestigacaoEmpresarial">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> Investiga????o empresarial
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="InvestigacaoConjugal">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> Investiga????o conjugal
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="InvestigacaoPolitica">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> Investiga????o pol??tica
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="PessoasDesaparecidas">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> Localiza????o de pessoas
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="CelularEspiao">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> Celular VIP
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="ProvasAdvogados">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> Provas para advogados
                      </button>
                      <button class="btn d-flex mt-1 mb-3 align-items-center fw-500 px-0 py-0" @click.prevent="CursoDetetive">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> Curso de detetive
                      </button>
                      <span class="fs-19 text-vermelho fw-500">T??picos</span>
                      <button class="btn d-flex mt-2 align-items-center text-left line-height-topicos fw-500 pl-0 py-0" @click.prevent="SinaisFraudeEmpresarial">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> Sinais de fraude empresarial
                      </button>
                      <button class="btn d-flex mt-2 align-items-center text-left line-height-topicos fw-500 pl-0 py-0" @click.prevent="SinaisTraicao">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> <span class="col-10 px-0">Voc?? est?? sendo "traido"?</span>
                      </button>
                      <button class="btn d-flex mt-2 align-items-center text-left line-height-topicos fw-500 pl-0 py-0" @click.prevent="InscricaoCursoDetetive">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> <span class="col-10 px-0">Se inscreva no nosso curso de detetive</span>
                      </button>
                      <button class="btn d-flex mt-2 align-items-center text-left line-height-topicos fw-500 pl-0 py-0" @click.prevent="Legislacao">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> <span class="col-10 px-0">Lei para o detetive particular</span>
                      </button>
                      <button class="btn d-flex mt-2 align-items-center text-left line-height-topicos fw-500 pl-0 py-0" @click.prevent="TrabalheConosco">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> <span class="col-10 px-0">Trabalhe conosco</span>
                      </button>
                      <button class="btn d-flex mt-2 align-items-center text-left line-height-topicos fw-500 pl-0 py-0" @click.prevent="Politica">
                        <ion-icon class="text-vermelho fs-16 mr-2" name="send-outline" /> <span class="col-10 px-0">Pol??tica de privacidade e Cookies</span>
                      </button>
                    </div>
                  </b-collapse>
                </div>
                <div class="bg-white border-radius-25">
                  <button v-b-toggle.collapse-estados class="btn d-flex mt-10 align-items-center pl-15 bg-white border-radius-25 py-10 border-radius-0-right col-12">
                    <ion-icon class="fs-25 text-vermelho" name="location-outline" />
                    <span class="ml-10 fs-19 text-vermelho fw-500">Onde atendemos</span>
                    <ion-icon class="ml-auto rotate-down fs-22 text-vermelho" name="arrow-redo" />
                  </button>
                  <b-collapse id="collapse-estados" class="pl-20">
                    <div class="pb-15 mt-1">
                      <button class="btn d-flex align-items-center fw-500 px-0 py-0" @click.prevent="SantaCatarina">
                        <ion-icon class="text-vermelho fs-16 mr-1" name="navigate-outline" /> Santa Catarina
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="Parana">
                        <ion-icon class="text-vermelho fs-16 mr-1" name="navigate-outline" /> Paran??
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="RioGrandeDoSul">
                        <ion-icon class="text-vermelho fs-16 mr-1" name="navigate-outline" /> Rio Grande do Sul
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="SaoPaulo">
                        <ion-icon class="text-vermelho fs-16 mr-1" name="navigate-outline" /> S??o Paulo
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="RioDeJaneiro">
                        <ion-icon class="text-vermelho fs-16 mr-1" name="navigate-outline" /> Rio de Janeiro
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="DistritoFederal">
                        <ion-icon class="text-vermelho fs-16 mr-1" name="navigate-outline" /> Distrito Federal
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="MinasGerais">
                        <ion-icon class="text-vermelho fs-16 mr-1" name="navigate-outline" /> Minas Gerais
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="MatoGrosso">
                        <ion-icon class="text-vermelho fs-16 mr-1" name="navigate-outline" /> Mato Grosso do Sul
                      </button>
                      <button class="btn d-flex mt-1 align-items-center fw-500 px-0 py-0" @click.prevent="Goias">
                        <ion-icon class="text-vermelho fs-16 mr-1" name="navigate-outline" /> Goi??s
                      </button>
                    </div>
                  </b-collapse>
                </div>
                <button class="btn d-flex mt-10 align-items-center pl-15 bg-white border-radius-25 py-10 border-radius-0-right col-12" @click.prevent="ScrollContato">
                  <ion-icon class="fs-25 text-vermelho" name="call-outline" />
                  <span class="ml-10 fs-19 text-vermelho fw-500">Contato</span>
                  <ion-icon class="ml-auto fs-22 text-vermelho" name="arrow-redo-outline" />
                </button>
              </div>
              <div class="px-15 mt-30 d-flex">
                <a href="https://www.facebook.com/Excellence-Detetives-1046988452361673" class="quadrado-redes-sociais d-flex justify-content-center align-items-center bg-white border-radius-15">
                  <ion-icon class="text-vermelho fs-35" name="logo-facebook" />
                </a>
                <a href="https://www.instagram.com/excellencedetetives/" class="quadrado-redes-sociais d-flex justify-content-center align-items-center mx-2 bg-white border-radius-15">
                  <ion-icon class="text-vermelho fs-35" name="logo-instagram" />
                </a>
                <a href="https://br.pinterest.com/excellencedetetives/_saved/" class="quadrado-redes-sociais d-flex justify-content-center align-items-center bg-white border-radius-15">
                  <ion-icon class="text-vermelho fs-35" name="logo-pinterest" />
                </a>
                <a href="https://www.youtube.com/channel/UCj1qP7tCKe9lCSZZApw835A" class="quadrado-redes-sociais d-flex justify-content-center align-items-center mx-2 bg-white border-radius-15">
                  <ion-icon class="text-vermelho fs-35" name="logo-youtube" />
                </a>
                <a href="https://twitter.com/Excellencedet" class="quadrado-redes-sociais d-flex justify-content-center align-items-center bg-white border-radius-15">
                  <ion-icon class="text-vermelho fs-35" name="logo-twitter" />
                </a>
              </div>
              <div class="px-15 mt-30">
                <h6 class="text-white fw-600 mb-0 d-flex align-items-center justify-content-center fs-18">
                  Contate-nos nos links abaixo
                </h6>
                <div class="d-flex justify-content-center">
                  <ion-icon class="fs-19 text-white" name="chevron-down-outline" />
                </div>
              </div>
              <div class="mt-10">
                <a href="tel:4740549146" class="d-flex border-bottom row no-underline col-10 pb-10 justify-content-center px-0 align-items-center mx-auto">
                  <ion-icon class="mr-1 text-white fs-30 rotate-telefone" name="call-outline" />
                  <div class="text-white">
                    <div class="fs-17 text-center fw-500">Baln. Cambori??</div>
                    <div class="fs-17 text-center fw-500">+55 (47) 4054-9146</div>
                  </div>
                </a>
                <a href="tel:4840429667" class="d-flex row no-underline col-10 border-bottom pb-10 justify-content-center mt-10 px-0 align-items-center mx-auto">
                  <ion-icon class="mr-1 text-white fs-30 rotate-telefone" name="call-outline" />
                  <div class="text-white">
                    <div class="fs-17 text-center fw-500">Florian??polis</div>
                    <div class="fs-17 text-center fw-500">+55 (48) 4042-9667</div>
                  </div>
                </a>
                <a href="tel:4140637970" class="d-flex row no-underline col-10 border-bottom pb-10 justify-content-center mt-10 px-0 align-items-center mx-auto">
                  <ion-icon class="mr-1 text-white fs-30 rotate-telefone" name="call-outline" />
                  <div class="text-white">
                    <div class="fs-17 text-center fw-500">Curitiba</div>
                    <div class="fs-17 text-center fw-500">+55 (41) 4063-7970</div>
                  </div>
                </a>
                <a href="tel:4932400968" class="d-flex row no-underline col-10 justify-content-center mt-10 px-0 align-items-center mx-auto">
                  <ion-icon class="mr-1 text-white fs-30 rotate-telefone" name="call-outline" />
                  <div class="text-white">
                    <div class="fs-17 text-center fw-500">Lages</div>
                    <div class="fs-17 text-center fw-500">+55 (49) 3240-0968</div>
                  </div>
                </a>
              </div>
            </aside>
          </transition>
        </div>
      </nav>
      <nav v-scroll="ScrollNav" class="navbar nav d-xs-none d-sm-none d-lg-flex fixed-top" :class="{'pt-40': !NavScroll, 'bg-grafite pt-10 pb-1 shadow': NavScroll}">
        <div class="container px-0">
          <a href="https://excellencedetetives.com.br/">
            <img src="../assets/img/logo-excellence.webp" :class="{'w-160': !NavScroll, 'w-120': NavScroll}" alt="Logo">
          </a>
          <div id="navbar-telefones" class="ml-auto pr-3 d-flex" :class="{'mt-2': !NavScroll, 'mt-0': NavScroll}">
            <a href="tel:4740549146" class="d-flex row no-underline align-items-center mx-0">
              <ion-icon class="mr-1 fs-30 rotate-telefone" name="call-outline" />
              <div class="text-white">
                <div class="fs-13 text-center">Baln. Cambori??</div>
                <div class="fs-13 text-center">+55 (47) 4054-9146</div>
              </div>
            </a>
            <a href="tel:4840429667" class="d-flex row no-underline align-items-center mx-30">
              <ion-icon class="mr-1 fs-30 rotate-telefone" name="call-outline" />
              <div class="text-white">
                <div class="fs-13 text-center">Florian??polis</div>
                <div class="fs-13 text-center">+55 (48) 4042-9667</div>
              </div>
            </a>
            <a href="tel:+4140637970" class="d-flex row no-underline align-items-center mx-0">
              <ion-icon class="mr-1 fs-30 rotate-telefone" name="call-outline" />
              <div class="text-white">
                <div class="fs-13 text-center">Curitiba</div>
                <div class="fs-13 text-center">+55 (41) 4063-7970</div>
              </div>
            </a>
            <a href="tel:4932400968" class="d-flex row no-underline align-items-center ml-30">
              <ion-icon class="mr-1 fs-30 rotate-telefone" name="call-outline" />
              <div class="text-white">
                <div class="fs-13 text-center">Lages</div>
                <div class="fs-13 text-center">+55 (49) 3240-0968</div>
              </div>
            </a>
          </div>
          <div id="navbar-links" class="px-0 col-12 d-flex row mx-auto border-top" :class="{'mt-15': !NavScroll, 'mt-10': NavScroll}">
            <button id="buttons-navbar" class="btn py-2 col border-radius-0" @click="ScrollHome">
              <div class="border-red active" />
              <span class="text-uppercase d-block fs-15 fw-500 letter-spacing-05 text-white">
                Home
              </span>
              <span class="text-uppercase d-block letter-spacing-05 fs-11 text-white-50 text-white">
                P??gina inicial
              </span>
            </button>
            <div class="border-separation mx-1" />
            <button id="buttons-navbar" class="btn py-2 col border-radius-0" @click.prevent="ScrollSobre">
              <div class="border-red" />
              <span class="text-uppercase d-block fs-15 fw-500 letter-spacing-05 text-white">
                Sobre n??s
              </span>
              <span class="text-uppercase d-block letter-spacing-05 fs-11 text-white-50 text-white">
                Sobre a excellence
              </span>
            </button>
            <div class="border-separation mx-1" />
            <button id="buttons-navbar" class="btn py-2 col border-radius-0 d-flex justify-content-center row mx-0 position-relative" @mouseenter="MethodShowDropdownServicos" @mouseleave="MethodHideDropdownServicos">
              <div class="border-red" />
              <span class="text-uppercase d-block fs-15 fw-500 letter-spacing-05 text-white">
                Servi??os
              </span>
              <span class="text-uppercase d-block letter-spacing-05 fs-11 text-white-50 text-white">
                Nossas habilidades
              </span>
              <transition enter-active-class="animate__animated animate__fadeIn" leave-active-class="animate__animated animate__fadeOut">
                <div v-show="ShowDropdownServicos" id="dropdown-servicos" class="pt-30">
                  <div class="col-12 position-relative cursor-normal px-10 py-10 d-flex justify-content-center row mx-0 rounded shadow-lg bg-vermelho-pouco-escuro h-100">
                    <div id="seta-dropdown" class="bg-vermelho-pouco-escuro" />
                    <div class="d-flex row col-12 px-0 mx-auto">
                      <h6 class="text-white col-12 px-0 fw-400 text-left">
                        Principais servi??os
                      </h6>
                      <div class="col px-0">
                        <button class="btn btn-dark d-flex align-items-center col-12" @click.prevent="InvestigacaoEmpresarial">
                          <ion-icon class="fs-22 mr-2" name="bar-chart-outline" />
                          Casos empresariais
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                        <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="InvestigacaoConjugal">
                          <ion-icon class="fs-22 mr-2" name="heart-dislike-outline" />
                          Casos conjugais
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                        <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="InvestigacaoPolitica">
                          <ion-icon class="fs-21 mr-2" name="cash-outline" />
                          Casos pol??ticos
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                        <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="ProvasAdvogados">
                          <ion-icon class="fs-23 mr-2" name="reader-outline" />
                          Provas para advogados
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                      </div>
                      <div class="col px-0 ml-2">
                        <button class="btn btn-dark d-flex align-items-center col-12" @click.prevent="PessoasDesaparecidas">
                          <ion-icon class="fs-23 mr-2" name="compass-outline" />
                          Pessoas desaparecidas
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                        <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="CelularEspiao">
                          <ion-icon class="fs-23 mr-2" name="phone-portrait-outline" />
                          Celular VIP
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                        <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="CursoDetetive">
                          <ion-icon class="fs-23 mr-2" name="school-outline" />
                          Curso de detetive particular
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                        <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="TodosOsServicos">
                          <ion-icon class="fs-23 mr-2" name="grid-outline" />
                          Todos os servi??os
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                      </div>
                    </div>
                    <div class="mt-3 d-flex row col-12 px-0 mx-auto">
                      <h6 class="text-white col-12 px-0 fw-400 text-left">
                        Navegue por nossos t??picos
                      </h6>
                      <div class="col px-0">
                        <button class="btn btn-dark d-flex align-items-center col-12" @click.prevent="SinaisFraudeEmpresarial">
                          <ion-icon class="fs-22 mr-2" name="bar-chart-outline" />
                          Sinais de desvios empresariais
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                        <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="SinaisTraicao">
                          <ion-icon class="fs-22 mr-2" name="heart-dislike-outline" />
                          Voc?? est?? sendo "tra??do"?
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                        <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="InscricaoCursoDetetive">
                          <ion-icon class="fs-22 mr-2" name="school-outline" />
                          Se inscreva no curso de detetive
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                      </div>
                      <div class="col ml-2 px-0">
                        <button class="btn btn-dark d-flex align-items-center col-12" @click.prevent="Legislacao">
                          <ion-icon class="fs-22 mr-2" name="newspaper-outline" />
                          Lei para o detetive particular
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                        <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="TrabalheConosco">
                          <ion-icon class="fs-22 mr-2" name="briefcase-outline" />
                          Trabalhe conosco
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                        <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="Politica">
                          <ion-icon class="fs-22 mr-2" name="lock-closed-outline" />
                          Pol??tica de privacidade e Cookies
                          <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                        </button>
                      </div>
                    </div>
                  </div>
                </div>
              </transition>
            </button>
            <div class="border-separation mx-1" />
            <button id="buttons-navbar" class="btn py-2 col border-radius-0 d-flex justify-content-center row mx-0 position-relative" @mouseenter="MethodShowDropdownEstados" @mouseleave="MethodHideDropdownEstados">
              <div class="border-red" />
              <span class="text-uppercase d-block col-12 px-0 fs-15 fw-500 letter-spacing-05 text-white">
                Onde atendemos
              </span>
              <span class="text-uppercase d-block col-12 px-0 letter-spacing-05 fs-11 text-white-50 text-white">
                Estados atendidos
              </span>
              <transition enter-active-class="animate__animated animate__fadeIn" leave-active-class="animate__animated animate__fadeOut">
                <div v-show="ShowDropdownEstados" id="dropdown-estados" class="pt-30">
                  <div class="col-12 position-relative cursor-normal px-10 py-10 rounded shadow-lg d-flex justify-content-center bg-vermelho-pouco-escuro h-100">
                    <div id="seta-dropdown" class="bg-vermelho-pouco-escuro" />
                    <div class="col-12 px-0">
                      <button class="btn btn-dark d-flex align-items-center col-12" @click.prevent="SantaCatarina">
                        <ion-icon class="fs-22 mr-1" name="location-outline" />
                        Santa Catarina
                        <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                      </button>
                      <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="Parana">
                        <ion-icon class="fs-22 mr-1" name="location-outline" />
                        Paran??
                        <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                      </button>
                      <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="RioGrandeDoSul">
                        <ion-icon class="fs-22 mr-1" name="location-outline" />
                        Rio Grande do Sul
                        <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                      </button>
                      <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="SaoPaulo">
                        <ion-icon class="fs-22 mr-1" name="location-outline" />
                        S??o Paulo
                        <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                      </button>
                      <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="RioDeJaneiro">
                        <ion-icon class="fs-22 mr-1" name="location-outline" />
                        Rio de Janeiro
                        <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                      </button>
                      <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="DistritoFederal">
                        <ion-icon class="fs-22 mr-1" name="location-outline" />
                        Distrito Federal
                        <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                      </button>
                      <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="MinasGerais">
                        <ion-icon class="fs-22 mr-1" name="location-outline" />
                        Minas Gerais
                        <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                      </button>
                      <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="MatoGrosso">
                        <ion-icon class="fs-22 mr-1" name="location-outline" />
                        Mato Grosso do Sul
                        <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                      </button>
                      <button class="btn btn-dark mt-2 d-flex align-items-center col-12" @click.prevent="Goias">
                        <ion-icon class="fs-22 mr-1" name="location-outline" />
                        Goi??s
                        <ion-icon class="fs-20 ml-auto" name="arrow-redo-outline" />
                      </button>
                    </div>
                  </div>
                </div>
              </transition>
            </button>
            <div class="border-separation mx-1" />
            <button id="buttons-navbar" class="btn py-2 col border-radius-0" @click.prevent="ScrollContato">
              <div class="border-red" />
              <span class="text-uppercase d-block fs-15 fw-500 letter-spacing-05 text-white">
                Contato
              </span>
              <span class="text-uppercase d-block letter-spacing-05 fs-11 text-white-50 text-white">
                Fale com a gente
              </span>
            </button>
          </div>
        </div>
      </nav>
    </header>
  </div>
</template>
<script>
export default {
  data () {
    return {
      NavScroll: false,
      ShowDropdownEstados: false,
      ShowDropdownServicos: false,
      ShowNav: false
    }
  },
  methods: {
    ScrollNav () {
      if (window.scrollY > 10) {
        this.NavScroll = true
        this.MethodHideDropdownEstados()
        this.MethodHideDropdownServicos()
      } else {
        this.NavScroll = false
      }
    },
    ShownNav () {
      this.ShowNav = true
      document.body.classList.add('overflow-hidden')
    },
    HideNav () {
      this.ShowNav = false
      document.body.classList.remove('overflow-hidden')
    },
    MethodShowDropdownEstados () {
      this.ShowDropdownEstados = true
    },
    MethodHideDropdownEstados () {
      this.ShowDropdownEstados = false
    },
    MethodShowDropdownServicos () {
      this.ShowDropdownServicos = true
    },
    MethodHideDropdownServicos () {
      this.ShowDropdownServicos = false
    },

    // Scrolls
    ScrollTodosOsServicos () {
      this.$smoothScroll({
        scrollTo: document.getElementById('servicos'),
        duration: 500,
        offset: -215
      })
    },
    ScrollServicos () {
      this.$smoothScroll({
        scrollTo: document.getElementById('servicos'),
        duration: 500,
        offset: -170
      })
    },
    ScrollCidades () {
      this.$smoothScroll({
        scrollTo: document.getElementById('sobre'),
        duration: 500,
        offset: -100
      })
    },

    // Scroll Bot??es
    ScrollHome () {
      this.$smoothScroll({
        scrollTo: document.getElementById('home'),
        duration: 500,
        offset: -100
      })
      this.HideNav()
    },
    ScrollSobre () {
      this.$smoothScroll({
        scrollTo: document.getElementById('sobre'),
        duration: 500,
        offset: -100
      })
      this.HideNav()
    },
    ScrollContato () {
      this.$smoothScroll({
        scrollTo: document.getElementById('contato'),
        duration: 500,
        offset: -100
      })
      this.HideNav()
    },

    // Cidades
    SantaCatarina () {
      this.$router.push('/detetive-particular-em-Santa-Catarina/#sobre')
      this.ScrollCidades()
      this.HideNav()
    },
    Parana () {
      this.$router.push('/detetive-particular-no-Parana/#sobre')
      this.ScrollCidades()
      this.HideNav()
    },
    RioGrandeDoSul () {
      this.$router.push('/detetive-particular-no-Rio-Grande-do-Sul/#sobre')
      this.ScrollCidades()
      this.HideNav()
    },
    SaoPaulo () {
      this.$router.push('/detetive-particular-em-Sao-Paulo/#sobre')
      this.ScrollCidades()
      this.HideNav()
    },
    RioDeJaneiro () {
      this.$router.push('/detetive-particular-no-Rio-de-Janeiro/#sobre')
      this.ScrollCidades()
      this.HideNav()
    },
    DistritoFederal () {
      this.$router.push('/detetive-particular-no-Distrito-Federal/#sobre')
      this.ScrollCidades()
      this.HideNav()
    },
    MinasGerais () {
      this.$router.push('/detetive-particular-em-Minas-Gerais/#sobre')
      this.ScrollCidades()
      this.HideNav()
    },
    MatoGrosso () {
      this.$router.push('/detetive-particular-no-Mato-Grosso-do-Sul/#sobre')
      this.ScrollCidades()
      this.HideNav()
    },
    Goias () {
      this.$router.push('/detetive-particular-em-Goias/#sobre')
      this.ScrollCidades()
      this.HideNav()
    },

    // Servi??os
    TodosOsServicos () {
      this.$router.push('/servicos/#servicos')
      this.HideNav()
    },
    InvestigacaoEmpresarial () {
      this.$router.push('/servicos/investigacao-empresarial/#servicos')
      this.HideNav()
    },
    InvestigacaoConjugal () {
      this.$router.push('/servicos/investigacao-conjugal/#servicos')
      this.HideNav()
    },
    InvestigacaoPolitica () {
      this.$router.push('/servicos/investigacao-politica/#servicos')
      this.HideNav()
    },
    ProvasAdvogados () {
      this.$router.push('/servicos/provas-para-advogados/#servicos')
      this.HideNav()
    },
    PessoasDesaparecidas () {
      this.$router.push('/servicos/localizacao-de-pessoas-desaparecidas/#servicos')
      this.HideNav()
    },
    CelularEspiao () {
      this.$router.push('/servicos/celular-VIP/#servicos')
      this.HideNav()
    },
    CursoDetetive () {
      this.$router.push('/servicos/curso-de-detetive-particular/#servicos')
      this.HideNav()
    },

    // Topicos
    SinaisFraudeEmpresarial () {
      this.$router.push('/servicos/investigacao-empresarial/#sinais-de-desvios-empresariais')
      this.HideNav()
    },
    SinaisTraicao () {
      this.$router.push('/servicos/investigacao-conjugal/#sinais-de-infidelidade-conjugal')
      this.HideNav()
    },
    Legislacao () {
      this.$router.push('/legislacao-para-a-profissao-de-detetive-particular/#servicos')
      this.HideNav()
    },
    TrabalheConosco () {
      this.$router.push('/trabalhe-conosco/#servicos')
      this.HideNav()
    },
    Politica () {
      this.$router.push('/politica-de-privacidade/#servicos')
      this.HideNav()
    },
    InscricaoCursoDetetive () {
      this.$router.push('/servicos/curso-de-detetive-particular/#inscricao-curso-detetive')
      this.HideNav()
    }
  }
}
</script>
<style scoped>
  ion-icon[name="return-up-forward-outline"]{
    --ionicon-stroke-width: 40px;
  }
  nav, nav img{
    transition: all .3s;
    -o-transition: all .3s;
    -moz-transition: all .3s;
    -webkit-transition: all .3s;
  }
  .line-height-topicos{
    line-height: 18px;
  }
  .rotate-down{
    transform: rotate(90deg);
    -o-transform: rotate(90deg);
    -moz-transform: rotate(90deg);
    -webkit-transform: rotate(90deg);
  }
  .animate__animated{
    animation-duration: .3s;
    -o-animation-duration: .3s;
    -moz-animation-duration: .3s;
    -webkit-animation-duration: .3s;
  }
  .border-red{
    position: absolute;
    top: -3px;
    left: -1px;
    height: 3px;
    width: calc(100% + 3px);
    transition: all .3s;
    -o-transition: all .3s;
    -moz-transition: all .3s;
    -webkit-transition: all .3s;
  }
  .border-red.active{
    background-color: var(--vermelho_pouco_escuro);
  }
  .w-180{
    width: 180px;
  }
  .w-160{
    width: 160px;
  }
  .w-130{
    width: 130px;
  }
  .w-120{
    width: 120px;
  }
  .w-125{
    width: 125px;
  }
  .border-separation{
    border-left: 1px solid #b5b5b595;
    height: 30px;
  }
  #buttons-navbar:hover .border-red{
    background-color: var(--vermelho);
  }
  #buttons-navbar:hover{
    background-color: #ffffff48;
  }
  #navbar-telefones ion-icon{
    color: #ffffff;
    transition: all .3s;
    -o-transition: all .3s;
    -moz-transition: all .3s;
    -webkit-transition: all .3s;
    font-size: 30px;
  }
  #navbar-telefones a:hover ion-icon{
    color: var(--vermelho);
  }
  #seta-dropdown{
    position: absolute;
    top: -6px;
    width: 15px;
    height: 15px;
    border-radius: 3px;
    transform: rotate(45deg);
    z-index: -1;
  }
  #dropdown-estados{
    position: absolute;
    top: 47px;
    width: 280px;
  }
  #dropdown-servicos{
    position: absolute;
    top: 47px;
    width: 740px;
  }
  #nav-offset {
    background-color: #ffffffd2;
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    right: 0;
    z-index: 19;
  }
  #nav-event {
    background-color: var(--vermelho_pouco_escuro);
    width: 310px;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 20;
    overflow-y: scroll;
    -ms-overflow-style: none;
    scrollbar-width: none;
  }
  #nav-event::-webkit-scrollbar {
    width: 0px !important;
  }
  .quadrado-redes-sociais{
    width: 50px;
    height: 50px;
  }
</style>
