<template>
  <div class="Chat__Main">
    <userHeader class="userHeader"/>
    <chatHistory/>
    <textEntry/>
  </div>
</template>

<script>
import userHeader from '../chat/user_header'
import chatHistory from '../chat/chat_history'
import textEntry from '../chat/text_entry'

export default {
  components: {
    chatHistory, textEntry, userHeader
  }
}
</script>

<style>
.Chat__Main {
  display:flex;
  flex-flow:column;
}

.userHeader {
  position: absolute;
  top:0;
  height:50px;
  width:100%;
}

chatHistory {
  flex:1;
}

textEntry {
  position: absolute;
  bottom:0;
  width:100%;
  height:50px;
  background-color: black;
}
</style>
