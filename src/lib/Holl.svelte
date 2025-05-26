<script>
  let mine = ""
  let com = 0
  let result = ""

  function myclick() {
    if (mine !== "홀" && mine !== "짝") {
      result = "홀 또는 짝을 입력해주세요"
      com = 0
      return
    }

    const num = Math.floor(Math.random() * 10) + 1
    com = num

    const parity = num % 2 === 0 ? "짝" : "홀"

    result = mine === parity ? "이겼습니다!" : "졌습니다!"
  }
</script>


<table>
  <tbody>
  <tr>
    <td>내 선택</td>
    <td>
      <input type="text" bind:value={mine} placeholder="홀 또는 짝">
    </td>
  </tr>
  <tr>
    <td>컴퓨터 숫자</td>
    <td>
      <input type="number" bind:value={com} readonly>
    </td>
  </tr>
  <tr>
    <td>결과</td>
    <td>
      <input type="text" bind:value={result} readonly>
    </td>
  </tr>
  <tr>
    <td colspan="2">
      <input type="button" on:click={myclick} value="게임하기">
    </td>
  </tr>
  </tbody>
</table>
<style>

</style>
