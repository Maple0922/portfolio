<template>
  <section class="main__container profile" id="profile" :class="{ show: show }">
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
          <p class="profile__list__item__text" :class="profile.name">
            {{ profile.text }}
          </p>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
import ProfileImage from "@/assets/images/photo/profile2.jpg";
import UserSvg from "@/assets/images/svg/user.svg";
import CalendarSvg from "@/assets/images/svg/calendar.svg";
import PinSvg from "@/assets/images/svg/pin.svg";
import UnivSvg from "@/assets/images/svg/univ.svg";
import CommentSvg from "@/assets/images/svg/comment.svg";

export default {
  name: "Profile",

  data() {
    return {
      show: false,
      profileImage: ProfileImage,
      profiles: [
        {
          name: "user",
          icon: "UserSvg",
          text: "中島楓人",
        },
        {
          name: "calendar",
          icon: "CalendarSvg",
          text: `1999年生まれ (${this.calcAge()}歳)`,
        },
        {
          name: "pin",
          icon: "PinSvg",
          text: "東京都杉並区 在住",
        },
        {
          name: "univ",
          icon: "UnivSvg",
          text: "明治大学 総合数理学部 在学中(24卒)",
        },
        {
          name: "comment",
          icon: "CommentSvg",
          text:
            "Webエンジニアを目指している大学生です。身の回りの課題解決･効率化をするWebアプリを開発することが好きです。\n主にやっているのはフロントですが、課題解決のために必要な技術を考え学んでいます。\n大学では軽音サークルに入っており、趣味でギター、ベースを弾いています。\n",
        },
      ],
    };
  },

  created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },

  methods: {
    handleScroll() {
      if (!this.show) {
        var top = this.$el.getBoundingClientRect().top;
        this.show = top < window.innerHeight - 300;
      }
    },
    calcAge() {
      const myBirthDay = {
        year: 1999,
        month: 9,
        date: 22,
      };

      const birthDate = new Date(
        myBirthDay.year,
        myBirthDay.month - 1,
        myBirthDay.date
      );

      const y2 = birthDate.getFullYear().toString().padStart(4, "0");
      const m2 = (birthDate.getMonth() + 1).toString().padStart(2, "0");
      const d2 = birthDate.getDate().toString().padStart(2, "0");

      const today = new Date();
      const y1 = today.getFullYear().toString().padStart(4, "0");
      const m1 = (today.getMonth() + 1).toString().padStart(2, "0");
      const d1 = today.getDate().toString().padStart(2, "0");

      const age = Math.floor(
        (Number(y1 + m1 + d1) - Number(y2 + m2 + d2)) / 10000
      );

      return age;
    },
  },

  components: {
    UserSvg,
    CalendarSvg,
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
      margin-right: 16px;
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
      align-items: top;

      &:not(:last-child) {
        margin-bottom: 16px;
      }

      &__icon {
        margin-right: 14px;
        display: inline-block;
        min-width: 20px;
        opacity: 0.5;
        vertical-align: bottom;
        margin-top: 3px;
        @include mq("pc") {
          height: 20px;
        }
        @include mq("sp") {
          height: 14px;
        }
      }

      &__text {
        &.comment {
          white-space: pre-line;
        }
        @include mq("pc") {
          font-size: 15px;
        }

        @include mq("sp") {
          font-size: 13px;
        }
      }
    }
  }
}
</style>
