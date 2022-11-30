<script>
	import Modal from './Modal.svelte';
	import AddPersonForm from './AddPersonForm.svelte';

	let showModal = false;

	const toggleModal = () => {
		showModal = !showModal;
	}

	let people = [
		{ name: 'yoshi', beltColour: 'black', age: 25, id: 1},
		{ name: 'mario', beltColour: 'orange', age: 45, id: 2},
		{ name: 'luigi', beltColour: 'brown', age: 35, id: 3}

	];

	const handleClick = (e, id) => {
		people = people.filter((person) => person.id != id);
		console.log(e);
	}

	let num =5;
</script>

<Modal {showModal} on:click={toggleModal}> <!--everything below is passed thru to the Modal.svelte as a child @ <slot>-->
	<AddPersonForm /> <!--when modal is triggered, add person form gets put in <slot> in Modal.svelte-->
</Modal>
<main>
	<button on:click|once={toggleModal}>Open Modal</button>
	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			{#if person.beltColour === 'black'}
				<p><strong>MASTER NINJA</strong></p>
			{/if}
			<p>{person.age} years old, {person.beltColour} belt.</p>
			<!--when you pass a parameter, it is envoked-->
		</div>
		{:else}
			<p>There are no people to show...</p>
	{/each} 
</main>

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