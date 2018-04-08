<template>
<div class="card">
    <div class="row">
        <div class="nine columns">
            <h5 style="margin-bottom: 0;" v-html="$options.filters.highlight(config.title, search)"></h5>
            <p style="margin-bottom: 0;" v-html="$options.filters.highlight(config.type, search)"></p>
            <p style="margin-bottom: 0;" v-html="$options.filters.highlight(config.guid, search)"></p>
        </div>
        <div style="text-align: right;" class="three columns">
            <button v-if="isExpanded" class="button-primary" v-on:click="isExpanded = false">Close</button>
        </div>
    </div>
    <pre ref="configViewer"
        v-on:click="isExpanded = true" 
        v-bind:class="{expanded: isExpanded}"><code v-html="$options.filters.highlight(config.data, search)"></code></pre>
</div>
</template>

<script>
export default {
  props: ['config', 'search'],
  filters: {
      highlight: function(text, searchKey) {
        return text.split(searchKey).join('<mark>' + searchKey + '</mark>');
      }
  },
  data() {
      return {
          isExpanded: false
      }
  },
  updated() {
    let container = this.$refs.configViewer;
    let mark = this.$refs.configViewer.querySelector("mark");
    if (container && mark) {
        container.scrollTop = mark.offsetTop - container.offsetTop;
    }
  }
};
</script>

<style></style>
