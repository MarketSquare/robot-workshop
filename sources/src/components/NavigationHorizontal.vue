<template>
<section>
<b-nav  v-b-scrollspy:scroller.50 tag="nav" toggleable="lg" id="navigation" class="d-none d-md-block topbar" style="height: unset; padding-bottom: 6px">
    <b-nav-item v-for="item in pages" v-if="item.hide_from_nav != true && item.title !== ''" v-bind:key="item.title" v-scroll-to="'#'+item.title.toLowerCase()" :href="'#'+item.title.toLowerCase()" @click="click(item.title)">{{item.title.replace(/-and-/g,' & ').replace('-', ' ')}}</b-nav-item>
  <ShareNetwork
          v-for="network in networks"
          :network="network.network"
          :key="network.network"
          :style="{backgroundColor: network.color}"
          :url="sharing.url"
          :title="sharing.title"
          :description="sharing.description"
          :quote="sharing.quote"
          :hashtags="sharing.hashtags"
          :twitterUser="sharing.twitterUser"
        >
          <b-nav-item><i :class="network.icon"></i></b-nav-item>
    </ShareNetwork>
</b-nav>


 <b-navbar  toggleable="lg" fixed="top" type="dark" id="navigation-collapsed" class="d-md-none">

  <b-navbar-brand class="p-0 m-0 d-block d-md-none" href="#">
    <b-img :src="require('@/assets/img/ROBOTFW_Mark_White_LOW_cropped.png')" class="" style="height:33px;"  alt="Robot Frameworkg logo"/>
  </b-navbar-brand>
  <div class="mobile-header"><div style="float: left">WWWW></div>
    <transition name="header-slide" mode="out-in">
      <div :key="currentPageMutable" class="color" style="float: left">
        {{currentPageMutable}}
      </div>
    </transition>
  </div>
  <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
  <b-collapse is-nav id="nav_collapse" transition-duration="10">
    <b-navbar-nav class="align-middle">
      <b-nav-item v-for="(item, key) in pages" v-if="item.hide_from_nav != true" :key="key" :href="'#'+item.title.toLowerCase()" v-scroll-to="'#'+item.title.toLowerCase()" @click="click(item.title)">{{item.title.replace(/-and-/g,' & ').replace('-', ' ')}}</b-nav-item>
    </b-navbar-nav>
  </b-collapse>
</b-navbar>
</section>
</template>

<script>
export default {
  props: ["pages", "currentPage"],
  data () {
  return {
      currentPageMutable: this.currentPage || "02122020",
      sharing: {
            url: 'https://robot-work.shop/',
            title: 'Going to World Wide Workshop Wednesday 2020!',
            description: 'On 2nd of December 2020, Robot Framework - See you in the World Wide Web!',
            quote: 'The hot reload is so fast it\'s near instant. - Evan You',
            hashtags: 'robotframework',
            twitterUser: 'robotframework'
          },
          networks: [
            { network: 'facebook', icon: 'fab fah fa-lg fa-facebook-f', color: '#1877f2' },
            { network: 'linkedin', icon: 'fab fah fa-lg fa-linkedin', color: '#007bb5' },
            { network: 'reddit', icon: 'fab fah fa-lg fa-reddit-alien', color: '#ff4500' },
            { network: 'twitter', icon: 'fab fah fa-lg fa-twitter', color: '#1da1f2' },
          ]
    }
  },
  methods: {
    onActivate(target) {
      this.currentPageMutable = target.substring(1).toUpperCase().replace(/-AND-/g,'&').replace('-', ' ')
      ga('send', 'event', 'scrollTo', target)
    },
    click(a) {
      ga('send', 'event', 'navigationClick', a)
    }
  },
  created() {
    this.$root.$on("bv::scrollspy::activate", this.onActivate);
  }
};
</script>
