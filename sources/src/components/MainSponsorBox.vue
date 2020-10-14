<template>
<div
    class="container">
  <div class="col-lg-12 mt-5" style="display: flex; flex-wrap: wrap">
    <div v-for="(user, index) in data" :key="index" class="col-lg-5 col-md-6 col-sm-6 col-12 mt-2 my-lg-5 mx-lg-4 my-sm-0 my-4">
        <div class="text-center p-3" :style="'height:100px'">
        <a :href="user.href" target="blank" style="margin-top: 35px; display: inline-block; transform: translateY(-50%)"><img class="img-fluid pb-2 user-image" style="max-height: 100%" :src="user.img"/></a>
        </div>
        <div class="card-body">
        <p v-html="user.text"></p>
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
