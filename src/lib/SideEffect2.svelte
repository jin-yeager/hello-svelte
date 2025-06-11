<script>
    let count = 0;

    $effect(()=> {
        console.log(`count가 ${count}로 변경되었습니다.`);
    });

    const myclick = () => {
        count++;
    };
</script>

SIDE EFFECT<br />
{count}
<button onclick={myclick}>증가</button>

