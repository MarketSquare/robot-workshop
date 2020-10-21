<template>
  <div
    :class="
      header === '' && (type === 'workshop' || type === 'workshop-last')
        ? 'mb-5 pb-4'
        : 'mb-5'
    "
    :style="
      header === '' &&
      /*author !== 'Asko Soukka' &&
      author !== 'Pekka Klärck' &&*/
      type === 'workshop'
        ? 'border-bottom: dashed 2px'
        : ''
    "
  >
    <div v-if="margin" class="mt-5" />
    <div v-if="header !== ''">
      <h2 class="no-arrow mt-5">{{ header }}</h2>
    </div>
    <div v-else class="ml-0">
      <h3 class="white mb-0 ml-4" v-if="author !== ''">
        {{ author }}
      </h3>
      <div v-else class="mt-4" />
      <a
        class="mb-0 ml-4 link-title"
        :id="title.replace(/[^a-z0-9]/gmi, '').replace(/\s+/g, '').toLowerCase()"
        :name="title.replace(/[^a-z0-9]/gmi, '').replace(/\s+/g, '').toLowerCase()"
        :class="{ 'clickable-title': descriptionExpanded !== '' || url !== '' }"
        @click="
          descriptionExpanded !== '' || url !== ''
            ? (expanded = !expanded)
            : false
        "
      >
        {{ title }}
      </a>
    </div>
    <transition name="toggle-content" mode="out-in">
      <div v-if="expanded">
        <div class="row mt-0">
          <div v-if="url !== ''" class="col-lg-12">
            <b-embed type="iframe" :src="url" allowfullscreen />
          </div>
          <div v-else>
            <div
              class="col-lg-12 word-break ml-4 pr-4 mt-2 workshop-description"
            >
              <p>
              Start: {{ utc_time(start).format("LT") }} (UTC) <span class="local-time">/ {{ local_time(start).format("LT") }} ({{local_tz()}})</span><br>
              End: {{ utc_time(end).format("LT") }} (UTC) <span class="local-time">/ {{ local_time(end).format("LT") }} ({{local_tz()}})</span></p>
              <a v-if="pretixid !== ''" :href="'https://pretix.eu/robocon/WWWW2020/' + pretixid" target="blank" ><h3>&gt; Tickets</h3></a>

              <p v-html="description"></p>
              <p v-html="descriptionExpanded"></p>
              <div
                class="col-lg-12 mt-5"
                style="display: flex; flex-wrap: wrap"
              >
                <div
                  v-if="imgUrl !== ''"
                  class="col-lg-4 col-md-6 col-sm-6 mt-auto"
                >
                  <div v-for="image in imgUrl" :key="image">
                    <img
                      class="mb-3"
                      style="border-radius: 50%; width: 100px"
                      :src="require(`@/assets/img/users/${image}`)"
                    />
                    <h3 v-if="author !== ''">
                      {{ author }}
                    </h3>
                  </div>
                </div>
                <div
                  v-if="sponsorUrl !== ''"
                  class="col-lg-6 col-md-6 col-sm-6 mt-auto"
                >
                  <div>
                    <a :href="sponsorUrl" target="blank"
                      ><img
                        class="img-fluid mb-3 user-image"
                        style="max-height: 100px"
                        :src="sponsorLogo"
                      />
                    </a>
                    <h3>sponsored by:</h3>
                  </div>
                </div>
              </div>
              <template v-if="bio">
                <p class="mt-5" v-html="bio"></p>
              </template>
            </div>
          </div>
        </div>
      </div>
      <p
        v-else-if="header === ''"
        class="workshop-description ml-4 mt-2 cursor--pointer"
        @click="
          descriptionExpanded !== '' || url !== ''
            ? (expanded = !expanded)
            : false
        "
      >
      Start: <span class="local-time">{{ local_time(start).format("LT") }}</span> / End: <span class="local-time">{{ local_time(end).format("LT") }} ({{local_tz()}})</span><br>
      {{description}}</p> 
    </transition>
  </div>
</template>

<script>
import moment from "moment-timezone";

export default {
  name: "TalkerItem",
  props: {
    title: {
      type: String,
      default: "",
    },
    pretixid: {
      type: String,
      default: "",
    },
    description: {
      type: String,
      default: "",
    },
    imgUrl: {
      type: Array,
      default: () => [],
    },
    descriptionExpanded: {
      type: String,
      default: "",
    },
    bio: {
      type: String,
      default: "",
    },
    author: {
      type: String,
      default: "",
    },
    url: {
      type: String,
      default: "",
    },
    header: {
      type: String,
      default: "",
    },
    margin: {
      type: Boolean,
      default: false,
    },
    type: {
      type: String,
      default: "",
    },
    sponsorLogo: {
      type: String,
      default: "",
    },
    sponsorUrl: {
      type: String,
      default: "",
    },
    start: {
      type: String,
      default: "",
    },
    end: {
      type: String,
      default: "",
    },
  },
  data: () => ({
    expanded: false,
  }),
  watch: {
    expanded: {
      handler() {
        if (this.expanded)
          history.pushState(
            null,
            null,
            `#${this.title.replace(/[^a-z0-9]/gmi, "").replace(/\s+/g, "").toLowerCase()}`
          );
      },
    },
  },
  mounted() {
    const anchor =
      document.URL.split("#").length > 1 ? document.URL.split("#")[1] : null;
    if (anchor === this.title.replace(/[^a-z0-9]/gmi, "").replace(/\s+/g, "").toLowerCase())
      this.expanded = true;
  },
  methods: {
    moment,
    local_time,
    utc_time,
    local_tz,
  },
};

function utc_time(dataTime) {
  var locale = window.navigator.userLanguage || window.navigator.language;
  moment.locale(locale);
  return moment.tz(dataTime, "Africa/Freetown");
}

function local_time(dataTime) {
  var locale = window.navigator.userLanguage || window.navigator.language;
  moment.locale(locale);
  return moment.tz(dataTime, moment.tz.guess());
}

function local_tz() {
  return moment.tz.guess();
}
</script>
