<template>
    <div>
        <h1>{{ title }}</h1>
        <table>
            <thead>
            <tr>
                <th></th>
                <th><input type="checkbox" name="allChoose" value="1" v-model="allChoose" @change="allChooseChange"/>
                </th>
                <th>商品名称</th>
                <th>商品单价</th>
                <th>购买数量</th>
                <th>操作</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="(item, index) in list">
                <td>{{ index + 1 }}</td>
                <td><input type="checkbox" name="itemChoose" :value="item.id" v-model="chooses"
                           @change="checkboxChange"/></td>
                <td>{{ item.name }}</td>
                <td>{{ item.price }}</td>
                <td>
                    <button @click="item.count = item.count - 1" :disabled="item.count === 1">-</button>
                    {{ item.count }}
                    <button @click="item.count = item.count + 1">+</button>
                </td>
                <td>
                    <button @click="removeTr(index)">移除</button>
                </td>
            </tr>
            </tbody>
        </table>
        <div>总价:￥ {{ totalPrice }}</div>
    </div>
</template>

<script>
    export default {
        name: "admin",
        data() {
            return {
                title: 'admin',
                list: [
                    {id: 1, name: 'iPhone 7', price: 6188, count: 1},
                    {id: 2, name: 'iPad Pro', price: 5888, count: 1},
                    {id: 3, name: 'MacBook Pro', price: 21488, count: 1},
                    {id: 4, name: 'iPhone X', price: 9188, count: 2}
                ],
                allChoose: 0,
                chooses: []
            }
        },
        methods: {
            removeTr: function (index) {
                this.list.splice(index, 1);
            },
            checkboxChange: function () {
                if (this.list.length !== 0 && this.list.length === this.chooses.length) {
                    this.allChoose = 1;
                } else {
                    this.allChoose = 0;
                }
            },
            allChooseChange: function () {
                if (this.allChoose) {
                    this.chooses = this.list.map(function (v) {
                        return v.id;
                    });
                } else {
                    this.chooses = [];
                }
            }
        },
        computed: {
            totalPrice: function () {
                var sum = 0;
                for (var i = 0; i < this.list.length; i++) {
                    var item = this.list[i];
                    if (this.chooses.indexOf(item.id) !== -1) {
                        sum += item.price * item.count;
                    }
                }
                return sum.toString().replace(/\B(?=(\d{3})+$)/g, ',');
            }
        }
    }
</script>

<style scoped>
    [v-cloak] {
        display: none;
    }

    table {
        border: 1px solid #e9e9e9;
        border-collapse: collapse;
        border-spacing: 0;
        empty-cells: show;
    }

    th, td {
        padding: 8px 16px;
        border: 1px solid #e9e9e9;
        text-align: left;
    }

    th {
        background: #f7f7f7;
        color: #5c6b77;
        font-weight: 600;
        white-space: nowrap;
    }
</style>
