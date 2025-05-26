<script>
  let count = +"100"
  const myclick = () =>{
    count+=1;
  }
</script>

{count}
<button onclick={myclick}>
  INCREASE
</button>
