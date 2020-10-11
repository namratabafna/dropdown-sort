<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <br>
    
     <b-dropdown aria-role="list" v-model="param"  @change="onChange($event)">
            <button class="button active" slot="trigger">
                <span>Sort By</span>                
            </button>

            <b-dropdown-item value="id" aria-role="listitem">Id</b-dropdown-item>
            <b-dropdown-item value="text" aria-role="listitem">Text</b-dropdown-item>            
    </b-dropdown>   
    <br>
    <br> 
    <ul>
      <li v-for="{id, text} in sortedActivityList" :key="id">{{ id }}   {{ text }}</li>
    </ul>
    
  </div>
</template>

<script>

export default {
  name: 'App',
  methods: {
      onChange(event) {        
        // sessionStorage.setItem('filter', event);
        this.param = event;
      }
    },
    data() {
      return {
        activityList: [
        { id: 0, text: 'Run'},
        { id: 1, text: 'Jump' },
        { id: 2, text: 'Skip' },
        { id: 3, text: 'Dance'},
        { id: 4, text: 'Swing' },
        { id: 5, text: 'Hop' },
        { id: 6, text: 'Bounce' },
        { id: 7, text: 'Crawl' },
        { id: 8, text: 'Walk'},
        { id: 9, text: 'Spin' },
        { id: 10, text: 'Skate' },
        { id: 11, text: 'Hike' }
      ],

        param: 'id'
      };
    },
    computed: {      
      sortedActivityList: function() {                 
         
          function sortById(a, b) {            
            if (a.id < b.id) return -1;
            if (a.id > b.id) return 1;
            return 0;       
          }

          function sortByText(a, b) {
            if (a.text < b.text) return -1;
            if (a.text > b.text) return 1;  
            return 0;     
          }      
        
        return this.param == 'id' ? [...this.activityList].sort(sortById) : [...this.activityList].sort(sortByText);
     }
    }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
