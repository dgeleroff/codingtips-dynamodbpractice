<template>
    <div class="addtip">
        <form v-on:submit.prevent="postNewTip">
            <label>Author:</label>
            <input 
                v-model="postObj.author"
                type="text"
                class="fc--50"
                required
            />
            <br>
            <label>Category:</label>
            <input 
                v-model="postObj.category"
                type="text"
                class="fc--50"
                required
            />
            <br>
            <label>Tip:</label>
            <input 
                v-model="postObj.tip"
                type="text"
                required
            />
            <button class="button button--primary">Submit</button>
        </form>
        <!-- <button v-on:click="postNewTip">Post</button> -->
    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: "add-tip",
        data() {
            return{
                postObj: {
                    "author": "",
                    "tip": "",
                    "category": ""
                }
            }
        },
        methods : {
            postNewTip() { 
                console.log("gonna post the object: ");
                console.log(this.postObj);

                axios.post('https://laux4mb483.execute-api.us-east-1.amazonaws.com/default/tips/', (this.postObj))
                    .then((response) => {
                        console.log("got this in response: ")
                        console.log(response);
                        var emitObject = JSON.parse(JSON.stringify(this.postObj));
                        this.$emit('add:tip', emitObject);
                        console.log("Just emitted and about to clear");
                        this.postObj.author = "";
                        this.postObj.tip = "";
                        this.postObj.category = "";
                    })
                    .catch((error) => {
                        console.log("something went wrong")
                        console.log(error)
                    })
            }
        }


    }
</script>

<style>

</style>