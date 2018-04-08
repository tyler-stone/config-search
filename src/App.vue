<template>
  <div id="app">
    <search-bar v-model="search"></search-bar>
    <config-list v-bind:configs="filteredConfigs" v-bind:search="search"></config-list>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar';
import ConfigList from './components/ConfigList';

export default {
  name: 'App',
  components: {
    ConfigList,
    SearchBar
  },
  data() {
    return {
      search: '',
      configs: [{
        title: 'test1',
        type: 'Treatment',
        guid: '001-0001-0001',
        data: '{\n\n\n\n\n\n\n\n\n test this is a test \n\n\n\n\n\n\n\n\n\n\n\n\n\n}',
      }, {
        title: 'test2',
        type: 'Treatment',
        guid: '002-0002-0002',
        data: '{ this is also a trial run }',
      }, {
        title: 'test3',
        type: 'Treatment',
        guid: '003-0003-0003',
        data: '{ \n\n\nof course it is expected }',
      }, {
        title: 'test4',
        type: 'Treatment',
        guid: '004-0004-0004',
        data: '{ woop }',
      },
      ],
    };
  },
  computed: {
    filteredConfigs() {
      return this.configs.filter(config => {
        return (config.data.toLowerCase().indexOf(this.search.toLowerCase()) > -1 
          || config.title.toLowerCase().indexOf(this.search.toLowerCase()) > -1
          || config.guid.toLowerCase().indexOf(this.search.toLowerCase()) > -1
          || config.type.toLowerCase().indexOf(this.search.toLowerCase()) > -1);
      });
    }
  }
};
</script>

<style>
</style>
