<script>
	let files;
	let spreadsheet = [];
	export let name;
	const hello = () => {
		
		const inputFile = files[0];
		if (inputFile.name.endsWith(".csv")){
			const reader = new FileReader();
			reader.readAsText(inputFile);
			reader.onload = (e) => { 
				const text = e.target.result;
				const rows = text.split('\r\n');
				rows.forEach((element, index) => {
					const items = element.split(',');
					spreadsheet[index] = items;

				});
				console.log(spreadsheet)

			}
			
		} else {
			alert("U FAILED")
		}

	}
</script>

<main>

	{#if files && files[0]} <!--- when both are true -->
		<p>
			{files[0].name}
		</p>
	{/if}
	<input type="file" bind:files on:change={() => {hello()}}>  


	{#if spreadsheet.length > 0}
	<table>
		{#each spreadsheet as row}
			{#if spreadsheet.indexOf(row) == 0}
				{#each row as column}
					<th>{column}</th>
				{/each}
		    {:else}
			<tr>
			{#each row as column}
				<td>{column}</td>			
			{/each}
			</tr>
		{/if}
		{/each}
	</table>
	{/if}
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