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
        // Remove the script from the markup.
        const postMarkup = response.data.html.split('<script').shift()
        this.init(postMarkup)
      })
  },
  methods: {
    init (postMarkup) {
      this.$refs.igPost.innerHTML = postMarkup
      this.process()
    },
    process () {
      if (!window.instgrm) {
        // Load the apy, processing happens on load
        const apiScript = document.createElement('script')
        apiScript.async = 1
        apiScript.src = 'https://www.instagram.com/embed.js'
        document
          .getElementsByTagName('head')[0]
          .appendChild(apiScript)
      } else {
        // api already loaded just process the new post.
        window.instgrm.Embeds.process()
      }
    }
  }
}
</script>
