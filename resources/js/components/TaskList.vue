<template>
    <div class="container mt-5">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">TaskList</div>

                    <div class="card-body">
                        <ul>
                            <li v-for="task in tasks" :key="task.id">{{ task.title }}</li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            tasks: []
        }
    },

    created() {
        // version 1
        // axios.get('./api/task')
        // .then(response => this.tasks = response.data)

        // version 2 --- it has a bug
        // Event.$on('taskCreated', () => {
        //     axios.get('./api/task')
        //     .then(response => this.tasks = response.data);
        // });


        axios.get('./api/task')
        .then(response => this.tasks = response.data);


        Event.$on('taskCreated', (title) => {
            this.tasks.push(title);
        });
    }
}
</script>

<style>

</style>
