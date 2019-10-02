<template>
  <li>
    <span v-show="!todo.edit">{{ todo.text }}</span>
    <input
      type="text"
      v-show="todo.edit"
      v-model="todo.text"
      @keyup.enter="$emit('doneEdit', todo.text)"
    />
    <button @click="$emit('remove', todo.id)">
      X
    </button>
    <button @click="$emit('edit', todo)">
      Edit
    </button>
  </li>
</template>

<script>
  export default {
    props: {
      todo: {
        type: Object,
        required: true
      }
    }
  }
</script>
