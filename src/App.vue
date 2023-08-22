<script setup>

</script>

<template class="position">
  <div class="container">
    <div class="search-bar">
      <img src="src\imgs\logo.png" alt="logomilanfanclub">
      <img src="src\imgs\Milan Club.png" alt="title">
    </div>
    <div class="top-container">
      <div class="stories">
        Stories
      </div>
      <div class="profile">
        <div class="logo-user"></div>
        <div class="username">
          Alessio Rossi
        </div>
      </div>
    </div>
    <!---->
    <div class="bottom-container">
      <div class="posts">
        <div class="post">
          <div class="post-img">
            <img
              src="https://tmssl.akamaized.net/images/foto/galerie/olivier-giroud-ac-mailand-2022-1644135835-79775.jpg?lm=1644135848"
              alt="">
          </div>
          <div class="post-content">
            Olivier Giroud, segna ancora una volta. Contro il Bologna si è girato Giroud!!!!!
          </div>
        </div>
        <div class="post">
          <div class="post-img">
            Img here
          </div>
          <div class="post-content">
            Content Here
          </div>
        </div>
        <div class="post">
          <div class="post-img">
            Img here
          </div>
          <div class="post-content">
            Content Here
          </div>
        </div>
      </div>
      <div class="direct">
        All messages
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  position: relative;

  .search-bar {
    width: 100%;
    height: 100px;
    background-color: white;
    border: 1px solid grey;
    border-radius: 10px;
    z-index: 999;
    position: fixed;
    top: 0;
    left: 0;
    padding: 10px;

    img {
      width: 80px;
      height: 80px;
    }
  }

  .top-container {
    width: 100%;
    display: flex;
    margin-top: 100px;
    border: 1px solid gold;

    .stories {
      width: 60%;
      height: 90px;
      border: 2px solid black;
    }
  }

  .bottom-container {
    flex-grow: 1;
    display: flex;

    .posts {
      width: 60%;
      border: 2px solid yellow;
      padding: 10px;

      .post {
        width: 60%;
        margin: 0 auto;
        height: 400px;
        display: flex;
        flex-direction: column;

        .post-img {
          width: 100%;
          height: 60%;
          border: 1px solid black;

          img {
            width: 464px;
            height: 238px;
          }
        }

        .post-content {
          flex-grow: 1;
          background-color: gold;
        }
      }
    }
  }
}
</style>
