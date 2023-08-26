<script>
    import { base } from '$app/paths';

    let isRotated = false;
    let rotationComplete = true;

    async function toggleRotation() {
        if (rotationComplete) {
            rotationComplete = false;
            isRotated = !isRotated;

            const image = document.querySelector('.rotate-icon');
            image.classList.toggle('rotate');

            await image.animate(
                [
                    { transform: 'rotate(0deg)' },
                    { transform: 'rotate(360deg)' }
                ],
                {
                    duration: 1000,
                    easing: 'ease-out',
                    fill: 'forwards'
                }
            ).finished;

            isRotated = !isRotated;
            rotationComplete = true;
        }
    }
</script>

<p>
    <img class="rotate-icon {isRotated ? 'rotate' : ''}"
         src={`${base}/icon.png`}
         alt="Deformed penguin illustration"
         on:click={toggleRotation}
    >
</p>

<style>
.rotate-icon {
    border-radius:50%;
    width: 75px;
    height: 75px;
}
</style>
