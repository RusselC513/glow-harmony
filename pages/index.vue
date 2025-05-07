<template>
    <NuxtLayout>
        <section class="bg-white mainSection ">
            <div class="container mx-auto w-9/12">
                <div class="grid sm:grid-cols-2 lg:grid-cols-2 gap-6">
                    <div class="flex flex-col items-center justify-center">
                        <h3>Cleanning Services For all yours Needs</h3>
                        <p class="subtext">Enjoy a spotless home with reliable cleaning experts</p>
                    </div>
                    <div>
                        <AppForm></AppForm>
                        <!-- <NuxtImg 
                        src="/main-cleaning.png"
                        width="400"
                        /> -->
                    </div>
                </div>
            </div>
        </section>
        <section  id="services">
            <div class="container mx-auto px-4 py-6 w-9/12">
                <h3 class="text-center">Our Services</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-2">
                    <div class="text-white px-6 text-center" v-for="n in 2" :key="n">
                        <div class="box">
                            <h4>End of lease clean</h4>
                            <NuxtImg 
                            src="/main-cleaning.png"
                            width="200"
                            />
                            <p>
                                Ensure your property is left in perfect condition at the end of your lease. This includes a deep cleaning of the kitchen, bathrooms, floors, windows, and more, ensuring you get your security deposit back.
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </NuxtLayout>
  </template>

<style lang="scss">
.mainSection {
  padding-top: 90px;
  background: white;
  background-image: url("@/public/blurred-terrace-min.jpg");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;

  h3 {
    color: $primary-color;
    text-align: center;
    width: 80%;
    font-size: 3.4em;
    font-weight: 700;
    text-transform: uppercase;
    line-height: 1em;
  }
  .subtext{
    background-color: $primary-color;
    margin: 15px 0;
    color: #fff;
    padding: 5px 10px;
    font-size: 700;
    font-size: 1.1em;
  }
}
#services{
    padding: 30px 0;
    h3{
        color: $color-fuente;
        font-size: 3em;
    }
    background-color: $fondo-plomizo;
    h4{
        font-weight: 700;
        color: $color-fuente;
        font-size: 1.2em;
    }
    p{
        color: $color-fuente;
        font-size: 1em;  
    }
}

</style>