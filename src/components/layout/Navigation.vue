<template>
  <div class="navigation">
    <div class="logo">
      <router-link :to="{ name: 'tips' }">
        <img
          alt=""
          src="../../assets/headerLogo.svg"
        >
      </router-link>
    </div>
    <div class="navigation__item tips">
      <router-link :to="{ name: 'tips' }">
        <IconTips class="navigation__item__image" />
        <span>{{ $t('tips') }}</span>
      </router-link>
    </div>
    <div
      v-if="isLoggedIn"
      class="navigation__item profile"
    >
      <router-link :to="{ name: 'user-profile', params: { address: account } }">
        <IconUser class="navigation__item__image" />
        <span>{{ $t('components.layout.Navigation.MyProfile') }}</span>
      </router-link>
    </div>
    <div class="navigation__item league">
      <router-link :to="{ name: 'league' }">
        <IconDiamond class="navigation__item__image" />
        <span>{{ $t('components.layout.Navigation.League') }}</span>
      </router-link>
    </div>
    <div class="navigation__item governance">
      <router-link :to="{ name: 'voting' }">
        <IconGovernance class="navigation__item__image" />
        <span>{{ $t('components.layout.Navigation.Governance') }}</span>
      </router-link>
    </div>
    <div class="navigation__item faq">
      <router-link :to="{ name: 'faq' }">
        <IconHelp class="navigation__item__image" />
        <span>{{ $t('FAQ') }}</span>
      </router-link>
    </div>
    <div class="navigation__item networking">
      <router-link :to="{ name: 'conference' }">
        <IconMeet class="navigation__item__image" />
        <span>{{ $t('Networking.MenuLink') }}</span>
      </router-link>
    </div>
  </div>
</template>

<script>
import { mapState, mapGetters } from 'vuex';
import IconTips from '../../assets/iconTips.svg?icon-component';
import IconUser from '../../assets/iconUser.svg?icon-component';
import IconHelp from '../../assets/iconHelp.svg?icon-component';
import IconDiamond from '../../assets/iconDiamond.svg?icon-component';
import IconGovernance from '../../assets/iconGovernance.svg?icon-component';
import IconMeet from '../../assets/iconMeet.svg?icon-component';

export default {
  name: 'Navigation',
  components: {
    IconTips,
    IconUser,
    IconHelp,
    IconDiamond,
    IconGovernance,
    IconMeet,
  },
  computed: {
    ...mapGetters(['isLoggedIn']),
    ...mapState(['account']),
  },
};
</script>

<style lang="scss">
  .logo {
    margin-bottom: 0.75rem;

    img {
      width: 9.2rem;
    }
  }

  .navigation {
    color: $standard_font_color;
    font-size: 1rem;
    font-weight: 500;
  }

  .navigation__item {
    font-size: 0.93rem;
    margin-bottom: 0.65rem;

    a {
      align-items: center;
      color: #fff;
      cursor: pointer;
      display: flex;
      line-height: 1;
    }

    a:hover,
    .router-link-exact-active {
      color: $custom_links_color;
      text-decoration: none;
    }
  }

  .navigation__item__image {
    display: inline-block;
    height: 1.3rem;
    margin-right: 0.5rem;
    width: 1.3rem;

    .league & path {
      transform: scale(1.05);
    }

    .league &,
    .governance & {
      padding: 0.2rem;
    }
  }

  @media (min-width: 1440px) {
    .navigation__item {
      color: #fff;
      font-size: 1rem;
      height: 1.2rem;
      line-height: 1.2rem;
      margin-bottom: 1.55rem;
    }
  }

  .iconMeet {
    width: 27px;
    height: 18px;
    padding-left: 5px;
  }
</style>
