<template>
  <div id="translateform" class="row">
  <div class="col-md-6 col-md-offset-3">
	  <form id="transForm" v-on:submit="formSubmit" class="well form-inline">
	  	<input type="text" v-model="textToTranslate" placeholder="Enter a word" class="form-control">
	  	<select v-on:change="selectChange" v-model="language" class="form-control">
	  		<option value="ru">Russian</option>
	  		<option value="es">Spanish</option>
	  		<option value="fr">French</option>
	  		<option value="zh">Chinese</option>
	  		<option value="en">English</option>
	  		<option value="pt">Portuguese</option>
	  	</select>
	  	<input type="submit" value="Translate" class="btn btn-primary">
	  </form>
  </div>
  </div>
</template>

<script>

export default {
  name: 'translateform',
  data() {
  	return {
  		textToTranslate: '',
  		language: ''
  	}
  },
  created() {
  	this.language = 'ru';
  },
  methods: {
  	formSubmit(e) {
  		this.$emit('formSubmit', this.textToTranslate, this.language);
  		e.preventDefault();
  	},
    selectChange(e) {
      this.formSubmit(e);
    }
  } 
}
</script>

<style>

#transForm {
	border-radius: 10px;
	border: 1px #ccc solid;
}

</style>
