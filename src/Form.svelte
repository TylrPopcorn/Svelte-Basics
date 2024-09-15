<!-- https://svelte.dev/docs/introduction -->
<!-- https://svelte.dev/repl/c399ebf9700b4b25bf6fce7d0b3d4ffd?version=4.2.19 -->

<!-- javascript -->
<script>
    import {createEventDispatcher} from "svelte";
    let dispatch = createEventDispatcher(); //Will dispatch custom events so we can pass data from one file to another

    let name;
    let colour;
    let age;
    let Running = false;
    let skills = [];

    const handleSubmit = () =>{
       const person = {
        name,
        colour,
        age,
        Running, 
        skills,
        id: Math.random(),
       } 
       dispatch('AddPerson', person);
    }
</script>

<!-- HTML -->
<!-- PreventDefault will keep the page from refreshing -->
<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="name" bind:value={name}>
	<input type="text" placeholder="color" bind:value={colour}>
    <input type="number"  placeholder="age" bind:value={age}>
    <label>Skills:</label>
    <!-- example 1 -->
    <input type="checkbox" bind:checked={Running}>Running<br>
    <!-- example 2 -->
    <input type="checkbox" bind:group={skills} value="Walking">Walking<br>
    <input type="checkbox" bind:group={skills} value="Swimming">Swimming<br>
	<button>Add Person</button>
    <!-- example 3 -->
     <select bind:value={colour}>
        <option value = "red">Red</option>
        <option value = "blue">Blue</option>
     </select>
</form>

<!-- css -->
<style>

</style>