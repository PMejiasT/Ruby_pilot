<template>
    <div>
    <h1>Default</h1>
    <nav>
      <ul>
        <li>
          <NuxtLink to="/components/TodoList">TodoList</NuxtLink>
        </li>
    </ul>
    </nav>
    <NuxtChild  />
  </div>
</template>
<style scoped>
ul {
  list-style: none;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0;
}
li {
  margin: 0 0.5rem;
  padding: 0.25rem;
  font-size: 1rem;
}
</style>