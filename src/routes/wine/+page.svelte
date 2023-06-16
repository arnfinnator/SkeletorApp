<script>
	import PersonForm from '../../components/PersonForm.svelte';
	import PersonTable from '../../components/PersonTable.svelte';

	import { TabGroup, Tab } from '@skeletonlabs/skeleton';

    import WineChart from '../../components/WineChart.svelte';
    import WineResultTable from '../../components/WineResultTable.svelte';

	let tabSet = 2; //default tab, 0 based
</script>

<div class="wine-container">
	<TabGroup>
		<Tab bind:group={tabSet} name="tab1" value={0}>Play</Tab>
		<Tab bind:group={tabSet} name="tab2" value={1}>Entries</Tab>
		<Tab bind:group={tabSet} name="tab3" value={2}>Statistics</Tab>
		<!-- Tab Panels --->
		<svelte:fragment slot="panel">
			{#if tabSet === 0}
				Trekning
			{:else if tabSet === 1}
				<PersonForm />
				<hr class="!border-t-2" style="margin: 5vh 0;" />
				<PersonTable />
			{:else if tabSet === 2}
                <WineChart/>
                <div style="margin-top: 10vh"></div>
                <WineResultTable />
			{/if}
		</svelte:fragment>
	</TabGroup>
</div>

<style>
	.wine-container {
		max-width: 720px;
		margin: 0 auto;

        overflow: overlay
	}
</style>
