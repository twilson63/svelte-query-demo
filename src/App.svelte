<script>
import { QueryClient, QueryClientProvider } from '@sveltestack/svelte-query'
import { Route } from 'tinro'
import Users from './Users.svelte'
import Todos from './Todos.svelte'
import Posts from './Posts.svelte'

const queryClient = new QueryClient()

</script>
<QueryClientProvider client={queryClient}>
  <Route path="/">
    <h1>Svelte Query Demo</h1>
    <div>
      <a href="/users">Users</a>
      <a href="/todos">Todos</a>
      <a href="/posts">Posts</a>
    </div>
  </Route>
  <Route path="/users">
    <Users />
  </Route>
  <Route path="/todos">
    <Todos />
  </Route>
  <Route path="/posts">
    <Posts />
  </Route>
</QueryClientProvider>
  
