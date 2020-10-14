<template>
<div
    class="container">
  <div class="col-lg-12 mt-5" style="display: flex; flex-wrap: wrap">
    <div v-for="(user, index) in data" :key="index" class="col-lg-4 col-md-4 col-sm-6 col-xs-12 mt-2 pr-lg-1 pl-lg-3 pl-md-0 pl-sm-3 p-xs-1 pt-5">
      <div class="text-center p-3" :style="'height:0px'">
        <a :href="user.href" target="blank" style="margin-top: 35px; display: inline-block; transform: translateY(-100%)">
            <img class="mb-3" style="border-radius: 50%; width: 100px" :src="user.img"/>
        </a>
      </div>
      <div class="card-body">
        <p style="text-align: center;" v-html="user.text"></p>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  props: ["data"]
};
</script>
