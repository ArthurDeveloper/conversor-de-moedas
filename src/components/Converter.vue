<template>
	<div id="converter">
		<h1>Conversor de moedas</h1>
		<slot />
	</div>
</template>

<script>
export default {
  name: 'Converter'
}
</script>

<style scoped>
    
#converter {
	display: flex;
	flex-direction: column;
	align-items: center;
	background-color: #FFFFFF;
	padding: 20px;
	border-radius: 15px;
	overflow: auto;
	width: 70vw;
	height: 65vh;
}

</style>
