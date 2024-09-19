<template>
  <div class="header">
    <h1>pokemon</h1>
     <img class="imagen-logo" src="C:\Users\Admin\Desktop\Taller\taller\src\assets\logo_pokemon.png" alt="">
 </div>


      <div class="mosaicos" id="div-imagenes" >
         
       </div>
  
<!--  -->

  
</template>
<script>
export default {
    name: 'App',
    methods: {
        cargarImagenes: async function () {
            let url = 'https://cobuses.com.co/APIV2/model/pokemon.php?dato=getallpokemon';

            await this.axios.get(url)
                .then(response => {
                    // Manejar la respuesta exitosa
                    let ImagesResponse = response.data;
                    const div_imagenes = document.getElementById('div-imagenes');
                    ImagesResponse.forEach(image => {
                        const div_imagen = document.createElement("div");
                        console.log(image.image)
                        div_imagen.innerHTML = `<div class="joi">`+`
                            <img src="${image.imagen}"/>


                        `+`<h1>${image.nombre}</h1>`+
                        +`<h1 style="">${image.type_name}</h1>`+`</div>`
                        div_imagenes.appendChild(div_imagen)
                    });
                })
                .catch(error => {
                    
                    console.error(error);
                });
        }
    },
    mounted() {
        this.cargarImagenes();
    }
}
</script>
<style>
.header {
  color: antiquewhite;
    background: #000;
    height: 80px;

    display: flex;
    justify-content: center;
    align-items: center;
}
/* .imagen-logo {
    height: 100%;
    object-fit: cover;
    object-position: center center;
} */
.mosaicos {
    width: 80%;
    margin: auto;
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    border: 3px;
    background-color: burlywood ;
    }
</style>
