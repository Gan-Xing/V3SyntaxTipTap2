<template>
  <div>
    <EditorContent :editor="editor" />
  </div>
</template>

<script>
import { ref, onMounted, onBeforeUnmount } from '@vue/composition-api';
import { Editor, EditorContent } from '@tiptap/vue-2';
import StarterKit from '@tiptap/starter-kit';

export default {
  name: 'TiptapEditor',
  components: {
    EditorContent
  },
  setup() {
    const editor = ref(null);

    onMounted(() => {
      editor.value = new Editor({
        extensions: [
          StarterKit
        ],
        content: '<p>Hello World! 🌍</p>',
      });
    });

    onBeforeUnmount(() => {
      if (editor.value) {
        editor.value.destroy();
      }
    });

    return {
      editor
    };
  }
}
</script>
