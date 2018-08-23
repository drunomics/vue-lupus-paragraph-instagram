<template>
  <div class="paragraph paragraph--instagram">
    <div 
      class="paragraph__field-media"
      v-html="embedHtml"
    >
    </div>
  </div>
</template>
<script>
  import axios from 'axios';
  export default {
    name: 'PgInstagram',
    props: {
      dataInstagramUrl: { type: String, default: () => '' },
    },
    data() {
      return {
        embedHtml: '',
      }
    },
    mounted() {
      if (this.dataInstagramUrl !== '') {
        axios.get('https://api.instagram.com/oembed/?url=' + this.dataInstagramUrl).then(response => {
          this.embedHtml = response.data.html;
        });
      }
    },
  };
</script>
