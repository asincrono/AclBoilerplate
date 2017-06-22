<template>
  <div id="root">
  <gmap-map
    :center="center"
    :zoom="15"
    :options="{streetViewControl: false,
               mapTypeControl: false,
               zoomControl: false,
               scaleControl: false,
               fullscreenControl: false}"
    style="width: 100%; height: 800px"
  >
  <gmap-cluster>
    <gmap-marker
      v-for="m in markers"
      :position="m.position"
      :icon.sync="m.icon"
      :clickable="true"
      :draggable="false"
      @g-click="center=m.position"
      @click="handleClickMarker(m.id)">




      <gmap-info-window v-if="show === m.id"
          :idinfo="m.id"
          :opened.sync="m.isClicked">
          {{m.name}}
          <article class="search-info-window">
            <a target="_blank" title="Belle chambre meublée très proche de l'ehl"
               href="/property/5862e945c3edb4027d0f88ac">
              <div class="listing-img-link"
                   style="background-image: url('/statics/images/icons/salad-677913_960_720.jpg');opacity: 1;">
                <div class="listing-img-link__price">
                  <span>1'080 <span class="currency">CHF</span></span>
                </div>
                <div class="listing-img-link__text-wrap">
                  <h3 class="text-size-normal listing-img-link__name listing-img-link__name--search">
                    Belle chambre meublée très proche de l'ehl
                  </h3>
                  <span class="text-size-small">Lausanne 26, Switzerland</span>
                </div>
              </div>
            </a>
            <div class="listing-img-link__meta text-size-small"> <span>Individual bedrooms</span>
              <div class="listing-img-link__icon-info">
                <img class="listing-img-link__icon-info__img" src="/statics/images/icons/apartment-listing.svg" alt="Apartment">
                <div class="listing-img-link__icon-info__label">Apartment</div> </div>
              </div>
          </article>
      </gmap-info-window>
    </gmap-marker>
  </gmap-cluster>
  </gmap-map>
</div>
</template>

<script>
import Vue from 'vue'
import * as VueGoogleMap from 'vue2-google-maps'
// import latlngChangedHandler from '../utils/latlngChangedHandler.js'

  // New in 0.4.0
document.addEventListener('DOMContentLoaded', function () {
  Vue.component('google-map', VueGoogleMap.Map)
  Vue.component('google-marker', VueGoogleMap.Marker)
  Vue.component('google-cluster', VueGoogleMap.Cluster)
  Vue.component('google-info', VueGoogleMap.InfoWindow)
})

export default {
  // el: '#root',
  methods: {
    handleClickMarker (idinfo) {
      console.log('show:', this.show)
      console.log('idinfo:', idinfo)
      if (idinfo === this.show) {
        this.show = -idinfo
      }
      else {
        this.show = idinfo
      }
      console.log('to show:', this.show)
      return this.show
    }
  },
  data: function data () {
    return {
      show: 0,
      center: {lat: 41.3941772, lng: 2.2002508},
      markers: [{
        id: 1,
        position: {lat: 41.39625, lng: 2.20108},
        isClicked: true,
        icon: {url: '/statics/images/icons/point1.png'}
      }, {
        id: 2,
        position: {lat: 41.39311, lng: 2.20428},
        isClicked: true,
        icon: {url: '/statics/images/icons/point2.png'}
      }]
    }
  }
}
</script>

<style>


.listing-img-link__icon-info__img{
  border-bottom-color:rgb(53,69,89);
  border-bottom-style:none;
  border-bottom-width:0px;
  border-image-outset:0px;
  border-image-repeat:stretch;
  border-image-slice:100%;
  border-image-source:none;
  border-image-width:1;
  border-left-color:rgb(53,69,89);
  border-left-style:none;
  border-left-width:0px;
  border-right-color:rgb(53,69,89);
  border-right-style:none;
  border-right-width:0px;
  border-top-color:rgb(53,69,89);
  border-top-style:none;
  border-top-width:0px;
  box-sizing:border-box;
  color:rgb(53,69,89);
  cursor:default;
  display:block;
  filter:grayscale(1);
  font-family:Lato,"Helvetica Neue",Helvetica,Arial,sans-serif;
  font-size:14.2222px;
  font-style:normal;
  font-weight:normal;
  height:16px;
  line-height:21.3334px;
  max-width:16px;
  text-align:left;
  text-size-adjust:100%;
  vertical-align:middle;
  width:16px;
  -webkit-font-smoothing:antialiased;
}

.listing-img-link__icon-info{
  align-items:center;
  box-sizing:border-box;
  color:rgb(53,69,89);
  cursor:default;
  display:flex;
  font-family:Lato,"Helvetica Neue",Helvetica,Arial,sans-serif;
  font-size:14.2222px;
  font-style:normal;
  font-weight:normal;
  height:21px;
  line-height:21.3334px;
  text-align:left;
  text-size-adjust:100%;
  width:92px;
  -webkit-font-smoothing:antialiased;
}

.listing-img-link__meta{
  box-sizing:border-box;
  color:rgb(53,69,89);
  cursor:default;
  display:flex;
  font-family:Lato,"Helvetica Neue",Helvetica,Arial,sans-serif;
  font-size:14.2222px;
  font-style:normal;
  font-weight:normal;
  height:21px;
  justify-content:space-between;
  line-height:21.3334px;
  margin-top:7.89232px;
  text-align:left;
  text-size-adjust:100%;
  width:350px;
  -webkit-font-smoothing:antialiased;
}

.search-info-window{
  box-sizing:border-box;
  color:rgb(53,69,89);
  cursor:default;
  display:block;
  font-family:Lato,"Helvetica Neue",Helvetica,Arial,sans-serif;
  font-size:16px;
  font-style:normal;
  font-weight:normal;
  height:268.891px;
  line-height:24px;
  text-align:left;
  text-size-adjust:100%;
  width:350px;
  -webkit-font-smoothing:antialiased;
}


.text-size-normal{
  box-sizing:border-box;
  color:rgb(53,69,89);
  cursor:pointer;
  display:block;
  font-family:Lato,"Helvetica Neue",Helvetica,Arial,sans-serif;
  font-size:16px;
  font-style:normal;
  font-weight:normal;
  height:17px;
  line-height:17.6px;
  margin-bottom:18.688px;
  margin-left:0px;
  margin-right:0px;
  margin-top:23.36px;
  text-align:left;
  text-size-adjust:100%;
  width:321.562px;
  -webkit-font-smoothing:antialiased;
  -webkit-margin-after:18.688px;
  -webkit-margin-before:23.36px;
  -webkit-margin-end:0px;
  -webkit-margin-start:0px;
  -webkit-tap-highlight-color:rgba(0,0,0,0);
}

.text-size-small{
  font-size: .88889rem;
}


.listing-img-link{
  background-color:rgb(242,242,242);
  background-position-x:50%;
  background-position-y:50%;
  background-size:cover;
  border-bottom-left-radius:3px;
  border-bottom-right-radius:3px;
  border-top-left-radius:3px;
  border-top-right-radius:3px;
  box-sizing:border-box;
  color:rgb(112,182,132);
  cursor:pointer;
  display:block;
  font-family:Lato,"Helvetica Neue",Helvetica,Arial,sans-serif;
  font-size:16px;
  font-style:normal;
  font-weight:normal;
  height:240px;
  line-height:24px;
  min-height:240px;
  opacity:1;
  position:relative;
  text-align:left;
  text-size-adjust:100%;
  width:350px;
  -webkit-font-smoothing:antialiased;
}

.listing-img-link__text-wrap{
  background-attachment:scroll;
  background-clip:border-box;
  background-color:rgba(255,255,255,0.901961);
  background-image:none;
  background-origin:padding-box;
  background-position-x:0%;
  background-position-y:0%;
  background-repeat-x:;
  background-repeat-y:;
  background-size:auto;
  border-top-color:rgb(255,255,255);
  border-top-style:solid;
  border-top-width:5px;
  bottom:0px;
  box-sizing:border-box;
  color:rgb(53,69,89);
  cursor:pointer;
  display:block;
  font-family:Lato,"Helvetica Neue",Helvetica,Arial,sans-serif;
  font-size:14.2222px;
  font-style:normal;
  font-weight:normal;
  height:62px;
  left:0px;
  line-height:21.3334px;
  padding-bottom:7.0154px;
  padding-left:14.2222px;
  padding-right:14.2222px;
  padding-top:7.0154px;
  position:absolute;
  text-align:left;
  text-size-adjust:100%;
  width:350px;
  -webkit-font-smoothing:antialiased;
}

.listing-img-link__price{
  padding-top:.38974em;
  padding-bottom:.38974em;
  padding-left:1em;
  padding-right:1em;
  top:1rem;
  color:#2b3949;
  right:0;
  background:rgba(255,255,255,0.9);
  position:absolute;
  text-transform:uppercase;
}

.listing-img-link__name{
  box-sizing:border-box;
  color:rgb(43,57,73);
  cursor:pointer;
  display:block;
  font-family:Quicksand,"Helvetica Neue",Helvetica,Arial,sans-serif;
  font-size:16px;
  font-style:normal;
  font-weight:bold;
  height:22px;
  letter-spacing:-0.48px;
  line-height:22.7813px;
  margin-bottom:0px;
  margin-left:0px;
  margin-right:0px;
  margin-top:0px;
  overflow-x:hidden;
  overflow-y:hidden;
  text-align:left;
  text-overflow:ellipsis;
  text-size-adjust:100%;
  white-space:nowrap;
  width:321.562px;
  -webkit-font-smoothing:antialiased;
  -webkit-margin-after:0px;
  -webkit-margin-before:0px;
  -webkit-margin-end:0px;
  -webkit-margin-start:0px;
}


</style>
