<template>
<section>
    <div class="container">
        <div class="row-md-5 row-lg-4 order-1 textblock-left no-border dashed-header link-fix">
      <h1 v-if="data.header.length" v-html="data.header"/>
    </div>
      <b-embed v-if="typeof data.src != 'undefined'"
        type="iframe"
        :src="data.src"
        allowfullscreen />

    </div>
</section>
</template>

<script>
export default {
  props: ["data"]
};
</script>
