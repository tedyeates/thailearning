<script lang="ts">
    export let top: string
    export let left: string
    export let rotationBefore: string
    export let rotationAfter: string
    export let arrowRight: string
    export let arrowLength: string
</script>

<div class="icon" style="--top:{top}; --left:{left}; --arrow-length:{arrowLength}">
    <div class="arrow" style="--rotationBefore:{rotationBefore}; --rotationAfter:{rotationAfter}; --right:{arrowRight}"></div>
</div>

<style lang="sass">
    $arrow-color: #000

    .arrow::before
        transform: var(--rotationBefore)

    .arrow::after
        transform: var(--rotationAfter)

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
        right: var(--right)
        background-color: $arrow-color

    .arrow::after
        top: -12px

    .arrow::before
        top: 12px

    .icon
        position: absolute
        top: var(--top)
        left: var(--left)
        transform: translate(-50%,-50%)
        width: var(--arrow-length)
        height: 60px
        cursor: pointer
</style>