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
            <div class="form__group-checkbox">
                <input class="form__checkbox" type="checkbox" name="rememberMe" id="rememberMe">
                <label class="form__label-checkbox"  for="rememberMe">
                    <div class="form__custom-input"></div>
                    Remember me
                </label>
            </div>
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

export default {
    components: {ShowPassword, TheButton},
}
</script>

<style scoped>
.form{
    display: grid;
    row-gap: 24px;
    margin-bottom: 56px;
}

.form__label{
    
}
</style>