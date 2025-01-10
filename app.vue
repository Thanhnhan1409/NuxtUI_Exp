<script setup lang="ts">

interface IChatConversation {
  id: string;
  content: string;
  isLTR: boolean;
}

interface IHistoryItem {
  id: string;
  label: string;
}

interface IHistoryChats {
  id: string;
  date: string;
  historyItems: IHistoryItem[];
}
const { toggleDocsSearch, isDocsSearchModalOpen } = useUIState()
const links = [{
  label: 'Home',
  icon: 'i-heroicons-home'
}, {
  label: 'Inbox',
  icon: 'i-heroicons-inbox',
  badge: '4'
}, {
  label: 'Users',
  icon: 'i-heroicons-user-group'
}, {
  label: 'Settings',
  icon: 'i-heroicons-cog-8-tooth',
  children: [{
    label: 'General'
  }, {
    label: 'Members'
  }, {
    label: 'Notifications'
  }]
}]

const historyChats: IHistoryChats[] = [{
  id: '1',
  date: '2023-10-01',
  historyItems: [{
    id: '1',
    label: 'Hello, how are you?'
  }, {
    id: '2',
    label: 'I am fine, thank you!'
  }]
}, {
  id: '2',
  date: '2023-10-02',
  historyItems: [{
    id: '3',
    label: 'What are you doing today?'
  }, {
    id: '4',
    label: 'I am working on a project.'
  }]
}, {
  id: '3',
  date: '2023-10-03',
  historyItems: [{
    id: '5',
    label: 'That sounds great!'
  }, {
    id: '6',
    label: 'Yes, it is.'
  }]
}, {
  id: '4',
  date: '2023-10-04',
  historyItems: [{
    id: '7',
    label: 'I am happy for you.'
  }, {
    id: '8',
    label: 'Thank you!'
  }]
}]

const chatConversation: IChatConversation[] = [{
  id: '1',
  content: 'Hello, how are you?',
  isLTR: true
}, {
  id: '2',
  content: 'I am fine, thank you!',
  isLTR: false
}, {
  id: '3',
  content: 'What are you doing today?',
  isLTR: true
}, {
  id: '4',
  content: 'I am working on a project.',
  isLTR: false
}, {
  id: '5',
  content: 'That sounds great!',
  isLTR: true
}, {
  id: '6',
  content: 'Yes, it is.',
  isLTR: false
}, {
  id: '7',
  content: 'I am happy for you.',
  isLTR: true
}, {
  id: '8',
  content: 'Thank you!',
  isLTR: false
}]
const textAreaRef = ref<HTMLTextAreaElement>();
function onFocusTextArea() {
  if (textAreaRef.value) {
      textAreaRef.value.focus();
  }
}
</script>

<template>
  <UContainer :ui="{base: 'relative flex h-full w-full overflow-hidden transition-colors z-0 overflow-hidden'}">
    <ChatsCustomHeader />
    <UDashboardPanel :width="260">
      <UDashboardSidebar>
        <template #header>
          <div class="flex items-center justify-between">
            <UIcon name="i-heroicons-light-bulb" class="w-5 h-5" />
            <div class="flex gap-4">
              <UIcon name="i-heroicons-light-bulb" class="w-5 h-5" />
              <UColorModeButton />
            </div>
          </div>
        </template>
        <div>
          <div v-for="historyChat in historyChats" :key="historyChat.id">
            <div>{{ historyChat.date }}</div>
            <UDashboardSidebarLinks :links="historyChat.historyItems" :ui="{ 
              active: 'text-gray-900  bg-yellow-900 dark:text-white before:bg-gray-100 dark:before:bg-gray-800',
              inactive: ' hover:bg-yellow-900 \text-gray-500 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white  hover:before:bg-red-900 dark:hover:before:bg-gray-800/50',}" />
          </div>
        </div>
        <!-- <UDashboardSidebarLinks :links="links" /> -->
      </UDashboardSidebar>
    </UDashboardPanel>
<!-- flex flex-col m-auto text-base md:px-4 w-full md:px-5 lg:px-4 xl:px-5 md:max-w-3xl lg:max-w-[40rem] xl:max-w-[48rem] overflow-hidden -->
    <div class="flex h-full flex-1 flex-col focus-visible:outline-0">
      <!-- <div class=" mx-auto text-base"> -->
        <div class="flex-1 w-full m-auto text-bases md:max-w-3xl lg:max-w-[40rem] xl:max-w-[48rem]">
          <template v-for="conversation in chatConversation" :key="conversation.id">
            <ChatsChatBubbleItem :text="conversation.content" :is-l-t-r="conversation.isLTR" />
          </template>
        </div>
      <!-- </div> -->
      <div @click="onFocusTextArea" class="flex w-full cursor-text flex-col rounded-3xl px-2.5 py-1 transition-colors contain-inline-size bg-[#f4f4f4] dark:bg-[#2f2f2f] mx-auto text-base md:gap-5 lg:gap-6 md:max-w-3xl lg:max-w-[40rem] xl:max-w-[48rem]">
        <UTextarea
          ref="textAreaRef"
          :rows="1"
          :maxrows="7"
          :minrows="1"
          autoresize
          autofocus
          variant="none"
          class="min-h-[40px]"
        />
        <div class="flex h-[44px] items-center justify-between">
          <UButton class="h-8 min-w-8 items-center justify-center rounded-lg p-1 text-xs font-semibold hover:bg-black/10 focus-visible:outline-black dark:focus-visible:outline-white" variant="ghost" >
            <UIcon name="i-heroicons-link" class="w-6 h-6 text-black dark:text-white" />
          </UButton>
          <UButton class="h-8 min-w-8 items-center justify-center rounded-lg p-1 text-xs font-semibold hover:bg-black/10 focus-visible:outline-black dark:focus-visible:outline-white" variant="ghost" >
            <UIcon name="i-heroicons-paper-airplane" class="w-6 h-6 text-black dark:text-white" />
          </UButton>
        </div>
      </div>
    </div>
  </UContainer>
</template>

