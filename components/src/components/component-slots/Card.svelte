<script>
  // PROP
  // export let content;
</script>

<!-- BASIC  -->
<!-- <div class={`card`}>{content}</div> -->

<div class={`card`}>
  <!-- SLOT -->
  <!-- <slot /> -->

  <!-- SLOT WITH DEFAULT CONTENT -->
  <!-- <slot>Default content</slot> -->
  <div class="card-header"><slot name="header" /></div>
  <div class="card-content"><slot name="content">Default content</slot></div>
  {#if $$slots.footer}
    <hr />
    <div class="card-footer"><slot name="footer" /></div>
  {/if}
</div>

<style>
  .card {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    padding: 16px;
    margin-bottom: 20px;
    width: 200px;
  }

  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  }
</style>
