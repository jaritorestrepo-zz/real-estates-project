<template>
  <div>
    <nav class="bg-white border-b border-gray-light font-silka text-base">
      <div class="max-w-6xl mx-auto px-4">
        <div class="md:flex justify-between">
          <div class="flex space-x-7">
            <div>
              <div class="flex items-center py-4 px-2">
                <div class="md:hidden block items-center pr-2">
                  <button class="mobile-menu-button flex" v-on:click="toggle()">
                    <button class="inline-block relative md:hidden block">
                      <img
                        :src="require('../assets/images/hamburger.svg')"
                        alt="Hamburger"
                        class="md:hidden h-6 mr-2"
                      />
                      <span
                        class="animate-ping absolute top-0 right-1.5 block h-1 w-1 rounded-full ring-2 ring-caribbean bg-caribbean"
                      ></span>
                    </button>
                  </button>
                </div>
                <img
                  :src="require('../assets/images/logo.svg')"
                  alt="Logo"
                  class="md:hidden h-8 mr-2"
                />
                <img
                  :src="require('../assets/images/logo-letras.svg')"
                  alt="Letras logo"
                  class="hidden md:flex h-6 mr-2"
                />
              </div>
            </div>
          </div>
          <div
            v-bind:class="open ? 'block' : 'hidden'"
            class="md:flex items-center space-x-3"
          >
            <div class="text-sm md:flex">
              <div class="py-2 pr-10 font-medium text-jungle">
                Cundinamarca
              </div>
              <div class="py-2 pr-10 font-medium text-jungle">
                Antioquia
              </div>
              <div class="py-2 pr-10 font-medium text-jungle">
                Recursos
              </div>
              <div class="py-2 font-medium text-jungle font-semibold">
                <div class="flex items-center">
                  Mi Perfil
                  <button class="inline-block relative hidden md:block">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-4 w-4"
                      fill="none"
                      viewBox="0 0 24 24"
                      stroke="currentColor"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M19 9l-7 7-7-7"
                      />
                    </svg>
                    <span
                      class="animate-ping absolute top-0.5 right-0 block h-1 w-1 rounded-full ring-2 ring-caribbean bg-caribbean"
                    ></span>
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Menu",
  data() {
    return {
      open: false
    };
  },
  methods: {
    toggle() {
      this.open = !this.open;
    }
  }
};
</script>
