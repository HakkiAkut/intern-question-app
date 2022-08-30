<template>
  <div class="user-info">
    <div class="column">
      <div class="avatar"><circle-user-avatar size="medium" /></div>

      <router-link to="#" class="username">{{ user.name }}</router-link>
      <p class="position">{{ user.position }}</p>
      <div class="contribution column">
        <router-link class="contribution__link --type-questions" to="#">
          <p>{{ user.contribution.questions }} Questions</p></router-link
        >

        <router-link class="contribution__link --type-answers" to="#"
          ><p>{{ user.contribution.answers }} Answers</p></router-link
        >
        <router-link class="contribution__link --type-best" to="#"
          ><p>{{ user.contribution.bestAnswers }} Best Answers</p></router-link
        >
        <router-link class="contribution__link --type-points" to="#"
          ><p>{{ user.contribution.points }} Points</p></router-link
        >
      </div>
      <button-base
        class="view-btn"
        :color="['backblue', 'fontwhite', 'hoverbackred']"
        :fontfamily="'roboto'"
        @click="routerPush"
      >
        View Profile
      </button-base>
    </div>
  </div>
</template>

<script>
import ButtonBase from "./buttonBase.vue";
export default {
  name: "UserInfoPopup",
  components: {
    CircleUserAvatar: () => import("./CircleUserAvatar.vue"),
    ButtonBase,
  },
  data: () => ({
    user: {
      name: "Hakki Akut",
      position: "Frontend  Intern",
      contribution: {
        questions: 1,
        answers: 10,
        bestAnswers: 3,
        points: 250,
      },
    },
  }),
  methods: {
    routerPush: function () {
      // TO DO: push to user page
    },
  },
};
</script>

<style lang="scss" scoped>
@mixin link-icon($url) {
  content: url($url);
  position: absolute;
  left: 40px;
  width: 13px;
  height: 13px;
  flex-shrink: 1;
}
.user-info {
  content: "";
  width: 260px;
  background: $main-background;
  border: 1px solid $background-gray-300;
  border-radius: 2px;
  position: absolute;
  padding: 20px 0;
  z-index: 9999;
  text-align: center;
  @include flex(column, center, center);
  & .username {
    margin: 10px 0 6px 0;
    text-decoration: none;
    @include font($roboto, $blue, 15px, 700);
    &:hover {
      color: $primary-color;
    }
  }
  p {
    &.position {
      @include font($arial, $text-gray-400, 13px);
      margin-bottom: 20px;
    }
  }
}

.contribution {
  background-color: $background-gray-300;
  text-align: left;
  width: 200px;
  padding: 12px;

  & > #{&}__link {
    @include font($roboto, $text-gray-400, 13px);
    align-items: center;
    text-decoration: none;
    margin: 6px 0;
    margin-left: 18px;
    &:hover {
      color: $blue;
    }
    &.--type-questions > p::before {
      @include link-icon("@/assets/icons/open-book.svg");
    }
    &.--type-answers > p::before {
      @include link-icon("@/assets/icons/comment.svg");
    }
    &.--type-best > p::before {
      @include link-icon("@/assets/icons/graduation-cap.svg");
    }
    &.--type-points > p::before {
      @include link-icon("@/assets/icons/bucket.svg");
    }
  }
}
.avatar {
  margin-left: auto;
  margin-right: auto;
}
.view-btn {
  margin-top: 20px;
  padding-top: 10px;
  padding-bottom: 10px;
}
</style>
