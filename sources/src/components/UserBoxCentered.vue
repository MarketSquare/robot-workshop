<template>
  <div class="row col-lg-8 col-md-10 mx-auto">
  <div v-for="(user, index) in data.users" :key="index" class="col-lg-3 col-md-4 col-sm-3 col-xs-3 pr-lg-1 pl-lg-3 pl-md-5 pl-sm-3 p-xs-1">
        <div class="logo-center text-center p-3" style="height:100px;background-color:#fff;">
        <a :href="user.href"><img class="img-fluid pb-2 user-image" :src="user.img"/></a>
        </div>
        <div class="card-body">
        <p v-html="user.text"></p>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["data"]
};
</script>
