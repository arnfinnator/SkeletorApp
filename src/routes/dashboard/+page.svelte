<script>
	import VesselCard from '../../components/VesselCard.svelte';

</script>

<div class="vessel-dashboard-container">
	<h2>Fleet</h2>
	<div class="vessel-card-container">
		{#each { length: 6 } as _, i}
			<VesselCard />
		{/each}
	</div>
</div>

<style>
	.vessel-dashboard-container {
		margin: 0 40px;
	}
	.vessel-card-container {
		border: 1px solid #ccc;
		padding: 12px;
		display: flex;
		flex-wrap: wrap;
		justify-content: center;

		/* max-height: 40vh;
		overflow: auto; */
	}
</style>
