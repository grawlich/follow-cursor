<script>
  import FollowCursor from "$lib/components/FollowCursor.svelte";
</script>


<FollowCursor class="blob" duration={6000} />


<style>
  :global(.blob) {
    position: absolute;
    top: 0;
    left: 0;
    translate: -50% -50%;
    background: conic-gradient(
      in oklch,
      var(--grad-4),
      var(--grad-1),
      var(--grad-2),
      var(--grad-3),
      var(--grad-4)
    );
    height: 12rem;
    aspect-ratio: 1;
    border-radius: 100vw;
    animation: rotate 20s linear infinite;
    filter: blur(var(--blur));
    -webkit-filter: blur(var(--blur));
  }


  @keyframes rotate {
    from {
      rotate: 0deg;
    }
    50% {
      scale: 1.25;
      filter: blur(calc(var(--blur) * 1.25));
    }
    to {
      rotate: 360deg;
    }
  }
</style>