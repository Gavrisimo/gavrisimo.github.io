---
title: Dropdown menu where menu is not child of the navigation item
author: Miloš Gavrilović
layout: post
permalink: /dropdown-menu-where-menu-is-not-child-of-the-navigation-item/
categories:
  - Tips
---
It's easy to have dropdown using jQuery .hide() and .show() when dropdown menu is child element to the navigation element that is being click on, or hovered because when you move your mouse to the dropdown menu, you are still on that navigation item, so mouseleave wasn't called yet, and that's when you want to actually hide the dropdown menu.

It's just a little bit harder to do that when you have navigation item and dropdown menu totally separated, for example if dropdown menu is positioned absolutely below the navigation in order to have 100% width of the window.

This is just copy/paste for this functionality from one of the projects I'm working on:

<pre class="brush: jscript; title: ; notranslate" title="">var navigation_timer = null;

// Show/hide main navigation dropdown
$('.main-navigation').find('a:first-child').on({
  mouseenter: function() {
    if ( navigation_timer ) {
      clearTimeout( navigation_timer );
    }

    $('.main-navigation-dropdown-menu').show();
  },
  mouseleave: function() {
    if ( navigation_timer ) {
      clearTimeout( navigation_timer );
    }

    navigation_timer = setTimeout( function() {
      $('.main-navigation-dropdown-menu').hide();
    }, 100 );
  }
});

$('.main-navigation-dropdown-menu').on({
  mouseenter: function() {
    if ( navigation_timer ) {
      clearTimeout( navigation_timer );
    }
  },
  mouseleave: function() {
    navigation_timer = setTimeout( function() {
      $('.main-navigation-dropdown-menu').hide();
    }, 100 );
  }
});
</pre>
