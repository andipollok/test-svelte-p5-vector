<script lang="ts">
    import p5 from "p5";
    import P5 from "p5-svelte";
    import type { Sketch } from "p5-svelte";

    let width = 55;
    let height = 55;

    const sketch: Sketch = (p5) => {
        p5.setup = () => {
            p5.createCanvas(400, 400);

            const myVector: Vector = p5.createVector(100, 100); // that works
            console.log(myVector.x);

            const myNode: Node = new Node(100, 100); // that works
            console.log(myNode.x); // 200
        };

        p5.draw = () => {
            p5.ellipse(p5.width / 2, p5.height / 2, width, height);
        };
    };

    // Here's the problem. This isn't working, "ReferenceError: Vector is not defined". Also using p5.Vector doesn't work.
    class Node extends p5.Vector {
        constructor(x, y) {
            super(x, y);
            this.x = x;
            this.y = y;
            this.mult(2);
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
