<script>
	import { onMount } from "svelte";
	let countdownDate = new Date('Jan 1, 2023 00:00:01').getTime();
	let currentDate = new Date();
    let dateForDistance = currentDate.getTime()
    console.log(currentDate)
	let distance = countdownDate - dateForDistance;
    console.log(distance)

	let days = Math.floor(distance / (1000 * 60 * 60 * 24));
	let hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
	let minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
	let seconds = Math.floor((distance % (1000 * 60)) / 1000);
    
		const interval = setInterval(() => {
			currentDate = new Date();
		}, 1000);
	
</script>

<div class="flex items-center justify-center h-screen">
    {#if days < 1}
    <h1 class="text-red-500 text-9xl">{`${hours} : ${minutes} : ${seconds}`}</h1>
    {:else}
    <h1 class="text-red-500 text-9xl">{`${days} : ${hours} : ${minutes} : ${seconds}`}</h1>
    {/if}
</div>
