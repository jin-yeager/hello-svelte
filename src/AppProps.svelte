<script>
import MyInput from "./lib/MyInput.svelte";

let obj = null
let value = "hello"

const myclick = () => {
    obj.value = "bye"
    value = "bye"
}

</script>

<main>

    <input type="text" value="hello" bind:this={obj} /><br/>
    <MyInput {value} /><br/>
    <button onclick={myclick}>CHANGE TEXT</button>

</main>

<style>

</style>
