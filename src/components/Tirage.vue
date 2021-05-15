<template>
    <main class="main">
        <p class="main__text">{{ msg }}</p>
        <p class="main__text">Ajoutez plusieurs éléments, puis cliquez sur le bouton "Tirer au sort".</p>
        <form action="" @submit="addElements" class="main__form">
            <input type="text" v-model="addedElement" class="main__form__input">
            <!-- v-bind:class="{ disabled: !addedElement }" : the scss class "disabled" will only be added when the data addedElement is NOT empty -->
            <!-- :disabled="addedElement === ''" : the attribute disabled will be added in the button only if the data addedElement IS empty-->
            <button type="submit" class="main__form__btn" v-bind:class="{ disabled: !addedElement }"  :disabled="addedElement === ''">Ajouter</button>
        </form>

        <section class="main__addedElements">
            <ul class="main__addedElements__ul">
                <li v-for="element in elements" :key="element.id" class="main__addedElements__el">{{ element.name }} <span class="main__addedElements__remove" @click="removeElement">⤬</span></li>
            </ul>
        </section>
        <button class="main__btn">Tirer au sort</button>
    </main>
</template>

<script>
export default {
    name: "Tirage",
    props: {
        msg: String,
    },
    data() {
        return {
            elements: [],
            addedElement: "",
            futurAddedElementId: 1,
        }
    },
    methods: {
        addElements(event) {
            event.preventDefault(); // Prevent submit
            
            //console.log("addedElement", this.addedElement);
            //console.log("elements", this.elements);

            // Push to addedElement into the elements array
            this.elements.push({
                id: this.futurAddedElementId++,
                name : this.addedElement
            });

            // Empty the input after submiting 
            this.addedElement = "";
        },
        removeElement() {
            // remove the clicked element from the elements array
            this.elements.pop({
                id: this.addedElement,
                name : this.addedElement
            });
        },
        sortsElements() {

        },
    },
}
</script>

<style lang="scss">
@import '../scss/vars.scss';

.main {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;

    &__text {
        text-align: center;
        padding: $gutter / 3;
    }

    &__form {
        margin: $gutter 0;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;

        &__input {
            border: 3px solid $hotPink;
            height: $gutter * 1.5;
            margin: 0 $gutter;
            color: $hotPink;
        }

        &__btn {
            border: 3px solid $hotPink;
            background-color: $hotPink;
            color: $white;
            font-weight: bold;

            &:hover {
                cursor: pointer;
                background-color: $black;
                border: 3px solid $black;
            }
        }
    }

    &__btn {
        border: 3px solid $black;
        background-color: $black;
        color: $white;
        font-weight: bold;
        padding: $gutter;
        margin: $gutter auto;

        &:hover {
            cursor: pointer;
            background-color: $hotPink;
            border: 3px solid $black;
        }
    }

    &__addedElements {
        &__ul {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            align-items: center;
        }

        &__el {
            margin: $gutter;
            padding: $gutter;
            background-color: $hotPink;
            font-weight: bold;
        }

        &__remove {
            font-size: $gutter * 1.3;
            color: $white;
            margin-left: $gutter;
            font-weight: normal;

            &:hover {
                cursor: pointer;
                color: $black;
            }
        }

    }
}

/* Styles for disabled btn */
.disabled {
    background-color: lighten($hotPink, 15%);
    border: 3px solid lighten($hotPink, 15%);
    color: $white;
    font-weight: bold;

    &:hover {
        cursor: not-allowed;
        background-color: lighten($hotPink, 15%);
        border: 3px solid lighten($hotPink, 15%);
    }
}


</style>