<template>
  <div
    class="min-h-8 text-message flex w-full flex-col gap-2 whitespace-normal break-words text-start m-auto text-base py-[18px] px-3 md:px-4 w-full md:px-5 lg:px-4 xl:px-5"
    :class="{
      'items-end': isLTR,
    }"
  >
    <div
      class="relative rounded-3xl px-5 py-2.5"
      :class="{
        'bg-[#e8e8e880] max-w-[var(--user-chat-width,70%)]': isLTR,
      }"
    >
      <div v-if="isLTR" class="w-fit">
        {{ text }}
      </div>
      <div
        v-else
        class="flex gap-4 text-base md:gap-5 lg:gap-6 md:max-w-3xl lg:max-w-[40rem] xl:max-w-[48rem]"
      >
        <div
          class="flex-shrink-0 h-8 w-8 flex items-center justify-center overflow-hidden rounded-full border border-[#ececec]"
        >
          <UIcon name="i-heroicons-light-bulb" class="w-5 h-5" />
        </div>
        <div>
          {{ text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">

defineProps({
  text: {
    type: String,
    required: true,
  },
  isLTR: {
    type: Boolean,
    default: true,
  },
});

// const displayedText = ref("");
// let typingInterval: NodeJS.Timeout | null = null;
// function simulateTyping(text: string) {
//   displayedText.value = "";
//   let index = 0;

//   if (typingInterval) clearInterval(typingInterval);

//   typingInterval = setInterval(() => {
//     if (index < text.length) {
//       displayedText.value += text[index];
//       index++;
//     } else {
//       clearInterval(typingInterval!);
//     }
//   }, 50);
// }
// watch(
//   () => [props.text, props.isLTR],
//   ([text, isLTR]) => {
//     if (!isLTR) {
//       onMounted(() => {
//         simulateTyping(text as string); // Gọi simulateTyping sau khi component đã mount trên client
//       });
//     } else {
//       displayedText.value = text as string;
//     }
//   },
//   { immediate: true }
// );

// onUnmounted(() => {
//   if (typingInterval) clearInterval(typingInterval);
// });

</script>
