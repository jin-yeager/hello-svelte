<script>
    import empty from '../assets/0.png';
    import black from '../assets/1.png';
    import white from '../assets/2.png';

    // 19x19 바둑판 배열 초기화
    let arr2D = [
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
        [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ]
    ];

    // 이미지 배열
    const images = [empty, black, white];

    // 흑돌/백돌 전환 플래그 (true: 흑돌 차례, false: 백돌 차례)
    let flag_bw = true;
    let flag_end = false;

    // 각 방향으로 같은 돌이 몇 개 연속되는지 계산하는 함수들
    function getUP(i, j, stone) {
        let ret = 0;
        try {
            while (true) {
                i--;
                if (arr2D[i][j] == stone) ret++;
                else return ret;
            }
        } catch (error) { return ret; }
    }
    function getDW(i, j, stone) {
        let ret = 0;
        try {
            while (true) {
                i++;
                if (arr2D[i][j] == stone) ret++;
                else return ret;
            }
        } catch (error) { return ret; }
    }
    function getRI(i, j, stone) {
        let ret = 0;
        try {
            while (true) {
                j++;
                if (arr2D[i][j] == stone) ret++;
                else return ret;
            }
        } catch (error) { return ret; }
    }
    function getLE(i, j, stone) {
        let ret = 0;
        try {
            while (true) {
                j--;
                if (arr2D[i][j] == stone) ret++;
                else return ret;
            }
        } catch (error) { return ret; }
    }
    function getUR(i, j, stone) {
        let ret = 0;
        try {
            while (true) {
                i--;
                j++;
                if (arr2D[i][j] == stone) ret++;
                else return ret;
            }
        } catch (error) { return ret; }
    }
    function getUL(i, j, stone) {
        let ret = 0;
        try {
            while (true) {
                i--;
                j--;
                if (arr2D[i][j] == stone) ret++;
                else return ret;
            }
        } catch (error) { return ret; }
    }
    function getDR(i, j, stone) {
        let ret = 0;
        try {
            while (true) {
                i++;
                j++;
                if (arr2D[i][j] == stone) ret++;
                else return ret;
            }
        } catch (error) { return ret; }
    }
    function getDL(i, j, stone) {
        let ret = 0;
        try {
            while (true) {
                i++;
                j--;
                if (arr2D[i][j] == stone) ret++;
                else return ret;
            }
        } catch (error) { return ret; }
    }

    // 클릭 시 바둑돌 놓기 로직
    function myclick(i, j) {
        if(flag_end == true){
            return;
        }

        // 이미 놓여진 자리면 무시
        if (arr2D[i][j] > 0) return;

        // 돌 놓기 및 현재 차례 설정
        let stone = flag_bw ? 1 : 2;
        arr2D[i][j] = stone;

        // 8방향 탐색 결과 로그 출력
        let up = getUP(i, j, stone);
        let dw = getDW(i, j, stone);
        let ri = getRI(i, j, stone);
        let le = getLE(i, j, stone);

        let ur = getUR(i, j, stone);
        let ul = getUL(i, j, stone);
        let dr = getDR(i, j, stone);
        let dl = getDL(i, j, stone);

        let d1 = dl + ur + 1;
        let d2 = le + ri + 1;
        let d3 = dr + ul + 1;
        let d4 = up + dw + 1;

        if(d1 == 5 || d2 == 5 || d3 == 5 || d4 == 5){
            if(flag_bw == true){
                setTimeout(() => alert('흑돌 승리'), 0);
            }
            else{
                setTimeout(() => alert('백돌 승리'), 0);
            }
            flag_end = true;
        }

        arr2D = arr2D;
        flag_bw = !flag_bw;
    }

    function fn_reset(){
        for(let i = 0; i < 19; i++){
            for(let j = 0; j < 19; j++){
                arr2D[i][j] = 0;
            }
        }
        flag_bw = true;
        flag_end = false;
        arr2D = arr2D;
    }
</script>

<style>
    table {
        border-collapse: collapse;
    }
    td {
        padding: 0;
    }
    img {
        display: block;
    }
</style>

<a href="#" on:click|preventDefault={fn_reset}>reset</a>
<table>
    {#each arr2D as row, i}
        <tr>
            {#each row as cell, j}
                <td>
                    <img src={images[cell]} alt="{i},{j}" on:click={() => myclick(i, j)} />
                </td>
            {/each}
        </tr>
    {/each}
</table>