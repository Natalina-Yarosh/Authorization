<template>
    <form action="#" class="form">
        <div class="form__group">
            <label class="form__label" for="userEmail">Email</label>
            <input class="form__input" type="email" id="userEmail">
        </div>
        <div class="form__group">
            <label class="form__label" for="userPassword">Password</label>
            <input class="form__input" type="password" id="userPassword">
            <ShowPassword />
        </div>
        <div class="form__info">
            <Checkbox />
            <button class="form__link">Forgot password?</button>
        </div>
        <div class="form__btns">
            <TheButton/>
            <TheButton/>
        </div>
    </form>
</template>

<script>
import ShowPassword from './icons/ShowPassword.vue'
import TheButton from './TheButton.vue'
import Checkbox from './icons/Checkbox.vue'

export default {
    components: {ShowPassword, TheButton, Checkbox},
}
</script>

<style scoped>
.form{
    display: grid;
    row-gap: 24px;
    margin-bottom: 56px;
    @media(max-width:767px){
        margin-bottom: 40px;
    }
}

.form__label{
    margin-bottom: 8px;
    color: var(--label-color);
    font-weight: 600;
    font-size: 16px;
    line-height: 1;
    display: block;

    @media(max-width:850px){
        font-size: 14px;
    }
    @media(max-width:767px){
        font-size: 16px;
    }
}

.form__input{
    display: block;
    width: 100%;
    padding: 15px 45px 15px 15px;
    border: 1px solid var(--border-color);
    border-radius: 8px;
    color: var(--primary-color);
    font-size: 16px;
    line-height: 24px;
    transition: border .3s linear;
    @media(max-width:850px){
        font-size: 14px;
        line-height: 16px;
    }

    @media(max-width:767px){
        font-size: 16px;
        padding: 17px;
    }
}

.form__input:hover, .form__input:focus{
    border: 1px solid var(--primary-color);
}

.form__group{
    position: relative;
}

.form__info{
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.form__link{
    color: var(--primary-color);
    font-size: 16px;
    line-height: 1;
    border: none;
    border-bottom: 1px solid var(--primary-color);
    background: transparent;
    transition: all .3s linear;
    cursor: pointer;
    @media(max-width:850px){
        font-size: 14px;
    }
    @media(max-width:767px){
        font-size: 16px;
    }
}

.form__link:hover{
    color: var(--secondary-color);
    border-color: transparent;
}

.form__btns{
    display: flex;
    column-gap: 24px;
}
</style>