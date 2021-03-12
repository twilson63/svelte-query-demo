<script>
import { useMutation } from '@sveltestack/svelte-query'
const url = 'https://jsonplaceholder.typicode.com/todos'
let title = ''

const mutation = useMutation(newTodo =>
  fetch(url, {
    method: 'POST',
    headers: {'Content-Type': 'application/json'},
    body: JSON.stringify(newTodo)
  })
)


const onSubmit = () => {
  $mutation.mutate({userId: 1, title})
  title = ''
}

</script>
<header>
  <a href="/">Home</a>
	<h1>Todos</h1>
</header>
{#if $mutation.isLoading}
  <p>Adding Todo...</p>
{:else if $mutation.isError}
  <p>Error: {$mutation.error.message}</p>
{:else if $mutation.isSuccess}
  <p>Todo Added Successfully!</p>
{:else}
<form on:submit|preventDefault={onSubmit}>
  <input bind:value={title} id="title" type="text" name="title" placeholder="todo" />
	<button type="submit">Submit</button>
</form>
{/if}

