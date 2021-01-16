<template>
  <section class="main__container profile" id="profile">
    <h2 class="main__container__title">
      <p class="main__container__title--en">Profile</p>
      <p class="main__container__title--ja">プロフィール</p>
    </h2>
    <div class="main__container__content profile__content">
      <img :src="profileImage" alt="中島楓人" class="profile__image" />
      <ul class="profile__list">
        <li
          class="profile__list__item"
          v-for="(profile, key) in profiles"
          :key="key"
        >
          <component class="profile__list__item__icon" :is="profile.icon" />
          <p class="profile__list__item__text">{{ profile.text }}</p>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
import ProfileImage from "@/assets/images/profile.jpg";
import UserSvg from "@/assets/images/user.svg";
import PinSvg from "@/assets/images/pin.svg";
import UnivSvg from "@/assets/images/univ.svg";
import CommentSvg from "@/assets/images/comment.svg";

export default {
  name: "Profile",

  data() {
    return {
      profileImage: ProfileImage,
      profiles: [
        {
          name: "user",
          icon: "UserSvg",
          text: "中島楓人(なかじまふうと)",
        },
        {
          name: "pin",
          icon: "PinSvg",
          text: "東京都杉並区在住",
        },
        {
          name: "univ",
          icon: "UnivSvg",
          text: "明治大学総合数理学部在学中(24卒)",
        },
        {
          name: "comment",
          icon: "CommentSvg",
          text:
            "Webエンジニアを目指している大学生です。身の回りの課題解決･効率化が大好きです。\n主にやっているのはフロントですが、課題解決のために必要な技術を考え学んでいます。\n大学では軽音サークルに入り、趣味でギター、ベースを弾いています。",
        },
      ],
    };
  },

  methods: {
    makeSvgUrl(name) {
      return "../../assets/images/" + name + ".svg";
    },
  },

  components: {
    UserSvg,
    PinSvg,
    UnivSvg,
    CommentSvg,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/import";

.profile {
  &__content {
    display: flex;
    align-items: center;

    @include mq("pc") {
      flex-direction: row;
      justify-content: space-between;
    }

    @include mq("sp") {
      flex-direction: column;
    }
  }

  &__image {
    border-radius: 50%;

    @include mq("pc") {
      width: 24vw;
      max-width: 240px;
      height: 24vw;
      max-height: 240px;
    }

    @include mq("sp") {
      max-width: 200px;
      margin-bottom: 20px;
    }
  }

  &__list {
    @include mq("pc") {
      width: 70vw;
      max-width: 700px;
    }

    @include mq("sp") {
      width: 100%;
    }

    &__item {
      display: flex;

      &:not(:last-child) {
        margin-bottom: 16px;
      }

      &__icon {
        margin-right: 14px;
        display: inline-block;
        min-width: 50px;
      }

      &__text {
        @include mq("pc") {
          font-size: 16px;
        }

        @include mq("sp") {
          font-size: 14px;
        }
      }
    }
  }
}
</style>
