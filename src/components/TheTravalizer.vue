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
    background-color: var(--white-color);
    display: grid;
    grid-template-columns: 1fr 61.3%;
    border-radius: 24px;
    overflow: hidden;
    max-width: 1326px;
    width: 100%;
    padding-left: 65px;
    row-gap: 62px;
    column-gap: 43px;
    @media(max-width:1170px){
        grid-template-columns: 1fr 50%;
    }
    @media(max-width:850px){
        padding-left: 30px;
        column-gap: 30px;
        row-gap: 30px;
    }

    @media(max-width:767px){
        padding: 38px 0 0;
        display: block;
        background: transparent;
        border-radius: 0;
    }
}

.info{
    margin-bottom: 66px;
    @media(max-width:850px){
        margin-bottom: 30px;
    }
    @media(max-width:767px){
        background-color: #fff;
        margin: 0;
        padding: 32px 24px;
    }
}

.info__title{
    margin-bottom: 16px;
    color: var(--primary-color);
    font-weight: 600;
    font-size: 24px;
    line-height: 1.5;

    @media(max-width:850px){
        font-size: 22px;
    }
    @media(max-width:767px){
       font-size: 20px;
       margin-bottom: 17px;
    }
}

.info__text{
    margin-bottom: 32px;
    color: var(--secondary-color);
    font-size: 16px;
    line-height: 1;
    @media(max-width:850px){
        font-size: 14px;
    }
    @media(max-width:767px){
        font-size: 16px;
        margin-bottom: 40px;
    }
}

.form__login{
    display: flex;
    align-items: center;
    column-gap: 24px;
    @media(max-width:992px){
        flex-wrap: wrap;
        justify-content: space-between;
        row-gap: 24px;
    }
    @media(max-width:850px){
        row-gap: 15px;
        column-gap: 15px;
    }
    @media(max-width:767px){
        row-gap: 23px;
    }
}

.form__login-text{
    color: var(--secondary-color);
    font-size: 16px;
    line-height: 1;
    @media(max-width:992px){
        width: 100%;
        text-align: center;
    }
    @media(max-width:850px){
        font-size: 14px;
    }
  
}

.form__login-link{
    color: var(--primary-color);
    font-size: 16px;
    font-weight: 500;
    line-height: 1;
    transition: all .3s linear;
    border-bottom: 1px solid transparent;
    @media(max-width:850px){
        font-size: 14px;
    }
}

.form__login-link:hover{
    border-bottom: 1px solid;
    color: var(--secondary-color);
}
</style>