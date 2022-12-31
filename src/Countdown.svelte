<script>
	import { onMount } from 'svelte';
	let countdownDate = new Date('Jan 1, 2023 00:00:00').getTime();
	$: currentDate = new Date();
	$: dateForDistance = currentDate.getTime();
	console.log(currentDate);
	$: distance = countdownDate - dateForDistance;
	console.log(distance);

	$: days = Math.floor(distance / (1000 * 60 * 60 * 24));
	$: hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
	$: minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
	$: seconds = Math.floor((distance % (1000 * 60)) / 1000);

	onMount(() => {
		const interval = setInterval(() => {
			currentDate = new Date();
		}, 1000);
	});
	$: hh = hours < 10 ? `0${hours}` : hours
	$: mm = minutes < 10 ? `0${minutes}` : minutes
	$: ss = seconds < 10 ? `0${seconds}` : seconds


</script>

<div class="flex items-center justify-center h-screen">
	{#if days < 1}
		<h1 class="text-red-500 text-9xl">
			{`${hh} : ${mm} : ${ss}`}
		</h1>
	{:else}
		<h1 class="text-red-500 text-9xl">
			{`${days} : ${hours} : ${mm} : ${ss}`}
		</h1>
	{/if}
</div>
