<template>
  <div class="mw7 center pv4 min-h-100 bg-white">
    <div class="ph4">
      <h1 class="mt0 mb3 f2 lh-title">Vue.js Money Button Component Demo</h1>

      <p class="mv3 f5 lh-copy">An unofficial Vue.js component for the Money Button. This library allows Money Button to be used in Vue.js projects and benefit from reactive properties.</p>

      <h3 class="mt4 mb2 f4 lh-title">Demo</h3>

      <form class="dt mb4">
        <div class="dt-row">
          <label class="dtc pv1 pr3 f6 lh-copy mid-gray">Amount: </label>
          <div class="dtc pv1">
            <input type="text"
              class="input-reset w-100 pv1 ph2 f6 lh-copy fw6 silver bg-light-gray ba bw2 b--light-gray br1"
              :value="amount"
              @change="amount = $event.target.value"
            />
          </div>
        </div>
        <div class="dt-row">
          <label class="dtc pv1 pr3 f6 lh-copy mid-gray">Label: </label>
          <div class="dtc pv1">
            <input type="text"
              class="input-reset w-100 pv1 ph2 f6 lh-copy fw6 silver bg-light-gray ba bw2 b--light-gray br1"
              :value="label"
              @change="label = $event.target.value"
            />
          </div>
        </div>
      </form>

      <MoneyButton
        to="74"
        :amount="amount"
        :label="tipLabel"
        type="tip"

        @payment="onPayment"
        @error="onError"
      />

      <p class="mv3 f6 lh-copy mid-gray"><em>Disclaimer: This is a real Money Button. Sliding it will send me money.</em></p>
    </div>

    <h3 class="mt4 mb2 ph4 f4 lh-title">Installation</h3>

    <pre class="ph4 pv3 code f6 lh-copy bg-dark-gray washed-yellow ws-normal"><code>
      npm install vue-money-button --save
    </code></pre>

    <h3 class="mt4 mb2 ph4 f4 lh-title">Usage</h3>

    <pre class="ph4 pv3 code f6 lh-copy bg-dark-gray washed-yellow"><code>{{ usageExample }}</code></pre>

    <div class="ph4">
      <h3 class="mt4 mb2 f4 lh-title">Find out more</h3>

      <ul class="pl3 f5 lh-copy">
        <li><a href="https://github.com/libitx/vue-money-button" class="link blue hover-red">Github page</a></li>
        <li><a href="https://www.moneybutton.com/" class="link blue hover-red">Money Button website</a></li>
        <li><a href="https://docs.moneybutton.com/" class="link blue hover-red">Money Button docs</a></li>
      </ul>

      <h3 class="mt4 mb2 f4 lh-title">Find out more</h3>

      <p class="mv0 f5 lh-copy">vue-money-button is open source and released under the <a href="https://github.com/libitx/vue-money-button/blob/master/license.md" class="link blue hover-red">MIT License</a>.</p>
      <p class="mv0 f5 lh-copy">Copyright &copy; 2018 libitx</p>
    </div>
  </div>
</template>

<script>
import MoneyButton from 'components/MoneyButton.vue'
import usage from 'demo/usage.txt'

export default {
  data() {
    return {
      amount: '0.50',
      label: 'Tip Libby'
    }
  },

  computed: {
    tipLabel() {
      return `$${ this.amount } ${ this.label }`;
    },
    usageExample() {
      return usage;
    }
  },

  methods: {
    onPayment(payment) {
      console.log('onPayment event:', payment)
    },
    onError(error) {
      console.log('onError event:', error)
    }
  },

  components: {
    MoneyButton
  }
}
</script>

<style scoped>
input:focus {
  color: #E7040F;
  border-color: #96CCFF;
  outline: none;
}
</style>