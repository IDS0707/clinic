<template>
  <div>
    <!-- ===== CONTACTS SECTION ===== -->
    <section id="contacts" class="py-20 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Title -->
        <div class="text-center mb-14">
          <h2 class="text-4xl font-bold text-stone-900 mb-3">{{ t.contacts_title }}</h2>
          <p class="text-stone-500 text-lg">{{ t.contacts_subtitle }}</p>
        </div>

        <!-- 3 info cards -->
        <div class="grid md:grid-cols-3 gap-6 mb-14">
          <div class="flex items-center gap-5 bg-blue-50 rounded-2xl p-6 border border-blue-100">
            <div class="w-14 h-14 bg-brand-600 rounded-xl flex items-center justify-center shrink-0">
              <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.8">
                <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 002.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 01-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 00-1.091-.852H4.5A2.25 2.25 0 002.25 4.5v2.25z" />
              </svg>
            </div>
            <div>
              <div class="text-sm text-stone-400 mb-1">{{ t.contacts_phone_label }}</div>
              <div class="font-bold text-stone-900 text-lg">{{ t.contacts_phone }}</div>
            </div>
          </div>
          <div class="flex items-center gap-5 bg-blue-50 rounded-2xl p-6 border border-blue-100">
            <div class="w-14 h-14 bg-brand-600 rounded-xl flex items-center justify-center shrink-0">
              <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.8">
                <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
                <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
              </svg>
            </div>
            <div>
              <div class="text-sm text-stone-400 mb-1">{{ t.contacts_address_label }}</div>
              <div class="font-bold text-stone-900 text-lg">{{ t.contacts_address }}</div>
            </div>
          </div>
          <div class="flex items-center gap-5 bg-blue-50 rounded-2xl p-6 border border-blue-100">
            <div class="w-14 h-14 bg-brand-600 rounded-xl flex items-center justify-center shrink-0">
              <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.8">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </div>
            <div>
              <div class="text-sm text-stone-400 mb-1">{{ t.contacts_hours_label }}</div>
              <div class="font-bold text-stone-900 text-lg">{{ t.contacts_hours }}</div>
            </div>
          </div>
        </div>

        <!-- Form + Sidebar -->
        <div class="grid md:grid-cols-2 gap-8 mb-16">
          <!-- Form -->
          <div class="bg-white rounded-3xl shadow-xl shadow-stone-900/[0.07] p-8 border border-stone-100">
            <h3 class="text-2xl font-bold text-stone-900 mb-8">{{ t.contacts_form_title }}</h3>
            <form @submit.prevent="sendMessage" class="space-y-5">
              <input
                v-model="form.name"
                :placeholder="t.contacts_name"
                class="w-full px-5 py-4 rounded-xl border border-stone-200 text-stone-800 placeholder-stone-400 focus:outline-none focus:ring-2 focus:ring-brand-400 focus:border-transparent transition-all duration-200"
              />
              <input
                v-model="form.phone"
                :placeholder="t.contacts_phone_field"
                class="w-full px-5 py-4 rounded-xl border border-stone-200 text-stone-800 placeholder-stone-400 focus:outline-none focus:ring-2 focus:ring-brand-400 focus:border-transparent transition-all duration-200"
              />
              <textarea
                v-model="form.message"
                :placeholder="t.contacts_message"
                rows="5"
                class="w-full px-5 py-4 rounded-xl border border-stone-200 text-stone-800 placeholder-stone-400 focus:outline-none focus:ring-2 focus:ring-brand-400 focus:border-transparent transition-all duration-200 resize-none"
              ></textarea>
              <button type="submit"
                class="w-full bg-brand-600 hover:bg-brand-700 text-white font-semibold py-4 rounded-xl transition-all duration-300 hover:-translate-y-0.5 hover:shadow-lg hover:shadow-brand-600/30 active:translate-y-0">
                {{ t.contacts_send }}
              </button>
            </form>
          </div>

          <!-- Blue sidebar -->
          <div class="bg-brand-600 rounded-3xl p-8 text-white flex flex-col gap-6">
            <h3 class="text-2xl font-bold">{{ t.contacts_sidebar_title }}</h3>
            <div class="flex items-start gap-4">
              <div class="w-10 h-10 bg-white/20 rounded-xl flex items-center justify-center shrink-0 mt-0.5">
                <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.8">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 002.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 01-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 00-1.091-.852H4.5A2.25 2.25 0 002.25 4.5v2.25z" />
                </svg>
              </div>
              <div>
                <div class="text-white/70 text-sm mb-1">{{ t.contacts_phone_label }}</div>
                <div class="font-semibold text-lg">{{ t.contacts_phone }}</div>
                <div class="font-semibold text-lg">{{ t.contacts_phone2 }}</div>
              </div>
            </div>
            <div class="flex items-start gap-4">
              <div class="w-10 h-10 bg-white/20 rounded-xl flex items-center justify-center shrink-0 mt-0.5">
                <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.8">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
                  <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
                </svg>
              </div>
              <div>
                <div class="text-white/70 text-sm mb-1">{{ t.contacts_address_label }}</div>
                <div class="font-semibold text-lg">{{ t.contacts_address }}</div>
              </div>
            </div>
          </div>
        </div>

        <!-- Map section -->
        <div class="mb-6">
          <div class="text-center mb-10">
            <h2 class="text-3xl font-bold text-stone-900 mb-2">{{ t.contacts_map_title }}</h2>
            <p class="text-stone-400">{{ t.contacts_map_subtitle }}</p>
          </div>
          <div class="grid md:grid-cols-2 gap-8 items-start">
            <!-- Google map embed -->
            <div class="rounded-2xl overflow-hidden shadow-lg border border-stone-100 h-80">
              <iframe
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2992.948523019946!2d72.36291167581!3d40.76539997137987!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x38bb77e3e6f4e3d5%3A0x5a52df93d7aadf0b!2sAndijon%2C%20Xuja%20ko&#39;chasi%2C%2027!5e0!3m2!1sru!2s!4v1713000000000"
                width="100%"
                height="100%"
                style="border:0;"
                allowfullscreen=""
                loading="lazy"
              ></iframe>
            </div>
            <!-- Map info card -->
            <div class="bg-white rounded-2xl shadow-lg border border-stone-100 p-8 space-y-6">
              <div class="flex items-start gap-4">
                <div class="w-12 h-12 bg-blue-50 rounded-xl flex items-center justify-center shrink-0">
                  <svg class="w-6 h-6 text-brand-600" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.8">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
                    <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
                  </svg>
                </div>
                <div>
                  <div class="font-bold text-stone-800 mb-1">{{ t.contacts_address_label }}</div>
                  <div class="text-stone-500">{{ t.contacts_address }}</div>
                </div>
              </div>
              <div class="flex items-start gap-4">
                <div class="w-12 h-12 bg-green-50 rounded-xl flex items-center justify-center shrink-0">
                  <svg class="w-6 h-6 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.8">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 002.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 01-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 00-1.091-.852H4.5A2.25 2.25 0 002.25 4.5v2.25z" />
                  </svg>
                </div>
                <div>
                  <div class="font-bold text-stone-800 mb-1">{{ t.contacts_phone_label }}</div>
                  <div class="text-stone-500">{{ t.contacts_phone }}</div>
                  <div class="text-stone-500">{{ t.contacts_phone2 }}</div>
                </div>
              </div>
              <div class="flex items-start gap-4">
                <div class="w-12 h-12 bg-purple-50 rounded-xl flex items-center justify-center shrink-0">
                  <svg class="w-6 h-6 text-purple-600" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.8">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                </div>
                <div>
                  <div class="font-bold text-stone-800 mb-1">{{ t.contacts_hours_label }}</div>
                  <div class="text-stone-500">{{ t.contacts_hours }}</div>
                </div>
              </div>
              <a
                href="https://maps.google.com/?q=Andijan+Xuja+27"
                target="_blank"
                class="flex items-center justify-center gap-2 w-full bg-brand-600 hover:bg-brand-700 text-white font-semibold py-4 rounded-xl transition-all duration-300 hover:-translate-y-0.5 hover:shadow-lg hover:shadow-brand-600/30"
              >
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.8">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
                  <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
                </svg>
                {{ t.contacts_directions }}
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== FOOTER ===== -->
    <footer class="bg-stone-900 text-white relative overflow-hidden">
      <div class="absolute top-0 left-1/2 -translate-x-1/2 w-[800px] h-px bg-gradient-to-r from-transparent via-brand-600/30 to-transparent"></div>
      <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-16 pb-10">
        <div class="grid md:grid-cols-4 gap-10 pb-12 border-b border-white/10">
          <!-- Brand -->
          <div class="md:col-span-2">
            <div class="flex items-center gap-3 mb-5">
              <div class="w-10 h-10 rounded-xl bg-brand-600 flex items-center justify-center">
                <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M12 3c.132 0 .263 0 .393 0a7.5 7.5 0 007.92 12.446A9 9 0 1112 2.992z" />
                </svg>
              </div>
              <div>
                <span class="text-lg font-bold tracking-tight">Hair Clinic</span>
                <span class="block text-[10px] font-medium tracking-widest uppercase text-brand-400">Трихология</span>
              </div>
            </div>
            <p class="text-white/40 text-sm leading-relaxed max-w-sm">{{ t.footer_desc }}</p>
          </div>

          <!-- Links -->
          <div>
            <h4 class="text-xs font-semibold tracking-widest uppercase text-white/60 mb-5">{{ t.footer_contacts }}</h4>
            <div class="space-y-3 text-sm text-white/40">
              <a :href="`tel:${t.contacts_phone.replace(/\s/g,'')}`" class="flex items-center gap-2.5 hover:text-white hover:translate-x-1 transition-all duration-300">
                <svg class="w-4 h-4 text-brand-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.8"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 002.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 01-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 00-1.091-.852H4.5A2.25 2.25 0 002.25 4.5v2.25z"/></svg>
                {{ t.contacts_phone }}
              </a>
              <div class="flex items-center gap-2.5">
                <svg class="w-4 h-4 text-brand-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.8"><path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z"/><path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z"/></svg>
                {{ t.contacts_address }}
              </div>
            </div>
          </div>

          <!-- Working hours -->
          <div>
            <h4 class="text-xs font-semibold tracking-widest uppercase text-white/60 mb-5">{{ t.contacts_hours_label }}</h4>
            <div class="space-y-3 text-sm text-white/40">
              <div class="flex justify-between">
                <span>Пн — Пт</span>
                <span class="text-white/60 font-medium">08:00 — 17:00</span>
              </div>
              <div class="flex justify-between">
                <span>Сб — Вс</span>
                <span class="text-white/60 font-medium">Выходной</span>
              </div>
            </div>
          </div>
        </div>

        <div class="mt-8 flex flex-col md:flex-row justify-between items-center gap-4">
          <p class="text-xs text-white/30">{{ t.footer_copy }}</p>
          <router-link to="/admin/login" class="text-xs text-white/20 hover:text-white/40 transition-colors duration-300">
            {{ t.footer_admin }}
          </router-link>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useLangStore } from '../stores/lang'

const langStore = useLangStore()
const t = computed(() => langStore.t)

const form = ref({ name: '', phone: '', message: '' })

function sendMessage() {
  if (!form.value.name || !form.value.phone) return
  const msg = `Имя: ${form.value.name}\nТелефон: ${form.value.phone}\nСообщение: ${form.value.message}`
  window.open(`https://t.me/+998901475130?text=${encodeURIComponent(msg)}`, '_blank')
  form.value = { name: '', phone: '', message: '' }
}
</script>
