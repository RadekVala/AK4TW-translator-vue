<script setup>
</script>

<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-md-8">
        <div class="card">
          <div class="card-body">
            <h3 class="card-title">Translator</h3>

            <input
              id="userInput"
              class="my-3 form-control form-control-lg"
              type="text"
              placeholder="Text for translation"
              aria-label="Text for translation"
            />

            <button id="btnTranslate" type="button" class="btn btn-primary">
              Translate
            </button>

            <p id="translationResult"></p>
          </div>
        </div>
      </div>

      <div class="col-md-4">Reklama</div>
    </div>
  </div>
</template>
