<template>
  <div class="paragraph paragraph--instagram">
    <slot :name="$slots.title ? 'title': 'default'" />
    <div
      class="instagram-post"
      ref="igPost"
    />
  </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'PgInstagram',
  props: {
    src: {
      type: String,
      required: true
    }
  },
  mounted () {
    axios
      .get('https://api.instagram.com/oembed/?url=' + this.src)
      .then((response) => {
        this.init(response.data.html)
      })
  },
  methods: {
    init (postMarkup) {
      this.$refs.igPost.innerHTML = postMarkup
      this.process();
    },
    process () {
      if (window.instgrm) {
        // api already loaded just process the new post.
        window.instgrm.Embeds.process()
      }
    }
  }
}
</script>
