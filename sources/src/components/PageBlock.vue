<template>
  <section :id="page.title.toLowerCase()">
    <examples v-if="Object.keys(page.data).length === 0 && page.data.constructor === Object"/>
    <feature-box v-if="page.feature_box == true" :data="page.data.text"/>
    <text-block v-if="page.text_block == true" :data="page.data.text"/>
    <text-block-centered v-if="page.text_block_centered == true" :data="page.data.text"/>
    <tab-box v-if="page.tab_box == true" :data="page.data.tabs"/>
    <tab-box-centered v-if="page.tab_box_centered == true" :data="page.data.tabs"/>
    <user-contact v-if="page.user_contact == true" :data="page.data.users"/>
    <main-sponsor-box v-if="page.main_sponsor_box == true" :data="page.data.users"/>
    <user-box v-if="page.user_box == true" :data="page.data.users"/>
    <user-box-centered v-if="page.user_box_centered == true" :data="page.data"/>

</section>
</template>

<script>
import FeatureBox from "@/Components/FeatureBox.vue";
import MainSponsorBox from "@/Components/MainSponsorBox.vue"
import TabBox from "@/Components/TabBox.vue";
import TabBoxCentered from "@/Components/TabBoxCentered.vue";
import TextBlock from "@/Components/TextBlock.vue";
import TextBlockCentered from "@/Components/TextBlockCentered.vue";
import UserContact from "@/Components/UserContact.vue";
import UserBox from "@/Components/UserBox.vue";
import UserBoxCentered from "@/Components/UserBoxCentered.vue";

import Examples from "@/components/pages/Examples";

export default {
  components: {
    FeatureBox,
    MainSponsorBox,
    TextBlock,
    TextBlockCentered,
    TabBox,
    TabBoxCentered,
    UserContact,
    UserBox,
    UserBoxCentered,
    Examples
  },
  props: ["page"]
};
</script>
