<script>
    import CcUsers from './components/users/main.vue'
    import { mapState, mapActions } from 'vuex'

    export default {
        name: 'AppVueX',
        mounted() {
            const payload = {
                name: 'Vinicius Feitosa da Silva',
                email: 'viniciusfesil@gmail.com',
                level: 'admin-da-porra-toda',
                city: 'Brasília',
                state: 'Distrito Federal',
            }

            setTimeout(() => {
                // this.$store.dispatch('changeUser', payload);
                //this.$store.commit('CHANGE_USER', payload)
                this.changeUser(payload)
            }, 1000)

        },
        components: {
            CcUsers
        },
        methods: {
            ...mapActions([
                'changeUser'
            ])
        },
        computed: {
            // com o mapState é possível ter mais de uma computed proprerty utilizando o vuex
            ...mapState({
                user: state => {
                    const {name, email} = state.user
                    return `O Usuário logado é ${name} e possui o e-mail ${email}`
                }
            })
        }
    }
</script>
<template>
    <div>
        <h1>Welcome Vue2</h1>
        <h4>{{ user }}</h4>
        <hr />
        <cc-users></cc-users>
    </div>
</template>