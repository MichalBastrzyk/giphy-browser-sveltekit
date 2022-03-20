<script>
	import { goto } from '$app/navigation';
	let searchBoxValue;

	const handleSubmit = () => {
		const url = searchBoxValue.split(' ').join('+');
		goto(`/search/${url}`);
	};
</script>

<header>
	<nav class="fixed z-50 w-full py-4 px-6 bg-black shadow-2xl">
		<div class="max-w-5xl m-auto flex space-around">
			<a href="/"> <h1 class="text-xl text-light-blue hover:text-green-blue">LOGO</h1></a>
			<form on:submit|preventDefault={handleSubmit}>
				<input
					type="text"
					bind:value={searchBoxValue}
					class="py-1 px-2 bg-dark-blue text-light-blue rounded-md focus:text-green-blue"
					required
				/>
				<button class="bg-light-blue text-green-blue">SEARCH</button>
			</form>
		</div>
	</nav>
</header>
