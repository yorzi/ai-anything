<script lang="ts" setup>
const { tool, step } = useCreateTool();
</script>
<template>
  <div w-full h-full>
    <h2 text-xl mb-2>Preview</h2>
    <div flex items-center justify-center h-full>
      <CreatePreviewTransition name="remove" mode="out-in">
        <ToolItem max-w-120 flex-1 v-if="step === 0" :tool="tool" />
        <Card max-w-2xl flex-1 v-else-if="step === 1">
          <ToolForms readonly :tool="tool" />
        </Card>
        <Card max-w-2xl flex-1 v-else-if="step === 2">
          <ToolHeader :tool="tool" />
          <ToolForms :tool="tool" />
          <ToolRequestPreview :tool="tool" />
        </Card>
      </CreatePreviewTransition>
    </div>
  </div>
</template>
