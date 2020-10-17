<template>
<div
    class="container">
  <div class="col-lg-12 mt-5" style="display: flex; flex-wrap: wrap">
    <div v-for="(user, index) in data" :key="index" class="col-lg-4 col-md-5 col-sm-8 col-xs-12 mt-2 mx-lg-2 mx-md-3 mx-sm-3 p-xs-1 pt-5">
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
