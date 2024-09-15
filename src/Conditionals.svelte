<!-- https://svelte.dev/docs/introduction -->

<!-- JavaScript -->
<script>
    //variable
	let people = [
        {name: 'Yoshi', Color: "Red", num: 23, id: 1},
        {name: 'Luigi', Color: "Orange", num: 14, id: 2},
        {name: 'Mario', Color: "Pink", num: 50, id: 3},
    ];

    //function
    const handleClick = (id) => {
        //delete person from people
        people = people.filter((person)=>{
            person.id != id
        })
    }

    let num = 5;
</script>

<!-- CONDITIONAL STATEMENT -->
{#if num > 20}
    <p>Greater than 20!</p>
{:else if num > 5}
    <p>Greater than 5!</p>
{:else}
    <p>Not greater than 5!</p>
{/if}

<!-- HTML -->
<main>
	<h1>Hello World</h1>

    <!-- LOOP -->
    {#each people as person (person.id)}
        <div>
            <h3>{person.name}</h3>
            <!-- CONDITIONAL STATEMENT -->
             {#if person.Color === "Red"}
                <strong>Blood red</strong>
             {/if}
            <p>{person.Color}</p>
            <!-- inline event -->
            <button on:click={()=>{handleClick(person.id)}}>Delete</button>
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