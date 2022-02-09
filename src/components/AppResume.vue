<template>
  <div class="card card-w70 center">
    <template v-if="blocks.length">
      <component
        v-for="block in blocks"
        :key="block.id"
        :is="'form-' + block.type"
        :="{value: block.value}"
      ></component>
    </template>
    <div class="card" v-else>
      <h3>Добавьте первый блок, чтобы увидеть результат</h3>
    </div>
  </div>
</template>

<script>
import FormTitle from '@/form/FormTitle'
import FormSubtitle from '@/form/FormSubtitle'
import FormAvatar from '@/form/FormAvatar'
import FormText from '@/form/FormText'
export default {
  props: ['blocks'],
  components: {FormTitle, FormSubtitle, FormAvatar, FormText}

}
</script>

<style scoped>
.center {
  justify-content: center;
}
</style>
