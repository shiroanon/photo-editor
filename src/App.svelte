<script>
  let contrast = 100;
  let brightness = 100;
  let saturate = 100;
  let blur = 0;
  let imgUrl = "";
  let fileInput;
  const handleFile = () => {
    const file = fileInput.files[0];
    if (file) {
      imgUrl = URL.createObjectURL(file);
    }
  };


</script>

<main>
  <section class = "InputContainer">
    <div>
      <span>Contrast </span>
      <p class="number"> {contrast}</p>
      <input type="range" bind:value={contrast} id="contrast-slider" min="0" max="200"  />
    </div>
      <div>
        <span>Brightness</span>
        <p class="number">{brightness}</p>
        <input type="range" bind:value={brightness} id="brightness" min="0" max="200"  />
      </div>
      <div>
        <span>Saturate</span>
        <p class="number">{saturate}</p>
        <input type="range" bind:value={saturate} id="saturate" min="0" max="200"  />
      </div>
      <div>
        <span>Blur</span>
        <p class="number">{blur}</p>
        <input type="range" bind:value={blur} id="blur" min="0" max="20" />
      </div>
    <div class="input-box">
      {#if imgUrl}
      <img src={imgUrl} alt="Preview" class="image-preview">
      {:else}
      <p>Drag & Drop Image</p>
      {/if}
      <input type="file" name="file" id="file" accept="image/*" on:change={handleFile} bind:this={fileInput} style="display:none;"/>
    <label for="file" class="input-label"></label></div>


  </section>
  <section class="ImagePreview" >
    {#if imgUrl}<img src={imgUrl} alt="Preview" class="preview"/>{/if}
  </section>

</main>

<style>
 main{
  display:grid;
  grid-template-columns: 1fr 1fr;
  min-height: 100vh;
 }
section {
  background-color: rgba(9,9,9,0.6);
}
.InputContainer{
  background-color: beige;
  margin:2em;
  border-radius:3em;
  display:flex;
  flex-direction: column;
  justify-content: center;
  gap:1em;
  padding:1em;
}
.input-box{
  height: 200px;
  border:3px dashed black;
  margin: 1em;
  display:flex;
  justify-content: center;
  align-items: center;
  position:relative;
  overflow: hidden;
}
.input-label{
  cursor: pointer;
  
}
.input-box p{
  font-size:20px;
}
.image-preview{
  max-width: 100%;
  max-height: 100%;
}
.preview{
  max-width: 100%;
  max-height: 100%;
}
input[type="range"] {
  -webkit-appearance: none;
  width: 100%;
  height: 5px;
  background: #d3d3d3;
  outline: none;
  opacity: 0.7;
  -webkit-transition: 0.2s;
  transition: opacity 0.2s;
}

div .number{
  padding: 0 1em;
}

div {
  display:flex;
}
</style>
