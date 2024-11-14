<script setup lang="ts">
    //변수 정의
    const msg = ref("start") //초기값.
    const showToast = ref(false); // 토스트 메시지 표시 여부


    //버튼 클릭 이벤트 
    const onButtonClick = (label:string, event : Event): void => {
      const target = event.target as HTMLButtonElement;
      const text = target.innerText;
      //result
      //msg.value = `${label} + ${text}` ;
      msg.value = label + " _ " + text;
    };

    //버튼에 마우스를 올렸을 경우 이벤트 
    const onMouseEnter = (): void => {
      // 토스트 메시지 표시
      showToast.value = true;
      
      // 1초 뒤에 토스트 메시지를 숨김
      setTimeout(() => {
        showToast.value = false;
      }, 1000);
    };

</script>

<template>
  <div>
    <h1>Hello Nuxt world!</h1>
    <p>{{ msg }}</p>
    <button v-on:click="onButtonClick('Hello', $event)"
            v-on:mouseenter="onMouseEnter"
    >안녕하세요.</button>
  </div>


  <!-- 토스트 메시지를 화면에 표시 -->
  <div v-if="showToast" class="toast">
      버튼 위에 마우스를 올렸습니다!
  </div>

</template>


<!-- 간단한 토스트 스타일 -->
<style scoped>
.toast {
  position: fixed;
  bottom: 20px;
  right: 20px;
  padding: 10px;
  background-color: #333;
  color: #fff;
  border-radius: 5px;
  opacity: 0.8;
  transition: opacity 0.5s ease-in-out;
}
</style>