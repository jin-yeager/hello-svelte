<script>
    import { onMount } from 'svelte';

    let com = [];
    let guess = '';
    let logs = [];

    onMount(() => {
        while (com.length < 3) {
            const ran = Math.floor(Math.random() * 9) + 1;
            if (!com.includes(ran)) com.push(ran);
        }
        console.log('정답:', com);
    });

    function myclick() {
        if (guess.length !== 3) return;
        let strike = 0, ball = 0;

        for (let i = 0; i < 3; i++) {
            const n = +guess[i];  // 넘버링
            if (n === com[i]) strike++;
            else if (com.includes(n)) ball++;
        }

        logs = logs.concat(`${guess} - ${strike}S ${ball}B`);
        const tried = guess;
        guess = '';

        if (strike === 3) {
            alert(`${tried} 축하합니다.`);
        }
    }
</script>

<main>
    <table border="1">
        <tbody>
        <tr>
            <td>맞출 수</td>
            <td><input type="text" bind:value={guess} /></td>
        </tr>
        <tr>
            <td colspan="2">
                <input type="button" value="맞춰보기" on:click={myclick} />
            </td>
        </tr>
        <tr>
            <td colspan="2">
                <div>
                    {#each logs as log}
                        <span>{log}<br/></span>
                    {/each}
                </div>
            </td>
        </tr>
        </tbody>
    </table>
</main>

<style>
    input[type=text] {
        width: 40px;
    }

    div {
        height: 170px;
    }

    table, tr, td {
        border: 1px solid aqua;
    }
</style>
