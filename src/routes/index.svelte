<script context="module">
	export async function load({ fetch }) {
		let res = await fetch(
			'https://api.giphy.com/v1/gifs/trending?api_key=GtU3P02qxm1IffgMjiQ35yktehH0l5H8'
		);

		if (res.ok) {
			let json = await res.json();
			return {
				props: {
					data: json.data
				}
			};
		}
		return {
			status: res.status,
			error: new Error()
		};
	}
</script>

<script>
	import GifCard from '$lib/GifCard.svelte';
	export let data = [];
</script>

<div class="grid justify-center items-center bg-black">
	{#each data as gif}
		<GifCard title={gif.title} src={gif.images.downsized.url} author={gif.user} />
	{/each}
</div>
