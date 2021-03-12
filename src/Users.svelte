<script>
import {useQuery} from '@sveltestack/svelte-query'
const url = 'https://jsonplaceholder.typicode.com/users'

const queryResult = useQuery('users', () => 
  fetch(url).then(res => res.json())
)


</script>
<header>
  <a href="/">Home</a>
  <h1>Users</h1>
</header>
{#if $queryResult.isLoading}
  Loading...
{:else if $queryResult.isError}
  Error {$queryResult.error.message}
{:else}
  <ul>
    {#each $queryResult.data as user}
    <li>{user.username} - {user.email}</li>
    {/each}
  </ul>
{/if}
