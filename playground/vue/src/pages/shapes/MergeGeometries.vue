<script setup>
import { MergeGeometries, OrbitControls } from '@tresjs/cientos'
import { TresCanvas } from '@tresjs/core'
</script>

<template>
  <TresCanvas
    window-size
    clear-color="#111"
  >
    <TresPerspectiveCamera
      :position="[0, 0, 7]"
      :fov="45"
      :aspect="1"
      :near="0.1"
      :far="1000"
    />
    <TresMesh>
      <MergeGeometries>
        <TresBoxGeometry :args="[1, 4, 1]" />
        <TresBoxGeometry :args="[4, 1, 1]" />
      </MergeGeometries>
      <TresMeshStandardMaterial />
    </TresMesh>
    <OrbitControls />
    <TresDirectionalLight
      :position="[0, 2, 4]"
      :intensity="2"
    />
    <TresAmbientLight />
  </TresCanvas>
</template>
