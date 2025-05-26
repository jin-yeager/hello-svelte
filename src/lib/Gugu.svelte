<script>
  let dan = ""
  let outText = "";

  const gugu = (dan) => {
    let text = "";
    for(let i = 1 ;i<=9; i++) {
      text += `${dan} x ${i} = ${dan*i}\n`;
    }
      return text;
  };

  function printGugu(){
    outText = gugu(dan);
  }

</script>

<table>
  <tbody>
    <tr>
      <td>출력단수</td>
      <td>
        <input type="text" bind:value="{dan}"/>
      </td>
    </tr>
    <tr>
      <td colspan="2">
        <input type="button" onclick={printGugu()} value="출력하기"/>
      </td>
    </tr>
    <tr>
      <td colspan="2">
        <textarea rows="13" cols="17">{outText}</textarea>

      </td>
    </tr>
  </tbody>
</table>
<style>
  table,tr,td{
    border:1px solid grey;
  }
  input[type='text']{
    width: 40px;
  }
</style>
