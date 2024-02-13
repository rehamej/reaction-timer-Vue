<template>
  <div class="Results">
    <template v-if="score <= 1000">
      <!-- <p>You win!</p> -->
      <p>A snail could've done this faster</p>
    </template>
    <template v-else>
      <!-- <p>A snail is faster than you!</p> -->
      <p>womb womb</p>
    </template>
    <!-- <template v-else>
      <p>womb womb</p>
    </template> -->
  </div>
</template>

<script>
export default {
  props: ['score'] //هذا اللي خلاه ما يشتغل عشان ماحطيت البروب ف ماعرف الكود هنا عن ايش انا اتكلم
};
</script>

<style>
.Results {
  font-size: 20px;
  margin-top: 20px;
}
</style>
