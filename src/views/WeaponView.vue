<template>
  <main>
    <h1>Это страница Оружия!</h1>
    <p>Тут пока что еще ничего нет...</p>
    <span>Пожалуйста ожидайте...)</span>
  </main>
</template>

<script>
export default {
  name: "WeaponView"
}
</script>

<style scoped>
h1, p, span {
  text-align: center;
}
main{
  height: 56% !important;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  align-content: center;
}
</style>