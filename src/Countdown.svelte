<script>
	import { onMount } from 'svelte';
	let countdownDate = new Date('Jan 01, 2024 00:00:01').getTime();
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

<div class="flex items-center justify-center h-screen w-screen">
	{#if days < 1}
		<h1 class="text-white text-9xl font-sans font-bold drop-shadow text-shadow-lg shadow-blue-400">
			{distance > 0 ? `${hh} : ${mm} : ${ss}` : 'BUON ANNO'}
		</h1>
	{:else}
		<h1 class="text-white text-9xl font-sans font-bold text-shadow-lg shadow-blue-400">
			{distance > 0 ? `${days} : ${hours} : ${mm} : ${ss}` : 'BUON ANNO'}
		</h1>
	{/if}
</div>
