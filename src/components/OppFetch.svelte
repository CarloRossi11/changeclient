<script>
  import { onMount } from 'svelte'
  import Card from '../shared/Card.svelte'

  let posts = []

  onMount(async () => {
    const res = await fetch('https://bchangeapi.herokuapp.com/opps')
    const json = await res.json()
    posts = json
    console.log(posts)
  })

</script>

{#each posts as posts}
    <Card>
      <li>{posts.title}</li>
    </Card>
{/each}

<style>

</style>

