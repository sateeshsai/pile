<script lang="ts">
  import { T } from "@threlte/core";
  import { AutoColliders } from "@threlte/rapier";
</script>

<T.Group position={[0, -0.1, 0]}>
  <AutoColliders shape={"cuboid"}>
    <T.Mesh receiveShadow>
      <T.BoxGeometry args={[200, 0.1, 200]} />
      <T.MeshStandardMaterial color="white" />
    </T.Mesh>
  </AutoColliders>
</T.Group>
