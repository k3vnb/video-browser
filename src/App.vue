<template>
  <div>
    <SearchBar></SearchBar>
    Hello from Vue video-browser app
  </div>
</template>

<script>
  import SearchBar from './components/SearchBar';
  export default {
    name: 'App',
    components: {
      //es6 says, since the keyvalue pairs are identical, you can just write SearchBar, but for clarity sake I included both key & value
      SearchBar: SearchBar
    }
  };
</script>
