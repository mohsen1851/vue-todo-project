<template>
  <li class="nav-item mx-1" role="presentation">
    <button class="nav-link" :class="{active}" id="pills-home-tab" data-bs-toggle="pill"
            data-bs-target="#pills-home" type="button" role="tab" aria-controls="pills-home"
            aria-selected="true">{{t}}<span class="badge bg-secondary mx-2">{{count}}</span></button>
  </li>
</template>

<script>
export default {
  name: "Tab",
  props:['count','t','active']
}
</script>

<style scoped>

</style>