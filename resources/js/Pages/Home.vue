<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import Welcome from '@/Components/Welcome.vue';

const stats = [
    { label: 'Active Blueprints', value: '03' },
    { label: 'Next Site Visit', value: 'Jan 28' },
    { label: 'Pending Reviews', value: '01' },
];

const activeProjects = [
    {
        name: 'The Terraced Villa',
        status: 'In Progress',
        phase: 'Structural Framing',
        progress: 65,
        image: 'https://images.unsplash.com/photo-1600585154340-be6199f7a009?q=80&w=500',
    },
    {
        name: 'Zen Retreat Interior',
        status: 'Planning',
        phase: 'Material Selection',
        progress: 20,
        image: 'https://images.unsplash.com/photo-1600210492486-724fe5c67fb0?q=80&w=500',
    }
];
</script>

<template>
    <AppLayout title="Client Dashboard">
        <template #header>
            <div class="flex flex-col md:flex-row md:items-center justify-between gap-4">
                <div>
                    <span class="text-[10px] font-bold uppercase tracking-[0.5em] text-[#D4B996]">Client Portal</span>
                    <h2 class="text-3xl font-light text-[#433932] leading-tight">
                        Welcome back, <span class="italic font-serif">{{ $page.props.auth.user.name }}</span>
                    </h2>
                </div>
                <div class="flex space-x-4">
                    <button class="bg-[#433932] text-white px-6 py-2 text-[10px] font-bold uppercase tracking-widest hover:bg-[#D4B996] transition-colors">
                        New Project
                    </button>
                </div>
            </div>
        </template>

        <div class="py-12 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto font-serif">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-12">
                <div v-for="stat in stats" :key="stat.label" 
                     class="bg-white p-8 border border-[#EADDCD]/50 shadow-sm">
                    <p class="text-[9px] uppercase tracking-[0.3em] text-[#8C7E71] mb-2 font-bold font-sans">{{ stat.label }}</p>
                    <p class="text-4xl font-light text-[#433932]">{{ stat.value }}</p>
                </div>
            </div>

            <div class="grid lg:grid-cols-3 gap-12">
                <div class="lg:col-span-2 space-y-8">
                    <h3 class="text-xl font-light tracking-widest uppercase border-b border-[#EADDCD] pb-4 mb-8">Current Assignments</h3>
                    
                    <div v-for="project in activeProjects" :key="project.name" 
                         class="group flex flex-col md:flex-row bg-white border border-[#EADDCD]/50 overflow-hidden hover:shadow-xl transition-shadow duration-500">
                        <div class="w-full md:w-48 h-48 overflow-hidden">
                            <img :src="project.image" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700" />
                        </div>
                        <div class="p-8 flex-1">
                            <div class="flex justify-between items-start mb-4">
                                <div>
                                    <p class="text-[9px] uppercase tracking-tighter text-[#D4B996] font-bold font-sans mb-1">{{ project.status }}</p>
                                    <h4 class="text-2xl font-light italic text-[#433932]">{{ project.name }}</h4>
                                </div>
                                <span class="text-[10px] font-sans font-bold text-[#8C7E71]">{{ project.progress }}%</span>
                            </div>
                            <div class="w-full h-[1px] bg-[#EADDCD] mb-4">
                                <div class="h-full bg-[#D4B996] transition-all duration-1000" :style="{ width: project.progress + '%' }"></div>
                            </div>
                            <p class="text-[11px] font-sans text-[#8C7E71] uppercase tracking-widest">Current Phase: {{ project.phase }}</p>
                        </div>
                    </div>
                </div>

                <div class="space-y-8">
                    <div class="bg-[#433932] p-8 text-[#FCFAf7]">
                        <h4 class="text-lg font-light italic mb-4">Need a site visit?</h4>
                        <p class="text-[11px] font-sans font-light text-[#EADDCD]/70 leading-relaxed mb-6">
                            Schedule a technical review with our lead architect in Malaybalay City.
                        </p>
                        <button class="w-full py-4 border border-[#D4B996] text-[#D4B996] text-[10px] font-bold uppercase tracking-[0.3em] hover:bg-[#D4B996] hover:text-white transition-all">
                            Book Schedule
                        </button>
                    </div>

                    <div class="bg-white border border-[#EADDCD]/50 p-8">
                        <h4 class="text-sm font-bold uppercase tracking-widest mb-6 font-sans">Recent Documents</h4>
                        <ul class="space-y-4">
                            <li v-for="i in 3" :key="i" class="flex items-center space-x-3 text-[11px] font-sans text-[#8C7E71] group cursor-pointer">
                                <svg class="w-4 h-4 text-[#D4B996]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path d="M7 21h10a2 2 0 002-2V9.414a1 1 0 00-.293-.707l-5.414-5.414A1 1 0 0012.586 3H7a2 2 0 00-2 2v14a2 2 0 002 2z"></path></svg>
                                <span class="group-hover:text-[#433932] transition-colors uppercase">Blueprint_Final_Rev{{ i }}.pdf</span>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;1,400&family=Inter:wght@300;400;700&display=swap');
.font-serif { font-family: 'Playfair Display', serif; }
.font-sans { font-family: 'Inter', sans-serif; }
</style>