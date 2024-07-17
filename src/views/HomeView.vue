<script setup lang="ts">
</script>

<template>
    <!--  <main>
        <TheWelcome />
        </main> -->
        <v-container>
            <v-row no-gutters>
                <RouterLink to="/characters">
                <v-col>
                    <v-card
                        class="mx-auto my-8 link-card"
                        max-width="344"
                        title="Karaktärer"
                        prepend-icon="mdi-account"
                        link
                        ></v-card>
                </v-col>
                </RouterLink>
                <RouterLink to="/spells">
                <v-col>
                    <v-card
                        class="mx-auto my-8 link-card"
                        max-width="344"
                        title="Trollformler"
                        prepend-icon="mdi-magic-staff"
                        link
                        ></v-card>
                </v-col>
                </RouterLink>
            </v-row>
        </v-container>
</template>
<style>
.link-card {
    background: #191b1c !important;
    color: white !important;
}
</style>
