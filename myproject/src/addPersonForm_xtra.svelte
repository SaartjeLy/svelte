<script>
    import { createEventDispatcher } from 'svelte';

    let dispatch = createEventDispatcher();
    let name;
    let beltColour;
    let age;
    // let fighting = false;
    // let sneaking = false;
    // let running = false;
    let skills=[];

    const handleSubmit = () => {
        console.log(name, beltColour, age, skills);
    };
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="name" bind:value={name}>
    <input type="text" placeholder="belt colour" bind:value={beltColour}>
    <input type="number" placeholder="age" bind:value={age}>
    <label>Skills:</label>
    <!--<input type="checkbox" bind:checked={fighting}>fighting<br>
    <input type="checkbox" bind:checked={sneaking}>sneaking<br>
    <input type="checkbox" bind:checked={running}>running<br> -->
    <input type="checkbox" bind:group={skills} value="fighting">fighting<br>
    <input type="checkbox" bind:group={skills} value="sneaking">sneaking<br>
    <input type="checkbox" bind:group={skills} value="running">running<br>
    <label>Belt colour:</label>
    <select bind:value={beltColour}>
        <option value="black">black</option>
        <option value="orange">orange</option>
        <option value="white">white</option>
    </select>
    <button>Add Person</button>
</form>
