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
                    <Action @create="create" />
                </template>
            </Resume>
        </template>
        <template #movements>
            <Movements
                :movements="movements"
                @remove="remove"
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
            movements: [{
                id: 0,
                title: "Moviemiento 0",
                description: "Descripcion 0",
                amount: 0,
                time: new Date("10-24-2022"),
            }, {
                id: 1,
                title: "Moviemiento 1",
                description: "Descripcion 1",
                amount: 2000,
                time: new Date("10-25-2022"),
            }, {
                id: 2,
                title: "Moviemiento 2",
                description: "Descripcion 2",
                amount: 5000,
                time: new Date("10-25-2022"),
            }, {
                id: 3,
                title: "Moviemiento 3",
                description: "Descripcion 3",
                amount: 2000,
                time: new Date("10-25-2022"),
            }, {
                id: 4,
                title: "Moviemiento 4",
                description: "Descripcion 4",
                amount: -4000,
                time: new Date("10-25-2022"),
            }, {
                id: 5,
                title: "Moviemiento 5",
                description: "Descripcion 4",
                amount: 5000,
                time: new Date("10-27-2022"),
            }, {
                id: 6,
                title: "Moviemiento 6",
                description: "Descripcion 4",
                amount: 3000,
                time: new Date("10-27-2022"),
            }, {
                id: 7,
                title: "Moviemiento 7",
                description: "Descripcion 4",
                amount: 1000,
                time: new Date("11-3-2022"),
            }]
        }
    },
    computed: {
        amounts() {
            const lastDays = this.movements
                .filter(m => {
                    const today = new Date();
                    const oldDate = today.setDate(today.getDate() - 30);

                    return m.time > oldDate;
                })
                .map(m => m.amount)
            return lastDays.map((m, i) => {
                const lastMovements = lastDays.slice(0, i);

                return lastMovements.reduce((suma, movement) => {
                    return suma + movement
                }, 0)
            });
        }
    },
    methods: {
        create(movement) {
            this.movements.push(movement);
        },
        remove(id) {
            const index = this.movements.findIndex(m => m.id === id);
            this.movements.splice(index, 1);
        }
    }
}
</script>