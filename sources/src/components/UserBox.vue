<template>
  <div class="container">
    <div class="col-lg-12 mt-5" style="display: flex; flex-wrap: wrap">
      <div
        v-for="(user, index) in data"
        :key="index"
        class="col-lg-3 col-md-4 col-sm-6 col-xs-12 mt-2 pr-lg-1 pl-lg-3 pl-md-0 pl-sm-3 p-xs-1"
      >
        <div class="text-center p-3" :style="'height:100px'">
          <a
            :href="user.href"
            target="blank"
            style="
              margin-top: 35px;
              display: inline-block;
              transform: translateY(-50%);
            "
            ><img
              class="img-fluid pb-2 user-image"
              style="max-height: 100%"
              :src="user.img"
          /></a>
        </div>
        <div class="card-body">
          <p v-html="user.text"></p>
        </div>
      </div>
      <p style="text-align: start; width: 100%; font-size: 0.85rem">
        Want your logo here?
        <a class="mb-0 ml-4"
          @click="
            descriptionExpanded !== '' || url !== ''
              ? (expanded = !expanded)
              : false
          "
          >More information</a
        >
      </p>
      <transition name="toggle-content" mode="out-in">
        <div v-if="expanded">
          <p style="text-align: start; width: 100%; font-size: 0.85rem">
            Do you want to be a sponsor of the future development of Robot Framework?<br>
            For a sponsorship of 2000€ (excl. VAT) you will get your logo here and you get 40 pre-sales
          vouchers.<br>
            With these voucher codes, you enable the owner of this code to buy a ticket before the public ticket sales starts.<br>
            <br>
            <b>Voucher Sale:</b> October 26st 2020<br>
            <b>Normal Ticket Sale:</b> November 4th 2020<br>
            <br>
            <a href="mailto:mikko@robotframework.org">mikko@robotframework.org</a>
            </p>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  props: ["data"],
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
            `#${this.title.replace(/ /g, "-").toLowerCase()}`
          );
      },
    },
  },
};
</script>
