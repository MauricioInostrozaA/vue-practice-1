<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
        <template #resume>
            <Resume
                :label="'Ahorro total'"
                :total-amount="1000000"
                :amount="amount"
            >
                <template #graphic>
                    <Graphic :amounts="amounts" />
                </template>
                <template #action>
                    <Action/>
                </template>
            </Resume>
        </template>
        <template #movements>
            <Movements
                :movements="movements"
            />
        </template>
    </Layout>
</template>

<script>
import Layout from './Layout.vue';
import Header from './Header.vue';
import Resume from './Resume/Index.vue';
import Movements from './Movements/Index.vue';
import Action from './Action.vue';
import Graphic from './Resume/Graphic.vue';

export default {
    components: {
        Layout,
        Header,
        Resume,
        Movements,
        Action,
        Graphic,
    },
    data() {
        return{
            label: null,
            amount: null,
            amounts: [100, 200, 500, 200, -400, 500, 0, -300, 600, 400, -100],
            movements: [{
                id: 0,
                title: "Moviemiento 0",
                description: "Descripcion 0",
                amount: 10000,
            }, {
                id: 1,
                title: "Moviemiento 1",
                description: "Descripcion 1",
                amount: 10000,
            }, {
                id: 2,
                title: "Moviemiento 2",
                description: "Descripcion 2",
                amount: 10000,
            }, {
                id: 3,
                title: "Moviemiento 3",
                description: "Descripcion 3",
                amount: -10000,
            }, {
                id: 4,
                title: "Moviemiento 4",
                description: "Descripcion 4",
                amount: 10000,
            }, {
                id: 5,
                title: "Moviemiento 5",
                description: "Descripcion 4",
                amount: 10000,
            }, {
                id: 6,
                title: "Moviemiento 6",
                description: "Descripcion 4",
                amount: 10000,
            }, {
                id: 7,
                title: "Moviemiento 7",
                description: "Descripcion 4",
                amount: -10000,
            }]
        }
    }
}
</script>