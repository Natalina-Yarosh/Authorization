<template>
    <div class="content">
        <Logo />
        <Image />
        <div class="info">
            <h1 class="info__title">Artificial Intelligence giving you travel recommendations</h1>
            <p class="info__text">Welcome Back, Please login to your account</p>
            <TheForm />
            <div class="form__login">
                <p class="form__login-text">Or, login with</p>
                <a class="form__login-link" href="#">Facebook</a>
                <a class="form__login-link" href="#">Linked In</a>
                <a class="form__login-link" href="#">Google</a>
            </div>
        </div>
    </div>
</template>

<script>
import Image from './icons/Image.vue'
import Logo from './icons/Logo.vue'
import TheForm from './TheForm.vue'

export default {
    components: {Image, Logo, TheForm},
}
</script>

<style scoped>
.content{
    background-color: #FFFFFF;
    display: grid;
    grid-template-columns: 1fr 57.5%;
    border-radius: 24px;
    overflow: hidden;
    max-width: 1296px;
    width: 100%;
    padding-left: 64px;
    row-gap: 62px;
    column-gap: 64px;
}

.info{
    margin-bottom: 66px;
}

.info__title{
    margin-bottom: 16px;
    color: var(--primary-color);
    font-weight: 600;
    font-size: 24px;
    line-height: 1.5;
}

.info__text{
    margin-bottom: 32px;
    color: var(--secondary-color);
    font-size: 16px;
    line-height: 1;
}
</style>