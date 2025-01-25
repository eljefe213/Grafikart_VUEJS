<template>
  <div class="layout">
    <header v-if="$slots.header">
      <slot name="header">1</slot>
    </header>
    <aside>
      <slot name="aside">2</slot>
    </aside>
    <main>
      <slot name="main">3</slot>
    </main>
    <footer>
      <slot name="footer">4</slot>
    </footer>
  </div>
</template>
<style>
.layout {
  display: grid;
  grid-template-columns: 200px 1fr;
}
.layout > * {
  border: solid 1px red;
}
.layout header,
.layout footer {
  grid-column: 1 / -1;
}
</style>