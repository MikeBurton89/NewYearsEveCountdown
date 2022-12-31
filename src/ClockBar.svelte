<script>
    import {onMount} from 'svelte'
    let currentTime = new Date()
    $: hours = currentTime.getHours()
    $: minutes = currentTime.getMinutes()
    $: seconds = currentTime.getSeconds()
    $: hh = hours < 10 ? `0${hours}` : hours
    $: mm = minutes < 10 ? `0${minutes}` : minutes
    $: ss = seconds < 10 ? `0${seconds}` : seconds

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
  <h1 class=" py-2 pr-2 text-white text-xl font-sans font-bold drop-shadow-2xl text-shadow shadow-amber-200">
    {`${hh} : ${mm} : ${ss}`}
  </h1>
</div>
