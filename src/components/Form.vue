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
      <p v-if="typing">digitando...</p> 
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
      message: '',
      typing: false
    }
  },
  methods: {
    addComment() {
      if(this.message.trim() === '') { return; }
      
      this.$emit('add-todo', {
        name: this.name,
        message: this.message,
      })

      this.name = '';
      this.message = '';
    }
  },
  watch: {
    message() {
      if(this.message) {
        this.typing = true;
  
        setTimeout(() => {
          this.typing = false;
        }, 3000);
      }
    }
  }
}
</script>