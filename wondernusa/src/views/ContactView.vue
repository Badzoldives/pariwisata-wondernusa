<script setup>
import { ref, reactive } from 'vue'

// Form data
const formData = reactive({
  name: '',
  email: '',
  phone: '',
  subject: '',
  message: ''
})

// Error states
const errors = reactive({
  name: '',
  email: '',
  phone: '',
  subject: '',
  message: ''
})

// Submit state
const isSubmitting = ref(false)
const submitSuccess = ref(false)

// Validate form
const validateForm = () => {
  let isValid = true

  // Reset errors
  Object.keys(errors).forEach(key => errors[key] = '')

  if (!formData.name.trim()) {
    errors.name = 'Nama wajib diisi'
    isValid = false
  }

  if (!formData.email.trim()) {
    errors.email = 'Email wajib diisi'
    isValid = false
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.email)) {
    errors.email = 'Format email tidak valid'
    isValid = false
  }

  if (!formData.phone.trim()) {
    errors.phone = 'No. Telepon wajib diisi'
    isValid = false
  }

  if (!formData.subject.trim()) {
    errors.subject = 'Subjek wajib diisi'
    isValid = false
  }

  if (!formData.message.trim()) {
    errors.message = 'Pesan wajib diisi'
    isValid = false
  }

  return isValid
}

// Submit handler
const handleSubmit = async () => {
  if (!validateForm()) {
    return
  }

  isSubmitting.value = true

  // Simulate API call
  await new Promise(resolve => setTimeout(resolve, 1500))

  // Reset form
  Object.keys(formData).forEach(key => formData[key] = '')
  submitSuccess.value = true
  isSubmitting.value = false

  // Hide success message after 3 seconds
  setTimeout(() => {
    submitSuccess.value = false
  }, 3000)
}
</script>

<template>
  <div class="min-h-screen bg-[#f5f5f5] pt-24 pb-16 font-sans">
    <div class="max-w-[900px] mx-auto px-6">
      <!-- Header -->
      <div class="text-center mb-12">
        <h1 class="text-[2.5rem] font-bold text-slate-900 mb-4">Contact Us</h1>
        <p class="text-base leading-[1.7] text-slate-500 max-w-[700px] mx-auto">
          Hubungi kami untuk pertanyaan, saran, atau informasi lebih lanjut tentang layanan kami.
          Tim Wondernusa siap membantu Anda merencanakan perjalanan impian ke seluruh Indonesia.
        </p>
      </div>

      <!-- Form Card -->
      <div class="bg-white rounded-3xl p-12 shadow-[0_4px_20px_rgba(0,0,0,0.08)]">
        <form @submit.prevent="handleSubmit" class="flex flex-col gap-6">
          <!-- Row 1: Name & Email -->
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div class="flex flex-col gap-2">
              <label for="name" class="text-sm font-semibold text-slate-700">Nama Lengkap</label>
              <input
                id="name"
                v-model="formData.name"
                type="text"
                placeholder="Masukkan nama lengkap"
                class="w-full py-3.5 px-4 bg-slate-100 border border-slate-200 rounded-xl text-[0.95rem] text-slate-900 transition-all duration-200 placeholder:text-slate-400 focus:outline-none focus:bg-white focus:border-[#41a55a] focus:shadow-[0_0_0_3px_rgba(65,165,90,0.1)]"
                :class="{ 'border-red-500! bg-red-50!': errors.name }"
              />
              <span v-if="errors.name" class="text-xs text-red-500 -mt-1">{{ errors.name }}</span>
            </div>

            <div class="flex flex-col gap-2">
              <label for="email" class="text-sm font-semibold text-slate-700">Email</label>
              <input
                id="email"
                v-model="formData.email"
                type="email"
                placeholder="nama@email.com"
                class="w-full py-3.5 px-4 bg-slate-100 border border-slate-200 rounded-xl text-[0.95rem] text-slate-900 transition-all duration-200 placeholder:text-slate-400 focus:outline-none focus:bg-white focus:border-[#41a55a] focus:shadow-[0_0_0_3px_rgba(65,165,90,0.1)]"
                :class="{ 'border-red-500! bg-red-50!': errors.email }"
              />
              <span v-if="errors.email" class="text-xs text-red-500 -mt-1">{{ errors.email }}</span>
            </div>
          </div>

          <!-- Row 2: Phone & Subject -->
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div class="flex flex-col gap-2">
              <label for="phone" class="text-sm font-semibold text-slate-700">No. Telepon</label>
              <input
                id="phone"
                v-model="formData.phone"
                type="tel"
                placeholder="08xx-xxxx-xxxx"
                class="w-full py-3.5 px-4 bg-slate-100 border border-slate-200 rounded-xl text-[0.95rem] text-slate-900 transition-all duration-200 placeholder:text-slate-400 focus:outline-none focus:bg-white focus:border-[#41a55a] focus:shadow-[0_0_0_3px_rgba(65,165,90,0.1)]"
                :class="{ 'border-red-500! bg-red-50!': errors.phone }"
              />
              <span v-if="errors.phone" class="text-xs text-red-500 -mt-1">{{ errors.phone }}</span>
            </div>

            <div class="flex flex-col gap-2">
              <label for="subject" class="text-sm font-semibold text-slate-700">Subjek</label>
              <input
                id="subject"
                v-model="formData.subject"
                type="text"
                placeholder="Subjek pesan"
                class="w-full py-3.5 px-4 bg-slate-100 border border-slate-200 rounded-xl text-[0.95rem] text-slate-900 transition-all duration-200 placeholder:text-slate-400 focus:outline-none focus:bg-white focus:border-[#41a55a] focus:shadow-[0_0_0_3px_rgba(65,165,90,0.1)]"
                :class="{ 'border-red-500! bg-red-50!': errors.subject }"
              />
              <span v-if="errors.subject" class="text-xs text-red-500 -mt-1">{{ errors.subject }}</span>
            </div>
          </div>

          <!-- Row 3: Message (full width) -->
          <div class="flex flex-col gap-2">
            <label for="message" class="text-sm font-semibold text-slate-700">Pesan</label>
            <textarea
              id="message"
              v-model="formData.message"
              rows="6"
              placeholder="Tulis pesan Anda di sini..."
              class="w-full py-3.5 px-4 bg-slate-100 border border-slate-200 rounded-xl text-[0.95rem] text-slate-900 transition-all duration-200 placeholder:text-slate-400 resize-y min-h-[150px] font-sans focus:outline-none focus:bg-white focus:border-[#41a55a] focus:shadow-[0_0_0_3px_rgba(65,165,90,0.1)]"
              :class="{ 'border-red-500! bg-red-50!': errors.message }"
            ></textarea>
            <span v-if="errors.message" class="text-xs text-red-500 -mt-1">{{ errors.message }}</span>
          </div>

          <!-- Success Message -->
          <transition
            enter-active-class="transition-opacity duration-300"
            leave-active-class="transition-opacity duration-300"
            enter-from-class="opacity-0"
            leave-to-class="opacity-0"
          >
            <div v-if="submitSuccess" class="p-4 bg-emerald-100 border border-emerald-300 rounded-xl text-emerald-900 font-medium text-center">
              ✓ Pesan berhasil dikirim! Kami akan menghubungi Anda segera.
            </div>
          </transition>

          <!-- Submit Button -->
          <div class="flex justify-center mt-4">
            <button
              type="submit"
              class="inline-flex items-center gap-3 py-3.5 px-10 bg-linear-to-br from-[#41a55a] to-[#107984] text-white text-base font-semibold border-none rounded-full cursor-pointer transition-all duration-300 shadow-[0_4px_12px_rgba(65,165,90,0.3)] hover:bg-linear-to-br hover:from-[#36914d] hover:to-[#2d7a41] hover:-translate-y-0.5 hover:shadow-[0_6px_16px_rgba(65,165,90,0.4)] disabled:opacity-60 disabled:cursor-not-allowed md:w-auto w-full md:justify-start justify-center"
              :disabled="isSubmitting"
            >
              <span class="text-xl">📨</span>
              <span>{{ isSubmitting ? 'Mengirim...' : 'Kirim Pesan' }}</span>
            </button>
          </div>
        </form>
      </div>

      <!-- Contact Information Card -->
      <div class="mt-12 bg-white rounded-3xl p-8 md:p-12 shadow-[0_4px_20px_rgba(0,0,0,0.08)]">
        <div class="text-center mb-8">
          <h2 class="text-2xl font-bold text-blue-500 mb-2">Contact With Us</h2>
          <p class="text-lg text-blue-400 font-medium">Hubungi Kami!</p>
        </div>

        <p class="text-slate-600 text-center mb-8 leading-relaxed">
          Jadikan kami mitra perjalanan Anda dan rasakan pengalaman liburan yang tak terlupakan di seluruh nusantara.
        </p>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
          <!-- Left: Map -->
          <div class="rounded-xl overflow-hidden shadow-lg">
            <iframe 
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d997.2071187493978!2d116.81037406950098!3d-1.2763027999194565!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2df147447e4a44ff%3A0x1e371ecd782508cc!2sJl.%20Pelayaran%2C%20Prapatan%2C%20Kec.%20Balikpapan%20Kota%2C%20Kota%20Balikpapan%2C%20Kalimantan%20Timur%2076111!5e0!3m2!1sen!2sid!4v1765257210810!5m2!1sen!2sid"
              width="100%" 
              height="300" 
              style="border:0;" 
              allowfullscreen="" 
              loading="lazy" 
              referrerpolicy="no-referrer-when-downgrade"
              class="w-full h-[300px]">
            </iframe>
          </div>

          <!-- Right: Contact Details -->
          <div class="flex flex-col gap-6">
            <!-- Phone -->
            <div class="flex items-start gap-4">
              <div class="w-12 h-12 bg-blue-500 rounded-lg flex items-center justify-center flex-shrink-0">
                <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                </svg>
              </div>
              <div>
                <h3 class="text-sm text-slate-500 mb-1">Have Any Questions?</h3>
                <a href="tel:+628115421487" class="text-lg font-semibold text-slate-900 hover:text-orange-500 transition-colors">
                  +6282346408012
                </a>
              </div>
            </div>

            <!-- Email -->
            <div class="flex items-start gap-4">
              <div class="w-12 h-12 bg-blue-500 rounded-lg flex items-center justify-center flex-shrink-0">
                <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                </svg>
              </div>
              <div>
                <h3 class="text-sm text-slate-500 mb-1">Send Email</h3>
                <a href="mailto:cs@intitalenta.co.id" class="text-lg font-semibold text-slate-900 hover:text-orange-500 transition-colors break-all">
                  ekaaprnsmri@gmail.com
                </a>
              </div>
            </div>

            <!-- Address -->
            <div class="flex items-start gap-4">
              <div class="w-12 h-12 bg-blue-500 rounded-lg flex items-center justify-center flex-shrink-0">
                <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                </svg>
              </div>
              <div>
                <h3 class="text-sm text-slate-500 mb-1">Office Address</h3>
                <p class="text-base text-slate-900 leading-relaxed">
                Jl.Pelayaran No.12
                </p>
                <a href="https://maps.google.com" target="_blank" class="inline-flex items-center gap-1 text-orange-500 hover:text-orange-600 mt-2 text-sm font-medium">
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
</div>
</template>
