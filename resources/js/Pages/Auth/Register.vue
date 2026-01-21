<script setup>
import { Head, Link, useForm } from '@inertiajs/vue3';
import Checkbox from '@/Components/Checkbox.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import TextInput from '@/Components/TextInput.vue';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
    terms: false,
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
    <Head title="Create Identity | Partner Registration" />

    <div class="flex min-h-screen bg-[#FCFAf7] font-serif selection:bg-[#D4B996] selection:text-white">
        <div class="hidden lg:flex lg:w-1/2 relative bg-[#433932] overflow-hidden">
            <img 
                src="https://images.unsplash.com/photo-1511818966892-d7d671e672a2?q=80&w=2071" 
                class="absolute inset-0 w-full h-full object-cover opacity-30 grayscale" 
                alt="Architectural Blueprint"
            />
            <div class="relative z-10 m-auto text-center px-12">
                <div class="text-[10px] tracking-[0.5em] text-[#D4B996] font-bold uppercase mb-4">Project Inquiry</div>
                <h2 class="text-5xl text-[#FCFAf7] font-light leading-tight">
                    Start Your <br/> <span class="italic font-serif text-[#D4B996]">Collaboration</span>
                </h2>
                <div class="mt-8 w-12 h-[1px] bg-[#D4B996] mx-auto opacity-50"></div>
                <p class="mt-8 text-[10px] uppercase tracking-[0.2em] text-[#EADDCD] max-w-xs mx-auto leading-loose">
                    Registering allows you to access our scheduling tools and project archives.
                </p>
            </div>
        </div>

        <div class="w-full lg:w-1/2 flex items-center justify-center p-8 lg:p-24 bg-[#FCFAf7]">
            <div class="w-full max-w-md">
                <div class="mb-12">
                    <h1 class="text-3xl font-light text-[#433932] mb-3 tracking-tight">Partner Registration</h1>
                    <div class="h-[2px] w-8 bg-[#D4B996] mb-6"></div>
                </div>

                <form @submit.prevent="submit" class="space-y-6">
                    <div class="space-y-2">
                        <InputLabel for="name" value="Legal Name / Business" class="font-sans text-[9px] uppercase tracking-[0.2em] text-[#433932] font-bold ml-1" />
                        <TextInput
                            id="name"
                            v-model="form.name"
                            type="text"
                            class="w-full bg-[#F3EEE7] border-none py-4 px-5 text-[#433932] text-sm font-sans focus:ring-1 focus:ring-[#D4B996] transition-all rounded-none shadow-sm"
                            placeholder="Full Name"
                            required
                            autofocus
                        />
                        <InputError class="text-[10px] mt-1" :message="form.errors.name" />
                    </div>

                    <div class="space-y-2">
                        <InputLabel for="email" value="Primary Contact Email" class="font-sans text-[9px] uppercase tracking-[0.2em] text-[#433932] font-bold ml-1" />
                        <TextInput
                            id="email"
                            v-model="form.email"
                            type="email"
                            class="w-full bg-[#F3EEE7] border-none py-4 px-5 text-[#433932] text-sm font-sans focus:ring-1 focus:ring-[#D4B996] transition-all rounded-none shadow-sm"
                            placeholder="email@address.com"
                            required
                        />
                        <InputError class="text-[10px] mt-1" :message="form.errors.email" />
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div class="space-y-2">
                            <InputLabel for="password" value="Security Pass" class="font-sans text-[9px] uppercase tracking-[0.2em] text-[#433932] font-bold ml-1" />
                            <TextInput
                                id="password"
                                v-model="form.password"
                                type="password"
                                class="w-full bg-[#F3EEE7] border-none py-4 px-5 text-[#433932] text-sm font-sans focus:ring-1 focus:ring-[#D4B996] transition-all rounded-none shadow-sm"
                                placeholder="••••••••"
                                required
                            />
                        </div>
                        <div class="space-y-2">
                            <InputLabel for="password_confirmation" value="Confirm Pass" class="font-sans text-[9px] uppercase tracking-[0.2em] text-[#433932] font-bold ml-1" />
                            <TextInput
                                id="password_confirmation"
                                v-model="form.password_confirmation"
                                type="password"
                                class="w-full bg-[#F3EEE7] border-none py-4 px-5 text-[#433932] text-sm font-sans focus:ring-1 focus:ring-[#D4B996] transition-all rounded-none shadow-sm"
                                placeholder="••••••••"
                                required
                            />
                        </div>
                    </div>
                    <InputError class="text-[10px] mt-1" :message="form.errors.password" />

                    <div v-if="$page.props.jetstream.hasTermsAndPrivacyPolicyFeature" class="py-2">
                        <label class="flex items-center cursor-pointer group">
                            <Checkbox id="terms" v-model:checked="form.terms" name="terms" class="rounded-none border-none bg-[#EADDCD] text-[#433932] focus:ring-0" required />
                            <span class="ms-3 text-[9px] uppercase tracking-widest text-[#8C7E71] leading-relaxed">
                                I accept the <a target="_blank" :href="route('terms.show')" class="text-[#D4B996] font-bold">Terms</a> and <a target="_blank" :href="route('policy.show')" class="text-[#D4B996] font-bold">Privacy Policy</a>
                            </span>
                        </label>
                        <InputError class="text-[10px] mt-1" :message="form.errors.terms" />
                    </div>

                    <button 
                        type="submit"
                        :class="{ 'opacity-25': form.processing }" 
                        :disabled="form.processing"
                        class="w-full bg-[#433932] text-[#FCFAf7] py-5 text-[10px] font-bold uppercase tracking-[0.5em] hover:bg-[#D4B996] transition-all duration-500 mt-4 shadow-lg active:scale-[0.98]"
                    >
                        Create Identity
                    </button>
                </form>

                <div class="mt-12 text-center">
                    <Link :href="route('login')" class="text-[10px] uppercase tracking-[0.2em] text-[#8C7E71] hover:text-[#D4B996] transition">
                        Already have an identity? <span class="font-bold border-b border-[#D4B996] pb-1">Authorize Login</span>
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

input:focus {
    outline: none !important;
    box-shadow: none !important;
}
</style>