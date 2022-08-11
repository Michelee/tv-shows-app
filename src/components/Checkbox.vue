<template>
  <div class="checkboxComp">
    <label :for="name">
      <input type="checkbox" :id="name" :name="name" :value="value" />
      {{ label }}
    </label>
  </div>
</template>

<script>
export default {
  name: "CheckboxComp",
  props: {
    name: String,
    value: String,
    label: String,
  },
};
</script>

<style scoped>
.checkboxComp {
  margin: 10px;
}

input[type="checkbox"] {
  -webkit-appearance: none;
  appearance: none;
  background-color: #000;
  margin: 0;
  color: white;
  width: 20px;
  height: 20px;
  border: 2px solid white;
  border-radius: 3px;
  margin-right: 10px;
  display: grid;
  place-content: center;
  cursor: pointer;
}

input[type="checkbox"]::before {
  content: "\2713";
  color: #42b983;
  transform: scale(0);
  transform-origin: bottom left;
  transition: 120ms transform ease-in-out;
}

input[type="checkbox"]:checked::before {
  transform: scale(1);
}

input[type="checkbox"]:checked,
input[type="checkbox"]:hover {
  border: 0.15em solid #42b983;
}

label {
  cursor: pointer;
  color: white;
  display: flex;
  align-items: center;
}
</style>
