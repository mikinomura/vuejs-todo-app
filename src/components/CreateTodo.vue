<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click='openForm' v-show='!isCreating'>
      <i class='plus icon'></i>
    </button>
    <div v-show='isCreating'>
      <div class='content'>
      	<div class='ui form'>
      	  <div class='field'>
      	  	<label>Title</label>
      	  	<input v-model='titleText' type='text' ref='title' defaultValue="">
      	  </div>

      	  <div class='field'>
      	  	<label>Project</label>
      	  	<input v-model='projectText' type="text" name="project" defaultValue="">
      	  </div>

      	  <div>
      	  	<button v-on:click='sendForm()'>
      	  	 Create
      	  	</button>

      	  	<button v-on:click='closeForm()'>
      	  	  Cancel	
      	  	</button>
      	  </div>
      	</div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
  	data() {
  	  return {
  	  	titleText: '',
  	  	projectText: '',
  	  	isCreating: false,
  	  };
  	},
  	methods: {
  	  openForm() {
  	  	this.isCreating = true;
  	  },
  	  closeForm() {
  	  	this.isCreating = false;
  	  },
  	  sendForm() {
  	  	console.log('send');
  	  	if (this.titleText.length > 0 && this.projectText.length > 0) {
  	  		console.log('send success');
  	  		const title = this.titleText;
  	  		const project = this.projectText;
  	  		this.$emit('create-todo', {
  	  			title,
  	  			project,
  	  			done: false,
  	  		});
  	  		this.newTodoText = '';
  	  	}
  	  	this.isCreating = false;
  	  },
  	},
  };
</script>