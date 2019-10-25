<template>
<div>
  <h1>First Vue Single File Component</h1>
  <p>{{ msg }}</p>
</div>
</template>

<script>
export default {
	data () {
		return {
			msg: 'Hello, Vue SFC!'
		};
	}
}
</script>
