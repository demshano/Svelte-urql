<!-- App.svelte -->
<script>
   
    import TodoList from '../lib/components/TodoList.svelte';

    import { Client, setContextClient, cacheExchange, fetchExchange } from '@urql/svelte';

const client = new Client({
  url: 'http://localhost:3000/query',
  exchanges: [cacheExchange, fetchExchange],
});

setContextClient(client);
  
  </script>
  
  <main>
    <h1>Todo App</h1>
   
    <TodoList />
  </main>
  
 
  