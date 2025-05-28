<script>
  // 메시지 바인딩용 변수
  let msg = '';

  function myclick() {
    msg = 'HAVE A GOOD DAY, EUGENES!';
  }
</script>

<p>{msg}</p>
<button on:click={myclick}>
NICE
</button>

