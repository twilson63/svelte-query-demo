<script>
	import { Query } from '@sveltestack/svelte-query'
  const url = p => `https://jsonplaceholder.typicode.com/posts?_page=${p}`


  let page = 1

</script>
<header>
  <a href="/">Home</a>
	<h1>Posts</h1>
</header>
<span>Current Page: {page}</span>
<div>
  <button disabled={page === 1} on:click={() => {
    if (page > 1) {
      page = page - 1
    }
  }}>Previous</button>
<button on:click={() => page = page + 1}>Next</button>
</div>
