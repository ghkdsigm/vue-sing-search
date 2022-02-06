<template>
    <header>
        <Logo />
        <div class="nav nav-pills">
            <div v-for="nav in navigations" :key="nav.name" class="nav-item">
                <Router-link :to="nav.href" active-class="active" class="nav-link">
                    {{nav.name}}
                </Router-link>
            </div>
        </div>
    </header>
</template>

<script>
import Logo from '~/components/Logo';

export default {
    components:{
        Logo
    },
    data(){
        return{
            navigations:[
                {
                    name: '노래찾기',
                    href: '/'
                },
                {
                    name: 'About me',
                    href: '/About'
                }
            ]
        }
    }
}
</script>

<style lang="scss" scoped>
@import "~/scss/main";
header {
    display:flex;
    align-content: center;
    padding:20px 40px;
    .nav-item {
        margin-right:15px;
        font-family: "Noto Sans KR", sans-serif;
        font-weight: 700;
        &:last-child {
            margin-right:0;
        }
    }
}
</style>