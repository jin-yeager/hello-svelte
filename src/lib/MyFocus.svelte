<script>
    let inputEl;

    function focusInput() {
        inputEl.focus();
    }
</script>

<input bind:this={inputEl} type="text" />

<button on:click={focusInput}>
    FOCUS
</button>

