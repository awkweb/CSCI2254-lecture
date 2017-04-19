<template>
  <li class="item__container">
    <input
    	class="item__name"
        v-model="todo.name"
        type="text">
    
    <input
    	v-model="todo.is_complete"
    	id="checkbox"
    	type="checkbox">
  </li>
</template>

<script>
export default {
  name: 'to-do-list-item',

  props: ['todo']
}
</script>

<style lang="scss">
$sans-serif: 'Avenir', Helvetica, Arial, sans-serif;
$gray: #EAEAEA;

.item {
	&__container {
		display: flex;
		align-items: center;
	   	border-bottom: {
	    	color: $gray;
	    	width: 1px;
	    	style: solid;
	    }
	    padding: {
	    	top: .65rem;
	      	right: .65rem;
	      	bottom: .65rem;
	      	left: .65rem;
	    }

	   	&:first-child {
	   		border-top: {
	    		color: $gray;
	    		width: 1px;
	    		style: solid;
	    	}
	    }
	}

	&__name {
		flex: 1;
		font: {
	      family: $sans-serif;
	      size: .85rem;
	    }
	    border: 0;
	}	
}
</style>
