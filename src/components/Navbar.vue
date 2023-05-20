<script>
import { RouterLink } from 'vue-router'

export default{
    name: 'Navbar'
}
</script>


<template>
    <header class='container'>
        <RouterLink to="/" class='logo'>
            <img src='https://archives.bulbagarden.net/media/upload/8/80/Pokenetlogo.png' alt='Logo Pokenet'/>
        </RouterLink>

        <form onsubmit={onSearchSubmit}>
            <div class='form-group'>
                <svg
                    xmlns='http://www.w3.org/2000/svg'
                    fill='white'
                    viewBox='0 0 24 24'
                    stroke-width='1.5'
                    stroke='currentColor'
                    class='icon-search'
                >
                    <path
                        stroke-linecap="round"
						stroke-linejoin="round"
						d='M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z'
                    />
                </svg>
                <input
                    type='search'
                    name='valueSearch'
                    id=''
                    placeholder='Buscar nombre de pokemon'
                />
            </div>

            <button class='btn-search'>Buscar</button>
        </form>
    </header>

</template>