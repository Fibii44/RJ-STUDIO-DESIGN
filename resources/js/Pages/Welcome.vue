<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: Boolean,
    canRegister: Boolean,
});

const projects = [
    {
        title: 'The Terraced Villa',
        category: 'Residential',
        image: 'https://images.unsplash.com/photo-1600585154340-be6199f7a009?q=80&w=1000',
        year: '2025',
        span: 'md:col-span-2' 
    },
    {
        title: 'Brutalista Office Hub',
        category: 'Commercial',
        image: 'https://images.unsplash.com/photo-1486406146926-c627a92ad1ab?q=80&w=1000',
        year: '2025',
        span: 'md:col-span-1'
    },
    {
        title: 'Minimalist Zen Retreat',
        category: 'Interior',
        image: 'https://images.unsplash.com/photo-1600210492486-724fe5c67fb0?q=80&w=1000',
        year: '2024',
        span: 'md:col-span-1'
    },
    {
        title: 'Glass Pavilion',
        category: 'Experimental',
        image: 'https://images.unsplash.com/photo-1564013799919-ab600027ffc6?q=80&w=1000',
        year: '2024',
        span: 'md:col-span-2'
    }
];
</script>

<template>
    <Head title="RJ Design Studio | Architectural Excellence" />

    <div class="bg-[#FCFAf7] text-[#433932] min-h-screen font-serif selection:bg-[#D4B996] selection:text-white overflow-x-hidden">
        
        <nav class="fixed w-full z-50 bg-[#FCFAf7]/80 backdrop-blur-xl px-6 lg:px-12 py-6 flex justify-between items-center border-b border-[#EADDCD]/50 transition-all duration-500">
            <div class="flex flex-col">
                <span class="text-[9px] tracking-[0.5em] text-[#D4B996] font-bold uppercase mb-1">Architectural Bureau</span>
                <div class="text-2xl font-light tracking-[0.15em] uppercase leading-none">
                    RJ <span class="italic font-serif text-[#D4B996] tracking-normal">Design Studio</span>
                </div>
            </div>
            
            <div v-if="canLogin" class="flex items-center space-x-6 lg:space-x-10 text-[10px] font-bold uppercase tracking-[0.3em]">
                <Link :href="route('login')" class="hover:text-[#D4B996] transition-colors relative group py-2">
                    Log In
                    <span class="absolute bottom-0 left-0 w-0 h-[1px] bg-[#D4B996] transition-all group-hover:w-full"></span>
                </Link>

                <Link v-if="canRegister" :href="route('register')" 
                    class="hidden sm:block bg-[#433932] text-[#FCFAf7] px-6 lg:px-8 py-3 lg:py-4 hover:bg-[#D4B996] transition-all duration-500 shadow-lg hover:shadow-[#D4B996]/20">
                    Sign Up
                </Link>
            </div>
        </nav>

        <main>
            <section class="relative min-h-screen flex items-center px-6 lg:px-12 pt-20">
                <div class="absolute right-0 top-0 w-full lg:w-1/2 h-full bg-[#EADDCD]/20 -z-10"></div>
                
                <div class="max-w-screen-2xl mx-auto grid lg:grid-cols-12 gap-12 items-center w-full">
                    <div class="lg:col-span-6 py-12 lg:pr-12 order-2 lg:order-1">
                        <span class="inline-block text-[#D4B996] text-xs font-bold uppercase tracking-[0.6em] mb-6">Est. MMXXVI</span>
                        <h1 class="text-6xl lg:text-[100px] leading-[0.9] mb-12 tracking-tighter">
                            Modern <br/> 
                            <span class="italic font-light text-[#D4B996] pl-8 lg:pl-20 block mt-4">Structures.</span>
                        </h1>
                        <p class="text-[#8C7E71] text-lg font-sans font-light leading-relaxed mb-12 max-w-md border-l border-[#D4B996] pl-8">
                            We synchronize natural light with rigid structural geometry to create spaces that inspire living.
                        </p>
                        <div class="flex items-center">
                            <Link :href="route('register')" class="group flex items-center space-x-6">
                                <span class="bg-[#433932] text-white p-5 rounded-full group-hover:bg-[#D4B996] transition-colors duration-500">
                                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                                </span>
                                <span class="text-[10px] font-bold uppercase tracking-[0.4em]">Inquire for Schedule</span>
                            </Link>
                        </div>
                    </div>

                    <div class="lg:col-span-6 relative h-[400px] lg:h-[650px] order-1 lg:order-2">
                        <div class="absolute inset-0 bg-[#EADDCD] translate-x-6 translate-y-6 z-0 opacity-50"></div>
                        <div class="relative w-full h-full overflow-hidden shadow-2xl z-10 border-[8px] lg:border-[12px] border-[#FCFAf7]">
                            <img src="https://images.unsplash.com/photo-1600607687940-47a04b621757?q=80&w=2070" class="w-full h-full object-cover scale-110 hover:scale-100 transition-transform duration-[2000ms]" />
                        </div>
                    </div>
                </div>
            </section>

            <section class="py-32 lg:py-48 px-6 lg:px-12 bg-white relative">
                <div class="max-w-screen-2xl mx-auto">
                    <div class="flex flex-col lg:flex-row justify-between items-end mb-24 gap-8">
                        <div class="max-w-xl">
                            <h2 class="text-5xl lg:text-7xl font-light leading-none mb-6 italic text-[#D4B996]">The <span class="not-italic text-[#433932]">Archives</span></h2>
                            <p class="font-sans text-[#8C7E71] tracking-wide uppercase text-[9px] font-bold">Previewing our latest residential & commercial blueprints</p>
                        </div>
                        <Link href="#" class="text-[10px] font-bold uppercase tracking-[0.4em] border-b border-[#433932] pb-2 hover:text-[#D4B996] hover:border-[#D4B996] transition">View Full Portfolio</Link>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-3 gap-10">
                        <div v-for="project in projects" :key="project.title" 
                            :class="[project.span, 'group relative overflow-hidden bg-[#FCFAf7] shadow-sm hover:shadow-2xl transition-shadow duration-700']">
                            <div class="aspect-[16/10] md:aspect-auto md:h-[450px] overflow-hidden">
                                <img :src="project.image" class="w-full h-full object-cover grayscale group-hover:grayscale-0 group-hover:scale-110 transition duration-[1500ms]" />
                            </div>
                            <div class="absolute bottom-0 left-0 w-full p-8 translate-y-full group-hover:translate-y-0 transition-transform duration-500 bg-gradient-to-t from-[#433932] to-transparent text-white">
                                <p class="text-[9px] uppercase tracking-[0.3em] mb-2 font-bold">{{ project.category }} — {{ project.year }}</p>
                                <h3 class="text-2xl font-light italic">{{ project.title }}</h3>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <section class="bg-[#433932] py-32 lg:py-48 px-6 lg:px-12 relative overflow-hidden">
                <div class="max-w-4xl mx-auto text-center relative z-10">
                    <span class="text-[#D4B996] text-[10px] font-bold uppercase tracking-[0.6em] mb-8 block">Project Planning</span>
                    <h2 class="text-4xl lg:text-6xl mb-12 font-light text-[#FCFAf7] leading-tight">Ready to map out <br/> your <span class="italic text-[#D4B996]">vision?</span></h2>
                    <p class="font-sans text-[#EADDCD]/60 text-base lg:text-lg mb-16 font-light leading-relaxed max-w-2xl mx-auto">
                        Our scheduling tool allows you to sync directly with our studio calendar for site visits and technical reviews.
                    </p>
                    <Link :href="route('register')" class="inline-block bg-[#FCFAf7] text-[#433932] px-12 lg:px-20 py-6 lg:py-8 text-[10px] font-bold uppercase tracking-[0.5em] hover:bg-[#D4B996] hover:text-white transition duration-500 rounded-sm">
                        Access Scheduling System
                    </Link>
                </div>
            </section>
        </main>

        <footer class="bg-[#FCFAf7] border-t border-[#EADDCD] py-20 px-6 lg:px-12">
            <div class="max-w-screen-2xl mx-auto grid md:grid-cols-2 gap-20">
                <div class="text-3xl font-light tracking-tighter uppercase">
                    RJ <span class="italic text-[#D4B996]">Studio</span>
                </div>
                <div class="grid grid-cols-2 gap-8">
                    <div class="space-y-4">
                        <h4 class="text-[9px] font-bold uppercase tracking-widest text-[#D4B996]">Region</h4>
                        <p class="text-[11px] font-sans text-[#8C7E71] leading-relaxed">Malaybalay City, <br/> Bukidnon, PH</p>
                    </div>
                    <div class="space-y-4">
                        <h4 class="text-[9px] font-bold uppercase tracking-widest text-[#D4B996]">Connect</h4>
                        <p class="text-[11px] font-sans text-[#8C7E71]">hello@rjdesign.studio</p>
                    </div>
                </div>
            </div>
            <div class="mt-20 pt-8 border-t border-[#EADDCD]/50 text-center">
                <p class="text-[9px] uppercase tracking-[0.4em] text-[#8C7E71]">&copy; 2026 RJ Design Studio • Architectural Excellence</p>
            </div>
        </footer>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Inter:wght@300;400;700&display=swap');
.font-serif { font-family: 'Playfair Display', serif; }
.font-sans { font-family: 'Inter', sans-serif; }
</style>