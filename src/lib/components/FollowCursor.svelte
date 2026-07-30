<script>
  let {
    duration = 8000,
    fill = 'forwards',
    ...restProps
  } = $props();


  let blob;


  const followCursor = (e) => {
    const {
      clientX,
      clientY
    } = e;

    blob.animate({ 
      left: `${clientX}px`,
      top: `${clientY}px`
    }, { duration, fill });
  };
</script>


<svelte:window onpointermove={followCursor} />


<div bind:this={blob} {...restProps}></div>