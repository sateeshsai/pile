<script>
  import { T, useFrame } from "@threlte/core";
  import { interactivity, useGltf } from "@threlte/extras";
  import { spring } from "svelte/motion";
  import { OrbitControls, GLTF } from "@threlte/extras";
  import { derived } from "svelte/store";

  import * as Three from "three";

  interactivity();
  const scale = spring(1);
  let dn = Date.now();
  useFrame((state, delta) => {
    dn = Date.now();
  });

  import { Instance, InstancedMesh } from "@threlte/extras";
  import Ground from "./components/Ground.svelte";
  import Side from "./components/Side.svelte";
  import { onMount } from "svelte";
  import {
    Collider,
    AutoColliders,
    BasicPlayerController,
    RigidBody,
  } from "@threlte/rapier";

  let light;

  const gltf = useGltf("/models/fork/scene.gltf");
  const helmet = derived(gltf, (gltf) => {
    if (!gltf || !gltf.nodes["ForkLiftMesh"]) return;
    return gltf.nodes["ForkLiftMesh"];
  });
</script>

<T.PerspectiveCamera makeDefault fov={50} position={[10, 20, 10]}>
  <!-- <T.OrthographicCamera
  makeDefault
  position={[15, 10, 10]}
  zoom={40}
  near={-200}
  rotation={[10, 20, 10]}
> -->
  <OrbitControls
    enableDamping
    maxPolarAngle={Math.PI}
    minPolarAngle={Math.PI / 4}
  />
</T.PerspectiveCamera>
<!-- <InstancedMesh>
  <T.BoxGeometry args={[0.5]} />
  <T.MeshStandardMaterial color="white" />
  <Instance position={[3, 3, 3]} />
  <Instance />
  <Instance />
  <Instance />
  <Instance />
</InstancedMesh> -->
<T.GridHelper args={[500]} />

<Side />
<!-- <Collider
    contactForceEventThreshold={30}
    restitution={0.4}
    shape={"cuboid"}
    args={[0.5, 0.5, 0.5]}
  /> -->
<!-- <RigidBody> -->
<!-- <AutoColliders shape={"ball"}> -->
<BasicPlayerController
  position={[2, 3, 1]}
  speed={3}
  radius={2.5}
  height={5}
  jumpStrength={5}
  on:keyup={(e) => console.log(e)}
>
  <T.Group>
    <!-- <Collider
      contactForceEventThreshold={30}
      restitution={0.4}
      shape={"cuboid"}
      args={[0.5, 0.5, 0.5]}
    /> -->
    <GLTF
      url="/models/fork/scene.gltf"
      scale={1.5}
      position={[0, 0, 0]}
      rotation={[0, 3.1, 0]}
    />
  </T.Group>
</BasicPlayerController>

<!-- </AutoColliders> -->
<!-- </RigidBody> -->
<!-- 
{#if $helmet}
  <T.Group position={[0, 2, 0]}>
    <RigidBody>
      <T.Mesh
        castShadow
        geometry={$helmet.geometry}
        material={$helmet.material}
      />
    </RigidBody>
  </T.Group>
{/if} -->

<T.SpotLight position={[1, 0, 3]} color="red" bind:light />
<T.AmbientLight intensity={0.1} />

<Ground />
