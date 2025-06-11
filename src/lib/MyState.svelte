<script>
    import { vo } from "../store.js";

    const myup = () => {
        $vo.cnt++
    };

    const mydw = () => {
        $vo.cnt--
    };
    const myyh = () => {
        $vo.nm = "영희";
    };
    const mycs = () => {
        $vo.nm = "철수";
    };
</script>

{$vo.cnt},{$vo.nm}
<button on:click={myup}>UP</button>
<button on:click={mydw}>DW</button>
<button on:click={myyh}>YH</button>
<button on:click={mycs}>CS</button>
