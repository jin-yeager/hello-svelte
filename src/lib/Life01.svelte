<script>
  import {onDestroy, onMount} from "svelte";

  let msg = "LIFE01"

  onMount(()=>{
      console.log("LIFE01 onMount")
  })
  onDestroy(()=>{
      console.log("LIFE01 onMount")
  })

</script>

<p>{msg}</p>

