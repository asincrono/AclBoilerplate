<template>
  <div class="home">
    <div class="enterprise">
      <div class="content-top">
        
        <h4>{{ msg }}</h4>
        <a href="#/menu">Inicio</a>
      </div>

      <div class="content-footer" id="wrapper">
        <div id="fixed_div">
          <a href="#/drawermenu" class="sidebar-icon footer-1">
            <i class="material-icons dp48">mail</i>
            <span class="ico-text">contacto</span>
          </a>

          <a href="#/" class="sidebar-icon footer-2">
            <i class="material-icons dp48">help_outline</i>
            <span class="ico-text">ayuda</span>
          </a>

          <a href="#/map" class="sidebar-icon footer-2" v-on:click="show = !show">
            <i class="material-icons dp48">room</i>
            <span class="ico-text">mapa&nbsp;</span>
          </a>
          <a href="#/" class="sidebar-icon footer-2">
            <i class="material-icons dp48">close</i>
            <span class="ico-text">cerrar</span>
          </a>
          </div>
      </div>
      <div class="content-legal">
        <ul>
          <li><a @click="openInBrowser(Legal)">Legal</a></li> |
          <li><a @click="openInBrowser(Terms)">Terms</a></li> |
          <li><a @click="openInBrowser(Site)">Website.com</a></li> |
          <li>V. 1.0.1</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import '../assets/menus-green.css'
// import { Utils } from 'quasar'
// new Vue({
//   el: '#demo',
//   data: {
//     show: true
//   }
// })

export default {
  name: 'home',
  data () {
    return {
      msg: 'HOME',
      show: true,
      Legal: 'http://portal.tendgo.es/tienda/retail/index.html',
      Terms: 'http://openyapi.servotal.com/appframe/terms',
      Site: 'http://openyapi.servotal.com/appframe/privacy'
    }
  },
  methods: {
    openInBrowser (locationUrl, target = '_blank', location = 'location=no') {
      cordova.InAppBrowser.open(locationUrl, target, location)
      // Utils.openURL(locationUrl)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
#wrapper {
    width: 100%;
    position: fixed;
    bottom: 25px;
}
#fixed_div {
    margin-left: auto;
    margin-right: auto;
    position: relative;
    width: 305px;
    text-align: center;
}

.content-footer{
  /*text-align: center;
  display: inline-block;*/
}

.content-legal{
    /*float:left;
    text-align: center;
    display: inline-block;*/
    position: fixed;
    bottom: 0px;
    width: 100%;
    font-size: 12px;
}


.content-legal ul{
    list-style:none;
    color:#fff;
}
.content-legal ul li a {
    color: #fff;
}

.content-footer a:hover {
    background-image: url('../assets/images/misc/nav_green/nav_green-3.png');

}
.content-footer a:hover .ico-text{
  color: #444444;
}
.content-footer a:hover .dp48{
  color: #444444;
}


.ico-text{
  position: relative;
  top: 12px;
  color: #fff;
  font-size:14px;
}


.dp48{
  font-size: 30px;
  width: 30px;
  height: 30px;
  color: #f4f4f4;
  position: relative;
  top: 15px;
}

.clear {
    clear: both;
    height: 0px;
    line-height: 0px;
}

.sidebar-icon {
    background-repeat: no-repeat;
    background-size: 70px 80px;
    height: 80px;
    width: 70px;
    float: left;
}

.enterprise {
  position: relative;
  top: 20%;
  text-align: center;
}
.home h1, .home h2 {
  font-weight: normal;
}

.home ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
  margin-bottom: 5px;
}

.home li {
  display: inline-block;
  margin: 0 10px;
}

.home h4 {
  font-family: 'Gotham Rounded', Helvetica, Arial, sans-serif;
  position: relative;
  top: -57px;
  font-weight: bold;
  color: #444444;
}

.home {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /*color: #2c3e50;*/

}

.home .content-top a {
  color: #fff;
  text-decoration: underline;
}

.home{
/*background: url(../statics/images/bg.jpg) no-repeat center center;*/
background-color: #76C34F;
background-attachment:fixed;
-webkit-background-size: 100%;
-moz-background-size: 100%;
-o-background-size: 100%;
background-size: 100%;
-webkit-background-size: cover;
-moz-background-size: cover;
-o-background-size: cover;
background-size: cover;
width: 100%;
height: 100%;
}



</style>
