<template>
  <div>
    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <span class="input-group-text">{{ label }}</span>
      </div>
      <select class="form-control from" @change="choiceCurrency($event, label)">
        <option value="">Select One …</option>
        <option v-for='cr in currencies' :value="cr" :key="cr">{{ cr }} </option>
      </select>
    </div>
  </div>
</template>
<script>
import {currencies} from '../assets/currencies.json'
export default {
  created() {
    this.currencies = currencies
  },
  mounted() {
    console.log('mounted', this)
  },
  updated() {
    console.log('updated', this)
  },
  unmounted() {
    console.log('unmounted', this)
  },
  emits: ['choice-currency'],
  props: {
    label: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      currencies:null
    }
  },
  methods: {
    choiceCurrency(evt, origin) {
      this.$emit(`choice-currency`,{ origin: origin, value: evt.target.value} )
    }
  },
}
</script>