<script>
import axios from 'axios';
export default {
  data() {
    return {
      profiles: {},
      posts: {},
      loaderPost: false,
      loaderProfile: false
    };
  },
  mounted() {
    axios.get('https://flynn.boolean.careers/exercises/api/boolgram/profiles').then((resp) => {
      this.profiles = resp.data;
      this.loaderProfile = true;
    });
    axios.get('https://flynn.boolean.careers/exercises/api/boolgram/posts').then((resp) => {
      this.posts = resp.data;
      this.loaderPost = true;
    });
  }
}
</script>

<template>
  <div v-if="!loaderPost" class="loader">
    Caricamento in corso
    <img src="src\imgs\spinner.gif" alt="Loader">
  </div>
  <div v-else class="container">
    <div class="search-bar">
      <img src="src\imgs\logo.png" alt="logo">
      <div class="searching-bar">
        <input type="text" placeholder="Cerca">
        <div class="search-icon">
          <i class="fa-solid fa-magnifying-glass"></i>
        </div>
      </div>
      <div class="menu-right">
        <i class="fa-solid fa-house"></i>
        <i class="fa-solid fa-heart"></i>
        <img src="src\imgs\Classe 90.jpg" alt="profile">
      </div>
    </div>
    <div class="top-container">
      <div class="stories">
        <div class="stories-container">
          <div v-for="(profile, index) in profiles" :key="index">
            <div class="story">
              <div class="story-profile">
                <img :src="profile.profile_picture" alt="profile">
              </div>
              <div class="story-user">
                {{ profile.profile_name }}
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="profile">
        <div class="logo-user">
          <img src="src\imgs\Classe 90.jpg" alt="profilephoto">
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
        <div v-for="(post, index) in posts" :key="index">
          <div class="post">
            <div class="post-user">
              <div class="post-created">
                <img :src="post.profile_picture" alt="Profile"> <span>{{ post.profile_name }}</span>
              </div>
              <i class="fa-solid fa-ellipsis"></i>
            </div>
            <div class="post-img">
              <img :src="post.post_image" alt="Post Image">
            </div>
            <div class="post-content">
              <div class="post-icons">
                <i class="fa-regular fa-heart heart"></i>
                <i class="fa-regular fa-paper-plane"></i>
              </div>
              <div class="likes">
                <img :src="post.likes.length > 0 ? post.likes[0].profile_picture : ''" alt="userphotolike">
                Piace a
                <p v-if="post.likes.length > 0" style="font-weight: bold;">{{ post.likes[0].username }}</p>
                e altri utenti
              </div>
              <div class="post-comments">
                <div v-if="post.comments.length == 0">
                  No comments here...
                </div>
                <div v-else>
                  <p>Comments</p>
                  <ul>
                    <li v-for="(item, index) in post.comments" :key="index" v-if="index < 4">
                      <span class="user-comment">{{ item.username }}</span> {{ item.text }}
                    </li>
                  </ul>
                </div>
              </div>
              <div class="post-date">
                Pubblicato il: {{ post.date.date.substr(0, 10) }}
              </div>
            </div>
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

.loader {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 30px;
  font-size: 3em;
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
    box-shadow: 11px 11px 22px #bcbcbc,
      -11px -11px 22px #ffffff;
    z-index: 999;
    position: fixed;
    top: 0;
    left: 0;
    padding: 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;

    img {
      width: 200px;
      height: 80px;
    }

    .searching-bar {
      display: flex;

      flex-grow: 1;
      justify-content: center;

      .search-icon {
        width: 25px;
        height: 25px;
        display: flex;
        align-items: center;
        justify-content: center;
        border: 1px solid grey;
        cursor: pointer;
      }

      .search-icon:hover {
        background-color: grey;
        color: white;
      }
    }

    .menu-right {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 20px;

      img {
        width: 50px;
        height: 50px;
        border: 1px solid black;
        border-radius: 50%;
      }

      i {
        font-size: 2em;
      }
    }
  }

  .top-container {
    width: 100%;
    display: flex;
    margin-top: 110px;

    .stories {
      width: 60%;
      height: 90px;
      display: flex;
      align-items: center;

      .stories-container {
        border-radius: 20px;
        box-shadow: 9px 9px 54px #777777,
          -9px -9px 54px #ffffff;
        width: 70%;
        height: 100%;
        margin: 0 auto;
        display: flex;
        align-items: center;
        padding: 5px;

        .story {
          width: 70px;
          height: 70px;
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;

          .story-user {
            font-size: 0.6em;
          }

          .story-profile {
            width: 70%;
            height: 70%;
            margin: 0 auto;
            overflow: hidden;

            img {
              width: 49px;
              height: 49px;
              border: 1px solid red;
              border-radius: 50%;
            }
          }
        }
      }
    }

    .profile {
      display: flex;
      align-items: center;
      flex-grow: 1;
      padding: 5px;
      border-radius: 20px;
      box-shadow: 9px 9px 54px #777777,
        -9px -9px 54px #ffffff;

      .logo-user {
        width: 80px;
        height: 80px;
        border-radius: 50%;
        margin-right: 10px;

        img {
          width: 80px;
          height: 80px;
          border: 1px solid red;
          border-radius: 50%;
        }
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
        margin-bottom: 30px;
        height: 700px;
        display: flex;
        flex-direction: column;
        border-radius: 20px;
        box-shadow: 9px 9px 54px #777777,
          -9px -9px 54px #ffffff;

        .post-user {
          width: 100%;
          height: 50px;
          display: flex;
          justify-content: space-between;
          align-items: center;

          i {
            font-size: 2em;
            margin-right: 5px;
            cursor: pointer;
          }

          i:hover {
            color: blue;
          }

          .post-created {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 5px;

            img {
              width: 40px;
              height: 40px;
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
          padding: 5px;

          .post-date {
            color: grey;
            font-weight: bold;
            height: 75px;
            display: flex;
            align-items: center;
          }

          .post-icons {
            font-size: 1.4em;
            letter-spacing: 1em;

            .heart:hover {
              color: red;
            }
          }

          .likes {
            width: 100%;
            display: flex;
            align-items: center;
            gap: 10px;

            img {
              width: 40px;
              height: 40px;
              border-radius: 50%;
            }
          }

          .post-comments {
            margin-top: 10px;
            max-height: 174px;
            overflow: hidden;
          }

          .post-comments ul {
            list-style-type: none;
            margin-top: 10px;

            .user-comment {
              font-weight: bold;
              margin-right: 30px;
            }
          }

          .post-comments ul li {
            margin-bottom: 10px;
          }
        }
      }
    }

    .direct {
      padding: 5px;
      border-radius: 5px;
      flex-grow: 1;

      .direct-column {
        width: 80%;
        margin: 0 auto;
        margin-top: 50px;
        padding: 5px;
        border-radius: 20px;
        box-shadow: 9px 9px 54px #777777,
          -9px -9px 54px #ffffff;

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
