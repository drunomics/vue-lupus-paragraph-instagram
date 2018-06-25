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
      this.getEmbedHtml();
    },
    methods: {
      getEmbedHtml() {
        this.$http.get('https://api.instagram.com/oembed/?url=' + this.dataInstagramUrl).then(response => {
          this.embedHtml = JSON.parse(response.body).html;
        })
      }
    },
  };
</script>
