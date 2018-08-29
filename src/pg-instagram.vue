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
      dataUrl: { type: String, default: () => '' },
    },
    data() {
      return {
        embedHtml: '',
      }
    },
    mounted() {
      if (this.dataUrl !== '') {
        axios.get('https://api.instagram.com/oembed/?url=' + this.dataUrl).then(response => {
          this.embedHtml = response.data.html;
          // The response HTML from instagram contains this script tag already,
          // but via v-html it does not get executed so we need to add this element here manually.
          const script = document.createElement('script')
          script.src = '//www.instagram.com/embed.js'
          document.head.appendChild(script)
        });
      }
    },
  };
</script>
