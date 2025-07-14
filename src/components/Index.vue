<template>
  <div class="min-h-screen bg-orange-50">
    <!-- Header -->
    <header class="bg-white shadow-md sticky top-0 z-50">
      <nav class="container mx-auto px-4 py-4">
        <div class="flex items-center justify-between">
          <div class="flex items-center space-x-2">
            <div class="w-10 h-10 bg-orange-500 rounded-full flex items-center justify-center">
              <span class="text-white font-bold text-xl">M</span>
            </div>
            <h1 class="text-2xl font-bold text-orange-800">Marcela Cocina</h1>
          </div>
          
          <!-- Mobile menu button -->
          <button 
            @click="mobileMenuOpen = !mobileMenuOpen"
            class="md:hidden p-2 rounded-md text-orange-800 hover:bg-orange-100"
          >
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" 
                    :d="mobileMenuOpen ? 'M6 18L18 6M6 6l12 12' : 'M4 6h16M4 12h16M4 18h16'">
              </path>
            </svg>
          </button>

          <!-- Desktop menu -->
          <div class="hidden md:flex space-x-8">
            <a href="#inicio" class="text-orange-800 hover:text-orange-600 font-medium transition-colors">Inicio</a>
            <a href="#menu" class="text-orange-800 hover:text-orange-600 font-medium transition-colors">Menú</a>
            <a href="#nosotros" class="text-orange-800 hover:text-orange-600 font-medium transition-colors">Nosotros</a>
            <a href="#contacto" class="text-orange-800 hover:text-orange-600 font-medium transition-colors">Contacto</a>
          </div>
        </div>

        <!-- Mobile menu -->
        <div v-show="mobileMenuOpen" class="md:hidden mt-4 pb-4 border-t border-orange-200">
          <div class="flex flex-col space-y-3 pt-4">
            <a href="#inicio" @click="mobileMenuOpen = false" class="text-orange-800 hover:text-orange-600 font-medium">Inicio</a>
            <a href="#menu" @click="mobileMenuOpen = false" class="text-orange-800 hover:text-orange-600 font-medium">Menú</a>
            <a href="#nosotros" @click="mobileMenuOpen = false" class="text-orange-800 hover:text-orange-600 font-medium">Nosotros</a>
            <a href="#contacto" @click="mobileMenuOpen = false" class="text-orange-800 hover:text-orange-600 font-medium">Contacto</a>
          </div>
        </div>
      </nav>
    </header>

    <!-- Hero Section -->
    <section id="inicio" class="bg-gradient-to-br from-orange-400 to-red-500 text-white py-20">
      <div class="container mx-auto px-4 text-center">
        <h2 class="text-5xl md:text-6xl font-bold mb-6">Marcela Cocina</h2>
        <p class="text-xl md:text-2xl mb-8 max-w-2xl mx-auto">
          Comida Kosher hecha con amor. Sabores auténticos que te harán sentir como en casa.
        </p>
        <button 
          @click="scrollToMenu"
          class="bg-white text-orange-600 px-8 py-3 rounded-full font-semibold text-lg hover:bg-orange-50 transition-colors shadow-lg"
        >
          Ver Menú
        </button>
      </div>
    </section>

    <!-- Menu Section -->
    <section id="menu" class="py-16 bg-white">
      <div class="container mx-auto px-4">
        <h3 class="text-4xl font-bold text-center text-orange-800 mb-12">Nuestro Menú</h3>
        
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8 max-w-6xl mx-auto">
          <div v-for="item in menuItems" :key="item.id" 
               class="bg-orange-50 rounded-lg overflow-hidden shadow-lg hover:shadow-xl transition-shadow">
            <div class="h-48 bg-gradient-to-br from-orange-200 to-orange-300 flex items-center justify-center">
              <div class="text-6xl">{{ item.emoji }}</div>
            </div>
            <div class="p-6">
              <h4 class="text-xl font-bold text-orange-800 mb-2">{{ item.name }}</h4>
              <p class="text-gray-600 mb-4">{{ item.description }}</p>
              <div class="flex justify-between items-center">
                <span class="text-2xl font-bold text-orange-600">${{ item.price }}</span>
                <button class="bg-orange-500 text-white px-4 py-2 rounded-full hover:bg-orange-600 transition-colors">
                  Pedir
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="nosotros" class="py-16 bg-orange-50">
      <div class="container mx-auto px-4">
        <div class="max-w-4xl mx-auto text-center">
          <h3 class="text-4xl font-bold text-orange-800 mb-8">Sobre Nosotros</h3>
          <div class="grid md:grid-cols-2 gap-12 items-center">
            <div>
              <div class="w-64 h-64 bg-gradient-to-br from-orange-300 to-red-400 rounded-full mx-auto flex items-center justify-center">
                <span class="text-8xl">👩‍🍳</span>
              </div>
            </div>
            <div class="text-left">
              <p class="text-lg text-gray-700 mb-6">
                En Marcela Cocina, creemos que la comida casera es el corazón de todo hogar. 
                Cada plato está preparado con ingredientes frescos y mucho amor, siguiendo 
                recetas tradicionales que han pasado de generación en generación.
              </p>
              <p class="text-lg text-gray-700 mb-6">
                Desde nuestra deliciosa tarta de sushi hasta la clásica tortilla de papas, 
                cada bocado te transportará a esos momentos especiales en familia.
              </p>
              <div class="flex flex-wrap gap-4">
                <span class="bg-orange-200 text-orange-800 px-3 py-1 rounded-full text-sm font-medium">Ingredientes Frescos</span>
                <span class="bg-orange-200 text-orange-800 px-3 py-1 rounded-full text-sm font-medium">Recetas Caseras</span>
                <span class="bg-orange-200 text-orange-800 px-3 py-1 rounded-full text-sm font-medium">Hecho con Amor</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contacto" class="py-16 bg-white">
      <div class="container mx-auto px-4">
        <h3 class="text-4xl font-bold text-center text-orange-800 mb-12">¡Hacé tu pedido!</h3>
        
        <div class="flex justify-center items-center gap-12 max-w-4xl mx-auto">
          <div>
          
            <div class="space-y-4">
              <div class="flex items-center space-x-3">
                <div class="w-10 h-10 bg-orange-500 rounded-full flex items-center justify-center">
                  <span class="text-white text-xl">📱</span>
                </div>
                <div>
                  <p class="font-semibold text-gray-800">WhatsApp</p>
                  <p class="text-gray-600">+54 9 11 1234-5678</p>
                </div>
              </div>
              
              <div class="flex items-center space-x-3">
                <div class="w-10 h-10 bg-orange-500 rounded-full flex items-center justify-center">
                  <span class="text-white text-xl">📍</span>
                </div>
                <div>
                  <p class="font-semibold text-gray-800">Ubicación</p>
                  <p class="text-gray-600">Buenos Aires, Argentina</p>
                </div>
              </div>
              
              <div class="flex items-center space-x-3">
                <div class="w-10 h-10 bg-orange-500 rounded-full flex items-center justify-center">
                  <span class="text-white text-xl">🕒</span>
                </div>
                <div>
                  <p class="font-semibold text-gray-800">Horarios</p>
                  <p class="text-gray-600">Lun - Dom: 11:00 - 22:00</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-orange-800 text-white py-8">
      <div class="container mx-auto px-4 text-center">
        <div class="flex items-center justify-center space-x-2 mb-4">
          <div class="w-8 h-8 bg-orange-500 rounded-full flex items-center justify-center">
            <span class="text-white font-bold">M</span>
          </div>
          <h5 class="text-xl font-bold">Marcela Cocina</h5>
        </div>
        <p class="text-orange-200 mb-4">Supervisado por Rab Mendi Tawil</p>
        <div class="flex justify-center space-x-6">
          <a href="#" class="text-orange-200 hover:text-white transition-colors">Instagram</a>
          <a href="#" class="text-orange-200 hover:text-white transition-colors">Facebook</a>
          <a href="#" class="text-orange-200 hover:text-white transition-colors">WhatsApp</a>
        </div>
        <div class="mt-6 pt-6 border-t border-orange-700">
          <p class="text-orange-300 text-sm">© 2024 Marcela Cocina. Todos los derechos reservados.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'MarcelaCocina',
  data() {
    return {
      mobileMenuOpen: false,
      menuItems: [
        {
          id: 1,
          name: 'Tarta de Sushi',
          description: 'Deliciosa tarta con salmón, palta y queso crema. Una fusión perfecta de sabores.',
          price: '2500',
          emoji: '🍣'
        },
        {
          id: 2,
          name: 'Carne con Papas',
          description: 'Tierna carne cocida a la perfección acompañada de papas doradas y condimentos caseros.',
          price: '1800',
          emoji: '🥩'
        },
        {
          id: 3,
          name: 'Tortilla de Papas',
          description: 'Clásica tortilla española con papas y huevos frescos. Un sabor tradicional irresistible.',
          price: '1200',
          emoji: '🥚'
        },
        {
          id: 4,
          name: 'Empanadas Caseras',
          description: 'Empanadas artesanales con rellenos variados: carne, pollo, jamón y queso.',
          price: '200',
          emoji: '🥟'
        },
        {
          id: 5,
          name: 'Milanesas',
          description: 'Milanesas de carne o pollo, crujientes por fuera y tiernas por dentro.',
          price: '1600',
          emoji: '🍖'
        },
        {
          id: 6,
          name: 'Pastas Caseras',
          description: 'Pastas frescas hechas en casa con salsas tradicionales y ingredientes selectos.',
          price: '1400',
          emoji: '🍝'
        }
      ]
    }
  },
  methods: {
    scrollToMenu() {
      document.getElementById('menu').scrollIntoView({ 
        behavior: 'smooth' 
      });
    },
    submitForm() {
      // Aquí integrarías con Laravel para enviar el formulario
      alert(`¡Gracias ${this.form.name}! Recibimos tu mensaje y te contactaremos pronto.`);
      
      // Reset form
      this.form = {
        name: '',
        phone: '',
        message: ''
      };
    }
  }
}
</script>

<style scoped>
/* Smooth scrolling for the entire page */
html {
  scroll-behavior: smooth;
}

/* Custom animations */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in-up {
  animation: fadeInUp 0.6s ease-out;
}
</style>