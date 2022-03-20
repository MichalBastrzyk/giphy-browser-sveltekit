<script>
	export let width = '16px';
	export let height = '16px';
	export let color = '#000';
</script>

<div class="icon" style={`width: ${width}; height: ${height}; color: ${color}`}>
	<slot />
</div>
