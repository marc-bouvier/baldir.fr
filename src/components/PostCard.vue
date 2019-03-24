<template>
  <div
    v-if="isPostPublished"
    class="post-card content-box"
    :class="{'post-card--has-poster' : post.poster}"
  >
    <div class="post-card__header">
      <g-image
        alt="Cover image"
        v-if="post.coverImage"
        class="post-card__image"
        :src="post.coverImage"
      />
    </div>
    <div class="post-card__content">
      <g-link class="post-card__link" :to="post.path">
        <h2 class="post-card__title" v-html="post.title"/>
      </g-link>
      <p class="post-card__description" v-html="post.description"/>

      <PostMeta class="post-card__meta" :post="post"/>
      <PostTags class="post-card__tags" :post="post"/>
      
    </div>
  </div>
</template>

<script>
import PostMeta from "~/components/PostMeta";
import PostTags from "~/components/PostTags";

export default {
  components: {
    PostMeta,
    PostTags
  },
  props: ["post"],
  computed: {
    isPostPublished() {
      return (
        this.post.published === null ||
        this.post.published === undefined ||
        this.post.published
      );
    }
  }
};
</script>

<style lang="scss">
.post-card {
  margin-bottom: var(--space);
  position: relative;

  &__header {
    margin-left: calc(var(--space) * -1);
    margin-right: calc(var(--space) * -1);
    margin-bottom: calc(var(--space) / 2);
    margin-top: calc(var(--space) * -1);
    overflow: hidden;
    border-radius: var(--radius) var(--radius) 0 0;

    &:empty {
      display: none;
    }
  }

  &__image {
    min-width: 100%;
  }

  &__title {
    margin-top: 0;
  }

  &:hover {
    transform: translateY(-5px);
    box-shadow: 1px 10px 30px 0 rgba(0, 0, 0, 0.1);
  }

  &__tags {
    z-index: 1;
    position: relative;
  }

  &__link {
    text-decoration: none;
  }
}
</style>