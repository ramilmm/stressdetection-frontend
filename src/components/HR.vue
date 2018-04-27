<template>
  <div class="HR">
  
  </div>
</template>

<script>


export default {
  name: 'HR',
  data () {
    return {
      loading: false,
      posts: [],
      allPosts: [],
      clicked: true,
      filterChanged: true,
      publics_id: {
        id:'73899416'
      },
      perPage: 120,
      offset: 0,
      filterMyPublic: false,
      mypublic_id: '',
      currentPage: 1,
      last_active: ''
    }
  },
  methods: {
    fetchPosts(page) {
      
    },
  },
  created() {
    
  },
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
