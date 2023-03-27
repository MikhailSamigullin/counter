<template>
  <div class="counter">
    <div class="button cross"></div>
  </div>
</template>

<script>
export default {
  name: "AddCounterComponent",
};
</script>

<style scoped>
.counter {
  width: 225px;
  height: 120px;
  background-color: #696969;
  margin: 22px 25px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.button {
  cursor: pointer;
}

.cross::before {
  content: "";
  position: absolute;
  left: 9px;
  background-color: #9e9e9e;
  height: 21px;
  width: 3px;
}
.cross::after {
  content: "";
  position: absolute;
  top: 9px;
  left: 0px;
  background-color: #9e9e9e;
  height: 3px;
  width: 21px;
}

.cross {
  position: relative;
  height: 20px;
  width: 17px;
}
</style>
