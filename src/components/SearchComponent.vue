<template>
  <div class="searchComponent">
    <div class="search">
      <label for="search__input" class="search__label">Search</label>
      <input id="search__input"
             class="search__input"
             name="search__input"
             v-model="searchValue"
             @input="handleInput"/>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import axios  from 'axios';
import debounce from 'lodash/debounce';

const API = 'https://images-api.nasa.gov/search';

@Component
export default class SearchComponent extends Vue {
  searchValue: string = '';

  handleInput() {
    console.log('handle input');
    debounce(() => {
      console.log('debounce');
      this.getRequest();
    }, 500);
  }

  getRequest() {
    axios.get(`${API}?q=${this.searchValue}&media_type=image`)
      .then((response) => {
        console.log(response);
      })
      .catch((error) => {
        console.log(error);
      });
  }
}
</script>

<style scoped lang="scss">
  .search {
    width: 250px;
    display: flex;
    flex-direction: column;

    &__label {
      text-align: left;
      font-size: 14px;
      font-family: Montserrat, sans-serif;
    }

    &__input {
      height: 30px;
      border: 0;
      border-bottom: 1px solid black;

      &:focus {
        outline: none;
      }
    }
  }
</style>