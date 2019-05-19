<template>
    <v-flex xs6 lg3 class="pa-3">
        <div v-if="!info">
            <v-card>
                <v-responsive class="pt-4">
                    <v-img aspect-ratio="2.75" src height="200px">
                        <v-progress-circular :size="70" :width="7" indeterminate color="primary"></v-progress-circular>
                    </v-img>
                </v-responsive>
                <v-card-title primary-title>
                    <div>
                        <h3 class="headline mb-0">{{pokemon.name}}</h3>
                    </div>
                </v-card-title>
            </v-card>
        </div>
        <div v-else>
            <v-card>
                <v-img :src="info.sprites.front_default"></v-img>
                <v-card-title primary-title>
                    <div>
                        <h3 class="headline mb-0">{{info.name}}</h3>
                    </div>
                </v-card-title>
            </v-card>
        </div>
    </v-flex>
</template>

<script>
import axios from "axios";
export default {
    props: ["pokemon"],
    data() {
        return {
            info: null
        };
    },
    async created() {
        const { data } = await axios.get(this.pokemon.url);
        this.info = data;
        //debugger;
    }
};
</script>

<style lang="stylus" scoped>
.v-progress-circular {
    margin: 3rem;
}




</style>

