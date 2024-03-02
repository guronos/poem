<template>
    <div class="poem">
        <header>
            <div class="title">
                Invictus
            </div>
            <div class="sub-title">
                By William Ernest Henley
            </div>
        </header>
        <main>
            <div class="main__btns">
                <template v-for="(squre, key) in poem" :key="`sq_${squre.id}`">
                    <div
                        class="square"
                        :class="{square_fill: squre.show}"
                        @click="actionVisibleQuatrain(key)"
                    ></div>
                </template>
            </div>
            <div class="quatrain_wrapper">
                <div v-for="quatrain in poem"
                     class="quatrain"
                     :key="quatrain.id">
                    <template v-if="quatrain.show">
                        <TextBlock
                            :rowText="quatrain.text" />
                    </template>
                </div>
            </div>
        </main>
    </div>
</template>
<script setup>
import TextBlock from "@/components/TextBlock.vue";
import {computed, ref} from "vue";

const poem = ref({
    1: {
        id: 1,
        show: true,
        text: 'Out of the night that covers me,\n' +
            'Black as the pit from pole to pole,\n' +
            'I thank whatever gods may be\n' +
            'For my unconquerable soul.',
    },
    2: {
        id: 2,
        show: true,
        text: 'In the fell clutch of circumstance\n' +
            'I have not winced nor cried aloud.\n' +
            'Under the bludgeonings of chance\n' +
            'My head is bloody, but unbowed.'
    },
    3: {
        id: 3,
        show: true,
        text: 'Beyond this place of wrath and tears\n' +
            'Looms but the Horror of the shade,\n' +
            'And yet the menace of the years\n' +
            'Finds and shall find me unafraid.'
    },
    4: {
        id: 4,
        show: true,
        text: 'It matters not how strait the gate,\n' +
            'How charged with punishments the scroll,\n' +
            'I am the master of my fate,\n' +
            'I am the captain of my soul.'
    }
})

const validateCountQuatrain = computed(() => {
    return Object.values(poem.value).filter((quatrain) => quatrain.show === true).length > 1
})

const actionVisibleQuatrain = (key) => {
    if (validateCountQuatrain.value || !poem.value[key].show) poem.value[key].show = !poem.value[key].show
}
</script>
<style scoped>
header {
    display: flex;
    align-items: baseline;
    margin-left: 38rem;
    margin-top: 1rem;
    line-height: 3rem;
    gap: 8rem;
}
.poem {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-size: 2.5rem;
}
.title {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    font-size: 4rem;
    font-weight: 500;
}
.sub-title {
    font-size: 2rem;
    font-weight: 500;
}
main {
    display: flex;
    margin: -1rem 0 auto;
}
.main__btns {
    height: 2rem;
    display: flex;
    margin: 2.7rem 3rem 0 0;
    gap: 2.7rem;
}
.square {
    width: 2rem;
    height: 2rem;
    outline: 2px solid #000000;
    cursor: pointer;
}
.square_fill {
    background: #000000;
}
.quatrain {
    margin-top: 1.8rem;
}
@media (max-width: 820px) {
    header {
        flex-direction: column;
        margin: 2rem 0;
        gap: 1rem;
    }
    main {
        flex-direction: column;
        justify-content: center;
    }
    .main__btns {
        margin: 0 auto;
    }
    .quatrain_wrapper {
        width: 80vw;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
    .quatrain {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
}
</style>
