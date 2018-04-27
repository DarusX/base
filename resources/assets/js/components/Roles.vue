<template>
    <div>
        <button v-on:click="show" class="btn btn-default">Mostrar</button>
        <table class="table">
            <thead>
                <tr>
                    <th>Role</th>
                    <th>Editar</th>
                    <th>Eliminar</th>
                </tr>
            </thead>
            <tbody v-if="roles && roles.length">
                <tr v-for="role in roles">
                    <td>{{role.role}}</td>
                    <td>
                        <a v-bind:href="role.id">Editar</a>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
    import axios from 'axios'

    export default {
        data() {
            return {
                roles: [],
                errors: []
            }
        }, methods: {
            show: function() {
                axios.get("/role/json").then(response => {
                    this.roles = response.data
                })
            }
        }
    }

</script>