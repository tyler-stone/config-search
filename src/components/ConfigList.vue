<template>
<div class="container" style="margin-top: 25px;">
    <h5>{{ configs.length }} Config(s)</h5>
    <config-item v-for="config in configs" :key="config.guid" 
        v-bind:config="config"
        v-bind:search="search"></config-item>
</div>
</template>

<script>
import ConfigItem from './ConfigItem';

export default {
  components: {
      ConfigItem
  },
  props: ['configs', 'search'],
};
</script>

<style></style>
