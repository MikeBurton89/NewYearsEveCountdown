<script>
    import {onMount} from 'svelte'
    let currentTime = new Date()
    $: hours = currentTime.getHours()
    $: minutes = currentTime.getMinutes()
    $: seconds = currentTime.getSeconds()
    onMount(() => {
		const interval = setInterval(() => {
			currentTime = new Date();
		}, 1000);
        return () => {
			clearInterval(interval);
		};
	})
    
</script>

<div class='flex h-2 w-full justify-end'>
  <h1 class=" py-2 pr-2 text-xl text-red-600">
    {`${hours} : ${minutes} : ${seconds}`}
  </h1>
</div>
