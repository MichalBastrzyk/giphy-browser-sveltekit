<script>
	import { inview } from 'svelte-inview';
	import { fly as fade } from 'svelte/transition';
	export let title, src, author;

	let isInView;
	const inViewOptions = {
		rootMargin: '-25px',
		unobserveOnEnter: true
	};
	const handleChange = ({ detail }) => (isInView = detail.inView);
</script>

<div
	use:inview={inViewOptions}
	on:change={handleChange}
	class="p-4 m-4 bg-black text-light-blue shadow-2xl rounded-xl"
>
	{#if isInView}
		<div class="flex flex-col items-center justify-center" in:fade={{ duration: 1000 }}>
			<img class="h-96 w-96" {src} alt={title} />
			<div class="p-4 shadow-xl">
				<h1 class="text-xl hover:text-green-blue">{title}</h1>
				<div class=" p-2 flex items-center gap-4 ">
					{#if author}
						<img class="h-12 w-12 rounded-full" src={author.avatar_url} alt={author.username} />
						<h3 class="text-green-blue">{author.username}</h3>
					{:else}
						<h3 class="text-blue">Author not found</h3>
					{/if}
				</div>
			</div>
		</div>
	{/if}
</div>
