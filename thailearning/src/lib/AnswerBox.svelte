<script lang="ts">
    import {onMount} from 'svelte'

    export let top: string
    export let left: string
    export let arrowRight: string
    export let arrowLengthDirection: string
    export let inputShift: string
    export let answer: string
    export let name: string

    let label = ""
    let attempts = 0
    let showInput = true
    let isCorrect = false
    function checkAnswer(event: Event){
        let inputElement = event.target as HTMLInputElement
        if (inputElement.value === answer){
            label = `${answer}`
            isCorrect = true
            showInput = false
            return
        }

        if (attempts > 1) {
            label = `${answer}`
            showInput = false
            return
        }
        attempts++

        label = `Incorrect Answer, attempt ${attempts}`
    }

</script>

<div class="answer" style="
    --top:{top}; --left:{left}; --right:{arrowRight}; 
    --arrow-length:{arrowLengthDirection};
    --input-shift:{inputShift}
">
    {#if showInput}
        <input id={name} on:change={(e) => checkAnswer(e)} />
    {/if}
    
    <label class:correct={isCorrect} for={name}>{label}</label>
</div>

<style lang="sass">
    .answer
        position: absolute
        top: calc(var(--top) - .5rem)
        left: calc(var(--left) - var(--right) + var(--arrow-length) + var(--input-shift))
        width: 12rem

        label
            color: red

        label.correct
            color: green

        input
            display: block
            width: 100%
</style>