<script>
let mine = "."
let com = ".."
let result = "..."

const myclick = () => {
    console.log("mine",mine)
    console.log("com",com)
    console.log("result",result)

	var rnd = Math.random();
	if(rnd>0.5){
		com = "홀";
	}else{
		com = "짝";
	}
    if(mine == com){
		result = "이김";
	} else {
		result = "짐";
	}
}

</script>
<table>
    <tbody>
        <tr>
            <td> 나</td>
            <td>
                <input type="text" bind:value={mine} >
            </td>
        </tr>
        <tr>
            <td> 컴</td>
            <td>
                <input type="text" value={com} >
            </td>
        </tr>
        <tr>
            <td> 결과</td>
            <td>
                <input type="text" value={result} >
            </td>
        </tr>
        <tr>

            <td colspan="2">
                <input type="button" value="게임하기" onclick={myclick} />
            </td>
        </tr>

    </tbody>

</table>
<style>
    input[type='text']{
        width: 40px;
    }
    table,tr,td{
        border: 1px  solid gainsboro;
    }

</style>