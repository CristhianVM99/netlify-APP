<template>
  <loading 
  v-model:active="isLoading"
  :can-cancel="false"
  :background-color="fondobg"
  :opacity="opacidadbg"
  :color="coloricon"
  :loader="loader"
  :is-full-page="fullPage"/>
  <!-- Main content Start -->
  <div class="main-content">
    <!-- Breadcrumbs Start -->
    <div class="sc-breadcrumbs breadcrumbs-overlay">
      <div class="breadcrumbs-img">
        <img src="/bgUpea.jpg" alt="Breadcrumbs Image" />
      </div>
      <div class="breadcrumbs-text white-color">
        <h1 class="page-title">
          Sobre Nosotros
        </h1>
        <ul>
          <router-link :to="{ name: 'home' }">
            <button class="btn-page mr-40">
              Home
            </button>
          </router-link>          
          <button class="btn-page">
            nosotros
          </button>
        </ul>
      </div>
    </div>
    <!-- Breadcrumbs End -->

    <!-- About Section Start -->
    <div
      id="sc-about"
      class="sc-about pt-80 pb-170 md-pt-40 md-pb-70 position-relative arrow-animation-1"
    >
      <div class="container">
        <div class="row align-items-center">
          <div class="col-lg-5 md-mb-115">
            <div class="img-part position-relative">
              <img :src="url_api + '/InstitucionUpea/' + Institucion.institucion_logo" alt="img" />
              <!--<div class="about-experience text-center">
                <span>22+</span>
                Años de Experiencia
              </div>-->
            </div>
          </div>
          <div class="col-lg-7 pl-90 md-pl-15">
            <div class="sec-title mb-20">
              <div class="sub-title position-relative">
                Sobre la Carrera <span class="heading-border-line"></span>
              </div>
              <h2 class="title mb-20">{{ Institucion.institucion_nombre }}</h2>
              <h3 class="title mb-10">Mision</h3>
              <div class="des" v-html="Institucion.institucion_mision"></div>
              <h3 class="title mb-10">Vision</h3>
              <div class="des" v-html="Institucion.institucion_vision"></div>
            </div>
          </div>
        </div>
      </div>
      <div class="animated-arrow-1 animated-arrow left-right-new">
        <img src="/src/assets/images/arrow-1.png" alt="" />
      </div>
      <div class="animated-arrow-2 animated-arrow up-down-new">
        <img src="/src/assets/images/arrow-2.png" alt="" />
      </div>

      <div class="animated-arrow-3 animated-arrow up-down-new">
        <img src="/src/assets/images/arrow-3.png" alt="" />
      </div>
      <div class="animated-arrow-4 animated-arrow left-right-new">
        <img src="/src/assets/images/arrow-3.png" alt="" />
      </div>
    </div>
    <!-- About Section End -->

    <!-- Counter Section Start -->
    <div
      class="sc-counter style2-about pt-120 pb-115 md-pt-80 md-pb-50 counter-bg1 position-relative arrow-animation-1"
      v-if="this.carrera_id != 0"
    >
      <div class="container">
        <div class="row couter-area">
          <div class="col-lg-3 col-md-6 md-mb-30">
            <div class="counter-item text-center">
              <div class="icon-part">
                <i class="flaticon flaticon-laptop"></i>
              </div>
              <h2 class="counter-title">
                <span class="sc-count">{{ Convocatorias.length }}</span
                ><span class="text">+</span>
              </h2>
              <h5 class="title mb-0">Convocatorias, Comunicados & Avisos</h5>
            </div>
          </div>
          <div class="col-lg-3 col-md-6 md-mb-30">
            <div class="counter-item text-center ping-color">
              <div class="icon-part">
                <i class="flaticon flaticon-study"></i>
              </div>
              <h2 class="counter-title">
                <span class="sc-count">{{ Cursos.length }}</span
                ><span class="text">+</span>
              </h2>
              <h5 class="title mb-0">Cursos & Seminarios</h5>
            </div>
          </div>
          <div class="col-lg-3 col-md-6 md-mb-30">
            <div class="counter-item text-center green-color">
              <div class="icon-part">
                <i class="flaticon flaticon-teacher"></i>
              </div>
              <h2 class="counter-title">
                <span class="sc-count">{{ Servicios.length }}</span
                ><span class="text">+</span>
              </h2>
              <h5 class="title mb-0">Servicios</h5>
            </div>
          </div>
          <div class="col-lg-3 col-md-6 md-mb-30">
            <div class="counter-item text-center yellow-color">
              <div class="icon-part">
                <i class="flaticon flaticon-monitor"></i>
              </div>
              <h2 class="counter-title">
                <span class="sc-count">{{ Ofertas.length }}</span
                ><span class="text">+</span>
              </h2>
              <h5 class="title mb-0">Ofertas Academicas</h5>
            </div>
          </div>
        </div>
      </div>
      <div class="animated-arrow-1 animated-arrow left-right-new">
        <img src="/src/assets/images/arrow-5.png" alt="" />
      </div>
      <div class="animated-arrow-2 animated-arrow up-down-new">
        <img src="/src/assets/images/arrow-2.png" alt="" />
      </div>

      <div class="animated-arrow-3 animated-arrow up-down-new">
        <img src="/src/assets/images/arrow-4.png" alt="" />
      </div>
      <div class="animated-arrow-4 animated-arrow left-right-new">
        <img src="/src/assets/images/arrow-3.png" alt="" />
      </div>
    </div>
    <!-- Counter Section End -->

    <!-- About Section Start -->
    <div id="sc-about" class="sc-about about-style2 pt-120 pb-120 md-pt-80 md-pb-70">
      <div class="container">
        <div class="row">          
          <div class="col-lg-7 md-mt-50">
            <div class="sec-title mb-20">
              <div class="sub-title position-relative">
                {{ Institucion.institucion_nombre }} <span class="heading-border-line"></span>
              </div>
              <h2 class="title mb-20">
                Historia de la Institucion
              </h2>
              <div class="des mb-40" v-html="Institucion.institucion_historia"></div>
            </div>            
          </div>
          <div class="col-lg-5">
            <div class="img-part position-relative">
                <img
                :src="
                  url_api + '/InstitucionUpea/' + Institucion.institucion_logo
                "
                width="300"
                alt=""
              />
            </div>
            <div class="img-part position-relative" v-if="(this.carrera_id!=0)">
                <img src="../assets/images/upea.png" alt="img" 
                width="300"
                />
            </div>
            <div class="img-part position-relative">
                <img src="../assets/images/sie.png" alt="img" 
                width="300"
                />
            </div>
          </div>
        </div>
        <img class="up-down-new" src="../assets/images/about/shap_image.png" alt="" />
      </div>
    </div>
    <!-- About Section End -->
  </div>
  <!-- Main content End -->
</template>
<script>
import { mapState } from 'vuex'
import Services from '@/services/Services'
import Loading from 'vue-loading-overlay'
import 'vue-loading-overlay/dist/css/index.css'

export default {
  name: 'AboutView',
  data() {
    return {
      Convocatorias: [],
      Cursos: [],
      Servicios: [],
      Ofertas: [],

      loader: "bars",
      isLoading: false,
      fullPage: true,
      fondobg:"#C10202",
      opacidadbg:1,
      coloricon:"#fff"
    }
  },
  components:{
    Loading
  },
  computed: {
    ...mapState(['Institucion', 'url_api','carrera_id'])
  },
  methods: {
    async getConvocatoriasAll() {
      try {
        //optenemos todas la convocatorias, comunicados y avisos.
        const response = await Services.getConvocatoriasAll()
        this.Convocatorias = response.data        
      } catch (e) {
        console.log(e)
      }
    },
    async getCursosAll() {
      try {
        //optenemos todos los cursos y seminarios.
        const response = await Services.getCursosAll()
        this.Cursos = response.data
      } catch (e) {
        console.log(e)
      }
    },
    async getServiciosAll() {
      try {
        //optenemos todos los servicios
        const response = await Services.getServiciosAll()
        this.Servicios = response.data
      } catch (e) {
        console.log(e)
      }
    },
    async getOfertasAll() {
      try {
        //optenemos todas las ofertas
        const response = await Services.getOfertasAll()
        this.Ofertas = response.data
      } catch (e) {
        console.log(e)
      }
    },     
    //metodo que ejecuta los demas
    async createdComponent(){
      this.isLoading=true
      if(this.carrera_id!=0){        
        await this.getConvocatoriasAll()
        await this.getCursosAll()
        await this.getServiciosAll()
        await this.getOfertasAll()
      }
      setTimeout(()=>{
          this.isLoading = false
      },2000)
    }
  },
  created(){
    this.createdComponent()
  }
}
</script>
<style>
@import './css/AboutView.css';
</style>
