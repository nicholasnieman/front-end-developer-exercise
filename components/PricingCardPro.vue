<template>
	<b-col cols="12" md="8" lg="4">
		<b-card class="mx-0 mx-md-5 mx-lg-0 my-5 my-lg-0" :title="'$' + cost + '/mo'" header-tag="header">
			<template #header>
				<h4>{{name}}</h4>
			</template>
			<b-card-text class="mb-0">{{users}}</b-card-text>
			<b-card-text class="mb-0">{{storage}}</b-card-text>
			<b-card-text class="mb-0">{{support}}</b-card-text>
			<b-card-text>{{access}}</b-card-text>
			<b-button v-b-modal.selected-plan-modal variant="primary" v-on:click="selectPlan">{{cta}}</b-button>
		</b-card>
	</b-col>
</template>

<script>
export default {
  name: 'PricingCardPro',
  props: {
    name: String,
    cost: Number,
    users: String,
    storage: String,
    support: String,
    access: String,
    cta: String
  },
  methods: {
    selectPlan() {
      this.$store.commit('chosenPlanPro')
    }
  },
};
</script> 