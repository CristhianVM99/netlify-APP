<template>
  <!--Preloader area start here-->
  <!--<section class="loader_first">
    <div class="circular-spinner"></div>
  </section>-->
  <!--Preloader area End here-->

  <!--Full width header Start-->
  <div class="sc-header-section">
    <!--Header Start-->
    <header id="sc-header" class="sc-header">
      <!-- Topbar Area Start -->
      <div class="topbar-area">
        <div class="container">
          <div class="row align-items-center">
            <div class="col-md-7">
              <ul class="topbar-contact">
                <li>
                  <i class="flaticon flaticon-call"></i>
                  <a href="tel:+(111)256352">+591 {{ Institucion.institucion_telefono1 }} </a>
                </li>
                <li>
                  <i class="flaticon flaticon-mail"></i>
                  <a href="mailto:support@rstheme.com">{{ Institucion.institucion_correo1 }} </a>
                </li>
              </ul>
            </div>
            <div class="col-md-5 text-end">
              <ul class="topbar-right">
                <li class="login-register">
                  <i class="fa fa-sign-in"></i>
                  <a href="http://administracionpaginas.upea.edu.bo/login">Ingresar</a>
                  <!--<router-link :to="{ name: 'register' }">Register</router-link>-->
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <!-- Topbar Area End -->

      <!-- Menu Start -->
      <div class="menu-area menu-sticky">
        <div class="container">
          <div class="row align-items-center">
            <div class="col-lg-3">
              <div class="logo-cat-wrap">
                <div class="logo-part">
                  <router-link
                    :to="{ name: 'home' }"
                    v-if="this.carrera_id == 0"
                    class="logo-content"
                  >
                    <img src="../assets/images/logoupeanuevo.png" alt="logo" />
                  </router-link>
                  <router-link :to="{ name: 'home' }" class="logo-content-2" v-if="this.carrera_id!=0">
                    <img
                      :src="url_api + '/InstitucionUpea/' + Institucion.institucion_logo"
                      alt=""
                    />
                    <span>{{ Institucion.institucion_nombre }}</span>
                  </router-link>
                </div>
              </div>
            </div>
            <div class="col-lg-9 align-items-center d-flex text-end justify-content-end">
              <div class="sc-menu-area">
                <div class="main-menu">
                  <div class="mobile-menu">
                    <a class="sc-menu-toggle" @click="toogleMenu">
                      <i class="fa fa-bars"></i>
                    </a>
                  </div>
                  <nav
                    class="sc-menu"
                    :class="{ 'sc-menu-close': !isOpen }"
                    :style="{ height: isOpen ? menuHeight + 'px' : '0px' }"
                  >
                    <ul class="nav-menu">
                      <li class="menu-item-has-children">
                        <router-link to="/" href="#">Inicio</router-link>
                        <ul class="sub-menu">
                          <li>
                            <router-link :to="{ name: 'about' }">Sobre Nosotros</router-link>
                          </li>
                          <li v-if="this.carrera_id == 0">
                            <router-link :to="{ name: 'contacto' }">Contacto</router-link>
                          </li>
                        </ul>
                      </li>

                      <li
                        class="menu-item-has-children"
                        id="menu_convocatorias"
                        v-if="this.carrera_id == 0"
                      >
                        <a href="#">Areas y Carreras </a>
                        <ul class="sub-menu">
                          <li v-for="(area, id_area) in this.MenuAreasyCarreras" :key="id_area">
                            <a href="#">{{ area.area.toLowerCase() }}</a>
                            <ul class="sub-menu">
                              <li v-for="(carrera, id_carrera) in area.carreras" :key="id_carrera">
                                <a
                                  :href="`http://${carrera.nombre_simple.toLowerCase()}.upea.edu.bo/`"
                                  target="_blank"
                                  >{{ carrera.carrera }}</a
                                >
                              </li>
                            </ul>
                          </li>
                        </ul>
                      </li>

                      <li
                        class="menu-item-has-children"
                        id="menu_convocatorias"
                        v-if="this.carrera_id == 0"
                      >
                        <a href="#">Unidades Administrativas</a>
                        <ul class="sub-menu">
                          <li>
                            <a href="#">Rectorado</a>
                            <ul class="sub-menu">
                              <li>
                                <a href="https://titulos.upea.bo/" target="_blank"
                                  >Unidad de Titulos y Diplomas</a
                                >
                              </li>
                            </ul>
                          </li>
                          <li>
                            <a href="#">Vicerrectorado</a>
                            <ul class="sub-menu">
                              <li>
                                <a href="https://vicerrectorado.upea.bo/l" target="_blank"
                                  >Vicerrectorado</a
                                >
                              </li>
                              <li>
                                <a href="https://www.sie.upea.bo/l" target="_blank"
                                  >Unidad de Sistemas de Informacion y Estadistica</a
                                >
                              </li>
                              <li>
                                <a href="https://registrosadmisiones.upea.bo/" target="_blank"
                                  >Registros y Admiciones</a
                                >
                              </li>
                            </ul>
                          </li>
                          <li>
                            <a href="#">Extencion Universitaria (Bienestar Estudiantil)</a>
                            <ul class="sub-menu">
                              <li>
                                <a href="https://solid.upea.bo/" target="_blank"
                                  >Direccion de Interaccion Social y Cultural</a
                                >
                              </li>
                            </ul>
                          </li>
                          <li>
                            <a href="#">Decanatura Area Ingenierias</a>
                          </li>
                          <li>
                            <a href="#">Auditoria Interna </a>
                            <ul class="sub-menu">
                              <a
                                href="https://www.upea.bo/u/xqOXL3NKgwqJF17iNKEQraWzP"
                                target="_blank"
                                >Direccion de Auditoria Interna</a
                              >
                            </ul>
                          </li>
                        </ul>
                      </li>

                      <li
                        class="menu-item-has-children"
                        id="menu_convocatorias"
                        v-if="this.carrera_id != 0"
                      >
                        <a href="#">Convocatorias </a>
                        <ul class="sub-menu">
                          <li v-for="(link, id_conv) in MenuConvocatorias" :key="id_conv">
                            <router-link
                              :to="{
                                name: 'convocatorias',
                                params: {
                                  tipo: link.tipo_conv_comun_titulo.toLowerCase()
                                }
                              }"
                              >{{ link.tipo_conv_comun_titulo.toLowerCase() }}</router-link
                            >
                          </li>
                        </ul>
                      </li>

                      <li class="menu-item-has-children" v-if="this.carrera_id != 0">
                        <a href="#">Cursos</a>
                        <ul class="sub-menu">
                          <li v-for="(link, id_conv) in MenuCursos" :key="id_conv">
                            <router-link
                              :to="{
                                name: 'cursos',
                                params: {
                                  tipo: link.tipo_conv_curso_nombre.toLowerCase()
                                }
                              }"
                              >{{ link.tipo_conv_curso_nombre.toLowerCase() }}</router-link
                            >
                          </li>
                        </ul>
                      </li>

                      <li class="menu-item-has-children" v-if="this.carrera_id == 0">
                        <a href="#">Mas</a>
                        <ul class="sub-menu">
                          <li v-if="this.carrera_id != 0">
                            <router-link
                              :to="{
                                name: 'servicios',
                                params: {
                                  tipo: 'servicios'
                                }
                              }"
                              >Servicios</router-link
                            >
                          </li>
                          <li v-if="this.carrera_id != 0">
                            <router-link
                              :to="{
                                name: 'ofertasacademicas',
                                params: {
                                  tipo: 'ofertasacademicas'
                                }
                              }"
                              >Ofertas Academicas</router-link
                            >
                          </li>
                          <li>
                            <router-link
                              :to="{
                                name: 'publicaciones',
                                params: {
                                  tipo: 'publicaciones'
                                }
                              }"
                              >Publicaciones</router-link
                            >
                          </li>
                          <li>
                            <router-link
                              :to="{
                                name: 'gacetas',
                                params: {
                                  tipo: 'gacetas'
                                }
                              }"
                              >Gaceta</router-link
                            >
                          </li>
                          <li>
                            <router-link
                              :to="{
                                name: 'eventos',
                                params: {
                                  tipo: 'eventos'
                                }
                              }"
                              >Eventos</router-link
                            >
                          </li>
                          <li>
                            <router-link
                              :to="{
                                name: 'videos',
                                params: {
                                  tipo: 'videos'
                                }
                              }"
                              >Videos</router-link
                            >
                          </li>
                        </ul>
                      </li>

                      <li class="menu-item-has-children" v-if="this.carrera_id != 0">
                        <a href="#">Links</a>
                        <ul class="sub-menu">
                          <li v-for="(link, id_link) of Links" :key="id_link">
                            <a :href="link.ei_link" target="_blank">{{ link.ei_nombre }}</a>
                          </li>
                        </ul>
                      </li>

                      <li v-if="this.carrera_id != 0">
                        <router-link :to="{ name: 'contacto' }">Contacto</router-link>
                      </li>
                    </ul>
                    <!-- //.nav-menu -->
                  </nav>
                </div>
                <!-- //.main-menu -->
              </div>
              <div class="expand-btn-inner text-end">
                <ul>
                  <!--<li>
                    <a
                      class="hidden-xs sc-search"
                      data-bs-target="#search-modal"
                      data-bs-toggle="modal"
                      href="#"
                    >
                      <i class="flaticon flaticon-magnifying-glass"></i>
                    </a>
                  </li>-->
                </ul>
                <span>
                  <a id="nav-expander" class="nav-expander">
                    <span class="dot1"></span>
                    <span class="dot2"></span>
                    <span class="dot3"></span>
                  </a>
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- Menu End -->

      <!-- Canvas Menu start -->
      <nav class="right_menu_togle hidden-md">
        <div class="close-btn">
          <div id="nav-close">
            <div class="line"><span class="line1"></span><span class="line2"></span></div>
          </div>
        </div>
        <div class="canvas-logo">
          <router-link :to="{ name: 'home' }"
            ><img
              :src="url_api + '/InstitucionUpea/' + Institucion.institucion_logo"
              alt="logo"
              width="70"
              height="70"
          /></router-link>
        </div>
        <div class="offcanvas-text">
          <p>
            Many desktop publishing packages and web page editors now use Lorem Ipsum as their
            default model text, and a search for web sites still in their infancy.
          </p>
        </div>

        <ul class="address-widget">
          <li>
            <i class="flaticon flaticon-call"></i>
            <a href="tel:+(111)256352">Call: +(111)256 352</a>
          </li>
          <li>
            <i class="flaticon flaticon-mail"></i>
            <a href="mailto:infosimple@gmail.com">infosimple@gmail.com</a>
          </li>
          <li>
            <div class="desc">
              <i class="flaticon flaticon-maps-and-flags"></i>
              202 Raffles Ave, Carlisle CA2 7EF, United Kingdon
            </div>
          </li>
        </ul>
        <div class="canvas-contact">
          <ul class="social">
            <li>
              <a href="#"><i class="fa fa-facebook"></i></a>
            </li>
            <li>
              <a href="#"><i class="fa fa-twitter"></i></a>
            </li>
            <li>
              <a href="#"><i class="fa fa-pinterest-p"></i></a>
            </li>
            console.log(this.MenuConvocatorias.length)
            <li>
              <a href="#"><i class="fa fa-linkedin"></i></a>
            </li>
          </ul>
        </div>
      </nav>
      <!-- Canvas Menu end -->
    </header>
    <!--Header End-->
  </div>
  <!--Full width header End-->
</template>
<script>
import { mapState } from 'vuex'

export default {
  name: 'HeaderComp',

  data() {
    return {
      isOpen: false,
      menuHeight: 0
    }
  },
  computed: {
    ...mapState([
      'url_api',
      'MenuConvocatorias',
      'MenuCursos',
      'Institucion',
      'Links',
      'carrera_id',
      'MenuAreasyCarreras'
    ])
  },
  methods: {
    toogleMenu() {
      this.isOpen = !this.isOpen
      const menuRef = this.$refs.menu
      if (menuRef) {
        this.menuHeight = menuRef.clientHeight
      }
    },
    handleClick(event) {
      //agregar al componente span.sc-menu-parent @click="handleClick"
    event.preventDefault();
    
    const t = $(event.target);
    let menu = t.siblings('ul');
    const parent = t.parent('li');
    const siblings = parent.siblings('li');
    const arrow_target = 'span.sc-menu-parent';
    
    if (menu.hasClass('sub-menu')) {
      menu = t.siblings('ul.sub-menu');
    } else if (menu.hasClass('mega-menu')) {
      menu = t.siblings('ul.mega-menu');
    }
    
    if (menu.hasClass('visible')) {
      setTimeout(() => {
        menu.removeClass('visible');
      }, 10);
      t.html(arrow_down);
    } else {
      setTimeout(() => {
        menu.addClass('visible');
      }, 10);
      t.html(arrow_up);
    }
    
    /*-------------------------------------*/
    /*    CLOSE MENUS
    /*-------------------------------------*/
    
    // Close sub menus
    parent.find('ul.visible').removeClass('visible');
    
    // Close sub menus parents
    parent.siblings('li').children('ul').removeClass('visible');
    
    // Close sub menus child parents
    siblings.find('ul.visible').removeClass('visible');
    
    /*-------------------------------------*/
    /*    INSERT ARROW DOWN
    /*-------------------------------------*/
    
    // Insert arrow down in sub menus
    parent.children('ul').find(arrow_target).html(arrow_down);
    
    // Insert arrow down in sub menus parents
    siblings.children(arrow_target).html(arrow_down);
    
    // Insert arrow down in sub menus child parents
    siblings.find(arrow_target).html(arrow_down);
    },
    menu_script(){

    // Defines variables
    const arrowUp = '<i class="fa fa-angle-up" aria-hidden="true"></i>';
    const arrowDown = '<i class="fa fa-angle-down" aria-hidden="true"></i>';
    const arrowSpan = '<span class="sc-menu-parent">' + arrowDown + '</span>';
    const closeButton = '<div class="sub-menu-close"><i class="fa fa-times" aria-hidden="true"></i>Close</div>';

    // Insert all arrow down span element
    $('.nav-menu .sc-mega-menu').append(arrowSpan);
    $('.nav-menu > .menu-item-has-children').append(arrowSpan);
    $('.nav-menu > .menu-item-has-children .sub-menu > .menu-item-has-children').append(arrowSpan);
    $('.nav-menu .menu-item-has-children .sub-menu li .sub-menu').after(arrowSpan);
    

    // Insert all close button element
    $('.nav-menu .menu-item-has-children .sub-menu').append(closeButton);
    $('.nav-menu .sc-mega-menu .mega-menu').append(closeButton);

    /*-----------------------------------------------------------------------------------*/
    /*  OPEN SUB MENU FUNCTION
    /*-----------------------------------------------------------------------------------*/
    $('span.sc-menu-parent').on('click', function (e) {
      e.preventDefault();

      const t = $(this);
      let menu = t.siblings('ul');
      const parent = t.parent('li');
      const siblings = parent.siblings('li');
      const arrowTarget = 'span.sc-menu-parent';

      if (menu.hasClass('sub-menu')) {
        menu = t.siblings('ul.sub-menu');
      } else if (menu.hasClass('mega-menu')) {
        menu = t.siblings('ul.mega-menu');
      }

      if (menu.hasClass('visible')) {
        setTimeout(function () {
          menu.removeClass('visible');
        }, 10);
        t.html(arrowDown);
      } else {
        setTimeout(function () {
          menu.addClass('visible');
        }, 10);
        t.html(arrowUp);
      }

      /*-------------------------------------*/
      /*  CLOSE MENUS
      /*-------------------------------------*/

      // Close sub menus
      parent.find('ul.visible').removeClass('visible');

      // Close sub menus parents
      parent.siblings('li').children('ul').removeClass('visible');

      // Close sub menus child parents
      siblings.find('ul.visible').removeClass('visible');

      /*-------------------------------------*/
      /*  INSERT ARROW DOWN
      /*-------------------------------------*/

      // Insert arrow down in sub menus
      parent.children('ul').find(arrowTarget).html(arrowDown);

      // Insert arrow down in sub menus parents
      siblings.children(arrowTarget).html(arrowDown);

      // Insert arrow down in sub menus child parents
      siblings.find(arrowTarget).html(arrowDown);
    });

    /*-----------------------------------------------------------------------------------*/
    /*  CLOSE BUTTON
    /*-----------------------------------------------------------------------------------*/
    $('ul.nav-menu div.sub-menu-close').on('click', function (e) {
      e.preventDefault();

      const a = $(this).parent('ul');
      a.removeClass('visible');
      a.siblings('span.sc-menu-parent').html(arrowDown);
    });

    /*-----------------------------------------------------------------------------------*/
    /*  EFFECTS ON MENU TOGGLE
    /*-----------------------------------------------------------------------------------*/
    $('a.sc-menu-toggle').on('click', function (e) {
      e.preventDefault();
      const menuHeight = $('.sc-menu ul').height();

      if ($(this).hasClass('sc-menu-toggle-open')) {
        $(this).removeClass('sc-menu-toggle-open').addClass('sc-menu-toggle-close');
        $('.sc-menu').animate({ height: '0px' }, { queue: false, duration: 300 }).addClass('sc-menu-close');
      } else {
        $(this).removeClass('sc-menu-toggle-close').addClass('sc-menu-toggle-open');
        $('.sc-menu').animate({ height: menuHeight }, { queue: false, duration: 300 }).removeClass('sc-menu-close');
      }
    });

    /*-----------------------------------------------------------------------------------*/
    /*  CLOSE MENUS ON RESIZE
    /*-----------------------------------------------------------------------------------*/
    let windowWidth = 0;

    $(window).on('load', function () {
      windowWidth = $(window).width();
      $('.sc-menu').addClass('sc-menu-close');
    });

    $(window).resize(function () {
      if (windowWidth !== $(window).width()) {
        $('.visible').removeClass('visible');
        $('.sc-menu-toggle').removeClass('sc-menu-toggle-open').addClass('sc-menu-toggle-close');
        $('.sc-menu').css('height', '0').addClass('sc-menu-close');

        $('span.sc-menu-parent').html(arrowDown);
        windowWidth = $(window).width();
      }
    });  
    },
  }, 
  created() {    
    this.menu_script();
  },
  mounted() {
    this.menu_script();
  },    
}
</script>
<style scoped>
@import './css/HeaderComp.css';
</style>
