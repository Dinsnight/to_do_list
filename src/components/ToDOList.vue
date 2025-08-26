<script setup>
import {ref} from "vue";

const newTask = ref('')
const tasks = ref([])

function addTask() {
    if (newTask.value.trim() !== '') {
        tasks.value.push({
            text: newTask.value,
            date: Date().toLocaleString()
        })
    }
    newTask.value = '';
}

function removeTask(index) {
    tasks.value.splice(index, 1)
}
</script>

<template>
    <div class="container text-center m-5 bg-primary rounded">
        <div class="row justify-content-center">
            <div class="col-6 bg-light m-4 rounded">
                <form @submit.prevent="addTask">
                    <div class="row g-3 align-items-center justify-content-center">
                        <div class="col-auto">
                            <input
                                type="text"
                                placeholder="Type task"
                                class="form-control"
                                v-model="newTask"
                            />
                        </div>
                        <div class="col-auto">
                            <button class="btn btn-primary m-2 px-4">Add</button>
                        </div>
                    </div>

                </form>
                <ul class="list-unstyled w-100">
                    <li v-for="(task, index) in tasks" :key="index">
                        <div
                            class="d-flex justify-content-between rounded p-2 align-content-center m-4 bg-info">
                            <span class="fw-bold">{{ task.text }} </span>
                            <small class="text-muted">{{task.date}}</small>
                            <button class="btn btn-light" @click="removeTask(index)">🗑</button>
                        </div>
                    </li>
                </ul>
            </div>

        </div>

    </div>
</template>

<style scoped>
span{
    word-wrap: break-word;
    white-space: normal;
}
</style>