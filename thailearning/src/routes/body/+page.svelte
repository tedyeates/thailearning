<script lang="ts">
	import TransLabel from '$lib/TransLabel.svelte';

    let src = "phil/PhilHair.jpg"
    
    type Translation = {
        english: string
        thai: string
        arrow: {
            top: string
            left: string
            direction: string
        }
    }

    let translations:Array<Translation> = [
        {
            english: "eye",
            thai: "ตา",
            arrow: {
                top: "37%",
                left: "85%",
                direction: "left"
            }
        },
        {
            english: "eyebrow",
            thai: "คิ้ว",
            arrow: {
                top: "26%",
                left: "-10%",
                direction: "right"
            }
        }
    ]
</script>

<center>
    <section>
        <header>
            <h1>Face</h1>
        </header>
        <div class="face-image">
            <img {src} alt="Face" />
            <div>
                {#each translations as translation}
                    <TransLabel 
                        answer={translation.thai} 
                        name={translation.english}
                        {...translation.arrow} 
                    />   
                {/each}
            </div>
        </div>
    </section>
</center>

<style lang="sass">
    $arrow-color: #000
    $arrow-length: 15rem
    
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