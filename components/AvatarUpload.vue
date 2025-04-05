<template>
  <div class="relative group">
    <input
      type="file"
      @change="handleUpload"
      accept="image/*"
      class="hidden"
      ref="fileInput"
    />
    <div class="w-40 h-40 rounded-full border-4 border-white/80 shadow-lg overflow-hidden transition-transform duration-300 group-hover:scale-105">
      <img
        :src="modelValue || defaultAvatar"
        :alt="alt"
        class="w-full h-full object-cover"
      />
      <!-- Upload overlay - only show when not readonly -->
      <div
        v-if="!readonly"
        @click="triggerUpload"
        class="absolute inset-0 bg-black/40 opacity-0 group-hover:opacity-100 transition-all cursor-pointer flex items-center justify-center"
      >
        <div v-if="!isUploading" class="text-white flex flex-col items-center gap-2">
          <Icon name="ph:camera-bold" class="w-8 h-8" />
          <span class="text-sm">Thay đổi ảnh</span>
        </div>
        <div v-else class="text-white">
          <Icon name="ph:spinner-gap-bold" class="w-8 h-8 animate-spin" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const props = withDefaults(defineProps<{
  modelValue: string | null;
  alt: string;
  readonly?: boolean;
}>(), {
  modelValue: null,
  alt: '',
  readonly: false
})

const emit = defineEmits(['update:modelValue'])

const updateValue = (val: string) => {
  emit('update:modelValue', val)
}

const fileInput = ref<HTMLInputElement | null>(null)
const isUploading = ref(false)
const defaultAvatar = '/images/avatar.jpg'

const triggerUpload = () => {
  fileInput.value?.click()
}

const handleUpload = async (event: Event) => {
  const input = event.target as HTMLInputElement
  if (!input.files?.length) return

  const file = input.files[0]
  if (!file.type.startsWith('image/')) {
    alert('Vui lòng chọn file ảnh')
    return
  }

  try {
    isUploading.value = true
    const base64 = await convertToBase64(file)
    updateValue(base64)

    // Save to localStorage
    localStorage.setItem('userAvatar', base64)
  } catch (error) {
    console.error('Upload error:', error)
    alert('Không thể tải ảnh lên. Vui lòng thử lại.')
  } finally {
    isUploading.value = false
  }
}

const convertToBase64 = (file: File): Promise<string> => {
  return new Promise((resolve, reject) => {
    const reader = new FileReader()
    reader.onload = () => resolve(reader.result as string)
    reader.onerror = reject
    reader.readAsDataURL(file)
  })
}

// Load saved avatar from localStorage on mount
onMounted(() => {
  const savedAvatar = localStorage.getItem('userAvatar')
  if (savedAvatar) {
    updateValue(savedAvatar)
  }
})
</script>
