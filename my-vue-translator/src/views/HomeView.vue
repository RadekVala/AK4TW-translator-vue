<script>
import { ref } from "vue";

export default {
  setup() {
    const userInput = ref("");
    let translationResult = ref("");

    function handleClick() {
      console.log("Submitted: " + userInput.value);
      fetchData(userInput.value);
    }

    async function fetchData(userInput) {
      /*
      try {
        const response = await fetch(
          `https://api.mymemory.translated.net/get?q=${userInput}&langpair=en|cs`
        );
        const data = await response.json();
        console.log(data);
        translationResult.value = data.responseData.translatedText;

        let history = [];
        const historyLS = localStorage.getItem("history");
        if (historyLS) {
          history = JSON.parse(historyLS);
        }

        history.push(data.responseData.translatedText);
        localStorage.setItem("history", JSON.stringify(history));
      } catch (error) {
        console.error(error);
      }
      */

      fetch(`https://api.mymemory.translated.net/get?q=${userInput}&langpair=en|cs`)
    .then(response => response.json())
    .then(data => {
        // Do something with the JSON data
        console.log(data);
        translationResult.value =  data.responseData.translatedText;
    })
    .catch(error => console.error(error));
    }

    return {
      userInput,
      handleClick,
      translationResult,
    };
  },
};
</script>

<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-md-8">
        <div class="card">
          <div class="card-body">
            <h3 class="card-title">Translator</h3>

            <input
              v-model="userInput"
              class="my-3 form-control form-control-lg"
              type="text"
              placeholder="Text for translation"
              aria-label="Text for translation"
            />

            <button @click="handleClick" type="button" class="btn btn-primary">
              Translate
            </button>

            <p id="translationResult">{{ translationResult }}</p>
          </div>
        </div>
      </div>

      <div class="col-md-4">Reklama</div>
    </div>
  </div>
</template>
