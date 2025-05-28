<script>
    import { onMount } from 'svelte';

    let ran;              // 정답
    let guess = '';       // 인풋값
    let lines = [];       // 결과 로그

    onMount(() => {
        ran = Math.floor(Math.random() * 99) + 1;
    });

    function myclick() {
        const num = parseInt(guess, 10);
        if (isNaN(num)) {
            alert('숫자를 입력하세요.');
            return;
        }

        let text;
        if (num === ran) {
            text = '정답!';
            alert('정답!');
        } else if (num < ran) {
            text = '더 큰 수를 입력하세요.';
        } else {
            text = '더 작은 수를 입력하세요.';
        }

        lines = [...lines, { guess: num, msg: text }];
        guess = '';  // 입력란 비우기
    }
</script>

<table>
    <tbody>
    <tr>
        <td>맞출 수</td>
        <td>
            <input
                    type="number"
                    bind:value={guess}
                    placeholder="1~99 사이 숫자"
            />
        </td>
    </tr>
    <tr>
        <td colspan="2">
            <button on:click={myclick}>맞춰보기</button>
        </td>
    </tr>
    <tr>
        <td colspan="2">
            {#each lines as result}
                <div>
                     {result.guess} : {result.msg}
                </div>
            {/each}
        </td>
    </tr>
    </tbody>
</table>
