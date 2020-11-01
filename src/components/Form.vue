<template>
    <div class="coments form-group">
      <p>
        <input
          v-model="name"
          class="form-control"
          placeholder="nome"
          type="text"
          name="author"
        />
      </p>
      <p>
        <textarea
          v-model="message"
          class="form-control"
          placeholder="comentário"
          name="message"
        ></textarea>
      </p>
      <button v-on:click="addComment" type="submit" class="btn btn-primary">
        Comentar
      </button>
    </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      message: ''
    }
  },
  methods: {
    addComment() {
      if(this.message.trim() === '') { return; }
      
      this.$emit('add-todo', {
        name: this.name,
        message: this.message
      })

      this.name = '';
      this.message = '';
    }
  }
}
</script>