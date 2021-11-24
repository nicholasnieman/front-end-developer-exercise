<template>
  <b-row class="justify-content-center">
    <b-card-group deck class="w-100 py-5 justify-content-center">
        <pricing-card-free
          v-for="feature in freePlan"
          v-bind:feature="feature"
          v-bind:key="feature.id"
          v-bind:name="feature.name"
          v-bind:cost="feature.cost"
          v-bind:users="feature.features[0]"
          v-bind:storage="feature.features[1]"
          v-bind:support="feature.features[2]"
          v-bind:access="feature.features[3]"
          v-bind:cta="feature.cta"
        ></pricing-card-free>

        <pricing-card-pro
          v-for="feature in proPlan"
          v-bind:feature="feature"
          v-bind:key="feature.id"
          v-bind:name="feature.name"
          v-bind:cost="feature.cost"
          v-bind:users="feature.features[0]"
          v-bind:storage="feature.features[1]"
          v-bind:support="feature.features[2]"
          v-bind:access="feature.features[3]"
          v-bind:cta="feature.cta"
        ></pricing-card-pro>

        <pricing-card-enterprise
          v-for="feature in enterprisePlan"
          v-bind:feature="feature"
          v-bind:key="feature.id"
          v-bind:name="feature.name"
          v-bind:cost="feature.cost"
          v-bind:users="feature.features[0]"
          v-bind:storage="feature.features[1]"
          v-bind:support="feature.features[2]"
          v-bind:access="feature.features[3]"
          v-bind:cta="feature.cta"
        ></pricing-card-enterprise>
    </b-card-group> 

    <b-modal id="selected-plan-modal" title="New Plan Selected">
      <p class="my-6">You have chosen: <b>{{chosenPlan}}</b></p>
    </b-modal>
  </b-row>
</template>

<script>
import PricingCardFree from './PricingCardFree.vue';
import PricingCardPro from './PricingCardPro.vue';
import PricingCardEnterprise from './PricingCardEnterprise.vue';
export default {
  components: {PricingCardFree, PricingCardPro, PricingCardEnterprise},
  name: 'PricingCard',
  computed: {
    freePlan () {
      return this.$store.state.pricingOptions.filter(option => option.name == "Free");
    },
    proPlan () {
      return this.$store.state.pricingOptions.filter(option => option.name == "Pro");
    },
    enterprisePlan () {
      return this.$store.state.pricingOptions.filter(option => option.name == "Enterprise");
    },
    chosenPlan () {
      return this.$store.state.chosenPlan
    }
  },
};
</script>

<style lang="scss" scoped>
#pricing-card-container {
  width: 100%;
  padding: 3rem 0;
}
</style>
