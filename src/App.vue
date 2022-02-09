<template>
  <div class="container column">
    <app-form @add-form="addBlock"></app-form>
    <app-resume :blocks="blocks"></app-resume>

  </div>
  <app-loader v-if="loading"></app-loader>
  <app-comment
    v-else
    :comments="comments"
    @load="loadComments"
  ></app-comment>

</template>

<script>
import AppForm from '@/components/AppForm'
import axios from 'axios'
import AppResume from '@/components/AppResume'
import AppLoader from '@/components/AppLoader'
import AppComment from '@/components/AppComment'

export default {
  data () {
    return {
      blocks: [],
      loading: false,
      comments: []
    }
  },
  methods: {
    addBlock (block) {
      this.blocks.push(block)
    },
    async loadComments() {
      this.loading = true
      const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = Object.keys(data).map(key => {
        return {
          id: key,
          email: data[key].email,
          body: data[key].body
        }
      })
      this.loading = false
    }
  },
  components: {AppForm, AppResume, AppLoader, AppComment}
}
</script>

<style>

</style>
