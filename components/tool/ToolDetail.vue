<script lang="ts" setup>
import { ToolItem } from "~/composables/useTools";
const props = defineProps<{
  tool: ToolItem;
}>();
const { storageOptions } = useChatGPT();
const { send, loading, result, resultHtml } = useAi(props.tool.id!);

function submit(data: any) {
  if (storageOptions.value.apiKey) {
    send(data);
  } else {
    ElMessage.warning("Please set the API key first");
  }
}
</script>
<template>
  <div>
    <ToolHeader show-action :tool="tool" />
    <ToolForms :loading="loading" @submit="submit" :tool="tool" />
    <ToolResult v-if="result" :html="resultHtml" />
  </div>
</template>
