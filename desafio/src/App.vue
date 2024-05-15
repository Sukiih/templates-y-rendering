<template>
  <div class="wrapper">
    <div class="form">
      <div class="field">
        <!--background -->
        <label for="backgroundColor">Color de fondo</label><br>
        <input v-model="backgroundColor" type="text" id="backgroundColor">
      </div>
      
      <div class="field">
        <!--color del texto-->
        <label for="textColor">Color de texto</label><br>
        <input v-model="textColor" type="text" id="textColor">
      </div>
      
      <div class="field-checkbox">
        <!--checkbox de mostrar texto-->
        <label for="showText">Mostar texto</label>
        <input v-model="showText" type="checkbox" id="showText">
      </div>
      <br>
      <div class="field">
        <!--borde elemento-->
        <label for="borderRadius">Borde  </label>
        <input v-model="borderRadius" type="range" id="borderRadius">
      </div>

      <div class="field">
        <!--caja de texto-->
        <label for="textContent">Contenido textual</label><br>
        <textarea v-model="textContent" id="textContent" cols="20" rows="5" ></textarea>
      </div>

      <div class="field">
        <!--tipografia-->
        <label for="fontFamily">Tipografía  </label>
        <select v-model="fontFamily" name="fontFamily" id="fontFamily">
          <option v-for="option in fontOptions" :key="option">{{ option }}</option>
        </select>
      </div>
      
      <div class="field-checkbox">
        <!--opacidad-->
        <label for="opacidad">Opaco</label>
        <input v-model="opacidad" type="checkbox" id="opacidad">
      </div>

      <div class="field-radio">
        <p class="tamañoLetra">Tamaño de letra</p><br>
          <!--tamaño letra-->
          <input type="radio" id="pequeño" v-model="fontSize" value="small">
          <label for="pequeño">Pequeño</label><br>
          <input type="radio" id="mediano" v-model="fontSize" value="medium">
          <label for="mediano">Mediano</label><br>
          <input type="radio" id="grande" v-model="fontSize" value="large">
          <label for="grande">Grande</label><br>
      </div>
    </div>
    <div class="content"
      :class="{ opacity: opacidad }"
      :style="{
        backgroundColor: backgroundColor,
        color: textColor,
        borderRadius: borderRadius + 'px',
        fontFamily: fontFamily,
        fontSize: fontSize + 'px'
      }"
    >
      <p v-show="showText" :class="{'pequeño': enPequeño, 'mediano': enMediano, 'grande': enGrande}">
        {{ textContent }} </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      backgroundColor: "darkgreen",
      textColor: "white",
      showText: true,
      borderRadius: 50,
      textContent: "Awesome Vue.js",
      fontFamily: "cursive",
      fontSize: 20,
      opacidad: false,
      fontOptions: [
        "cursive",
        "monospace",
        "roboto",
        "fantasy",
        "lucida sans"
      ],
      sizes: ["Small", "Medium", "Large"],
    };
  },
  computed: {
    enPequeño() {
      return this.fontSize === "small";
    },
    enMediano() {
      return this.fontSize === "medium";
    },
    enGrande() {
      return this.fontSize === "large";
    }
  }
};
</script>




<style>
body, html {
  margin: 30px;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #c493e0;
}

.wrapper {
  display: flex;
  justify-content: center;
  align-items: flex-start; 
}


.form {
  padding: 20px;
  width: 200px;
  background-color: #18313b;
  box-shadow: 10px 10px 10px black; 
  color: white;
}

.content {
  flex: 1;
  text-align: center;
  line-height: 200px;
  width: 200px;
  height: 200px;
  padding: 20px;
  margin-left: 50px;
  box-shadow: 5px 10px 5px #18010198; 
}

.field {
  margin-bottom: 20px;
}

.field-checkbox label,
.field--radio label {
  margin-bottom: 15px; 
}

.field--radio input[type="radio"] {
  margin-right: 5px;
}

.tamañoLetra{
  margin-bottom: -5px;
}

.field--radio label {
  display: inline-block; 
}

.content p {
  margin: 0;
}
.opacity {
  opacity: 0.5;
}
.pequeño{
  font-size: small;
}
.mediano{
  font-size: medium;
}
.grande{
  font-size: larger;
}

</style>
