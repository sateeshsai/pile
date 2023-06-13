<script>
  import { T, useFrame } from "@threlte/core";
  import { OrbitControls, GLTF } from "@threlte/extras";
  import {
    AutoColliders,
    Collider,
    CollisionGroups,
    RigidBody,
  } from "@threlte/rapier";
  import { BoxGeometry, MeshStandardMaterial } from "three";
</script>

<!-- FRAME -->
<RigidBody>
  <AutoColliders shape={"cuboid"}>
    <T.Group position={[10, 0, 10]}>
      <T.Mesh position={[0, 2, 0]} castShadow>
        <T.BoxGeometry args={[0.2, 4, 4]} />
        <T.MeshStandardMaterial color="red" />
      </T.Mesh>
      <T.Mesh position={[2.1, 2.1, 1.9]} castShadow>
        <T.BoxGeometry args={[4, 3.8, 0.2]} />
        <T.MeshStandardMaterial color="orange" />
      </T.Mesh>
      <T.Mesh position={[2.1, 2.1, -1.9]} castShadow>
        <T.BoxGeometry args={[4, 3.8, 0.2]} />
        <T.MeshStandardMaterial color="purple" />
      </T.Mesh>
      <T.Mesh position={[2.1, 0.1, 0]} castShadow>
        <T.BoxGeometry args={[4, 0.2, 4]} />
        <T.MeshStandardMaterial color="blue" />
      </T.Mesh>
    </T.Group>
  </AutoColliders>
</RigidBody>
