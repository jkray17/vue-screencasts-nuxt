<template>
  <v-btn :color="color" :outlined="outlined" @click="click" :disabled="loading || disabled">
    <slot />
    <span v-if="loading">
      &nbsp;
      <v-progress-circular indeterminate  size="20" />
    </span>
  </v-btn>
</template>

<script>
  export default {
    data(){
      return {
        loading: false
      }
    },
    methods: {
      async click(){
        this.loading = true;
        
        await this.clickAction();

        this.loading = false;
      }
    },
    props: {
      color: {
        type: String,
        default: 'Purple'
      },
      clickAction: {
        type: Function,
        required: true
      },
      outlined: {
        type: Boolean,
        default: false
      },
      disabled: {
        type: Boolean,
        default: false
      }
    }
    
  }
</script>

<style lang="scss" scoped>

</style>