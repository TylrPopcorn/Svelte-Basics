<!-- https://svelte.dev/docs/introduction -->

<!-- JavaScript -->
<script>
	//imports
	import Modal from "./Components.svelte"; //component
	import Slots from "./Slots.svelte";
	import Form from "./Form.svelte";

	//------------- VARIABLES ----------- \\
	let Color =  "943360";
	let showModal = false;
	let showModal2 = false;
	// $: {console.log(Color)} //Will print out each time Color is changed.
	//------
	//Reactive values
	let firstName = "Jack";
	let lastName = "Black";
	$: fullName = `${firstName} ${lastName}`;
	let people = [];

	//-------------- FUNCTIONS ---------------\\
	//Will set Color to a corresponding color
	const handleClick = () =>{
		Color =  Math.floor(Math.random() * 16777215).toString(16); // 16777215 is the decimal for "FFFFFF"
	}

	//Will handle input of the ColorInput input
	const handleInput = (e) =>{
		Color = e.target.value;
	}

	//Will change 'showModal'
	const toggleModal = function(){
		showModal = !showModal;
	}

	//Will change 'showModal2'
	const toggleModal2 = function(){
		showModal2 = !showModal2;
	}

	//Will add a new person to the data
	const AddPerson = (e) =>{
		const person = e.detail;
		people = [person, ...people]
	}
</script>

<!-- Component / PROPS -->
<Modal message="This is a prop variable" isPromo={true} {showModal} on:click={toggleModal}>
	<Form on:AddPerson={AddPerson}/>
</Modal>

<!-- Slot -->
<Slots {showModal2} on:click={toggleModal2}>
	<!-- component -->
	<Form />
</Slots>

<!-- HTML -->
<main>
	<h1 style="color: #{Color}">Hello {Color}!</h1>
	<!-- input field (two-way binding)-->
	<input class="ColorInput" type="text" on:input={handleInput} value={Color}>

	<!-- Color Button -->
	<button on:click={handleClick} style="background-color: #{Color}">Update Color</button>

	<!----------------------->
	<br>
	<!----------------------->

	<!-- Reactive values -->
	<!-- https://svelte.dev/docs/element-directives#bind-property -->
	<h2 style="margin-top: 60px">Hello {fullName}</h2>
	<input type="text" bind:value={firstName}>
	<input type="text" bind:value={lastName}>

	<!----------------------->
	<br>
	<!----------------------->

	<!-- Modal Button -->
	 <!-- 'once' is an event modifier. -->
	<button on:click|once={toggleModal} style="margin-top: 30px">Open Modal 1</button>

	<!-- Modal Buton (slot )-->
	<button on:click|once={toggleModal2} style="margin-top: 30px">Open Modal 2</button>
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