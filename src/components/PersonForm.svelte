<script>
	const roles = ['Salg', 'Utvikler', 'Tekniker', 'Mini boss', 'Boss', 'Final boss'];
</script>

<div style="display:flex;">
	<div style="width: 80%; margin-right: 6px;">
		<label class="label">
			<span>Name</span>
			<input class="input" type="text" placeholder="Add a person..." />
		</label>
	</div>
	<div>
		<label class="label">
			<span>Role</span>
			<select class="select">
				{#each roles as role, i}
					<option value={i}>{role}</option>
				{/each}
			</select>
		</label>
	</div>
</div>
<div style="width: 100%; display:flex; flex-direction: row-reverse;">
	<button type="button" class="btn variant-outline">Add</button>
</div>

<style>
	.input {
		border-radius: 8px;
	}
	.btn {
		border-radius: 8px;
		margin: 12px 0;
	}
</style>
