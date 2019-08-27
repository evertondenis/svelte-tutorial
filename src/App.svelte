<script>
  import Form from "./Form.svelte";
  import Fetch from "./Fetch.svelte";

  let searchTerm;

  function handleSubmit() {
    const { value } = this.elements.search;
    searchTerm = value;
  }
</script>

<Fetch {searchTerm} let:data>
  <h1>A list of links</h1>
  <Form {handleSubmit} />
  <ul>
    {#each data as link}
      <li>
        <a href={link.url} target="_blank" rel="norefferer">{link.title}</a>
      </li>
    {/each}
  </ul>

</Fetch>
