<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    let name;
    let beltColor;
    let age;
    let skills = [];
    const handleSubmit = () => {
        let person = {
            name,
            beltColor,
            age,
            skills,
            id: Math.random(),
        };
        dispatch("addPerson", person);
    };
</script>

<form on:submit|preventDefault={handleSubmit}>
    <h3>Add new Person</h3>
    <input type="text" placeholder="Name" bind:value={name} />
    <!-- <input type="text" placeholder="Belt color" bind:value={beltColor} /> -->
    <input type="number" placeholder="age" bind:value={age} /><br />
    <input type="checkbox" value="fighting" bind:group={skills} />Fighting<br />
    <input type="checkbox" value="sneaking" bind:group={skills} />sneaking<br />
    <input type="checkbox" value="running" bind:group={skills} />Running<br />
    <select bind:value={beltColor}>
        <option value="black">Black</option>
        <option value="white">White</option>
        <option value="yellow">Yellow</option>
        <option value="green">Green</option>
    </select>

    <button>Add person</button>
</form>

<style>
</style>
