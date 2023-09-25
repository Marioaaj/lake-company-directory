<script setup>
import { ref } from 'vue'
import { useAuth } from '@/components/composables/useAuth'

const {isAuthenticated, logout, user} = useAuth()

const brand =ref('⛵ Lake Company Directory')
</script>

<template>
    <nav>
        <div class="wrapper">
            <RouterLink :to="{name: 'Home'}" class="brand">
                <span class="brand-title">{{ brand }}</span>
            </RouterLink>
            <div class="menu">
                <p v-show="isAuthenticated" class="px-2 py-4">Welcome back <strong><i>{{ user.name }}</i></strong></p>
                    <div v-if="isAuthenticated">
                        <RouterLink :to="{name: 'Settings' }" href="#" class="menu-item">Settings</RouterLink>
                        <button href="#" class="menu-logout" @click="logout">Logout</button>
                </div>                
                <div v-else>
                    <RouterLink :to="{name: 'Login' }"  href="#" class="menu-login">Login</RouterLink>
                </div>
            </div>
        </div>
    </nav>
</template>

<style scoped lang="postcss">
    nav{
    @apply flex h-20 bg-teal-700 text-slate-200;
    .wrapper {
      @apply container mx-auto flex w-full items-center justify-between;
      .brand {
        &-title {
          @apply text-3xl font-bold text-lime-300;
        }
      }
      .menu {
        @apply flex gap-2;
        &-item {
          @apply rounded-md px-4 py-2 hover:bg-purple-300 hover:text-red-700;
        }
        &-item:hover {
          @apply font-bold;
        }
        &-login {
          @apply rounded-md bg-orange-300 px-4 py-2 font-bold text-slate-800 hover:bg-purple-300;
        }
                &-logout{
                    @apply mx-2 rounded-md bg-orange-300 px-4 py-2 hover:bg-yellow-500 hover:text-slate-900;
                }
            }
        }
    }
</style>
