<script>
  import { Canvas } from "@threlte/core";
  import Scene from "./scene/Scene.svelte";
  import { World, Debug } from "@threlte/rapier";
</script>

<div class="scene-wrapper">
  <Canvas>
    <World>
      <!-- <Debug /> -->
      <Scene />
    </World>
  </Canvas>
</div>

<style>
  .scene-wrapper {
    box-sizing: border-box;
    border: 1px solid red;
    min-height: 100vh;
    min-width: 100vw;
    position: absolute;
  }
</style>
