<script>
	import { onMount } from 'svelte';
	import config from './config.js';
	import Sidebar from './Sidebar.svelte';

	let items = [];

	onMount(async () => {
		let musicCollectionUrl = config.musicCollectionUrl;
		if (musicCollectionUrl.endsWith('/')) {
			musicCollectionUrl = musicCollectionUrl.slice(0, -1);
		}
		const fullUrl = `${musicCollectionUrl}/.cal/meta/artists.json`;
		console.log(fullUrl); // Log the URL
		const response = await fetch(fullUrl);
		const data = await response.json();
		items = data.filter(item => !item.name.startsWith('.'));
		items = items.map(item => item.name.endsWith('.sonic') ? { ...item, name: item.name.slice(0, -6) } : item);
	});
</script>

<div class="container">
	<Sidebar/>
	<main>
		<h1>Artists</h1>
		<ul class="button-block">
			{#each items as item, index (item.name)}
				<li>
					<button class={`listbutton ${index === 0 ? 'first' : ''} ${index === items.length - 1 ? 'last' : ''}`}>
						{item.name}
					</button>
				</li>
			{/each}
		</ul>
	</main>
</div>

<style>
    .container {
        display: flex;
    }

    main {
        margin-left: 14rem; /* Adjust this value to match the width of your sidebar */
        width: calc(100% - 14rem); /* Subtract the width of the sidebar */
    }

    .button-block {
        padding: 0;
        list-style-type: none;
        width: 100%;
    }

    .button-block li {
        width: 100%;
        display: block;
    }

    .listbutton {
        width: 100%;
        box-sizing: border-box;
    }
</style>