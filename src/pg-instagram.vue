<template>
  <div class="paragraph paragraph--instagram">
    <div class="paragraph__field-media">
      <slot
        name="field_media"
        v-html="embedHtml"
      >
      </slot>
      <slot />
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
    created() {
      if (this.dataInstagramUrl !== '') {
        axios.get('https://api.instagram.com/oembed/?url=' + this.dataInstagramUrl).then(response => {
          this.embedHtml = response.html;
        });
      }
    },
  };
</script>
