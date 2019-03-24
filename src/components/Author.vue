<template>
	<div class="author">

		<g-image alt="Marc Bouvier Photo" class="author__image" src="~/assets/images/marc_bouvier_400x400.jpg" width="180" height="180" blur="5" />

		<h1 v-if="showTitle" class="author__site-title">
			{{ $static.metaData.siteName }}
		</h1>

		<p class="author__intro">
			Hi! I am Marc, Software Craftsman. I am always learning to improve my craft and trying new ways to add value to products.
		</p>

		<p class="author__links">
			<a href="//twitter.com/marcbouvier_">Follow on Twitter</a>
			<a href="//github.com/marc-bouvier">GitHub</a>
			<a href="mailto:m.bouvier.dev@gmail.com">Email</a>
		</p>

	</div>
</template>

<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>

<script>
export default {
	props: ['showTitle']
}
</script>

<style lang="scss">
.author {
	margin: 0 auto;
	max-width: 500px;
	text-align: center;
	padding: calc(var(--space) / 2) 0;

	&__image {
		border-radius: 100%;
		width: 90px;
		height: 90px;
		margin-bottom: 1em;
	}

	&__intro {
		opacity: .8;
	}

	&__site-title {
		font-size: 1.5em;
	}

	&__links {
		margin-top: -.5em;
		a {
			margin: 0 .5em;
		}
	}
}
</style>