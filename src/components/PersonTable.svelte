<script>
	var persons = [
		{
			name: 'Arnfinn',
			role: 'Utvikler',
			totalEntries: 10,
			totalWins: 10,
			tickets: 1
		},
		{
			name: 'Jonatan Løve Franzen',
			role: 'Tekniker',
			totalEntries: 10,
			totalWins: 3,
			tickets: 3
		}
	];

	var searchTerm;
</script>

<input class="input" bind:value={searchTerm} type="search" placeholder="Search..." />
<div class="table-container" style="margin-top:6px;">
	<!-- Native Table Element -->
	<table class="table table-hover">
		<thead>
			<tr>
				<th>Name</th>
				<th>Role</th>
				<th>Entries</th>
				<th>Wins</th>
				<th>Tickets</th>
			</tr>
		</thead>
		<tbody>
			{#each persons as row, i}
				<tr>
					<td>{row.name}</td>
					<td>{row.role}</td>
					<td>{row.totalEntries}</td>
					<td>{row.totalWins}</td>
					<td>{row.tickets}</td>
				</tr>
			{/each}
		</tbody>
		<tfoot>
			<tr>
				<th colspan="3">Budget</th>
				<td>{persons.length * 125}kr</td>
			</tr>
		</tfoot>
	</table>
</div>

<style>
	.input {
		border-radius: 8px;
	}
</style>
