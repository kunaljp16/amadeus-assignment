<script>
import logoWhite from "./../assets/logos/Logo White.vue";
import MenuWhite from "./../assets/icons/Menu White.vue";
import CloseWhite from "./../assets/icons/Close White.vue";
export default {
  components: {
    logoWhite,
    MenuWhite,
    CloseWhite,
  },
  data() {
    return {
      isPanelOpen: false,
    };
  },
  methods: {
    openPanel: function () {
      return (this.isPanelOpen = true);
    },
    closePanel: function () {
      return (this.isPanelOpen = false);
    },
  },
};
</script>

<template>
  <section class="headerWrapper container-fluid">
    <header class="header container d-flex justify-content-between" id="header">
      <a href="#"><logoWhite /></a>
      <ul class="nav justify-content-end mt-1 desktop">
        <li class="nav-item home">
          <a class="nav-link active" aria-current="page" href="#">HOME</a>
        </li>
        <li class="nav-item ourScreens">
          <a class="nav-link" href="#">OUR SCREENS</a>
        </li>
        <li class="nav-item schedule">
          <a class="nav-link" href="#">SCHEDULE</a>
        </li>
        <li class="nav-item movieLibrary">
          <a class="nav-link" href="#">MOVIE LIBRARY</a>
        </li>
        <li class="nav-item contact">
          <a class="nav-link" href="#">LOCATION &amp; CONTACT</a>
        </li>
      </ul>
      <div class="mobileMenuWrapper">
        <a href="javascript:void(0)" @click="openPanel"><MenuWhite /></a>
        <div
          :class="isPanelOpen ? 'mobileMenuPanel panelOpen' : 'mobileMenuPanel'"
        >
          <span class="closeBtn" >
            <a href="javascript:void(0)" role="button" @click="closePanel">
            <CloseWhite class="justify-content-end" />
          </a>
          </span>
          <ul class="menuList mobile">
            <li class="nav-item home">
              <a class="nav-link active" aria-current="page" href="#">HOME</a>
            </li>
            <li class="nav-item ourScreens">
              <a class="nav-link" href="#">OUR SCREENS</a>
            </li>
            <li class="nav-item schedule">
              <a class="nav-link" href="#">SCHEDULE</a>
            </li>
            <li class="nav-item movieLibrary">
              <a class="nav-link" href="#">MOVIE LIBRARY</a>
            </li>
            <li class="nav-item contact">
              <a class="nav-link" href="#">LOCATION &amp; CONTACT</a>
            </li>
            <li class="nav-item gallery">
              <a class="nav-link" href="#">GALLERY</a>
            </li>
          </ul>
        </div>
      </div>
    </header>
  </section>
</template>

<style lang="scss">
@import "./../assets/scss/variables";

.headerWrapper {
  border-bottom: 1px solid $dark-gray;

  .header {

    @media (min-width: 375px) and (max-width: 1279px) {
      width: calc(100% - 20px);
      padding: 20px;
    }
    padding: 20px 0;

    & > a {
      margin-right: auto;
    }

    .nav-link {
      color: $white;

      &:hover {
        text-decoration: underline;
      }
    }
    .mobileMenuWrapper {
      margin: 6px 0 0;
    }
    .mobileMenuPanel {
      display: none;
      width: 300px;
      height: 100vh;
      background-color: $black;
      padding: 10px 30px 0 10px;
      position: absolute;
      top: 0;
      right: 0;

      &.panelOpen {
        display: block;
      }
    }
    .menuList {
      list-style: none;
      padding: 0;
      margin: 0 30px 0 0;

      li {
        padding: 12px 10px;
        &:hover {
          cursor: pointer;
          background: $dark-gray2;
        }
      }
    }
    .closeBtn {
      display: block;
      margin: 0 30px 10px 0;
      text-align: right;
      background: none;
      border: none;
    }
    .mobile {
      .contact,
      .home,
      .ourScreens,
      .schedule,
      .movieLibrary,
      .contact {
        display: none;
      }
    }
  }
}

@media (min-width: 375px) and (max-width: 767px) {
  .headerWrapper {
    .header {
      .mobile {
        .contact,
        .home,
        .ourScreens,
        .schedule,
        .movieLibrary,
        .contact {
          display: block;
        }
      }

      .desktop {
        display: none;
      }
    }
  }
}
@media (min-width: 768px) and (max-width: 1024px) {
  .headerWrapper {
    .header {
      .desktop .contact {
        display: none;
      }
      .mobile .contact {
        display: block;
      }
    }
  }
}
</style>
