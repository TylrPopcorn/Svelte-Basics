<!-- https://svelte.dev/docs/introduction -->

<!-- JavaScript -->
<script>
	let people = [
        {name: 'Yoshi', Color: "Red", num: 23, id: 1},
        {name: 'Luigi', Color: "Orange", num: 14, id: 2},
        {name: 'Mario', Color: "Pink", num: 50, id: 3},
    ]
</script>

<!-- HTML -->
<main>
	<h1>Hello World</h1>

    <!-- LOOP -->
    {#each people as person (person.id)}
         <!-- show data -->
        <div>
            <h3>{person.name}</h3>
            <p>{person.Color}</p>
        </div>
    {:else}
    <!-- If array is empty, this will show-->
        <p>No people found</p>
    {/each}
</main>

<!-- CSS -->
<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>