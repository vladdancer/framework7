<template>
  <f7-page>
    <f7-navbar title="Appbar" back-link="Back"></f7-navbar>
    <f7-block strong>
      <p>
        Appbar is the main app bar with actions on top of the whole app. It is designed to be used
        in desktop apps with Aurora theme.
      </p>
    </f7-block>
    <f7-block strong>
      <f7-button fill @click="toggleAppbar">Toggle Appbar</f7-button>
    </f7-block>
  </f7-page>
</template>
<script>
import { f7Page, f7Navbar, f7Block, f7Button, f7 } from 'framework7-vue';
import $ from 'dom7';

let appbarEnabled = false;

export default {
  components: {
    f7Page,
    f7Navbar,
    f7Block,
    f7Button,
  },
  data() {
    return {
      appbarEnabled,
    };
  },
  methods: {
    enableAppbar() {
      const self = this;
      self.appbarEnabled = true;
      appbarEnabled = true;
      f7.root.prepend(`
        <div class="appbar">
          <div class="appbar-inner">
            <div class="left">
              <a href="#" class="button button-small panel-toggle display-flex" data-panel="left">
                <i class="f7-icons">bars</i>
              </a>
              <a href="#" class="button button-small display-flex margin-left-half">
                <i class="f7-icons">square_list</i>
              </a>
              <a href="#" class="button button-small display-flex margin-left-half">
                <i class="f7-icons">arrowshape_turn_up_left_fill</i>
              </a>
              <a href="#" class="button button-small display-flex margin-left-half">
                <i class="f7-icons">arrowshape_turn_up_right_fill</i>
              </a>
            </div>
            <div class="right">
              <div class="searchbar searchbar-inline">
                <div class="searchbar-input-wrap">
                  <input type="text" placeholder="Search app">
                  <i class="searchbar-icon"></i>
                  <div class="input-clear-button"></div>
                </div>
              </div>
            </div>

          </div>
        </div>
        `);
    },
    disableAppbar() {
      const self = this;
      self.appbarEnabled = false;
      appbarEnabled = false;
      $('.appbar').remove();
    },
    toggleAppbar() {
      const self = this;
      if (self.appbarEnabled) {
        self.disableAppbar();
      } else {
        self.enableAppbar();
      }
    },
  },
};
</script>
