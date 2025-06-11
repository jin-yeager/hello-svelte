<script>
    let count = 0;

    $: document.title = `Count is ${count}`;

    const myclick = () => {
        count++;
    };
</script>

SIDE EFFECT<br />
{count}
<button on:click={myclick}>증가</button>
