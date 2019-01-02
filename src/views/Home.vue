<template>
  <div class="home wrapper">
    <SearchComponent />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import SearchComponent from '@/components/SearchComponent.vue'// @ is an alias to /src

@Component({
  components: {
    SearchComponent
  },
})
export default class Home extends Vue {}
</script>
<style lang="scss" scoped>
  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0;
    padding: 30px;
    width: 100%;
    box-sizing: border-box;
  }
</style>