<script lang="ts" setup>
import type { BufferGeometry } from 'three'
import { shallowRef, useSlots, watchEffect } from 'vue'
import * as BufferGeometryUtils from 'three/examples/jsm/utils/BufferGeometryUtils.js'

const mergedGeometry = shallowRef()
const slots = useSlots()

watchEffect(() => {
  if (mergedGeometry.value) {
    if (slots.default) {
      const geometries = slots.default().map(slot => slot.el) as BufferGeometry[]
      mergedGeometry.value.geometry.dispose()
      mergedGeometry.value.geometry = BufferGeometryUtils.mergeGeometries(geometries)
    }
  }
})

defineExpose({
  instance: mergedGeometry,
})
</script>

<template>
  <TresMesh ref="mergedGeometry">
    <slot>
      <TresBoxGeometry :args="[1, 1, 1]" />
    </slot>
  </TresMesh>
</template>
