<script lang="ts">
    import P5 from "p5-svelte";
    import type { Sketch } from "p5-svelte";

    // import { Vector } from "p5"; // This doesn't work, p5 not found: "Internal server error: Failed to resolve import "p5" from "src/routes/+page.svelte". Does the file exist?"
    // import { Vector as p5Vector } from "p5"; // This doesn't work. Same message.

    import type { Vector } from "p5";

    let width = 55;
    let height = 55;

    const sketch: Sketch = (p5) => {
        p5.setup = () => {
            p5.createCanvas(400, 400);
            const myVector: Vector = p5.createVector(100, 100);
            console.log(myVector.x);
        };

        p5.draw = () => {
            p5.ellipse(p5.width / 2, p5.height / 2, width, height);
        };
    };

    // This isn't working, "ReferenceError: Vector is not defined"
    class Node extends Vector {
        constructor(x, y) {
            super(x, y);
            this.x = x;
            this.y = y;
        }
    }
</script>

<label>
    Width
    <input type="range" bind:value={width} min="100" max="1000" step="0.01" />
    {width}
</label>

<label>
    Height
    <input type="range" bind:value={height} min="100" max="1000" step="0.01" />
    {height}
</label>

<P5 {sketch} />
