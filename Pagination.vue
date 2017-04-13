<template>
  <div v-if="visible" class="pagination">
    <a v-if="prev" href="#" @click="getPage(prev)">&laquo;</a>
    <a v-for="page in pages" :class="{'active': page == pagination.current_page}" href="#" @click="getPage(page)">{{ page }}</a>
    <a v-if="next" href="#" @click="getPage(next)">&raquo;</a>
  </div>
</template>

<script>
  export default {
    props: {
      pagination: {},
      callback:{
        type: Function
      },
      offset: {
        type: Number,
        default: 5
      }
    },
    computed: {
      visible: function(){
        if(this.pagination.last_page!=1)
          return true;
        return false;
      },
      prev: function(){
        if(this.pagination.current_page>1)
          return this.pagination.current_page-1;
        return false;
      },
      next: function(){
        if(this.pagination.current_page<this.pagination.last_page)
          return this.pagination.current_page+1;
        return false;
      },
      pages: function () {
        var pages = [];
        var from = this.pagination.current_page-this.offset;
        var to = this.pagination.current_page+this.offset;

        if(from < 1)
          from = 1;

        if(to >= this.pagination.last_page)
          to = this.pagination.last_page;

        for(var i=from; i<=to; i++){
          pages.push(i);
        }

        return pages;
      }
    },
    methods: {
      getPage: function(page){
        this.pagination.current_page=page;
        this.callback();
      }
    },
    mounted() {

    }
  }
</script>
