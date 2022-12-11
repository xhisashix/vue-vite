<script setup>
import HelloWorld from "./components/HelloWorld.vue";
import Push from 'push.js';

console.log("通知の許可: " + Push.Permission.has())

let notificationConfirm = () => {
  let arrow = confirm('通知を受け取りますか。');
  console.log(arrow)
  return arrow;
}

let notification = () => {
  Push.create("Hello world!", {
      body: "How's it hangin'?",
      timeout: 4000,
      link: 'http://google.com',
      onClick: function () {
          window.focus();
          window.open(
            'http://google.com',
          )
          this.close();
      }
  });
}


if(notificationConfirm()) {
  notification()
}else {
  console.log('通知が許可されませんでした。')
}
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
