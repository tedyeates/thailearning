<script lang="ts">
	import AnswerBox from "./AnswerBox.svelte";
    import Arrow from "./Arrow.svelte";

    export let top: string
    export let left: string
    export let direction: string
    export let arrowLength: string = "15rem"
    export let answer: string
    export let name: string

    const rotateForward = "rotate(45deg)"
    const rotateBackward = "rotate(-45deg)"

    let rotationBefore = rotateForward
    let rotationAfter = rotateBackward

    let arrowRight = "11.5rem"
    let arrowLengthDirection = arrowLength
    let inputShift = "2rem"
    if (direction === "right") {
        rotationBefore = rotateBackward
        rotationAfter = rotateForward
        arrowRight = "-1rem"
        arrowLengthDirection = `-${arrowLengthDirection}`
        inputShift = `-6rem`
    }

    let position = {
        top,
        left,
        rotationBefore,
        rotationAfter,
        arrowRight, arrowLength
    }
</script>

<div>
    <Arrow {...position} />
    <AnswerBox 
        {top} {left} {arrowRight} {arrowLengthDirection} {inputShift}
        {answer} {name}
    />
</div>