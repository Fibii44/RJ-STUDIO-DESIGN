<script setup>
import { ref } from 'vue';
import { Head, Link, router } from '@inertiajs/vue3';
import Banner from '@/Components/Banner.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';

defineProps({
    title: String,
});

const showingNavigationDropdown = ref(false);

const logout = () => {
    router.post(route('logout'));
};
</script>

<template>
    <div>
        <Head :title="title" />
        <Banner />

        <div class="min-h-screen bg-[#FCFAf7] text-[#433932] font-serif selection:bg-[#D4B996] selection:text-white">
            <nav class="bg-[#FCFAf7]/80 backdrop-blur-xl border-b border-[#EADDCD]/50 sticky top-0 z-50 transition-all duration-500">
                <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                    <div class="flex justify-between h-24">
                        <div class="flex">
                            <div class="shrink-0 flex items-center">
                                <Link :href="route('home')" class="flex flex-col group">
                                    <span class="text-[8px] tracking-[0.5em] text-[#D4B996] font-bold uppercase leading-none mb-1">Architectural Bureau</span>
                                    <div class="text-xl font-light tracking-[0.15em] uppercase leading-none">
                                        RJ <span class="italic font-serif text-[#D4B996] tracking-normal">Design Studio</span>
                                    </div>
                                </Link>
                            </div>

                            <div class="hidden space-x-8 lg:space-x-12 sm:-my-px sm:ms-16 sm:flex">
                                <NavLink :href="route('home')" :active="route().current('home')" class="nav-text">
                                    Home
                                </NavLink>
                                <NavLink href="#" class="nav-text">
                                    Portfolio
                                </NavLink>
                                <NavLink href="#" class="nav-text">
                                    Services
                                </NavLink>
                                <NavLink href="#" class="nav-text text-[#D4B996] font-bold border-b-2 border-[#D4B996]">
                                    Scheduling
                                </NavLink>
                            </div>
                        </div>

                        <div class="hidden sm:flex sm:items-center sm:ms-6">
                            <div class="ms-3 relative">
                                <Dropdown align="right" width="48">
                                    <template #trigger>
                                        <button type="button" class="inline-flex items-center px-5 py-2.5 border border-[#EADDCD] text-[10px] font-bold uppercase tracking-[0.3em] text-[#433932] hover:bg-[#433932] hover:text-white transition-all duration-500 focus:outline-none">
                                            {{ $page.props.auth.user.name }}
                                            <svg class="ms-2 -me-0.5 size-3" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                                                <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
                                            </svg>
                                        </button>
                                    </template>

                                    <template #content>
                                        <div class="block px-4 py-2 text-[9px] font-bold uppercase tracking-widest text-[#D4B996]">Client Dashboard</div>
                                        <DropdownLink :href="route('profile.show')" class="text-[10px] tracking-widest uppercase">Profile Settings</DropdownLink>
                                        <div class="border-t border-[#EADDCD]/50" />
                                        <form @submit.prevent="logout">
                                            <DropdownLink as="button" class="text-[10px] tracking-widest uppercase text-red-800">Log Out</DropdownLink>
                                        </form>
                                    </template>
                                </Dropdown>
                            </div>
                        </div>

                        <div class="-me-2 flex items-center sm:hidden">
                            <button class="inline-flex items-center justify-center p-2 rounded-md text-[#433932] hover:text-[#D4B996] transition duration-150 ease-in-out" @click="showingNavigationDropdown = ! showingNavigationDropdown">
                                <svg class="size-6" stroke="currentColor" fill="none" viewBox="0 0 24 24">
                                    <path :class="{'hidden': showingNavigationDropdown, 'inline-flex': ! showingNavigationDropdown }" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                                    <path :class="{'hidden': ! showingNavigationDropdown, 'inline-flex': showingNavigationDropdown }" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                                </svg>
                            </button>
                        </div>
                    </div>
                </div>

                <div :class="{'block': showingNavigationDropdown, 'hidden': ! showingNavigationDropdown}" class="sm:hidden bg-[#FCFAf7] border-b border-[#EADDCD]">
                    <div class="pt-2 pb-3 space-y-1">
                        <ResponsiveNavLink :href="route('home')" :active="route().current('home')">Home</ResponsiveNavLink>
                        <ResponsiveNavLink href="#">Portfolio</ResponsiveNavLink>
                        <ResponsiveNavLink href="#">Services</ResponsiveNavLink>
                        <ResponsiveNavLink href="#">Scheduling</ResponsiveNavLink>
                    </div>
                </div>
            </nav>

            <header v-if="$slots.header" class="bg-white/30 border-b border-[#EADDCD]/20">
                <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:px-8">
                    <slot name="header" />
                </div>
            </header>

            <main>
                <slot />
            </main>
        </div>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Inter:wght@300;400;700&display=swap');
.font-serif { font-family: 'Playfair Display', serif; }
.font-sans { font-family: 'Inter', sans-serif; }

.nav-text {
    @apply text-[10px] font-bold uppercase tracking-[0.4em] transition-colors duration-500 hover:text-[#D4B996];
}
</style>