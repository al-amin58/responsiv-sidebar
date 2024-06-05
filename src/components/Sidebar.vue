<template>
	<aside :class="`${is_expanded ? 'is-expanded' : ''}`" class="flex flex-col overflow-hidden h-lvh p-6 text-white bg-gray-900 " >
		<div class="mb-6 w-16">
			<img :src="logoURL" alt="Vue" /> 
		</div>

		<div class="menu-toggle-wrap flex justify-end mb-3 relative transition  ease-in-out mt-[-3rem]">
			<button class="menu-toggle transition  ease-in-out hover:text-green-500  " @click="ToggleMenu">
				<span class="material-icons font-semibold transition  ease-in-out transform translate-x-2">keyboard_double_arrow_right</span>
			</button>
		</div>

		<h3 class="text-gray-300 font-normal mb-2 uppercase transition-opacity duration-300 ease-in-out opacity-0 ">Menu</h3>
		<div class=" mx-[-1rem] hover:bg-gray-500 hover:text-green-500 ">
			<router-link to="/" class="button  flex items-center no-underline transition duration-200 ease-in-out p-2">
				<span class="material-icons text-white hover:text-green-500 mr-4 font-medium transition duration-200 ease-in-out">home</span>
				<span class="text text-white transition-opacity duration-300 ease-in-out opacity-0">Home</span>
			</router-link>
		</div>
		<div class=" mx-[-1rem] hover:bg-gray-500 hover:text-green-500 ">
			<router-link to="/about" class="button  flex items-center no-underline transition duration-200 ease-in-out p-2">
				<span class="material-icons text-white hover:text-green-500 mr-4 font-medium transition duration-200 ease-in-out">home</span>
				<span class="text text-white transition-opacity duration-300 ease-in-out opacity-0">Home</span>
			</router-link>
		</div>
		
	</aside>
</template>

<script setup>
import { ref } from 'vue'
import logoURL from '../assets/logo.png'

const is_expanded = ref(localStorage.getItem("is_expanded") === "true")

const ToggleMenu = () => {
	is_expanded.value = !is_expanded.value
	localStorage.setItem("is_expanded", is_expanded.value)
}
</script>

<style lang="scss" scoped>
aside {

	width: calc(2rem + 32px);
	transition: 0.2s ease-in-out;
	
		.button {
			&:hover {
				.material-icons, .text {
					color: #4ade80;
				}
			}
			&.router-link-exact-active {
				background-color: #334155;
				border-right: 5px solid #4ade80;
				.material-icons, .text {
					color: #4ade80;
				}
			}
		}
	&.is-expanded {
		width: 300px;
	.menu-toggle {
		transform: rotate(-180deg);
	}
		h3, .button .text {
			opacity: 1;
		}
		
	}

	
}
</style>