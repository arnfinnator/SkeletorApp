<script>
	import chartjs from 'chart.js/auto';
	let chartData;
	import { onMount } from 'svelte';

	let chartValues = [1, 2, 3, 3, 4, 4, 4, 5, 5, 5, 5, 5];
	let chartValues2 = [0, 0, 1, 2, 2, 2, 4, 5, 6, 6, 6, 7];
	let chartLabels = [
		'January',
		'February',
		'March',
		'April',
		'May',
		'June',
		'July',
		'August',
		'September',
		'November',
		'December'
	];
	let ctx;
	let chartCanvas;

	onMount(async (promise) => {
		ctx = chartCanvas.getContext('2d');
		var chart = new chartjs(ctx, {
			type: 'line',
			options: {
				plugins: {
					legend: {
						position: 'right',
						align: 'center'
					}
				}
			},
			data: {
				labels: chartLabels,
				datasets: [
					{
						label: 'Arnfinn',
						backgroundColor: 'rgb(255, 99, 132)',
						borderColor: 'rgb(122, 99, 132)',
						data: chartValues
					},
					{
						label: 'Jonatan',
						backgroundColor: 'rgb(255, 99, 132)',
						borderColor: 'rgb(144, 12, 125)',
						data: chartValues2
					}
				]
			}
		});
	});
</script>

<canvas bind:this={chartCanvas} id="myChart" />
