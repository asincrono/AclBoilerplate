## Quasar with airbnb eslint style

npm uninstal eslint-config-standard --save-dev
npm install --save-dev eslint-plugin-import
npm install --save-dev eslint-config-airbnb
npm install --save vue-resource

on .eslintrc.js
```
extends: 'airbnb-base'
```
## Config
 - Google API key AIzaSyDTn-9Z-I-KOjmINgdn9isIgANSPb4FDHs
 - Center: {lat: 41.3941772, lng: 2.2002508}
 - {lat: 41.39625, lng: 2.20108}
 - {lat: 41.39311, lng: 2.20428}
 - Marker 1: {lat: 41.448, lng: 2.18828}
 - Marker 2: {lat: 41.44725, lng: 2.19508}


## Links
Animations https://vuejs.org/v2/guide/transitions.html#Custom-Transition-Classes
Animation.css http://forum.quasar-framework.org/topic/199/add-animate-css
Vue-animate https://github.com/haydenbbickerton/vue-animate
COmming soon https://github.com/quasarframework/quasar/issues/169
Layouts http://forum.quasar-framework.org/topic/34/using-layouts-how/2
Open drawer https://github.com/quasarframework/quasar/issues/69
Multi Layput solved https://github.com/misterGF/CoPilot/blob/master/src/routes.js
Cordova plugin http://forum.quasar-framework.org/topic/79/example-use-cordova-plugin
Best practice about pages https://github.com/quasarframework/quasar/issues/30
Google map key markers https://developers.google.com/maps/documentation/javascript/error-messages#invalid-key-map-error
Vue Google mpas 2 https://github.com/xkjyeah/vue-google-maps
Map Play https://jsfiddle.net/ux4d3hbj/
Map issues https://github.com/GuillaumeLeclerc/vue-google-maps/issues/28
Google Map API https://developers.google.com/maps/documentation/javascript/custom-markers
Google Map Clustering https://developers.google.com/maps/documentation/ios-sdk/utility/marker-clustering



## Quasar commands
 - sudo npm install -g quasar-cli
 - quasar dev ios
 - quasar wrap cordova
 - quasar build ios
 - quasar build
 - quasar init nebula
 - cordova run ios --device
 - cordova build browser
 - cordova emulate ios --list
 - cordova emulate ios --target="iPhone-6s, 9.3"


## Some useful stuff

###

### Transition on button
```
<div id="demo">
  <transition name="fade">
    <h4 v-if="show">{{ msg }}</h4>
    <p v-if="show">hello</p>

  </transition>
</div>

<button v-on:click="show = !show">
  Toggle
</button>

data () {
  return {
    msg: 'Tendgo',
    show: true
  }
},

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
  opacity: 0
}
```

### Transition on q-view
```
Main.js
 import 'animate.css/animate.min.css'

<transition
             name="transitions"
             enter-active-class="animated tada"
             leave-active-class="animated fadeOut"
             mode="out-in"
     >
<router-view class="layout-view"></router-view>
</transition>
```

### Transition HOOKS
```
<transition name="fade" v-on:after-enter="afterEnter" v-on:before-enter="beforeEnter">
<img v-if="show" src="../assets/tendgo-logo.png" style="height:230px;">
</transition>

methods: {
  beforeEnter: function (el) {
    console.log('before')
  },
  afterEnter: function (el) {
    console.log('after')
    return {
      show: true
    }
  },


```
