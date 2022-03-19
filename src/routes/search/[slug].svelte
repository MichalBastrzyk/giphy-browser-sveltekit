<script context="module">
	export async function load({ fetch, params }) {
		let res = await fetch(
			`http://api.giphy.com/v1/gifs/search?q=${params.slug}&api_key=GtU3P02qxm1IffgMjiQ35yktehH0l5H8&limit=20`
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
		<GifCard title={gif.title} src={gif.images.downsized_large.url} author={gif.user} />
	{/each}
</div>
