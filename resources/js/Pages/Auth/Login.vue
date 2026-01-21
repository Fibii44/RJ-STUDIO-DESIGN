<script setup>
import { Head, Link, useForm } from '@inertiajs/vue3';
import AuthenticationCardLogo from '@/Components/AuthenticationCardLogo.vue';
import Checkbox from '@/Components/Checkbox.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import TextInput from '@/Components/TextInput.vue';

defineProps({
    canResetPassword: Boolean,
    status: String,
});

const form = useForm({
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.transform(data => ({
        ...data,
        remember: form.remember ? 'on' : '',
    })).post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

I understand—the floating label "Identity / Email" style can feel a bit cluttered or dated if the spacing isn't perfect. Let's pivot to a Boutique Ghost Input style.

Instead of moving labels, we will use very thin, elegant containers with a soft "Sand" background. This looks much more like a modern architectural software interface (like AutoCAD or Revit).

Updated Login.vue (Boutique Ghost Style)
Code snippet

<template>
    <Head title="Client Identity | Login" />

    <div class="flex min-h-screen bg-[#FCFAf7] font-serif selection:bg-[#D4B996] selection:text-white">
        <div class="hidden lg:flex lg:w-1/2 relative bg-[#433932] overflow-hidden">
            <img src="https://images.unsplash.com/photo-1486406146926-c627a92ad1ab?q=80&w=2070" class="absolute inset-0 w-full h-full object-cover opacity-30 mix-blend-overlay" />
            <div class="relative z-10 m-auto text-center px-12">
                <div class="text-[10px] tracking-[0.5em] text-[#D4B996] font-bold uppercase mb-4">Architectural Bureau</div>
                <h2 class="text-5xl text-[#FCFAf7] font-light leading-tight">
                    RJ <span class="italic font-serif text-[#D4B996]">Studio</span>
                </h2>
                <div class="mt-8 w-12 h-[1px] bg-[#D4B996] mx-auto opacity-50"></div>
            </div>
        </div>

        <div class="w-full lg:w-1/2 flex items-center justify-center p-8 lg:p-24 bg-[#FCFAf7]">
            <div class="w-full max-w-sm">
                <div class="mb-12">
                    <h1 class="text-3xl font-light text-[#433932] mb-3 tracking-tight">Access Portal</h1>
                    <div class="h-[2px] w-8 bg-[#D4B996] mb-6"></div>
                    <p class="font-sans text-[10px] uppercase tracking-[0.2em] text-[#8C7E71] leading-relaxed">Please provide your authorized credentials to view project schedules.</p>
                </div>

                <form @submit.prevent="submit" class="space-y-6">
                    <div class="space-y-2">
                        <InputLabel for="email" value="Email Address" class="font-sans text-[9px] uppercase tracking-[0.2em] text-[#433932] font-bold ml-1" />
                        <TextInput
                            id="email"
                            v-model="form.email"
                            type="email"
                            class="w-full bg-[#F3EEE7] border-none py-4 px-5 text-[#433932] text-sm font-sans focus:ring-1 focus:ring-[#D4B996] transition-all duration-300 rounded-none shadow-sm placeholder-[#B5A99E]"
                            placeholder="e.g. client@domain.com"
                            required
                            autofocus
                        />
                        <InputError class="text-[10px] mt-1" :message="form.errors.email" />
                    </div>

                    <div class="space-y-2">
                        <div class="flex justify-between items-center px-1">
                            <InputLabel for="password" value="Security Pass" class="font-sans text-[9px] uppercase tracking-[0.2em] text-[#433932] font-bold" />
                            <Link v-if="canResetPassword" :href="route('password.request')" class="text-[9px] uppercase tracking-widest text-[#D4B996] hover:text-[#433932]">Lost Code?</Link>
                        </div>
                        <TextInput
                            id="password"
                            v-model="form.password"
                            type="password"
                            class="w-full bg-[#F3EEE7] border-none py-4 px-5 text-[#433932] text-sm font-sans focus:ring-1 focus:ring-[#D4B996] transition-all duration-300 rounded-none shadow-sm placeholder-[#B5A99E]"
                            placeholder="••••••••"
                            required
                        />
                        <InputError class="text-[10px] mt-1" :message="form.errors.password" />
                    </div>

                    <div class="flex items-center py-2">
                        <label class="flex items-center cursor-pointer group">
                            <Checkbox v-model:checked="form.remember" class="rounded-none border-none bg-[#EADDCD] text-[#433932] focus:ring-0" />
                            <span class="ms-3 text-[10px] uppercase tracking-widest text-[#8C7E71] group-hover:text-[#433932]">Remember Device</span>
                        </label>
                    </div>

                    <button 
                        type="submit"
                        :class="{ 'opacity-25': form.processing }" 
                        :disabled="form.processing"
                        class="w-full bg-[#433932] text-[#FCFAf7] py-5 text-[10px] font-bold uppercase tracking-[0.5em] hover:bg-[#D4B996] transition-all duration-500 mt-4 shadow-lg active:scale-[0.98]"
                    >
                        Enter Studio
                    </button>
                </form>

                <div class="mt-12 text-center">
                    <Link :href="route('register')" class="text-[10px] uppercase tracking-[0.2em] text-[#8C7E71] hover:text-[#D4B996] transition">
                        New Project? <span class="font-bold border-b border-[#D4B996] pb-1">Register Identity</span>
                    </Link>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Inter:wght@300;400;700&display=swap');
.font-serif { font-family: 'Playfair Display', serif; }
.font-sans { font-family: 'Inter', sans-serif; }

/* Removing default input styles for that "Minimal" look */
input:focus {
    outline: none !important;
    box-shadow: none !important;
}
</style>