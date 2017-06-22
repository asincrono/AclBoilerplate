<template>
  <div class="menuu">
    <div class="enterprise">

      <div class="content-top" id="example-3">
        <h4>{{ msg }}</h4>
        <div class="indicators">
          <div :class="{ ok: cordova.deviceready }">
            <span></span>deviceready
          </div>
          <div v-for="(pluginTest, plugin) in plugins" :class="{ ok: pluginEnabled(plugin) }" @click="pluginTest">
            <span></span>{{ plugin }}</br></br>
          </div>
          <p>
            Click a plugin name to run a simple test
          </p>
        </div>        
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

          <a href="#/map" class="sidebar-icon footer-2">
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
          <li><a @click="openLegal()">Legal</a></li> |
          <li><a @click="openTerms()">Terms</a></li> |
          <li><a @click="openSite()">Website.com</a></li> |
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
import Vue from 'vue'

export default {
  name: 'menuu',
  data () {
    return {
      msg: 'Menu',
      cordova: Vue.cordova,
      plugins: {
        'cordova-plugin-camera': function () {
          if (!Vue.cordova.camera) {
            window.alert('Vue.cordova.camera not found !')
            return
          }
          Vue.cordova.camera.getPicture((imageURI) => {
            window.alert('Photo URI : ' + imageURI)
          }, (message) => {
            window.alert('FAILED : ' + message)
          }, {
            quality: 50,
            destinationType: Vue.cordova.camera.DestinationType.FILE_URI
          })
        },
        'cordova-plugin-device': function () {
          if (!Vue.cordova.device) {
            window.alert('FAILED : device information not found')
          }
          else {
            window.alert('Device : ' + Vue.cordova.device.manufacturer + ' ' + Vue.cordova.device.platform + ' ' + Vue.cordova.device.version + ' ' + Vue.cordova.device.uuid)
          }
        },
        'cordova-plugin-geolocation': function () {
          if (!Vue.cordova.geolocation) {
            window.alert('Vue.cordova.geolocation not found !')
            return
          }
          Vue.cordova.geolocation.getCurrentPosition((position) => {
            window.alert('Current position : ' + position.coords.latitude + ',' + position.coords.longitude)
          }, (error) => {
            window.alert('FAILED Error #' + error.code + ' ' + error.message)
          }, {
            timeout: 1000,
            enableHighAccuracy: true
          })
        },
        'cordova-plugin-contacts': function () {
          if (!Vue.cordova.contacts) {
            window.alert('Vue.cordova.contacts not found !')
            return
          }
          const ContactFindOptions = ContactFindOptions || function () {}
          Vue.cordova.contacts.find(['displayName'], (contacts) => {
            window.alert('Contacts found : ' + contacts.length)
          }, (error) => {
            window.alert('FAILED : ' + error.code)
          })
        }
      }
    }
  },
  methods: {
    pluginEnabled: function (pluginName) {
      return this.cordova.plugins.indexOf(pluginName) !== -1
    },
    openSite () {
      cordova.InAppBrowser.open('http://portal.tendgo.es/tienda/retail/index.html', '_blank', 'location=no')
      // Utils.openURL('http://portal.tendgo.es/tienda/retail/index.html')
    },
    openTerms () {
      cordova.InAppBrowser.open('http://openyapi.servotal.com/appframe/terms', '_blank', 'location=no')
      // Utils.openURL('http://portal.tendgo.es/tienda/retail/index.html')
    },
    openLegal () {
      cordova.InAppBrowser.open('http://openyapi.servotal.com/appframe/privacy', '_blank', 'location=no')
      // Utils.openURL('http://portal.tendgo.es/tienda/retail/index.html')
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
.menuu h1, .menuu h2 {
  font-weight: normal;
}

.menuu ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
  margin-bottom: 5px;
}

.menuu li {
  display: inline-block;
  margin: 0 10px;
}

.menuu h4 {
  font-family: 'Gotham Rounded', Helvetica, Arial, sans-serif;
  position: relative;
  top: -57px;
  font-weight: bold;
  color: #444444;
}

.menuu {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /*color: #2c3e50;*/

}

.menuu .content-top a {
  color: #fff;
  text-decoration: underline;
}

.menuu{
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
