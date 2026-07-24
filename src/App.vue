<template>
  <div class="min-h-screen bg-zinc-950 flex flex-col items-center pb-12 text-zinc-100 font-sans relative overflow-hidden">
    
    <!-- Efecto Glow -->
    <div class="absolute top-20 left-1/2 -translate-x-1/2 w-full max-w-lg h-96 bg-orange-600/10 rounded-full blur-[100px] pointer-events-none"></div>

    <header class="w-full max-w-md pt-6 pb-4 flex flex-col items-center relative z-10">
        <img src="/KECOs2.png" alt="KECO's Logo" class="w-60 drop-shadow-2xl" />
    </header>
    
    <!-- Banner Promocional Principal (Hero) -->
    <div class="w-full max-w-md px-4 mb-6 relative z-10">
        <div class="w-full h-48 rounded-2xl flex items-center justify-center overflow-hidden relative shadow-[0_10px_30px_rgba(249,115,22,0.1)] border border-white/10 group">
            
            <!-- Imagen de fondo -->
            <img src="/banner-principal.png" alt="Especialidad KECOs" class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
            
            <!-- Gradiente MUCHO más oscuro para garantizar la lectura -->
            <div class="absolute inset-0 bg-gradient-to-t from-black via-black/70 to-transparent/10"></div>
            
            <!-- Texto superpuesto con sombra forzada -->
            <div class="absolute bottom-4 left-5 flex flex-col z-10">
                <span class="text-orange-500 font-black text-[10px] tracking-widest uppercase mb-1 drop-shadow-md">Especialidad de la casa</span>
                <span class="text-zinc-50 font-black text-2xl tracking-wide drop-shadow-[0_2px_4px_rgba(0,0,0,1)]">SMASH BURGERS</span>
            </div>
            
        </div>
    </div>

    <!-- Navegación Sticky -->
    <nav class="w-full max-w-md sticky top-0 z-50 bg-zinc-950/90 backdrop-blur-md py-3 px-4 mb-2 border-b border-white/5">
        <div class="flex gap-3 overflow-x-auto pb-2 scrollbar-hide" style="scrollbar-width: none;">
            <button 
                v-for="categoria in categorias" 
                :key="categoria"
                @click="activeTab = categoria"
                :class="[
                    'px-5 py-2 rounded-full font-bold text-sm whitespace-nowrap transition-all border',
                    activeTab === categoria 
                        ? 'bg-orange-500 text-zinc-950 border-orange-500 shadow-[0_0_15px_rgba(249,115,22,0.4)]' 
                        : 'bg-zinc-900/50 text-zinc-400 border-white/10 hover:border-orange-500/50'
                ]"
            >
                {{ categoria }}
            </button>
        </div>
    </nav>
    
    <main class="w-full max-w-md px-4 relative z-10">
        
        <!-- ============================== -->
        <!--     SECCIÓN HAMBURGUESAS       -->
        <!-- ============================== -->
        <div v-show="activeTab === 'Hamburguesas'" class="animate-fade-in">
            
            <h2 class="text-2xl font-black text-orange-500 mt-6 mb-6 tracking-widest uppercase drop-shadow-md">Pan de Manteca</h2>
            <div class="flex flex-col mb-6">
                <div v-for="item in panDePapa" :key="item.id" class="relative flex justify-between items-center py-5 border-b border-zinc-800/60 active:bg-white/[0.02] transition-colors">
                    <div v-if="item.badge" class="absolute top-1 left-0 bg-orange-500 text-zinc-950 text-[10px] font-black px-2 py-0.5 rounded-sm uppercase tracking-wider">
                        {{ item.badge }}
                    </div>
                    <div class="text-left flex-1 pr-4 mt-2">
                        <span class="text-xl font-bold text-zinc-50 block uppercase tracking-wide">{{ item.name }}</span>
                    </div>
                    <span class="text-xl font-black text-orange-400">{{ formatPrice(item.price) }}</span>
                </div>
            </div>

            <!-- Imagen de Muestra -->
            <div class="w-full max-w-md px-4 mb-4 relative z-10">
                <div class="w-full h-40 bg-zinc-900 rounded-2xl flex items-center justify-center overflow-hidden relative shadow-lg border border-white/5">
                    <!-- Imagen sin opacidad, colores al 100% -->
                    <img src="/banner-burger.png" alt="Hamburguesa KECOs" class="absolute inset-0 w-full h-full object-cover" />
                    
                    <!-- Degradado súper sutil solo para darle profundidad -->
                    <div class="absolute inset-0 bg-gradient-to-t from-zinc-950/40 via-transparent to-transparent z-10 pointer-events-none"></div>
                </div>
            </div>

            <h2 class="text-2xl font-black text-orange-500 mt-8 mb-6 tracking-widest uppercase drop-shadow-md">De la casa</h2>
            <div class="flex flex-col mb-6">
                <div v-for="item in deLaCasa" :key="item.id" class="relative flex justify-between items-center py-5 border-b border-zinc-800/60 active:bg-white/[0.02] transition-colors">
                    <div class="text-left flex-1 pr-4">
                        <span class="text-xl font-bold text-zinc-50 block uppercase tracking-wide">{{ item.name }}</span>
                    </div>
                    <span class="text-xl font-black text-orange-400">{{ formatPrice(item.price) }}</span>
                </div>
            </div>
            
            <!-- Imagen de Muestra -->
            <div class="w-full max-w-md px-4 mb-4 relative z-10">
                <div class="w-full h-40 bg-zinc-900 rounded-2xl flex items-center justify-center overflow-hidden relative shadow-lg border border-white/5">
                    <!-- Imagen sin opacidad, colores al 100% -->
                    <img src="/banner-burger2.png" alt="Hamburguesa KECOs" class="absolute inset-0 w-full h-full object-cover" />
                    
                    <!-- Degradado súper sutil solo para darle profundidad -->
                    <div class="absolute inset-0 bg-gradient-to-t from-zinc-950/40 via-transparent to-transparent z-10 pointer-events-none"></div>
                </div>
            </div>

            <div class="mt-8 mb-8">
                <h3 class="text-lg font-black text-orange-500 mb-4 tracking-widest uppercase drop-shadow-md">Agregados</h3>
                
                <div class="flex flex-col gap-4">
                    <!-- Opción Destacada: Medallón Extra -->
                    <div class="flex justify-between items-center p-4 bg-orange-500/10 border border-orange-500/30 rounded-xl relative overflow-hidden">
                        <!-- Línea decorativa naranja a la izquierda -->
                        <div class="absolute top-0 left-0 w-1 h-full bg-orange-500"></div>
                        
                        <div class="flex flex-col pl-2">
                            <span class="text-orange-400 text-[10px] font-black uppercase tracking-widest mb-1">Recomendado</span>
                            <span class="text-base font-bold text-zinc-50 uppercase tracking-wide">Medallón Extra</span>
                        </div>
                        <span class="text-lg font-black text-orange-400">+ $ 2.000</span>
                    </div>

                    <!-- Lista de Agregados Clásicos -->
                    <div class="p-4 bg-zinc-900/50 border border-white/5 rounded-xl">
                        <!-- Encabezado con el precio por cada uno -->
                        <div class="flex justify-between items-end mb-4 border-b border-white/10 pb-2">
                            <span class="text-sm font-bold text-zinc-400 uppercase tracking-wide">Clásicos</span>
                            <span class="text-sm font-black text-orange-400">+ $ 2.000 c/u</span>
                        </div>
                        
                        <!-- Contenedor flexible para las píldoras de ingredientes -->
                        <div class="flex flex-wrap gap-2.5">
                            <span v-for="agregado in agregadosHamburguesas" :key="agregado" 
                                  class="px-3 py-1.5 bg-zinc-800/40 border border-zinc-700/50 text-zinc-300 text-[11px] font-bold uppercase tracking-wider rounded-lg shadow-sm">
                                {{ agregado }}
                            </span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- CAJA DESTACADA: BiG BURGER -->
            <h2 class="text-2xl font-black text-orange-500 mt-12 mb-6 tracking-widest uppercase drop-shadow-md text-center">
                BiG Burger
            </h2>
            
            <div class="relative bg-gradient-to-br from-zinc-900 to-zinc-950 p-1 rounded-3xl mb-12 shadow-[0_0_20px_rgba(249,115,22,0.15)] mx-auto w-full">
                <!-- Borde iluminado -->
                <div class="absolute inset-0 rounded-3xl border-2 border-orange-500/40 pointer-events-none"></div>
                <!-- Etiqueta superior centrada -->
                <div class="absolute -top-3 left-1/2 -translate-x-1/2 bg-orange-500 text-zinc-950 font-black px-4 py-1 rounded-full text-xs uppercase tracking-widest shadow-lg z-20">
                    Combos
                </div>
                
                <div class="bg-zinc-900/80 rounded-[22px] p-5 pt-8 backdrop-blur-sm flex flex-col gap-4 relative z-10">
                    <div v-for="combo in bigBurger" :key="combo.id" class="flex flex-row justify-between items-center border-b border-zinc-800/60 pb-4 last:border-0 last:pb-0 gap-4">
                        <span class="text-[14px] font-bold text-zinc-50 uppercase tracking-wide text-left leading-tight">
                            {{ combo.name }}
                        </span>
                        <span class="text-xl font-black text-orange-400 whitespace-nowrap text-right">
                            {{ formatPrice(combo.price) }}
                        </span>
                    </div>
                </div>
            </div>

            <!-- TARJETAS GIGANTES: EDICIONES ESPECIALES -->
            <h2 class="text-2xl font-black text-orange-500 mt-8 mb-6 tracking-widest uppercase drop-shadow-md text-center">
                Ediciones Especiales
            </h2>
            
            <div class="flex flex-col gap-8 mb-10 w-full">
                <div v-for="promo in especiales" :key="promo.id" class="relative w-full min-h-[450px] flex flex-col justify-end rounded-3xl overflow-hidden shadow-2xl border border-white/10 bg-zinc-900 mx-auto">
                    <img :src="promo.image" :alt="promo.name" class="absolute inset-0 w-full h-full object-cover opacity-90" />
                    <div class="relative z-10 w-full bg-gradient-to-t from-zinc-950 via-zinc-950/90 to-transparent p-6 pt-24 flex justify-between items-end">
                        <h3 class="text-2xl font-black text-zinc-50 uppercase tracking-widest drop-shadow-lg">
                            {{ promo.name }}
                        </h3>
                        <span class="text-xl font-black text-orange-400 bg-orange-950/90 px-3 py-1 rounded-xl border border-orange-500/50 backdrop-blur-md shadow-lg">
                            {{ formatPrice(promo.price) }}
                        </span>
                    </div>
                </div>
            </div>
        </div>

        <!-- ============================== -->
        <!--         SECCIÓN PIZZAS         -->
        <!-- ============================== -->
        <div v-show="activeTab === 'Pizzas'" class="animate-fade-in">
            
            <h2 class="text-2xl font-black text-orange-500 mt-6 mb-6 tracking-widest uppercase drop-shadow-md">Pizzas</h2>
            
            <div class="flex flex-col mb-6">
                <div v-for="pizza in pizzas" :key="pizza.id" class="relative flex justify-between items-center py-5 border-b border-zinc-800/60 active:bg-white/[0.02] transition-colors">
                    
                    <!-- Etiqueta / Badge (Solo aparece si la pizza tiene la propiedad 'badge') -->
                    <div v-if="pizza.badge" class="absolute top-1 left-0 bg-orange-500 text-zinc-950 text-[10px] font-black px-2 py-0.5 rounded-sm uppercase tracking-wider">
                        {{ pizza.badge }}
                    </div>

                    <!-- Nombre de la pizza (Le agregamos mt-2 para darle espacio al badge) -->
                    <div class="text-left flex-1 pr-4 mt-2">
                        <span class="text-xl font-bold text-zinc-50 block uppercase tracking-wide">{{ pizza.name }}</span>
                    </div>
                    
                    <!-- Contenedor de los precios -->
                    <div class="flex items-center gap-2 sm:gap-4">
                        
                        <!-- Columna X1 -->
                        <div class="flex flex-col items-center min-w-[80px]">
                            <span class="text-[10px] text-zinc-500 font-bold tracking-widest uppercase mb-1">X1</span>
                            <span class="text-xl font-black text-orange-400">{{ formatPrice(pizza.precioX1) }}</span>
                        </div>

                        <!-- Columna X2 -->
                        <div class="flex flex-col items-center min-w-[80px]">
                            <template v-if="pizza.precioX2">
                                <span class="text-[10px] text-zinc-500 font-bold tracking-widest uppercase mb-1">X2</span>
                                <span class="text-xl font-black text-orange-400">{{ formatPrice(pizza.precioX2) }}</span>
                            </template>
                        </div>

                    </div>

                </div>
            </div>

            <!-- Imagen de Muestra -->
            <div class="w-full max-w-md px-4 mb-4 relative z-10">
                <div class="w-full h-40 bg-zinc-900 rounded-2xl flex items-center justify-center overflow-hidden relative shadow-lg border border-white/5">
                    <!-- Imagen sin opacidad, colores al 100% -->
                    <img src="/pizza-banner.png" alt="Hamburguesa KECOs" class="absolute inset-0 w-full h-full object-cover" />
                    
                    <!-- Degradado súper sutil solo para darle profundidad -->
                    <div class="absolute inset-0 bg-gradient-to-t from-zinc-950/40 via-transparent to-transparent z-10 pointer-events-none"></div>
                </div>
            </div>
        </div>

        <!-- ============================== -->
        <!--         SECCIÓN LOMOS          -->
        <!-- ============================== -->
        <div v-show="activeTab === 'Lomos'" class="animate-fade-in">
            
            <h2 class="text-2xl font-black text-orange-500 mt-6 mb-6 tracking-widest uppercase drop-shadow-md">Lomos</h2>
            <div class="flex flex-col mb-6">
                <div v-for="lomo in lomos" :key="lomo.id" class="relative flex justify-between items-center py-5 border-b border-zinc-800/60 active:bg-white/[0.02] transition-colors">
                    <div v-if="lomo.badge" class="absolute top-1 left-0 bg-orange-500 text-zinc-950 text-[10px] font-black px-2 py-0.5 rounded-sm uppercase tracking-wider">
                        {{ lomo.badge }}
                    </div>

                    <div class="text-left flex-1 pr-4 mt-2">
                        <span class="text-xl font-bold text-zinc-50 block uppercase tracking-wide">{{ lomo.name }}</span>
                    </div>
                    
                    <div v-if="lomo.precio30" class="flex items-center gap-5">
                        <div class="flex flex-col items-center">
                            <span class="text-[10px] text-zinc-500 font-bold tracking-widest uppercase mb-1">22 CM</span>
                            <span class="text-xl font-black text-orange-400">{{ formatPrice(lomo.precio22) }}</span>
                        </div>
                        <div class="flex flex-col items-center">
                            <span class="text-[10px] text-zinc-500 font-bold tracking-widest uppercase mb-1">30 CM</span>
                            <span class="text-xl font-black text-orange-400">{{ formatPrice(lomo.precio30) }}</span>
                        </div>
                    </div>
                    <div v-else class="flex items-center">
                        <span class="text-xl font-black text-orange-400">{{ formatPrice(lomo.precioUnico) }}</span>
                    </div>
                </div>
            </div>

            <!-- Nuevo apartado de Milanesas dentro de Lomos -->
            <h2 class="text-2xl font-black text-orange-500 mt-8 mb-6 tracking-widest uppercase drop-shadow-md">Sándwich de Milanesa</h2>
            <div class="flex flex-col mb-6">
                <div v-for="mila in milanesas" :key="mila.id" class="relative flex justify-between items-center py-5 border-b border-zinc-800/60 active:bg-white/[0.02] transition-colors">
                    <div class="text-left flex-1 pr-4">
                        <span class="text-xl font-bold text-zinc-50 block uppercase tracking-wide">{{ mila.name }}</span>
                    </div>
                    <span class="text-xl font-black text-orange-400">{{ formatPrice(mila.price) }}</span>
                </div>
            </div>

            <!-- Imagen de Muestra -->
            <div class="w-full max-w-md px-4 mb-4 relative z-10">
                <div class="w-full h-40 bg-zinc-900 rounded-2xl flex items-center justify-center overflow-hidden relative shadow-lg border border-white/5">
                    <!-- Imagen sin opacidad, colores al 100% -->
                    <img src="/lomo-banner.png" alt="Hamburguesa KECOs" class="absolute inset-0 w-full h-full object-cover" />
                    
                    <!-- Degradado súper sutil solo para darle profundidad -->
                    <div class="absolute inset-0 bg-gradient-to-t from-zinc-950/40 via-transparent to-transparent z-10 pointer-events-none"></div>
                </div>
            </div>
        </div>

        <!-- ============================== -->
        <!--         SECCIÓN PANCHOS        -->
        <!-- ============================== -->
        <div v-show="activeTab === 'Panchos'" class="animate-fade-in">
            
            <h2 class="text-2xl font-black text-orange-500 mt-6 mb-6 tracking-widest uppercase drop-shadow-md">Pan Clásico</h2>
            
            <div class="flex flex-col mb-6">
                <div v-for="pancho in panchosClasicos" :key="pancho.id" class="relative flex justify-between items-center py-5 border-b border-zinc-800/60 active:bg-white/[0.02] transition-colors">
                    
                    <!-- 1. El cartelito usando la variable "pancho" -->
                    <div v-if="pancho.badge" class="absolute top-1 left-0 bg-orange-500 text-zinc-950 text-[10px] font-black px-2 py-0.5 rounded-sm uppercase tracking-wider">
                        {{ pancho.badge }}
                    </div>

                    <!-- 2. Al contenedor del nombre le agregamos mt-2 -->
                    <div class="text-left flex-1 pr-4 mt-2">
                        <span class="text-xl font-bold text-zinc-50 block uppercase tracking-wide">{{ pancho.name }}</span>
                    </div>
                    
                    <span class="text-xl font-black text-orange-400">{{ formatPrice(pancho.price) }}</span>
                </div>
            </div>

            <h2 class="text-2xl font-black text-orange-500 mt-8 mb-6 tracking-widest uppercase drop-shadow-md">A la Masa</h2>
            
            <div class="flex flex-col mb-8">
                <div v-for="pancho in panchosMasa" :key="pancho.id" class="relative flex justify-between items-center py-5 border-b border-zinc-800/60 active:bg-white/[0.02] transition-colors">
                    <div class="text-left flex-1 pr-4">
                        <span class="text-xl font-bold text-zinc-50 block uppercase tracking-wide">{{ pancho.name }}</span>
                    </div>
                    <span class="text-xl font-black text-orange-400">{{ formatPrice(pancho.price) }}</span>
                </div>
            </div>

            <!-- Destacado de Agregados estilo "Chips" -->
            <h2 class="text-xl font-black text-orange-500 mt-4 mb-4 tracking-widest uppercase drop-shadow-md">Agregados</h2>
            
            <div class="bg-zinc-900/40 backdrop-blur-sm p-5 rounded-2xl border border-dashed border-orange-500/40 mb-10 shadow-lg">
                <!-- Contenedor flex para que las etiquetas se acomoden solas -->
                <div class="flex flex-wrap gap-2 mb-5">
                    <span v-for="agregado in agregadosPanchos" :key="agregado" class="text-xs font-bold text-zinc-300 bg-zinc-950 px-3 py-1.5 rounded-md border border-white/5 uppercase tracking-wide">
                        {{ agregado }}
                    </span>
                </div>
                
                <div class="flex justify-between items-center border-t border-zinc-800/60 pt-4">
                    <span class="text-sm font-bold text-zinc-500 uppercase tracking-widest">Valor Adicional</span>
                    <span class="text-2xl font-black text-orange-400">$ 2.000 <span class="text-sm text-zinc-500 font-bold uppercase">c/u</span></span>
                </div>
            </div>

            <!-- Imagen de Muestra -->
            <div class="w-full max-w-md px-4 mb-4 relative z-10">
                <div class="w-full h-40 bg-zinc-900 rounded-2xl flex items-center justify-center overflow-hidden relative shadow-lg border border-white/5">
                    <!-- Imagen sin opacidad, colores al 100% -->
                    <img src="/pancho-banner.png" alt="Hamburguesa KECOs" class="absolute inset-0 w-full h-full object-cover" />
                    
                    <!-- Degradado súper sutil solo para darle profundidad -->
                    <div class="absolute inset-0 bg-gradient-to-t from-zinc-950/40 via-transparent to-transparent z-10 pointer-events-none"></div>
                </div>
            </div>

        </div>

        <!-- === SECCIÓN PAPAS === -->
        <div v-show="activeTab === 'Papas'" class="animate-fade-in">
            <h2 class="text-2xl font-black text-orange-500 mt-6 mb-6 tracking-widest uppercase drop-shadow-md">Papas</h2>
            
            <div class="flex flex-col mb-6">
                <div v-for="papa in papas" :key="papa.id" class="relative flex justify-between items-center py-5 border-b border-zinc-800/60 active:bg-white/[0.02] transition-colors">
                    <div class="text-left flex-1 pr-4">
                        <span class="text-xl font-bold text-zinc-50 block uppercase tracking-wide">{{ papa.name }}</span>
                    </div>
                    <span class="text-xl font-black text-orange-400">{{ formatPrice(papa.price) }}</span>
                </div>
            </div>

            <!-- Imagen de Muestra -->
            <div class="w-full max-w-md px-4 mb-4 relative z-10">
                <div class="w-full h-40 bg-zinc-900 rounded-2xl flex items-center justify-center overflow-hidden relative shadow-lg border border-white/5">
                    <!-- Imagen sin opacidad, colores al 100% -->
                    <img src="/papas-banner.png" alt="Hamburguesa KECOs" class="absolute inset-0 w-full h-full object-cover" />
                    
                    <!-- Degradado súper sutil solo para darle profundidad -->
                    <div class="absolute inset-0 bg-gradient-to-t from-zinc-950/40 via-transparent to-transparent z-10 pointer-events-none"></div>
                </div>
            </div>
        </div>

        <!-- ============================== -->
        <!--         SECCIÓN BEBIDAS        -->
        <!-- ============================== -->
        <div v-show="activeTab === 'Bebidas'" class="animate-fade-in w-full">
            
            <h2 class="text-2xl font-black text-orange-500 mt-6 mb-6 tracking-widest uppercase drop-shadow-md">Bebidas</h2>
            
            <div class="flex flex-col mb-10">
                <div v-for="bebida in bebidas" :key="bebida.id" class="relative flex justify-between items-center py-5 border-b border-zinc-800/60 active:bg-white/[0.02] transition-colors">
                    
                    <div class="text-left flex-1 pr-4">
                        <span class="text-xl font-bold text-zinc-50 block uppercase tracking-wide">{{ bebida.name }}</span>
                    </div>
                    
                    <div class="flex items-center">
                        <span class="text-xl font-black text-orange-400">{{ formatPrice(bebida.price) }}</span>
                    </div>

                </div>
            </div>

            <!-- Imagen de Muestra Bebidas -->
            <div class="w-full h-40 bg-zinc-900 rounded-2xl flex items-center justify-center overflow-hidden relative shadow-lg border border-white/5 mb-10">
                <img src="/foto-bebidas.jpg" alt="Bebidas KECOs" class="absolute inset-0 w-full h-full object-cover" />
                <div class="absolute inset-0 bg-gradient-to-t from-zinc-950/40 via-transparent to-transparent z-10 pointer-events-none"></div>
            </div>
            
        </div>

    </main>

    <!-- ============================== -->
    <!--           FOOTER / CONTACTO    -->
    <!-- ============================== -->
    <footer class="w-full max-w-md mt-auto pt-12 pb-8 px-4 flex flex-col items-center border-t border-zinc-800/50 relative z-10">
        
        <h3 class="text-xs font-black text-zinc-500 uppercase tracking-widest mb-5">Hacé tu pedido</h3>
        
        <div class="flex gap-4 w-full">
            <!-- Botón WhatsApp -->
            <a href="https://wa.me/5492634635298" target="_blank" class="flex-1 flex items-center justify-center gap-2 bg-zinc-900/80 border border-white/5 hover:border-[#25D366]/50 text-zinc-300 py-3.5 rounded-2xl transition-all shadow-lg group">
                <svg class="w-5 h-5 text-[#25D366] group-hover:scale-110 transition-transform" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51h-.57c-.198 0-.52.074-.792.347-.272.273-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
                <span class="font-bold text-sm tracking-wide">WhatsApp</span>
            </a>
            
            <!-- Botón Instagram -->
            <a href="https://www.instagram.com/kecos_food/" target="_blank" class="flex-1 flex items-center justify-center gap-2 bg-zinc-900/80 border border-white/5 hover:border-[#E1306C]/50 text-zinc-300 py-3.5 rounded-2xl transition-all shadow-lg group">
                <svg class="w-5 h-5 text-[#E1306C] group-hover:scale-110 transition-transform" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/></svg>
                <span class="font-bold text-sm tracking-wide">Instagram</span>
            </a>
        </div>
        
        <p class="text-[11px] text-zinc-600 mt-8 text-center uppercase tracking-widest font-medium">
            La Colonia, Mendoza<br/>
            © 2026 KECO's FOOD
        </p>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const categorias = ['Hamburguesas', 'Pizzas', 'Lomos', 'Panchos', 'Papas', 'Bebidas'] 
// Cambiá esta variable si querés que la página arranque en otra pestaña
const activeTab = ref('Hamburguesas')

const formatPrice = (price) => {
    return price.toLocaleString('es-AR', { style: 'currency', currency: 'ARS', minimumFractionDigits: 0 })
}

// Datos de Hamburguesas
const panDePapa = ref([
      { id: 1, name: "Moe (clásica)", price: 8000 },
      { id: 2, name: "Larry (doble cheese)", price: 10000, badge: "Más vendida" },
      { id: 3, name: "Curly (Oklahoma)", price: 11000 },
      { id: 4, name: "Con cheddar y Doritos", price: 10000 },
      { id: 5, name: "Hambur. Desmechada", price: 9000 },
      { id: 6, name: "Texas", price: 12000, badge: "Recomendada" },
      { id: 7, name: "Burger de Pollo", price: 8000 },
])

const deLaCasa = ref([
      { id: 7, name: "x1", price: 6000 },
      { id: 8, name: "x3 + papas", price: 20000 },
      { id: 9, name: "x3 + papas + gaseosa", price: 23000 },
      { id: 10, name: "Hambur pizza", price: 33000 },
])

const agregadosHamburguesas = ref([
    "Huevo", "Criolla", "Aceituna", "Barbacoa", 
    "Queso azul", "Picante", "Bacon", "Cheddar", 
    "Lluvia de papas", "Doritos"
])

// Nuevos Datos: Pizzas (Extraídos de WhatsApp Image 2026-07-21 at 18.57.47 (1)_2.jpeg)
const pizzas = ref([
      { id: 1, name: "Común", precioX1: 10000, precioX2: 18000 },
      { id: 2, name: "Doble Queso", precioX1: 13000, precioX2: 24000 },
      { id: 3, name: "Especial", precioX1: 15000, precioX2: 28000, badge: "Más vendida" },
      { id: 4, name: "Primavera", precioX1: 15000, precioX2: 28000 },
      { id: 5, name: "Fugazza", precioX1: 13000},
      { id: 6, name: "Fugazzeta", precioX1: 15000},
      { id: 7, name: "Calabresa", precioX1: 15000},
      { id: 8, name: "Con Palmitos", precioX1: 15000},
      { id: 9, name: "Con Champiñones", precioX1: 15000},
      { id: 10, name: "Con Roquefort", precioX1: 15000},
      { id: 11, name: "Primavera", precioX1: 15000},
      { id: 12, name: "Con Doritos", precioX1: 16000},
      { id: 13, name: "Con Bacon", precioX1: 20000},
      { id: 14, name: "Pizza Kecos", precioX1: 20000, badge: "Recomendada" },
      { id: 15, name: "La Envidiada", precioX1: 23000, precioX2: 40000, badge: "Premium" },
])

// Nuevos Datos: Lomos
const lomos = ref([
      { id: 1, name: "Lomos Completos", precio22: 15000, precio30: 19000, badge: "Más vendidos" },
      { id: 2, name: "Carne Desmechada", precio22: 15000, precio30: 19000, badge: "Recomendado" },
      { id: 3, name: "Lomo Pizza", precioUnico: 38000, badge: "Premium" },
      { id: 4, name: "Kecolucos", precioUnico: 20000 },
])

// Nuevos Datos: Panchos
const panchosClasicos = ref([
      { id: 1, name: "Común", price: 2500 },
      { id: 2, name: "Al poncho", price: 3000 },
      { id: 3, name: "A la pizza", price: 4000, badge: "Más vendido" },
      { id: 4, name: "Con cheddar y bacon", price: 5000, badge: "Recomendado" },
      { id: 5, name: "Queso azul", price: 3500 },
])

const panchosMasa = ref([
      { id: 1, name: "Común", price: 3000 },
      { id: 2, name: "Al poncho", price: 3500 },
      { id: 3, name: "A la pizza", price: 4500, badge: "Más vendido" },
      { id: 4, name: "Con cheddar y bacon", price: 6000, badge: "Premium" },
      { id: 5, name: "Queso azul", price: 4000 },
])

const agregadosPanchos = ref([
    "Huevo", "Choclo", "Criolla", "Aceituna", "Barbacoa", 
    "Queso azul", "Picante", "Bacon", "Cheddar", 
    "Lluvia de papas", "Doritos"
])

// Nuevos Datos: Milanesas
const milanesas = ref([
    { id: 1, name: "Común", price: 18000 },
    { id: 2, name: "Napolitana", price: 20000 }
])

// Nuevos Datos: Papas
const papas = ref([
    { id: 1, name: "Común", price: 5000 },
    { id: 2, name: "Salchipapas", price: 7000 },
    { id: 3, name: "Con cheddar y bacon", price: 13000 },
    { id: 4, name: "Con cheddar y Doritos", price: 12000 },
    { id: 5, name: "Papas a caballo", price: 7000 },
    { id: 6, name: "Nuggets de Pollo", price: 6000 },
])

// Nuevos Datos: Combos Big Burger
const bigBurger = ref([
    { id: 1, name: "1 Burger", price: 12000 },
    { id: 2, name: "2 Burgers + Papas + Pepsi/Seven", price: 28000 },
    { id: 3, name: "3 Burgers + Papas + Pepsi/Seven", price: 35000 },
])

// Nuevos Datos: Ediciones Especiales (Posters)
const especiales = ref([
    { id: 1, name: "La Aconcagua", price: 16000, image: "/promo1.jpeg" },
    { id: 2, name: "El Chapo", price: 14000, image: "/promo2.jpeg" },
    { id: 3, name: "Don Ramón", price: 12000, image: "/promo3.jpeg" },
    { id: 4, name: "La Argenta", price: 8000, image: "/promo4.jpeg" },
])

// Nuevos Datos: Bebidas
// Nuevos Datos: Bebidas
const bebidas = ref([
    { id: 1, name: "Gaseosa 500 ml", price: 1500 },
    { id: 2, name: "Jugo Cepita 1.5 Lts", price: 4500 },
    { id: 3, name: "Jugo Aquarius 2.5 Lts", price: 4500 },
    { id: 4, name: "Jugo Levite 2.5 Lts", price: 4000 },
    { id: 5, name: "Seven 2.25 Lts", price: 3500 },
    { id: 6, name: "Pepsi 2.25 Lts", price: 3500 },
    { id: 7, name: "Coca-Cola 2.5 Lts", price: 6000 },
    { id: 8, name: "Fanta 2.5 Lts", price: 6000 },
    { id: 9, name: "Sprite 2.5 Lts", price: 6000 },
    { id: 10, name: "Cerveza 710 ml", price: 4500 }
])
</script>

<style>
.scrollbar-hide::-webkit-scrollbar {
    display: none;
}
.animate-fade-in {
    animation: fadeIn 0.4s ease-out;
}
@keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
}
</style>