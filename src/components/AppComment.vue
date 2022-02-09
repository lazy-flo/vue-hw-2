<template>
  <div class="container">
    <div class="card" v-if="comments.length === 0">
      <button class="btn primary" @click="$emit('load')">Загрузить комментарии</button>
    </div>
    <div class="card" v-else>
      <h2>Комментарии</h2>
      <ul class="list">
        <li class="list-item"
            v-for="comment in comments"
            :key="comment.id"
        >
          <div>
            <p><strong>{{ comment.email }}</strong></p>
            <small>{{ comment.body }}</small>
            <hr/>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  emits: ['load'],
  props: ['comments']
}
</script>

<style scoped>

</style>
