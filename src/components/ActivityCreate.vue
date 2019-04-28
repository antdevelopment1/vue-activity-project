<template>
    <div class="activityCreateForm">
        <a
        v-if="!isFormDisplayed"
        class="button is-primary is-block is-alt is-large"
        href="#"
        @click="isFormDisplayed = !isFormDisplayed"
        >New Activity</a>
        <div
            v-if="isFormDisplayed"
            class="create-form"
            >
            h2>Create Activity</h2>
            <div class="field">
                <label
                class="label"
                for=""
                >Title</label>
                <div class="control">
                <input
                    v-model="newActivity.title"
                    type="text"
                    class="input"
                    placeholder="Read a Book"
                >
            </div>
    </div>
    <div class="field">
        <label
        for=""
        class="class"
        >Notes</label>
        <div class="control">
        <textarea
        id=""
        v-model="newActivity.notes"
        name=""
        cols="30"
        rows="10"
        placeholder="Write some note here..."
        />
        </div>
    </div>
    <div class="field">
        <label
        for=""
        class="class"
        >Notes</label>
        <div class="control">
        <select v-model="newActivity.category" name="" id="" class="select">
            <option disabled value="">Please Select One</option>
            <option v-for="category in categories" :key="category.id" :value="category.id">{{category.text}}</option>
        </select>
        </div>
    </div>
    <div class="field is-grouped">
        <div class="control">
        <button
            class="button is-link"
            :disabled="!isFormValid"

            @click.prevent="createActivity"
        >
            Create Activity
        </button>
        <button
            class="button is-text"
            @click="toggleFormDisplay()"
        >
            Cancel
        </button>
        </div>
    </div>
    </div>
</div>
</template>

<script>
import { createActivity } from '@/api';
export default {
    name: "activity-create",
    props: {
        categories: {
            type: Object,
            required: true
        }
    },
    data() {
        return { 
            isFormDisplayed: false,
            newActivity: {
                title: '',
                notes: '',
                category: ''
            },
        }
    },
    computed: {
        isFormValid() {
            return this.newActivity.title && this.newActivity.notes;
        },
    },
    methods: {
        toggleFormDisplay () {
            this.isFormDisplayed = !this.isFormDisplayed
        },
        createActivity () {
            debugger
            const activity = createActivity(this.newActivity);
            this.$emit('activityCreated', {...activity});
        }
    }
}
</script>

<style>

</style>

