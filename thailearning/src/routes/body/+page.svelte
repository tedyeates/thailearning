<script lang="ts">
	import TransLabel from '$lib/Label/TransLabel.svelte'
	import { onMount } from 'svelte'
    import type { TranslationType } from '$lib/util/types'
	import { translations } from '$lib/util/constants';

    let src = "phil/PhilHair.jpg"

    console.log(translations)

    let questionPool = [...translations]

    let history: Array<TranslationType> = []

    let challengeComplete = false
    let choosenQuestion: TranslationType
    function chooseNextQuestion(){
        console.log("choosing next question")
        console.log(questionPool)
        if(!questionPool || questionPool.length === 0) {
            challengeComplete = true
            return
        }

        choosenQuestion = questionPool.splice(Math.floor(Math.random()*translations.length), 1)[0]
        history = [
            ...history, 
            choosenQuestion
        ]
        console.log(choosenQuestion)
    }

    function showAll(){
        history = [...translations]
    }

    onMount(() => {
        chooseNextQuestion()
    })
</script>

<center>
    <section>
        <header>
            <h1>Face</h1>
        </header>
        <div class="face-image">
            {#if challengeComplete}
            Challenge Completed
            {:else}
                <button class="show-all" on:click={showAll}>Show All</button>
                <img {src} alt="Face" />
                <div>
                    {#each history as translation}
                        <TransLabel 
                            on:answer={chooseNextQuestion}
                            answer={translation.thai}
                            name={translation.english}
                            arrow={translation.arrow}
                        />   
                    {/each}
                </div>
            {/if}
        </div>
    </section>
</center>

<style lang="sass">
    $arrow-color: #000
    $arrow-length: 15rem

    .show-all
        position: absolute
    
    .face-image img
        max-height: 80vh

    .face-image
        position: relative
        width: fit-content
        margin-right: auto
        margin-left: auto

    .arrow
        position: absolute
        top: 25px
        width: 90%
        height: 10px
        background-color: $arrow-color

    .arrow::after, .arrow::before
        content: ''
        position: absolute
        width: 20%
        height: 10px
        right: 11.5rem
        background-color: $arrow-color

    .arrow::after
        top: -12px

    .arrow::before
        top: 12px

    .icon
        position: absolute
        transform: translate(-50%,-50%)
        width: $arrow-length
        height: 60px
        cursor: pointer



</style>