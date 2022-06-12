<script>
	import Modal from "./Modal.svelte";
	import AddPersonForm from "./AddPersonForm.svelte";
	let toShow = false;
	let people = [
		{
			name: "Ritik",
			age: "21",
			beltColor: "yellow",
			skills: ["running", "sneaking"],
			id: 1,
		},
		{
			name: "Ritik",
			age: "17",
			beltColor: "green",
			skills: ["running", "sneaking"],
			id: 2,
		},
		{
			name: "Abhi",
			age: "54",
			beltColor: "black",
			skills: ["running", "sneaking"],
			id: 3,
		},
	];
	const handleDelete = (id) => {
		people = people.filter((person) => person.id != id);
	};
	const openHandler = () => {
		toShow = !toShow;
	};
	const addPerson = (e) => {
		const person = e.detail;
		people = [person, ...people];
		toShow = false;
	};
</script>

<Modal isPromo={false} {toShow} on:click={openHandler}>
	<AddPersonForm on:addPerson={addPerson} />
</Modal>
<main>
	<button on:click={openHandler}>Open Modal</button>
	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			{#if person.beltColor === "black"}
				<p><strong>MASTER NINJA</strong></p>
			{/if}
			<p>I am {person.age} years old , {person.beltColor} belt</p>
			{#each person.skills as skill}
				<small>{skill}</small>
			{/each}<br />
			<button on:click={() => handleDelete(person.id)}>Delete</button>
		</div>
	{:else}
		<p>Nothing to show up....</p>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h4 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
		margin: 10px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
