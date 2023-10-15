<script>
  import { onMount } from "svelte";

  let posts = [];

  onMount(async () => {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts");
    posts = await response.json();
    console.log("posts >>> ", posts);
  });
</script>

{#each posts as post (post.id)}
  <div>
    <h3>{post.id}. {post.title}</h3>
    <p>{post.body}</p>
    <hr />
  </div>
{:else}
  <p>Loading...</p>
{/each}
