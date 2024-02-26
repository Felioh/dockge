<template>
    <div>
        <form class="mb-4" autocomplete="off" @submit.prevent="saveGitCredentials">
            <!-- Git Username -->
            <div class="my-4">
                <label for="git-username" class="form-label">
                    {{ $t("GitUsername") }}
                </label>
                <input
                    id="git-username"
                    v-model="gitUsername"
                    class="form-control"
                    required
                />
            </div>

            <div class="my-4">
                <label for="git-token" class="form-label">
                    {{ $t("GitToken") }}
                </label>
                <input
                    id="git-token"
                    v-model="settings.gitToken"
                    type="password"
                    class="form-control"
                    required
                />
            </div>

            <!-- Save Button -->
            <div>
                <button class="btn btn-primary" type="submit">
                    {{ $t("Save") }}
                </button>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    data() {
        return {};
    },
    computed: {
        settings() {
            return this.$parent.$parent.$parent.settings;
        },
        saveSettings() {
            return this.$parent.$parent.$parent.saveSettings;
        },
    },
    methods: {
        saveGitCredentials() {
            // TODO: check validity of git token
            /** Save the git credentials */
            this.settings.gitUsername = this.gitUsername;
            this.saveSettings();
            // axios.post('/api/saveGitUsername', { gitUsername: this.gitUsername })
            //     .then(response => {
            //         // Handle the response from the backend
            //         console.log(response.data);
            //     })
            //     .catch(error => {
            //         // Handle any errors
            //         console.error(error);
            //     });
        }
    }
};
</script>
