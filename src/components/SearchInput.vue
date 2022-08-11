<template>
  <form
    onSubmit=""
    className="flex py-1 border-gray-200 border-b mb-4 md:border md:mb-6 md:rounded-lg md:mr-6"
  >
    <input type="text" placeholder="Buscar por nombre..." className="border-none
    w-11/12 rounded" value={inputValue} onChange={(e) =>
    setInputValue(e.target.value)} />
    <button type="submit">
      <SearchIcon height="20" width="20" className="mx-2" />
    </button>
  </form>
</template>

<script>
export default {
  name: "SearchInput",
};
</script>

<style scoped>
.searchInputComp {
}
</style>
