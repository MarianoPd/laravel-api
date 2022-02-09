<template>
  <header>
      <nav>
          <ul>
              <li><a href="#">Home</a></li>
              <li><a href="#">Contatti</a></li>
              <li><a href="#">Chi siamo</a></li>
              <li><a href="#">Cosa facciamo</a></li>
              <li><a href="#">Da dove veniamo</a></li>
          </ul>
      </nav>
  </header>
</template>

<script>
export default {
    name: 'Header',
}
</script>

<style lang="scss" scoped>

    header{
        
        background-color: cadetblue;
        text-align: center;
        nav{
            ul{
                list-style: none;
                li{
                    display: inline-block;
                    padding: 30px;
                    a{
                        text-decoration: none;
                        color: white;
                        &:hover{
                            text-decoration: underline;
                        }
                    }
                }
            };
        }
    }

</style>