<template>
  <div class="features-boxed">
    <div v-if="!loading" class="container">
      <div class="intro">
        <h2 class="text-center">Category</h2>
      </div>
      <div class="row justify-content-center features">
        <CategoryItem
          v-for="cat in categories"
          :key="cat.id"
          :categories="cat"
        />
      </div>
    </div>
  </div>
</template>

<script>
import CategoryItem from '@/components/CategoryItem.vue'
export default {
  name: 'Category',
  data () {
    return {
      loading: true
    }
  },
  components: {
    CategoryItem
  },
  computed: {
    categories () {
      return this.$store.state.categories
    }
  },
  methods: {
    fetchCategories () {
      this.$store.dispatch('fetchCategories')
      this.loading = false
    }
  },
  created () {
    this.$loading(true)
    setTimeout(() => {
      this.$loading(false)
      this.fetchCategories()
    }, 500)
  }
}
</script>

<style>
.features-boxed {
  color:#313437;
  background-color:#eef4f7;
}

.features-boxed p {
  color:#7d8285;
}

.features-boxed h2 {
  font-weight:bold;
  margin-bottom:40px;
  padding-top:40px;
  color:inherit;
}

@media (max-width:767px) {
  .features-boxed h2 {
    margin-bottom:25px;
    padding-top:25px;
    font-size:24px;
  }
}

.features-boxed .intro {
  font-size:16px;
  max-width:500px;
  margin:0 auto;
}

.features-boxed .intro p {
  margin-bottom:0;
}

.features-boxed .item {
  text-align:center;
}

.features-boxed .item .box {
  text-align:center;
  padding:30px;
  background-color:#fff;
  margin-bottom:30px;
}

.features-boxed .item .icon {
  font-size:60px;
  color:#1485ee;
  margin-top:20px;
  margin-bottom:35px;
}

.features-boxed .item .name {
  font-weight:bold;
  font-size:18px;
  margin-bottom:8px;
  margin-top:0;
  color:inherit;
}

.features-boxed .item .description {
  font-size:15px;
  margin-top:15px;
  margin-bottom:20px;
}
</style>
