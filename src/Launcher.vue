<template>
  <ChatWindow
    :messageList="messageList"
    :onUserInputSubmit="onMessageWasSent"
    :participants="participants"
    :title="chatWindowTitle"
    :titleImageUrl="titleImageUrl"
    :showEmoji="showEmoji"
    :showFile="showFile"
    :placeholder="placeholder"
    :showTypingIndicator="showTypingIndicator"
    :colors="colors"
    :alwaysScrollToBottom="alwaysScrollToBottom"
    :messageStyling="messageStyling"
  />
</template>
<script>
import ChatWindow from './ChatWindow.vue'

export default {
  props: {
    showEmoji: {
      type: Boolean,
      default: false
    },
    showFile: {
      type: Boolean,
      default: false
    },
    participants: {
      type: Array,
      required: true
    },
    title: {
      type: String,
      default: () => ''
    },
    titleImageUrl: {
      type: String,
      default: () => ''
    },
    onMessageWasSent: {
      type: Function,
      required: true
    },
    messageList: {
      type: Array,
      default: () => []
    },
    newMessagesCount: {
      type: Number,
      default: () => 0
    },
    placeholder: {
      type: String,
      default: 'Write a reply'
    },
    showTypingIndicator: {
      type: String,
      default: () => ''
    },
    colors: {
      type: Object,
      required: false,
      validator: c =>
        'header' in c &&
        'bg' in c.header &&
        'text' in c.header &&
        'launcher' in c &&
        'bg' in c.launcher &&
        'messageList' in c &&
        'bg' in c.messageList &&
        'sentMessage' in c &&
        'bg' in c.sentMessage &&
        'text' in c.sentMessage &&
        'receivedMessage' in c &&
        'bg' in c.receivedMessage &&
        'text' in c.receivedMessage &&
        'userInput' in c &&
        'bg' in c.userInput &&
        'text' in c.userInput,
      default: function() {
        return {
          header: {
            bg: '#f86a2d',
            text: '#ffffff'
          },
          launcher: {
            bg: '#ffffff'
          },
          messageList: {
            bg: '#ffffff'
          },
          sentMessage: {
            bg: '#777777',
            text: '#ffffff'
          },
          receivedMessage: {
            bg: '#f86a2d',
            text: '#ffffff'
          },
          userInput: {
            bg: '#f4f7f9',
            text: '#565867'
          }
        }
      }
    },
    alwaysScrollToBottom: {
      type: Boolean,
      default: () => false
    },
    messageStyling: {
      type: Boolean,
      default: () => false
    }
  },
  computed: {
    chatWindowTitle() {
      if (this.title !== '') {
        return this.title
      }
      return this.participants[0].name
    }
  },
  components: {
    ChatWindow
  }
}
</script>
