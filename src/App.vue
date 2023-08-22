<script setup>

</script>

<template>
  <div class="container">
    <div class="left-container">
      <div class="stories">
        Stories
      </div>
      <div class="posts">
        <div class="post">
          <div class="post-img">
            Img here
          </div>
          <div class="post-content">
            Content Here
          </div>
        </div>
      </div>
    </div>
    <!---->
    <div class="right-container">
      <div class="profile">
        Your profile here
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

  .left-container {
    width: 60%;
    height: 100%;
    border: 1px solid red;
    position: relative;

    .stories {
      width: 100%;
      height: 20%;
      background-color: blue;
    }

    .posts {
      width: 100%;
      height: 80%;
      background-color: aquamarine;
      padding: 10px;

      .post {
        width: 60%;
        height: 400px;
        margin: 0 auto;
        border: 2px solid black;
        display: flex;
        flex-direction: column;

        .post-img {
          width: 100%;
          height: 60%;
          background-color: crimson;
        }
      }
    }
  }

  .right-container {
    flex-grow: 1;
    height: 100%;
    border: 2px solid black;
    position: relative;

    .profile {
      width: 100%;
      height: 20%;
      background-color: purple;
    }

    .direct {
      width: 100%;
      height: 80%;
      background-color: pink;
    }
  }
}
</style>
