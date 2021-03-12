<script>
	import { Query } from '@sveltestack/svelte-query'
  const url = p => `https://jsonplaceholder.typicode.com/posts?_page=${p}`

  let page = 1
  const fetchPosts = (page = 1) => fetch(url(page))
    .then(res => res.json())

  $: queryOptions = {
    queryKey: ['posts', page],
    queryFn: () => fetchPosts(page),
    keepPreviousData: true
  }

</script>
<header>
  <a href="/">Home</a>
	<h1>Posts</h1>
</header>
<Query options={queryOptions}>
  <div slot="query" let:queryResult>
    {#if queryResult.isLoading}
      Loading...
    {:else if queryResult.isError}
      <span>Error: {queryResult.error.message}</span>
    {:else}
      {#each queryResult.data as post}
      <p>{post.title}</p>
      {/each}
    {/if}
  </div>
</Query>
<span>Current Page: {page}</span>
<div>
  <button disabled={page === 1} on:click={() => {
    if (page > 1) {
      page = page - 1
    }
  }}>Previous</button>
<button on:click={() => page = page + 1}>Next</button>
</div>
