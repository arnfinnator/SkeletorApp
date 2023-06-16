<script>
	import { Table } from '@skeletonlabs/skeleton';
	import {
		tableMapperValues, // Utilities
		createDataTableStore,
		dataTableHandler,
		// Svelte Actions
		tableInteraction,
		tableA11y
	} from '@skeletonlabs/skeleton';

	const sourceData = [
		{ position: 1, name: 'Hydrogen', weight: 1.0079, symbol: 'H' },
		{ position: 2, name: 'Helium', weight: 4.0026, symbol: 'He' },
		{ position: 3, name: 'Lithium', weight: 6.941, symbol: 'Li' },
		{ position: 4, name: 'Beryllium', weight: 9.0122, symbol: 'Be' },
		{ position: 5, name: 'Boron', weight: 10.811, symbol: 'B' }
	];
	const tableSimple = {
		// A list of heading labels.
		head: ['Name', 'Est. Spending', 'Est. Winnings', 'Result', 'Actions'],
		// The data visibly shown in your table body UI.
		body: tableMapperValues(sourceData, ['name', 'position', 'weight', 'symbol']),
		// Optional: The data returned when interactive is enabled and a row is clicked.
		meta: tableMapperValues(sourceData, ['name', 'position', 'weight', 'Net']),
		// Optional: A list of footer labels.
		foot: ['Total spent', '', `<code class="code">${12 * 125}kr</code`]
	};

	const dataTableStore = createDataTableStore(
		// Pass your source data here:
		sourceData,
		// Provide optional settings:
		{
			// The current search term.
			search: '',
			// The current sort key.
			sort: '',
			// Paginator component settings.
			pagination: { offset: 0, limit: 5, size: 0, amounts: [1, 2, 5, 10] }
		}
	);

	// This automatically handles search, sort, etc when the model updates.
	dataTableStore.subscribe((model) => dataTableHandler(model));
</script>

<input class="input" bind:value={$dataTableStore.search} type="search" placeholder="Search..." />
<table class="table table-hover">
	<thead
		on:click={(e) => {
			dataTableStore.sort(e);
		}}
		on:keypress
	>
		<tr>
            <th><input type="checkbox" on:click={(e) => { dataTableStore.selectAll(e.currentTarget.checked) }} /></th>
			<th data-sort="position">Position</th>
			<th data-sort="name">Name</th>
			<th data-sort="name">Spent</th>
			<th data-sort="name">Earnings</th>
			<th data-sort="name">Net</th>
			<th data-sort="" />
			<!-- ... --->
		</tr>
	</thead>

	<tbody>
		{#each $dataTableStore.filtered as row, rowIndex}
			<tr class:table-row-checked={row.dataTableChecked}>
				<td><input type="checkbox" bind:checked={row.dataTableChecked} /></td>
				<td>{row.position}</td>
				<td>{row.name}</td>
				<td>{row.name}</td>
				<td>{row.name}</td>
				<td>{row.name}</td>
				<td>
					<span class="material-symbols-outlined"> data_usage </span>
					<span style="margin-left: 6px;" class="material-symbols-outlined"> show_chart </span>
				</td>
				<!-- ... --->
			</tr>
		{/each}
	</tbody>
</table>

<style>
	.input {
		border-radius: 8px;
		margin-bottom: 6px;
	}
</style>
