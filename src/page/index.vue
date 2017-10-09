
<template>
  <div>
    <myheader></myheader>
    <div class="article_list">
      <ul>
        <li v-for="i in list">
          <!--<time v-text="i.create_at"></time>-->
          <time v-text="$utils.goodTime(i.create_at)"></time>
          <router-link :to="'/content/' + i.id">
            {{i.title}}
          </router-link>
        </li>
      </ul>
    </div>
    <myfooter></myfooter>
  </div>
</template>
<script>
  import myheader from '../components/header.vue'
  import myfooter from '../components/footer.vue'
  export default {
    components: { myheader, myfooter },
    data () {
      return {
        list: []
      }
    },
    created () {
//      this.$api.get('topics', null, r => {
//        console.log(r)
//      })
      this.getData()
    },
    methods: {
      getData () {
        this.$api.get('topics', null, r => {
          this.list = r.data
        })
      }
    }
  }
</script>
