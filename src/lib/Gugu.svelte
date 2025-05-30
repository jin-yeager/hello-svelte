<script>
    let dan = "."
    let txt = ".."

    const myclick = () => {
        let idan = parseInt(dan)

        let _txt = ""

        for (let i = 1; i <= 9; i++) {
            _txt += idan + "*" + i + "=" + (idan * i) + "\n"

        }
        txt = _txt
    }

</script>

<table>
    <tbody>
    <tr>
        <td>출력단수</td>
        <td>
            <input type="text" bind:value={dan}/>
        </td>
    </tr>
    <tr>
        <td colspan="2">
            <input type="button" onclick={myclick} value="출력하기"/>
        </td>
    </tr>
    <tr>
        <td colspan="2">
            <textarea rows="13" cols="17">{txt}</textarea>
        </td>
    </tr>
    </tbody>
</table>
<style>
    table, tr, td {
        border: 1px solid gray;
    }

    input[type='text'] {
        width: 40px;
    }

</style>
