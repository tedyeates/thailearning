<script lang="ts">
	import AnswerBox from "./AnswerBox.svelte";
    import Arrow from "./Arrow.svelte";
	import type { ArrowType } from "../util/types";

    export let answer: string
    export let name: string
    export let arrow: ArrowType
    export let arrowLength: string = "15rem"

    $: console.log("updating")

    const rotateForward = "rotate(45deg)"
    const rotateBackward = "rotate(-45deg)"

    let rotationBefore: string
    let rotationAfter: string
    let arrowRight: string
    let arrowLengthDirection: string
    let inputShift:  string
    $: if (arrow.direction === "right") {
        rotationBefore = rotateBackward
        rotationAfter = rotateForward
        arrowRight = "-1rem"
        arrowLengthDirection = `-${arrowLength}`
        inputShift = `-6rem`
        console.log(name)
        console.log(arrow.direction)
        console.log(inputShift)
    } 
    else {
        rotationBefore = rotateForward
        rotationAfter = rotateBackward
        arrowRight = "11.5rem"
        arrowLengthDirection = arrowLength
        inputShift = `2rem`
        console.log(name)
        console.log(arrow.direction)
        console.log(inputShift)
    }


    $: position = {
        top: arrow.top,
        left: arrow.left,
        rotationBefore,
        rotationAfter,
        arrowRight, arrowLength
    }

    console.log(answer)
</script>

<div>
    <Arrow {...position} />
    <AnswerBox
        on:answer 
        top={arrow.top} 
        left={arrow.left} 
        {arrowRight} {arrowLengthDirection} {inputShift}
        {answer} {name}
    />
</div>