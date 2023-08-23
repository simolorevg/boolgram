<script>
import axios from 'axios';
export default {
  data() {
    return {
      profiles: {},
      posts: {}
    };
  },
  mounted() {
    axios.get('https://flynn.boolean.careers/exercises/api/boolgram/profiles').then((resp) => {
      this.profiles = resp.data;
    });
    axios.get('https://flynn.boolean.careers/exercises/api/boolgram/posts').then((resp) => {
      this.posts = resp.data;
    });
  }
}
</script>

<template class="position">
  <div class="container">
    <div class="search-bar">
      <img src="src\imgs\logo.png" alt="logo">
    </div>
    <div class="top-container">
      <div class="stories">
        <div class="stories-container">
          <div class="story">
            <div class="story-profile">

            </div>
            <div class="story-user">
              username
            </div>
          </div>
        </div>
      </div>
      <div class="profile">
        <div class="logo-user">

        </div>
        <div class="username">
          Mario Rossi
        </div>
      </div>
    </div>
    <!---->
    <div class="bottom-container">
      <!--POST CONTAINER-->
      <div class="posts">

        <!--SINGLE POST-->
        <div class="post">
          <div class="post-user">
            <div class="post-created">
              <img src="" alt="Profile"> <span>username</span>
            </div>
            options
          </div>
          <div class="post-img">
            <img src="" alt="Post Image">
          </div>
          <div class="post-content">

          </div>
        </div>
        <!--/SINGLE POST-->

      </div>
      <!--/POST CONTAINER-->

      <!--DIRECT CONTAINER-->
      <div class="direct">
        <div class="direct-column">
          <div class="advice">
            <p>For you</p>
            <div class="advice-btn">See More</div>
          </div>

          <!--ADVICES PROFILES LIST-->
          <div v-for="(item, index) in profiles" :key="index">

            <div class="advice-profile">
              <div class="advice-img">
                <img :src="item.profile_picture" alt="">
              </div>
              <div class="advice-username">
                {{ item.profile_name }}
              </div>
              <div class="btn-follow">Follow</div>
            </div>
          </div>
          <!--/ADVICES PROFILES LIST-->
        </div>
      </div>
      <!--/DIRECT CONTAINER-->
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
    border-bottom: 1px solid gray;
    z-index: 999;
    position: fixed;
    top: 0;
    left: 0;
    padding: 10px;

    img {
      width: 150px;
      height: 80px;
    }
  }

  .top-container {
    width: 100%;
    display: flex;
    margin-top: 100px;

    .stories {
      width: 60%;
      height: 90px;
      display: flex;
      align-items: center;

      .stories-container {
        border: 1px solid grey;
        border-radius: 5px;
        width: 70%;
        height: 100%;
        margin: 0 auto;
        display: flex;
        align-items: center;
        padding: 5px;

        .story {
          width: 80px;
          height: 80px;
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;

          .story-profile {
            width: 70%;
            height: 70%;
            margin: 0 auto;
            background-color: red;
            border-radius: 50%;
          }
        }
      }
    }

    .profile {
      display: flex;
      align-items: center;
      flex-grow: 1;
      padding: 5px;
      border: 1px solid black;

      .logo-user {
        width: 80px;
        height: 80px;
        background-color: red;
        border-radius: 50%;
        margin-right: 10px;
      }
    }
  }

  .bottom-container {
    flex-grow: 1;
    display: flex;

    .posts {
      width: 60%;
      padding: 10px;
      margin-top: 50px;

      .post {
        max-width: 70%;
        margin: 0 auto;
        height: 500px;
        display: flex;
        flex-direction: column;
        border: 1px solid grey;
        border-radius: 5px;

        .post-user {
          width: 100%;
          height: 50px;
          display: flex;
          justify-content: space-between;
          align-items: center;

          .post-created {
            display: flex;
            align-items: center;
            gap: 10px;

            img {
              width: 40px;
              border: 1px solid black;
              border-radius: 50%;
              margin-left: 5px;
            }
          }
        }

        .post-img {
          max-width: 100%;
          max-height: 60%;

          img {
            width: 544px;
            height: 300px;
          }
        }

        .post-content {
          flex-grow: 1;
        }
      }
    }

    .direct {
      padding: 5px;
      border: 1px solid grey;
      border-radius: 5px;
      flex-grow: 1;

      .direct-column {
        width: 80%;
        margin: 0 auto;
        border: 1px solid grey;
        padding: 5px;
        border-radius: 5px;

        .advice {
          width: 100%;
          display: flex;
          justify-content: space-between;
          margin-bottom: 10px;

          .advice-btn {
            font-weight: bold;
            cursor: pointer;
          }
        }

        .advice-profile {
          width: 100%;
          display: flex;
          justify-content: space-between;
          align-items: center;
          margin-bottom: 10px;

          .advice-img {
            width: 20%;
            height: 80px;
            border-radius: 50%;
            background-color: aqua;
            display: flex;
            justify-content: center;
            align-items: center;

            img {
              width: 100%;
              height: 100%;
              border: 1px solid red;
              border-radius: 50%;
            }
          }

          .advice-username {
            font-weight: bold;
          }

          .btn-follow {
            width: 20%;
            height: 30px;
            display: flex;
            justify-content: end;
            align-items: center;
            cursor: pointer;
            font-weight: bold;
            color: blue;
          }

          .btn-follow:hover {
            color: black;
          }
        }
      }
    }
  }
}
</style>
