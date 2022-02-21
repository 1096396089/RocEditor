<template>
  <div>
    <div style="border: 1px solid #ccc">
      <Toolbar
        :editorId="editorId"
        :defaultConfig="toolbarConfig"
        mode="default"
        style="border-bottom: 1px solid #ccc"
      />
      <Editor
        :editorId="editorId"
        :defaultConfig="editorConfig"
        :defaultHtml="defaultHtml"
        mode="default"
        style="height: 500px; overflow-y: hidden"
        @onChange="ok"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import {
  Editor,
  Toolbar
} from "@wangeditor/editor-for-vue";
let editorId = ref("w-e-1");
let text = ref('')

const prop = defineProps({
  uploadUrl: {
    default: '',
    type: String,
  },
  fileName:{
    default: 'file',
    type: String,
  },
  modelValue:{
    default: '',
    type: String,
  },
  
})

let toolbarConfig = ref({});
const defaultHtml = prop.modelValue;
const editorConfig = ref({
  placeholder: "请输入内容...",
  MENU_CONF: {
    uploadImage: {
      server: prop.uploadUrl,
      fieldName: prop.fileName,
        customInsert(res: any, insertFn) {
        insertFn(res.path)
    },
    },
  },
});

const emit = defineEmits(['update:modelValue'])
const ok = (editor) => {
  text.value =  editor.getHtml();
  emit('update:modelValue', editor.getHtml());
};

</script>
<style src="@wangeditor/editor/dist/css/style.css"></style>
