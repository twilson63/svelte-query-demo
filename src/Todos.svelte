<script>
import { useMutation } from '@sveltestack/svelte-query'
const url = 'https://jsonplaceholder.typicode.com/todos'

</script>
<header>
	<h1>Todos</h1>
</header>
<form>
  <input type="text" name="title" placeholder="todo" />
	<button type="submit">Submit</button>
</form>

