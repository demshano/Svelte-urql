<!-- <script>
    import { queryStore, gql, getContextClient } from '@urql/svelte';
  
    const todos = queryStore({
      client: getContextClient(),
      query: gql`
            query{
            users{
                ID
                Age
                Name
            }
        }
      `,
    });
    console.log("data", JSON.stringify(todos))
  </script>
  
  {#if $todos.fetching}
  <p>Loading...</p>
  {:else if $todos.error}
  <p>Oh no... {$todos.error.message}</p>
  {:else}
  {todos}
  {/if} -->

  <script>
    import { queryStore, gql, getContextClient } from '@urql/svelte';
  
    // Define the GraphQL query
    const GET_USERS = gql`
      query {
        users {
          ID
          Age
          Name
        }
      }
    `;
  
    // Fetch data using the queryStore
    const todos = queryStore({
      client: getContextClient(),
      query: GET_USERS,
    });
  
    // Access the data property of the todos store
    $: userData = $todos.data;
  </script>
  
  {#if $todos.fetching}
    <p>Loading...</p>
  {:else if $todos.error}
    <p>Error: {$todos.error.message}</p>
  {:else}
    <!-- Display the JSON data -->
    <pre>{JSON.stringify(userData, null, 2)}</pre>
  {/if}
  

 
  