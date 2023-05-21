<template>
    <div class="container flex">
                <button type="button" @click="$router.go(-1)" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 mr-2 mb-2 ">Back</button>
    </div>
    <div v-for="data in allUserData" :key="data.id">
        <div v-if="data.id==$route.params.id" class="container ">
            <div class="overflow-hidden rounded-lg border border-gray-200 shadow-md m-5">
                <table class="w-full border-collapse bg-white text-left text-lg text-gray-500">
                    <thead class="bg-gray-50">
                        <tr>
                            <th scope="col" class="px-6 py-4 font-medium text-gray-900">Avatar</th>
                            <th scope="col" class="px-6 py-4 font-medium text-gray-900">First Name</th>
                            <th scope="col" class="px-6 py-4 font-medium text-gray-900">Last Name</th>
                            <th scope="col" class="px-6 py-4 font-medium text-gray-900">Email</th>
                        </tr>
                    </thead>
                    <tbody class="divide-y divide-gray-100 border-t border-gray-100">
                        <tr class="hover:bg-gray-50">
                            <th class="grid gap-4 px-6 py-4 font-normal text-gray-900">
                                <div class="relative h-12 w-12">
                                    <img class="h-full w-full rounded-full object-cover object-center" :src="data.avatar"
                                        alt="" />
                                </div>
                            </th>
                            <td class="px-6 py-4">{{ data.first_name }}</td>
                            <td class="px-6 py-4">{{ data.last_name }}</td>
                            <td class="px-6 py-4">{{ data.email }}</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { RouterLink, route } from 'vue-router';

import { getAllUserData } from '../composable/multiUsers.js'

const url = ref('https://reqres.in/api/users/');

const { allUserData, errors } = getAllUserData(url)


</script>

<style lang="scss" scoped></style>