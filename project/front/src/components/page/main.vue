<template>
  <div class="main-container">
    <swiper class="swiper" :options="swiperOption">
      <swiper-slide><img src="../../assets/img/1.jpg" /></swiper-slide>
      <swiper-slide><img src="../../assets/img/2.jpg" /></swiper-slide>
      <swiper-slide><img src="../../assets/img/3.jpg" /></swiper-slide>
      <swiper-slide><img src="../../assets/img/4.jpg" /></swiper-slide>
      <swiper-slide><img src="../../assets/img/5.jpg" /></swiper-slide>
      <swiper-slide><img src="../../assets/img/6.jpg" /></swiper-slide>
      <swiper-slide><img src="../../assets/img/7.jpg" /></swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
      <div class="swiper-button-prev" slot="button-prev"></div>
      <div class="swiper-button-next" slot="button-next"></div>
    </swiper>
    <div>
      <div>
        <p style="text-align: center; font-size:45px; margin-top:30px;">Best Item</p>
      </div>
    </div>
        <div style="display: inline;" v-for="b in bestlist" v-bind:key="b.p_idx">
          <div class=img_box>
            <router-link :to="{ name:'List_ViewPage',params:{ p_idx: b.p_idx }}" style="text-decoration: none">
            <img
              class="img"
              :src="b.path"
            />
            <p>{{b.p_name}} <br/>
              {{b.p_price}}</p>
          </router-link>
          </div>
        </div>
        <div>
      <div>
        <p style="text-align: center; font-size:45px;"> O U T E R </p>
      </div>
    </div>
        <div style="display: inline;" v-for="p in list" v-bind:key="p.p_idx">
          <div class=img_box v-if="p.p_category=='OUTER'">
          <router-link :to="{ name:'List_OuterPage',params:{ p_idx: p.p_idx }}" style="text-decoration: none">
            <img
              class="img"
              :src="p.path"
            />
            <p>{{p.p_name}} <br/>
              {{p.p_price}}</p>
          </router-link>
          </div>
        </div>
        <div>
      <div>
        <p style="text-align: center; font-size:45px;"> T O P </p>
      </div>
    </div>
        <div style="display: inline;" v-for="p in list" v-bind:key="p.p_idx">
          <div class=img_box v-if="p.p_category=='TOP'">
          <router-link :to="{ name:'List_TopPage',params:{ p_idx: p.p_idx }}" style="text-decoration: none">
            <img
              class="img"
              :src="p.path"
            />
            <p>{{p.p_name}} <br/>
              {{p.p_price}}</p>
          </router-link>
          </div>
        </div>
        <div>
      <div>
        <p style="text-align: center; font-size:45px;"> S H I R T S </p>
      </div>
    </div>
        <div style="display: inline;" v-for="p in list" v-bind:key="p.p_idx">
          <div class=img_box v-if="p.p_category=='SHIRTS'">
          <router-link :to="{ name:'List_ShirtsPage',params:{ p_idx: p.p_idx }}" style="text-decoration: none">
            <img
              class="img"
              :src="p.path"
            />
            <p>{{p.p_name}} <br/>
              {{p.p_price}}</p>
          </router-link>
          </div>
        </div>
        <div>
      <div>
        <p style="text-align: center; font-size:45px;"> P A N T S </p>
      </div>
    </div>
        <div style="display: inline;" v-for="p in list" v-bind:key="p.p_idx">
          <div class=img_box v-if="p.p_category=='PANTS'">
          <router-link :to="{ name:'List_PantsPage',params:{ p_idx: p.p_idx }}" style="text-decoration: none">
            <img
              class="img"
              :src="p.path"
            />
            <p>{{p.p_name}} <br/>
              {{p.p_price}}</p>
          </router-link>
          </div>
        </div>
        <div>
      <div>
        <p style="text-align: center; font-size:45px;"> S H O E S </p>
      </div>
    </div>
        <div style="display: inline;" v-for="p in list" v-bind:key="p.p_idx">
          <div class=img_box v-if="p.p_category=='SHOES'">
          <router-link :to="{ name:'List_ShoesPage',params:{ p_idx: p.p_idx }}" style="text-decoration: none">
            <img
              class="img"
              :src="p.path"
            />
            <p>{{p.p_name}} <br/>
              {{p.p_price}}</p>
          </router-link>
          </div>
        </div>
        <div>
      <div>
        <p style="text-align: center; font-size:45px;"> B A G </p>
      </div>
    </div>
        <div style="display: inline;" v-for="p in list" v-bind:key="p.p_idx">
          <div class=img_box v-if="p.p_category=='BAG'">
          <router-link :to="{ name:'List_BagPage',params:{ p_idx: p.p_idx }}" style="text-decoration: none">
            <img
              class="img"
              :src="p.path"
            />
            <p>{{p.p_name}} <br/>
              {{p.p_price}}</p>
          </router-link>
          </div>
        </div>
  </div>
</template>

<script>
export default {
  name: "Main",
  props: {
    msg: String
  },
  data() {
    return {
    list: [],
      swiperOption: {
        slidesPerView: 2,
        centeredSlides: false,
        slideShadows : true,
        autoplay: {
          delay: 2500,
          disableOnInteraction: false
        },
        pagination: {
          el: ".swiper-pagination",
          clickable: true
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev"
        }
      }
    };
  },
  created () {
    const self = this;
    self.$axios.get('/products')
      .then(function(res) {
        if (res.data.result) {
          self.bestlist = res.data.bestlist;
          self.list = res.data.list;
          var i=0;
          for(i=0;i<self.list.length;i++){
            var imgarr = self.list[i].p_img.split('/');
            self.list[i].path = 'http://localhost:8888/products/img/' + imgarr[0];
          }
          for(i=0;i<self.bestlist.length;i++){
            var imgarr1 = self.bestlist[i].p_img.split('/');
            self.bestlist[i].path = 'http://localhost:8888/products/img/' + imgarr1[0];
          }
        } else {
          alert('fail');
        }
      });

   

  }

};
</script>




<style>
router-link{
  text-decoration: none;
}
p{
  font-size: 20px;
  font-weight: bold;
  color: #000;
  text-align: center;
  width: 100%;
  height: 40px;
}
html,
body {
  position: relative;
  height: 100%;
}

body {
  background: #eee;
  font-family: Helvetica Neue, Helvetica, Arial, sans-serif;
  font-size: 14px;
  color: #000;
  margin: 0;
  padding: 0;
  text-decoration: none!important;
}

.swiper-container {
  width: 100%;
  height: 100%;
}

.swiper-slide {
  text-align: center;
  font-size: 18px;
  background: #fff;

  /* Center slide text vertically */
  display: -webkit-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  -webkit-justify-content: center;
  justify-content: center;
  -webkit-box-align: center;
  -ms-flex-align: center;
  -webkit-align-items: center;
  align-items: center;
}

.swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.main-container {
  display: block;
  background: white;
  width: 100%;
  height: 100%;
  box-sizing: border-box;
}
.img_box{
  display: inline-block;
  width: 22%;
  height: 600px!important;
  margin: 20px 20px;
  box-sizing: border-box;
  text-align: center;
}

.img {
  display: inline-block;
  width: 100%;
  height: 500px!important;
  box-sizing: border-bod;
  margin: 20px 20px;
}
</style>
