<template>
    <Layout>
        <div class="markdown-body">
            <h1 v-html="$page.post.title"/>
            <img :src="$page.post.featuredImage" alt="blog" />
            <div v-html="$page.post.content" />
        </div>
    </Layout>
</template>

<page-query>
query Post ($path: String!) {
  post: post (path: $path) {
    title
    content
    featuredImage
  }
}
</page-query>

<script>
    export default {
        metaInfo() {
            return {
                title: this.$page.post.title
            }
        }
    }
</script>

<style scoped>
.markdown-body {
    box-sizing: border-box;
    min-width: 200px;
    max-width: 980px;
    margin: 0 auto;
    padding: 45px;
}

@media (max-width: 767px) {
    .markdown-body {
        padding: 15px;
    }
}
</style>
