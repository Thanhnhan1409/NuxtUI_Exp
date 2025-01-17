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
  <UContainer>
    <div class="relative whitespace-pre-line break-words text-3xl my-md md:my-lg">#F3F3EE</div>
    <div class="mb-lg">
      <div class="flex gap-2 items-center">
        <UIcon name="i-heroicons-inbox" />
        <span class="text-lg font-medium">Sources</span>
      </div>
      <UPopover mode="hover" :ui="{base: 'w-fit', overlay: {
          base: 'bg-red-500',}}">
        <UCard :ui="{ background: ' bg-[#F3F3EE]',
          base: 'items gap-sm cursor-pointer relative flex h-full max-w-full select-none flex-col justify-between px-sm pb-sm pt-sm',
          padding: 'p-1',
          body: {
            padding: 'sm:p-2',
            base: 'flex flex-col gap-2',
          }}">
          <div class="text-left line-clamp-2 default font-sans text-xs font-medium line-clamp-3">
            Chinese Social Media App RedNote Gains US Users Ahead of TikTok Ban
          </div>
          <div class="flex items-center gap-2 leading-4">
            <UIcon name="i-heroicons-inbox" />  
            <span>pymnts</span>
          </div>
        </UCard>

        <template #panel>
          <div class="py-2 px-4 max-w-[300px] flex flex-col gap-2">
            <div class="flex items-center gap-2 leading-4">
              <UIcon name="i-heroicons-inbox" />  
              <span>pymnts</span>
            </div>
            <div class="max-h-[40px] overflow-hidden text-sm font-medium">
              Chinese Social Media App RedNote Gains US Users Ahead of TikTok Ban
            </div>
            <div class="max-h-[80px] overflow-hidden text-sm">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Beatae labore optio accusantium totam sint ducimus illum aspernatur in quas, sunt sapiente, iste fuga laborum porro provident tenetur minus voluptatibus at?
            </div>
          </div>
        </template>
      </UPopover>
    </div>
    <div class="flex flex-col gap-2">
      <div class="flex gap-2 items-center">
        <UIcon name="i-heroicons-inbox" />
        <span class="text-lg font-medium">Answer</span>
      </div>
      <div>
        Adapting your responses to fit the flow of an interview conversation involves several key strategies that enhance engagement and ensure a natural dialogue. Here are some effective techniques:
      </div>
    </div>
  </UContainer>
</template>

