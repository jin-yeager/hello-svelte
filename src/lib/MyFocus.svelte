<script>
let myobj

const myclick = () => {
    myobj.focus()
}

</script>

<input type="text" bind:this={myobj}/>
<button onclick={myclick} >FOCUS</button>