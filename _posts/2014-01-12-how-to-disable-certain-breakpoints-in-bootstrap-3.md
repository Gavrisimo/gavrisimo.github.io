---
title: How to disable certain breakpoints in Bootstrap 3?
author: Miloš Gavrilović
layout: post
permalink: /how-to-disable-certain-breakpoints-in-bootstrap-3/
categories:
  - Tips
---
It's really easy, you just need to edit one file!

So, go ahead and open `_grid.scss`, or `_grid.less` if you are using normal less version, and find this part:

<pre class="brush: css; title: ; notranslate" title="">.container {
  @include container-fixed();

  @media (min-width: $screen-sm-min) {
    width: $container-sm;
  }
  @media (min-width: $screen-md-min) {
    width: $container-md;
  }
  @media (min-width: $screen-lg-min) {
    width: $container-lg;
  }
}
</pre>

So if you want to remove large version, just remove or comment that last part, so you have something like this:

<pre class="brush: css; title: ; notranslate" title="">.container {
  @include container-fixed();

  @media (min-width: $screen-sm-min) {
    width: $container-sm;
  }
  @media (min-width: $screen-md-min) {
    width: $container-md;
  }
}
</pre>

That will remove styling for .container on screens larger then 992px.

Next we need to remove columns for large displays. At the bottom of the same file there is this part:

<pre class="brush: css; title: ; notranslate" title="">// Large grid
//
// Columns, offsets, pushes, and pulls for the large desktop device range.

@media (min-width: $screen-lg-min) {
  @include make-grid-columns-float(lg);
  @include make-grid($grid-columns, lg, width);
  @include make-grid($grid-columns, lg, pull);
  @include make-grid($grid-columns, lg, push);
  @include make-grid($grid-columns, lg, offset);
}
</pre>

Just go ahead and remove it or comment it out. That should remove .col-lg-* classes from your compiled .css file.
