<script>
	
	let showModal = false;

	const toggleModal = () => {
		showModal = !showModal;
	};

	import Modal from "./Modal.svelte";
	import AddPersonForm from "./AddPersonForm.svelte";

	let people = [
		{ name: "yoshi", beltColour: "black", age: 25, id: 1 },
		{ name: "mario", beltColour: "orange", age: 45, id: 2 },
		{ name: "luigi", beltColour: "brown", age: 35, id: 3 },
	];
	const handleClick = (id) => {
		people = people.filter((person) => person.id != id);
	};

	let num = 3;

	const addPerson = (e) => {
		const person = e.detail;
		people = [person, ...people];
		showModal = false;
	};
</script>

<Modal message="Hey! I am a prop value!" {showModal} on:click={toggleModal}>

	<AddPersonForm on:addPerson={addPerson} />

	

</Modal>
<main>
	<button on:click={toggleModal}>Open Modal</button>

	<!-- {#if num > 20  }
	<p>Greater than 20</p>
	{:else if num > 5}
	<p> Greater than 5</p>
	{:else}
	<p>Not greater than 5</p>
	{/if} -->

	{#each people as person}
		<div>
			<h4>{person.name}</h4>
			{#if person.beltColour === "black"}
				<p><strong>Master Ninja is coming !!!</strong></p>
			{/if}
			<p>{person.age} years old, {person.beltColour} belt.</p>
			<button on:click={() => handleClick(person.id)}> Delete</button>
			<!-- <button on:click =  {handleClick(person.id)}> Delete</button> -->
			<!-- this comment code is also working, why should we right it inside another function -->
		</div>
	{:else}
		<p>There are no people to show!</p>
	{/each}
</main>

<Modal message="What is your name?" />

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
