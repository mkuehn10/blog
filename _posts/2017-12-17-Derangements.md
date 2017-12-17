---
layout: post
title: Stork Deliveries and Derangements
excerpt: I came across an odd problem that I had never really explored before in The Practice of Statistics, 5th Edition Annotated Teacher's Edition. In a sidebar alternative activity, there was mention of a "random baby" applet that simulated a stork delivering babies to homes. It was then suggested that the concept of a derangement be researched. I was intrigued, so I looked up what a derangement was.
---
<html>
<head><meta charset="utf-8" />
<title>Derangements</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>

<style type="text/css">
    /*!
*
* Twitter Bootstrap
*
*/
/*!
 * Bootstrap v3.3.7 (http://getbootstrap.com)
 * Copyright 2011-2016 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */
/*! normalize.css v3.0.3 | MIT License | github.com/necolas/normalize.css */
html {
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
body {
  margin: 0;
}
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
main,
menu,
nav,
section,
summary {
  display: block;
}
audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline;
}
audio:not([controls]) {
  display: none;
  height: 0;
}
[hidden],
template {
  display: none;
}
a {
  background-color: transparent;
}
a:active,
a:hover {
  outline: 0;
}
abbr[title] {
  border-bottom: 1px dotted;
}
b,
strong {
  font-weight: bold;
}
dfn {
  font-style: italic;
}
h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
mark {
  background: #ff0;
  color: #000;
}
small {
  font-size: 80%;
}
sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}
sup {
  top: -0.5em;
}
sub {
  bottom: -0.25em;
}
img {
  border: 0;
}
svg:not(:root) {
  overflow: hidden;
}
figure {
  margin: 1em 40px;
}
hr {
  box-sizing: content-box;
  height: 0;
}
pre {
  overflow: auto;
}
code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em;
}
button,
input,
optgroup,
select,
textarea {
  color: inherit;
  font: inherit;
  margin: 0;
}
button {
  overflow: visible;
}
button,
select {
  text-transform: none;
}
button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer;
}
button[disabled],
html input[disabled] {
  cursor: default;
}
button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}
input {
  line-height: normal;
}
input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: textfield;
  box-sizing: content-box;
}
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
fieldset {
  border: 1px solid #c0c0c0;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em;
}
legend {
  border: 0;
  padding: 0;
}
textarea {
  overflow: auto;
}
optgroup {
  font-weight: bold;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
td,
th {
  padding: 0;
}
/*! Source: https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css */
@media print {
  *,
  *:before,
  *:after {
    background: transparent !important;
    color: #000 !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }
  a,
  a:visited {
    text-decoration: underline;
  }
  a[href]:after {
    content: " (" attr(href) ")";
  }
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  a[href^="#"]:after,
  a[href^="javascript:"]:after {
    content: "";
  }
  pre,
  blockquote {
    border: 1px solid #999;
    page-break-inside: avoid;
  }
  thead {
    display: table-header-group;
  }
  tr,
  img {
    page-break-inside: avoid;
  }
  img {
    max-width: 100% !important;
  }
  p,
  h2,
  h3 {
    orphans: 3;
    widows: 3;
  }
  h2,
  h3 {
    page-break-after: avoid;
  }
  .navbar {
    display: none;
  }
  .btn > .caret,
  .dropup > .btn > .caret {
    border-top-color: #000 !important;
  }
  .label {
    border: 1px solid #000;
  }
  .table {
    border-collapse: collapse !important;
  }
  .table td,
  .table th {
    background-color: #fff !important;
  }
  .table-bordered th,
  .table-bordered td {
    border: 1px solid #ddd !important;
  }
}
@font-face {
  font-family: 'Glyphicons Halflings';
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot');
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot?#iefix') format('embedded-opentype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff2') format('woff2'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff') format('woff'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.ttf') format('truetype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular') format('svg');
}
.glyphicon {
  position: relative;
  top: 1px;
  display: inline-block;
  font-family: 'Glyphicons Halflings';
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.glyphicon-asterisk:before {
  content: "\002a";
}
.glyphicon-plus:before {
  content: "\002b";
}
.glyphicon-euro:before,
.glyphicon-eur:before {
  content: "\20ac";
}
.glyphicon-minus:before {
  content: "\2212";
}
.glyphicon-cloud:before {
  content: "\2601";
}
.glyphicon-envelope:before {
  content: "\2709";
}
.glyphicon-pencil:before {
  content: "\270f";
}
.glyphicon-glass:before {
  content: "\e001";
}
.glyphicon-music:before {
  content: "\e002";
}
.glyphicon-search:before {
  content: "\e003";
}
.glyphicon-heart:before {
  content: "\e005";
}
.glyphicon-star:before {
  content: "\e006";
}
.glyphicon-star-empty:before {
  content: "\e007";
}
.glyphicon-user:before {
  content: "\e008";
}
.glyphicon-film:before {
  content: "\e009";
}
.glyphicon-th-large:before {
  content: "\e010";
}
.glyphicon-th:before {
  content: "\e011";
}
.glyphicon-th-list:before {
  content: "\e012";
}
.glyphicon-ok:before {
  content: "\e013";
}
.glyphicon-remove:before {
  content: "\e014";
}
.glyphicon-zoom-in:before {
  content: "\e015";
}
.glyphicon-zoom-out:before {
  content: "\e016";
}
.glyphicon-off:before {
  content: "\e017";
}
.glyphicon-signal:before {
  content: "\e018";
}
.glyphicon-cog:before {
  content: "\e019";
}
.glyphicon-trash:before {
  content: "\e020";
}
.glyphicon-home:before {
  content: "\e021";
}
.glyphicon-file:before {
  content: "\e022";
}
.glyphicon-time:before {
  content: "\e023";
}
.glyphicon-road:before {
  content: "\e024";
}
.glyphicon-download-alt:before {
  content: "\e025";
}
.glyphicon-download:before {
  content: "\e026";
}
.glyphicon-upload:before {
  content: "\e027";
}
.glyphicon-inbox:before {
  content: "\e028";
}
.glyphicon-play-circle:before {
  content: "\e029";
}
.glyphicon-repeat:before {
  content: "\e030";
}
.glyphicon-refresh:before {
  content: "\e031";
}
.glyphicon-list-alt:before {
  content: "\e032";
}
.glyphicon-lock:before {
  content: "\e033";
}
.glyphicon-flag:before {
  content: "\e034";
}
.glyphicon-headphones:before {
  content: "\e035";
}
.glyphicon-volume-off:before {
  content: "\e036";
}
.glyphicon-volume-down:before {
  content: "\e037";
}
.glyphicon-volume-up:before {
  content: "\e038";
}
.glyphicon-qrcode:before {
  content: "\e039";
}
.glyphicon-barcode:before {
  content: "\e040";
}
.glyphicon-tag:before {
  content: "\e041";
}
.glyphicon-tags:before {
  content: "\e042";
}
.glyphicon-book:before {
  content: "\e043";
}
.glyphicon-bookmark:before {
  content: "\e044";
}
.glyphicon-print:before {
  content: "\e045";
}
.glyphicon-camera:before {
  content: "\e046";
}
.glyphicon-font:before {
  content: "\e047";
}
.glyphicon-bold:before {
  content: "\e048";
}
.glyphicon-italic:before {
  content: "\e049";
}
.glyphicon-text-height:before {
  content: "\e050";
}
.glyphicon-text-width:before {
  content: "\e051";
}
.glyphicon-align-left:before {
  content: "\e052";
}
.glyphicon-align-center:before {
  content: "\e053";
}
.glyphicon-align-right:before {
  content: "\e054";
}
.glyphicon-align-justify:before {
  content: "\e055";
}
.glyphicon-list:before {
  content: "\e056";
}
.glyphicon-indent-left:before {
  content: "\e057";
}
.glyphicon-indent-right:before {
  content: "\e058";
}
.glyphicon-facetime-video:before {
  content: "\e059";
}
.glyphicon-picture:before {
  content: "\e060";
}
.glyphicon-map-marker:before {
  content: "\e062";
}
.glyphicon-adjust:before {
  content: "\e063";
}
.glyphicon-tint:before {
  content: "\e064";
}
.glyphicon-edit:before {
  content: "\e065";
}
.glyphicon-share:before {
  content: "\e066";
}
.glyphicon-check:before {
  content: "\e067";
}
.glyphicon-move:before {
  content: "\e068";
}
.glyphicon-step-backward:before {
  content: "\e069";
}
.glyphicon-fast-backward:before {
  content: "\e070";
}
.glyphicon-backward:before {
  content: "\e071";
}
.glyphicon-play:before {
  content: "\e072";
}
.glyphicon-pause:before {
  content: "\e073";
}
.glyphicon-stop:before {
  content: "\e074";
}
.glyphicon-forward:before {
  content: "\e075";
}
.glyphicon-fast-forward:before {
  content: "\e076";
}
.glyphicon-step-forward:before {
  content: "\e077";
}
.glyphicon-eject:before {
  content: "\e078";
}
.glyphicon-chevron-left:before {
  content: "\e079";
}
.glyphicon-chevron-right:before {
  content: "\e080";
}
.glyphicon-plus-sign:before {
  content: "\e081";
}
.glyphicon-minus-sign:before {
  content: "\e082";
}
.glyphicon-remove-sign:before {
  content: "\e083";
}
.glyphicon-ok-sign:before {
  content: "\e084";
}
.glyphicon-question-sign:before {
  content: "\e085";
}
.glyphicon-info-sign:before {
  content: "\e086";
}
.glyphicon-screenshot:before {
  content: "\e087";
}
.glyphicon-remove-circle:before {
  content: "\e088";
}
.glyphicon-ok-circle:before {
  content: "\e089";
}
.glyphicon-ban-circle:before {
  content: "\e090";
}
.glyphicon-arrow-left:before {
  content: "\e091";
}
.glyphicon-arrow-right:before {
  content: "\e092";
}
.glyphicon-arrow-up:before {
  content: "\e093";
}
.glyphicon-arrow-down:before {
  content: "\e094";
}
.glyphicon-share-alt:before {
  content: "\e095";
}
.glyphicon-resize-full:before {
  content: "\e096";
}
.glyphicon-resize-small:before {
  content: "\e097";
}
.glyphicon-exclamation-sign:before {
  content: "\e101";
}
.glyphicon-gift:before {
  content: "\e102";
}
.glyphicon-leaf:before {
  content: "\e103";
}
.glyphicon-fire:before {
  content: "\e104";
}
.glyphicon-eye-open:before {
  content: "\e105";
}
.glyphicon-eye-close:before {
  content: "\e106";
}
.glyphicon-warning-sign:before {
  content: "\e107";
}
.glyphicon-plane:before {
  content: "\e108";
}
.glyphicon-calendar:before {
  content: "\e109";
}
.glyphicon-random:before {
  content: "\e110";
}
.glyphicon-comment:before {
  content: "\e111";
}
.glyphicon-magnet:before {
  content: "\e112";
}
.glyphicon-chevron-up:before {
  content: "\e113";
}
.glyphicon-chevron-down:before {
  content: "\e114";
}
.glyphicon-retweet:before {
  content: "\e115";
}
.glyphicon-shopping-cart:before {
  content: "\e116";
}
.glyphicon-folder-close:before {
  content: "\e117";
}
.glyphicon-folder-open:before {
  content: "\e118";
}
.glyphicon-resize-vertical:before {
  content: "\e119";
}
.glyphicon-resize-horizontal:before {
  content: "\e120";
}
.glyphicon-hdd:before {
  content: "\e121";
}
.glyphicon-bullhorn:before {
  content: "\e122";
}
.glyphicon-bell:before {
  content: "\e123";
}
.glyphicon-certificate:before {
  content: "\e124";
}
.glyphicon-thumbs-up:before {
  content: "\e125";
}
.glyphicon-thumbs-down:before {
  content: "\e126";
}
.glyphicon-hand-right:before {
  content: "\e127";
}
.glyphicon-hand-left:before {
  content: "\e128";
}
.glyphicon-hand-up:before {
  content: "\e129";
}
.glyphicon-hand-down:before {
  content: "\e130";
}
.glyphicon-circle-arrow-right:before {
  content: "\e131";
}
.glyphicon-circle-arrow-left:before {
  content: "\e132";
}
.glyphicon-circle-arrow-up:before {
  content: "\e133";
}
.glyphicon-circle-arrow-down:before {
  content: "\e134";
}
.glyphicon-globe:before {
  content: "\e135";
}
.glyphicon-wrench:before {
  content: "\e136";
}
.glyphicon-tasks:before {
  content: "\e137";
}
.glyphicon-filter:before {
  content: "\e138";
}
.glyphicon-briefcase:before {
  content: "\e139";
}
.glyphicon-fullscreen:before {
  content: "\e140";
}
.glyphicon-dashboard:before {
  content: "\e141";
}
.glyphicon-paperclip:before {
  content: "\e142";
}
.glyphicon-heart-empty:before {
  content: "\e143";
}
.glyphicon-link:before {
  content: "\e144";
}
.glyphicon-phone:before {
  content: "\e145";
}
.glyphicon-pushpin:before {
  content: "\e146";
}
.glyphicon-usd:before {
  content: "\e148";
}
.glyphicon-gbp:before {
  content: "\e149";
}
.glyphicon-sort:before {
  content: "\e150";
}
.glyphicon-sort-by-alphabet:before {
  content: "\e151";
}
.glyphicon-sort-by-alphabet-alt:before {
  content: "\e152";
}
.glyphicon-sort-by-order:before {
  content: "\e153";
}
.glyphicon-sort-by-order-alt:before {
  content: "\e154";
}
.glyphicon-sort-by-attributes:before {
  content: "\e155";
}
.glyphicon-sort-by-attributes-alt:before {
  content: "\e156";
}
.glyphicon-unchecked:before {
  content: "\e157";
}
.glyphicon-expand:before {
  content: "\e158";
}
.glyphicon-collapse-down:before {
  content: "\e159";
}
.glyphicon-collapse-up:before {
  content: "\e160";
}
.glyphicon-log-in:before {
  content: "\e161";
}
.glyphicon-flash:before {
  content: "\e162";
}
.glyphicon-log-out:before {
  content: "\e163";
}
.glyphicon-new-window:before {
  content: "\e164";
}
.glyphicon-record:before {
  content: "\e165";
}
.glyphicon-save:before {
  content: "\e166";
}
.glyphicon-open:before {
  content: "\e167";
}
.glyphicon-saved:before {
  content: "\e168";
}
.glyphicon-import:before {
  content: "\e169";
}
.glyphicon-export:before {
  content: "\e170";
}
.glyphicon-send:before {
  content: "\e171";
}
.glyphicon-floppy-disk:before {
  content: "\e172";
}
.glyphicon-floppy-saved:before {
  content: "\e173";
}
.glyphicon-floppy-remove:before {
  content: "\e174";
}
.glyphicon-floppy-save:before {
  content: "\e175";
}
.glyphicon-floppy-open:before {
  content: "\e176";
}
.glyphicon-credit-card:before {
  content: "\e177";
}
.glyphicon-transfer:before {
  content: "\e178";
}
.glyphicon-cutlery:before {
  content: "\e179";
}
.glyphicon-header:before {
  content: "\e180";
}
.glyphicon-compressed:before {
  content: "\e181";
}
.glyphicon-earphone:before {
  content: "\e182";
}
.glyphicon-phone-alt:before {
  content: "\e183";
}
.glyphicon-tower:before {
  content: "\e184";
}
.glyphicon-stats:before {
  content: "\e185";
}
.glyphicon-sd-video:before {
  content: "\e186";
}
.glyphicon-hd-video:before {
  content: "\e187";
}
.glyphicon-subtitles:before {
  content: "\e188";
}
.glyphicon-sound-stereo:before {
  content: "\e189";
}
.glyphicon-sound-dolby:before {
  content: "\e190";
}
.glyphicon-sound-5-1:before {
  content: "\e191";
}
.glyphicon-sound-6-1:before {
  content: "\e192";
}
.glyphicon-sound-7-1:before {
  content: "\e193";
}
.glyphicon-copyright-mark:before {
  content: "\e194";
}
.glyphicon-registration-mark:before {
  content: "\e195";
}
.glyphicon-cloud-download:before {
  content: "\e197";
}
.glyphicon-cloud-upload:before {
  content: "\e198";
}
.glyphicon-tree-conifer:before {
  content: "\e199";
}
.glyphicon-tree-deciduous:before {
  content: "\e200";
}
.glyphicon-cd:before {
  content: "\e201";
}
.glyphicon-save-file:before {
  content: "\e202";
}
.glyphicon-open-file:before {
  content: "\e203";
}
.glyphicon-level-up:before {
  content: "\e204";
}
.glyphicon-copy:before {
  content: "\e205";
}
.glyphicon-paste:before {
  content: "\e206";
}
.glyphicon-alert:before {
  content: "\e209";
}
.glyphicon-equalizer:before {
  content: "\e210";
}
.glyphicon-king:before {
  content: "\e211";
}
.glyphicon-queen:before {
  content: "\e212";
}
.glyphicon-pawn:before {
  content: "\e213";
}
.glyphicon-bishop:before {
  content: "\e214";
}
.glyphicon-knight:before {
  content: "\e215";
}
.glyphicon-baby-formula:before {
  content: "\e216";
}
.glyphicon-tent:before {
  content: "\26fa";
}
.glyphicon-blackboard:before {
  content: "\e218";
}
.glyphicon-bed:before {
  content: "\e219";
}
.glyphicon-apple:before {
  content: "\f8ff";
}
.glyphicon-erase:before {
  content: "\e221";
}
.glyphicon-hourglass:before {
  content: "\231b";
}
.glyphicon-lamp:before {
  content: "\e223";
}
.glyphicon-duplicate:before {
  content: "\e224";
}
.glyphicon-piggy-bank:before {
  content: "\e225";
}
.glyphicon-scissors:before {
  content: "\e226";
}
.glyphicon-bitcoin:before {
  content: "\e227";
}
.glyphicon-btc:before {
  content: "\e227";
}
.glyphicon-xbt:before {
  content: "\e227";
}
.glyphicon-yen:before {
  content: "\00a5";
}
.glyphicon-jpy:before {
  content: "\00a5";
}
.glyphicon-ruble:before {
  content: "\20bd";
}
.glyphicon-rub:before {
  content: "\20bd";
}
.glyphicon-scale:before {
  content: "\e230";
}
.glyphicon-ice-lolly:before {
  content: "\e231";
}
.glyphicon-ice-lolly-tasted:before {
  content: "\e232";
}
.glyphicon-education:before {
  content: "\e233";
}
.glyphicon-option-horizontal:before {
  content: "\e234";
}
.glyphicon-option-vertical:before {
  content: "\e235";
}
.glyphicon-menu-hamburger:before {
  content: "\e236";
}
.glyphicon-modal-window:before {
  content: "\e237";
}
.glyphicon-oil:before {
  content: "\e238";
}
.glyphicon-grain:before {
  content: "\e239";
}
.glyphicon-sunglasses:before {
  content: "\e240";
}
.glyphicon-text-size:before {
  content: "\e241";
}
.glyphicon-text-color:before {
  content: "\e242";
}
.glyphicon-text-background:before {
  content: "\e243";
}
.glyphicon-object-align-top:before {
  content: "\e244";
}
.glyphicon-object-align-bottom:before {
  content: "\e245";
}
.glyphicon-object-align-horizontal:before {
  content: "\e246";
}
.glyphicon-object-align-left:before {
  content: "\e247";
}
.glyphicon-object-align-vertical:before {
  content: "\e248";
}
.glyphicon-object-align-right:before {
  content: "\e249";
}
.glyphicon-triangle-right:before {
  content: "\e250";
}
.glyphicon-triangle-left:before {
  content: "\e251";
}
.glyphicon-triangle-bottom:before {
  content: "\e252";
}
.glyphicon-triangle-top:before {
  content: "\e253";
}
.glyphicon-console:before {
  content: "\e254";
}
.glyphicon-superscript:before {
  content: "\e255";
}
.glyphicon-subscript:before {
  content: "\e256";
}
.glyphicon-menu-left:before {
  content: "\e257";
}
.glyphicon-menu-right:before {
  content: "\e258";
}
.glyphicon-menu-down:before {
  content: "\e259";
}
.glyphicon-menu-up:before {
  content: "\e260";
}
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
*:before,
*:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
html {
  font-size: 10px;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  line-height: 1.42857143;
  color: #000;
  background-color: #fff;
}
input,
button,
select,
textarea {
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
}
a {
  color: #337ab7;
  text-decoration: none;
}
a:hover,
a:focus {
  color: #23527c;
  text-decoration: underline;
}
a:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
figure {
  margin: 0;
}
img {
  vertical-align: middle;
}
.img-responsive,
.thumbnail > img,
.thumbnail a > img,
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  display: block;
  max-width: 100%;
  height: auto;
}
.img-rounded {
  border-radius: 3px;
}
.img-thumbnail {
  padding: 4px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: all 0.2s ease-in-out;
  -o-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
  display: inline-block;
  max-width: 100%;
  height: auto;
}
.img-circle {
  border-radius: 50%;
}
hr {
  margin-top: 18px;
  margin-bottom: 18px;
  border: 0;
  border-top: 1px solid #eeeeee;
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
[role="button"] {
  cursor: pointer;
}
h1,
h2,
h3,
h4,
h5,
h6,
.h1,
.h2,
.h3,
.h4,
.h5,
.h6 {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  color: inherit;
}
h1 small,
h2 small,
h3 small,
h4 small,
h5 small,
h6 small,
.h1 small,
.h2 small,
.h3 small,
.h4 small,
.h5 small,
.h6 small,
h1 .small,
h2 .small,
h3 .small,
h4 .small,
h5 .small,
h6 .small,
.h1 .small,
.h2 .small,
.h3 .small,
.h4 .small,
.h5 .small,
.h6 .small {
  font-weight: normal;
  line-height: 1;
  color: #777777;
}
h1,
.h1,
h2,
.h2,
h3,
.h3 {
  margin-top: 18px;
  margin-bottom: 9px;
}
h1 small,
.h1 small,
h2 small,
.h2 small,
h3 small,
.h3 small,
h1 .small,
.h1 .small,
h2 .small,
.h2 .small,
h3 .small,
.h3 .small {
  font-size: 65%;
}
h4,
.h4,
h5,
.h5,
h6,
.h6 {
  margin-top: 9px;
  margin-bottom: 9px;
}
h4 small,
.h4 small,
h5 small,
.h5 small,
h6 small,
.h6 small,
h4 .small,
.h4 .small,
h5 .small,
.h5 .small,
h6 .small,
.h6 .small {
  font-size: 75%;
}
h1,
.h1 {
  font-size: 33px;
}
h2,
.h2 {
  font-size: 27px;
}
h3,
.h3 {
  font-size: 23px;
}
h4,
.h4 {
  font-size: 17px;
}
h5,
.h5 {
  font-size: 13px;
}
h6,
.h6 {
  font-size: 12px;
}
p {
  margin: 0 0 9px;
}
.lead {
  margin-bottom: 18px;
  font-size: 14px;
  font-weight: 300;
  line-height: 1.4;
}
@media (min-width: 768px) {
  .lead {
    font-size: 19.5px;
  }
}
small,
.small {
  font-size: 92%;
}
mark,
.mark {
  background-color: #fcf8e3;
  padding: .2em;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}
.text-center {
  text-align: center;
}
.text-justify {
  text-align: justify;
}
.text-nowrap {
  white-space: nowrap;
}
.text-lowercase {
  text-transform: lowercase;
}
.text-uppercase {
  text-transform: uppercase;
}
.text-capitalize {
  text-transform: capitalize;
}
.text-muted {
  color: #777777;
}
.text-primary {
  color: #337ab7;
}
a.text-primary:hover,
a.text-primary:focus {
  color: #286090;
}
.text-success {
  color: #3c763d;
}
a.text-success:hover,
a.text-success:focus {
  color: #2b542c;
}
.text-info {
  color: #31708f;
}
a.text-info:hover,
a.text-info:focus {
  color: #245269;
}
.text-warning {
  color: #8a6d3b;
}
a.text-warning:hover,
a.text-warning:focus {
  color: #66512c;
}
.text-danger {
  color: #a94442;
}
a.text-danger:hover,
a.text-danger:focus {
  color: #843534;
}
.bg-primary {
  color: #fff;
  background-color: #337ab7;
}
a.bg-primary:hover,
a.bg-primary:focus {
  background-color: #286090;
}
.bg-success {
  background-color: #dff0d8;
}
a.bg-success:hover,
a.bg-success:focus {
  background-color: #c1e2b3;
}
.bg-info {
  background-color: #d9edf7;
}
a.bg-info:hover,
a.bg-info:focus {
  background-color: #afd9ee;
}
.bg-warning {
  background-color: #fcf8e3;
}
a.bg-warning:hover,
a.bg-warning:focus {
  background-color: #f7ecb5;
}
.bg-danger {
  background-color: #f2dede;
}
a.bg-danger:hover,
a.bg-danger:focus {
  background-color: #e4b9b9;
}
.page-header {
  padding-bottom: 8px;
  margin: 36px 0 18px;
  border-bottom: 1px solid #eeeeee;
}
ul,
ol {
  margin-top: 0;
  margin-bottom: 9px;
}
ul ul,
ol ul,
ul ol,
ol ol {
  margin-bottom: 0;
}
.list-unstyled {
  padding-left: 0;
  list-style: none;
}
.list-inline {
  padding-left: 0;
  list-style: none;
  margin-left: -5px;
}
.list-inline > li {
  display: inline-block;
  padding-left: 5px;
  padding-right: 5px;
}
dl {
  margin-top: 0;
  margin-bottom: 18px;
}
dt,
dd {
  line-height: 1.42857143;
}
dt {
  font-weight: bold;
}
dd {
  margin-left: 0;
}
@media (min-width: 541px) {
  .dl-horizontal dt {
    float: left;
    width: 160px;
    clear: left;
    text-align: right;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .dl-horizontal dd {
    margin-left: 180px;
  }
}
abbr[title],
abbr[data-original-title] {
  cursor: help;
  border-bottom: 1px dotted #777777;
}
.initialism {
  font-size: 90%;
  text-transform: uppercase;
}
blockquote {
  padding: 9px 18px;
  margin: 0 0 18px;
  font-size: inherit;
  border-left: 5px solid #eeeeee;
}
blockquote p:last-child,
blockquote ul:last-child,
blockquote ol:last-child {
  margin-bottom: 0;
}
blockquote footer,
blockquote small,
blockquote .small {
  display: block;
  font-size: 80%;
  line-height: 1.42857143;
  color: #777777;
}
blockquote footer:before,
blockquote small:before,
blockquote .small:before {
  content: '\2014 \00A0';
}
.blockquote-reverse,
blockquote.pull-right {
  padding-right: 15px;
  padding-left: 0;
  border-right: 5px solid #eeeeee;
  border-left: 0;
  text-align: right;
}
.blockquote-reverse footer:before,
blockquote.pull-right footer:before,
.blockquote-reverse small:before,
blockquote.pull-right small:before,
.blockquote-reverse .small:before,
blockquote.pull-right .small:before {
  content: '';
}
.blockquote-reverse footer:after,
blockquote.pull-right footer:after,
.blockquote-reverse small:after,
blockquote.pull-right small:after,
.blockquote-reverse .small:after,
blockquote.pull-right .small:after {
  content: '\00A0 \2014';
}
address {
  margin-bottom: 18px;
  font-style: normal;
  line-height: 1.42857143;
}
code,
kbd,
pre,
samp {
  font-family: monospace;
}
code {
  padding: 2px 4px;
  font-size: 90%;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 2px;
}
kbd {
  padding: 2px 4px;
  font-size: 90%;
  color: #888;
  background-color: transparent;
  border-radius: 1px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
}
kbd kbd {
  padding: 0;
  font-size: 100%;
  font-weight: bold;
  box-shadow: none;
}
pre {
  display: block;
  padding: 8.5px;
  margin: 0 0 9px;
  font-size: 12px;
  line-height: 1.42857143;
  word-break: break-all;
  word-wrap: break-word;
  color: #333333;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 2px;
}
pre code {
  padding: 0;
  font-size: inherit;
  color: inherit;
  white-space: pre-wrap;
  background-color: transparent;
  border-radius: 0;
}
.pre-scrollable {
  max-height: 340px;
  overflow-y: scroll;
}
.container {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
@media (min-width: 768px) {
  .container {
    width: 768px;
  }
}
@media (min-width: 992px) {
  .container {
    width: 940px;
  }
}
@media (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}
.container-fluid {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
.row {
  margin-left: 0px;
  margin-right: 0px;
}
.col-xs-1, .col-sm-1, .col-md-1, .col-lg-1, .col-xs-2, .col-sm-2, .col-md-2, .col-lg-2, .col-xs-3, .col-sm-3, .col-md-3, .col-lg-3, .col-xs-4, .col-sm-4, .col-md-4, .col-lg-4, .col-xs-5, .col-sm-5, .col-md-5, .col-lg-5, .col-xs-6, .col-sm-6, .col-md-6, .col-lg-6, .col-xs-7, .col-sm-7, .col-md-7, .col-lg-7, .col-xs-8, .col-sm-8, .col-md-8, .col-lg-8, .col-xs-9, .col-sm-9, .col-md-9, .col-lg-9, .col-xs-10, .col-sm-10, .col-md-10, .col-lg-10, .col-xs-11, .col-sm-11, .col-md-11, .col-lg-11, .col-xs-12, .col-sm-12, .col-md-12, .col-lg-12 {
  position: relative;
  min-height: 1px;
  padding-left: 0px;
  padding-right: 0px;
}
.col-xs-1, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9, .col-xs-10, .col-xs-11, .col-xs-12 {
  float: left;
}
.col-xs-12 {
  width: 100%;
}
.col-xs-11 {
  width: 91.66666667%;
}
.col-xs-10 {
  width: 83.33333333%;
}
.col-xs-9 {
  width: 75%;
}
.col-xs-8 {
  width: 66.66666667%;
}
.col-xs-7 {
  width: 58.33333333%;
}
.col-xs-6 {
  width: 50%;
}
.col-xs-5 {
  width: 41.66666667%;
}
.col-xs-4 {
  width: 33.33333333%;
}
.col-xs-3 {
  width: 25%;
}
.col-xs-2 {
  width: 16.66666667%;
}
.col-xs-1 {
  width: 8.33333333%;
}
.col-xs-pull-12 {
  right: 100%;
}
.col-xs-pull-11 {
  right: 91.66666667%;
}
.col-xs-pull-10 {
  right: 83.33333333%;
}
.col-xs-pull-9 {
  right: 75%;
}
.col-xs-pull-8 {
  right: 66.66666667%;
}
.col-xs-pull-7 {
  right: 58.33333333%;
}
.col-xs-pull-6 {
  right: 50%;
}
.col-xs-pull-5 {
  right: 41.66666667%;
}
.col-xs-pull-4 {
  right: 33.33333333%;
}
.col-xs-pull-3 {
  right: 25%;
}
.col-xs-pull-2 {
  right: 16.66666667%;
}
.col-xs-pull-1 {
  right: 8.33333333%;
}
.col-xs-pull-0 {
  right: auto;
}
.col-xs-push-12 {
  left: 100%;
}
.col-xs-push-11 {
  left: 91.66666667%;
}
.col-xs-push-10 {
  left: 83.33333333%;
}
.col-xs-push-9 {
  left: 75%;
}
.col-xs-push-8 {
  left: 66.66666667%;
}
.col-xs-push-7 {
  left: 58.33333333%;
}
.col-xs-push-6 {
  left: 50%;
}
.col-xs-push-5 {
  left: 41.66666667%;
}
.col-xs-push-4 {
  left: 33.33333333%;
}
.col-xs-push-3 {
  left: 25%;
}
.col-xs-push-2 {
  left: 16.66666667%;
}
.col-xs-push-1 {
  left: 8.33333333%;
}
.col-xs-push-0 {
  left: auto;
}
.col-xs-offset-12 {
  margin-left: 100%;
}
.col-xs-offset-11 {
  margin-left: 91.66666667%;
}
.col-xs-offset-10 {
  margin-left: 83.33333333%;
}
.col-xs-offset-9 {
  margin-left: 75%;
}
.col-xs-offset-8 {
  margin-left: 66.66666667%;
}
.col-xs-offset-7 {
  margin-left: 58.33333333%;
}
.col-xs-offset-6 {
  margin-left: 50%;
}
.col-xs-offset-5 {
  margin-left: 41.66666667%;
}
.col-xs-offset-4 {
  margin-left: 33.33333333%;
}
.col-xs-offset-3 {
  margin-left: 25%;
}
.col-xs-offset-2 {
  margin-left: 16.66666667%;
}
.col-xs-offset-1 {
  margin-left: 8.33333333%;
}
.col-xs-offset-0 {
  margin-left: 0%;
}
@media (min-width: 768px) {
  .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
    float: left;
  }
  .col-sm-12 {
    width: 100%;
  }
  .col-sm-11 {
    width: 91.66666667%;
  }
  .col-sm-10 {
    width: 83.33333333%;
  }
  .col-sm-9 {
    width: 75%;
  }
  .col-sm-8 {
    width: 66.66666667%;
  }
  .col-sm-7 {
    width: 58.33333333%;
  }
  .col-sm-6 {
    width: 50%;
  }
  .col-sm-5 {
    width: 41.66666667%;
  }
  .col-sm-4 {
    width: 33.33333333%;
  }
  .col-sm-3 {
    width: 25%;
  }
  .col-sm-2 {
    width: 16.66666667%;
  }
  .col-sm-1 {
    width: 8.33333333%;
  }
  .col-sm-pull-12 {
    right: 100%;
  }
  .col-sm-pull-11 {
    right: 91.66666667%;
  }
  .col-sm-pull-10 {
    right: 83.33333333%;
  }
  .col-sm-pull-9 {
    right: 75%;
  }
  .col-sm-pull-8 {
    right: 66.66666667%;
  }
  .col-sm-pull-7 {
    right: 58.33333333%;
  }
  .col-sm-pull-6 {
    right: 50%;
  }
  .col-sm-pull-5 {
    right: 41.66666667%;
  }
  .col-sm-pull-4 {
    right: 33.33333333%;
  }
  .col-sm-pull-3 {
    right: 25%;
  }
  .col-sm-pull-2 {
    right: 16.66666667%;
  }
  .col-sm-pull-1 {
    right: 8.33333333%;
  }
  .col-sm-pull-0 {
    right: auto;
  }
  .col-sm-push-12 {
    left: 100%;
  }
  .col-sm-push-11 {
    left: 91.66666667%;
  }
  .col-sm-push-10 {
    left: 83.33333333%;
  }
  .col-sm-push-9 {
    left: 75%;
  }
  .col-sm-push-8 {
    left: 66.66666667%;
  }
  .col-sm-push-7 {
    left: 58.33333333%;
  }
  .col-sm-push-6 {
    left: 50%;
  }
  .col-sm-push-5 {
    left: 41.66666667%;
  }
  .col-sm-push-4 {
    left: 33.33333333%;
  }
  .col-sm-push-3 {
    left: 25%;
  }
  .col-sm-push-2 {
    left: 16.66666667%;
  }
  .col-sm-push-1 {
    left: 8.33333333%;
  }
  .col-sm-push-0 {
    left: auto;
  }
  .col-sm-offset-12 {
    margin-left: 100%;
  }
  .col-sm-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-sm-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-sm-offset-9 {
    margin-left: 75%;
  }
  .col-sm-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-sm-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-sm-offset-6 {
    margin-left: 50%;
  }
  .col-sm-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-sm-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-sm-offset-3 {
    margin-left: 25%;
  }
  .col-sm-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-sm-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-sm-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 992px) {
  .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
    float: left;
  }
  .col-md-12 {
    width: 100%;
  }
  .col-md-11 {
    width: 91.66666667%;
  }
  .col-md-10 {
    width: 83.33333333%;
  }
  .col-md-9 {
    width: 75%;
  }
  .col-md-8 {
    width: 66.66666667%;
  }
  .col-md-7 {
    width: 58.33333333%;
  }
  .col-md-6 {
    width: 50%;
  }
  .col-md-5 {
    width: 41.66666667%;
  }
  .col-md-4 {
    width: 33.33333333%;
  }
  .col-md-3 {
    width: 25%;
  }
  .col-md-2 {
    width: 16.66666667%;
  }
  .col-md-1 {
    width: 8.33333333%;
  }
  .col-md-pull-12 {
    right: 100%;
  }
  .col-md-pull-11 {
    right: 91.66666667%;
  }
  .col-md-pull-10 {
    right: 83.33333333%;
  }
  .col-md-pull-9 {
    right: 75%;
  }
  .col-md-pull-8 {
    right: 66.66666667%;
  }
  .col-md-pull-7 {
    right: 58.33333333%;
  }
  .col-md-pull-6 {
    right: 50%;
  }
  .col-md-pull-5 {
    right: 41.66666667%;
  }
  .col-md-pull-4 {
    right: 33.33333333%;
  }
  .col-md-pull-3 {
    right: 25%;
  }
  .col-md-pull-2 {
    right: 16.66666667%;
  }
  .col-md-pull-1 {
    right: 8.33333333%;
  }
  .col-md-pull-0 {
    right: auto;
  }
  .col-md-push-12 {
    left: 100%;
  }
  .col-md-push-11 {
    left: 91.66666667%;
  }
  .col-md-push-10 {
    left: 83.33333333%;
  }
  .col-md-push-9 {
    left: 75%;
  }
  .col-md-push-8 {
    left: 66.66666667%;
  }
  .col-md-push-7 {
    left: 58.33333333%;
  }
  .col-md-push-6 {
    left: 50%;
  }
  .col-md-push-5 {
    left: 41.66666667%;
  }
  .col-md-push-4 {
    left: 33.33333333%;
  }
  .col-md-push-3 {
    left: 25%;
  }
  .col-md-push-2 {
    left: 16.66666667%;
  }
  .col-md-push-1 {
    left: 8.33333333%;
  }
  .col-md-push-0 {
    left: auto;
  }
  .col-md-offset-12 {
    margin-left: 100%;
  }
  .col-md-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-md-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-md-offset-9 {
    margin-left: 75%;
  }
  .col-md-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-md-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-md-offset-6 {
    margin-left: 50%;
  }
  .col-md-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-md-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-md-offset-3 {
    margin-left: 25%;
  }
  .col-md-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-md-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-md-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 1200px) {
  .col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12 {
    float: left;
  }
  .col-lg-12 {
    width: 100%;
  }
  .col-lg-11 {
    width: 91.66666667%;
  }
  .col-lg-10 {
    width: 83.33333333%;
  }
  .col-lg-9 {
    width: 75%;
  }
  .col-lg-8 {
    width: 66.66666667%;
  }
  .col-lg-7 {
    width: 58.33333333%;
  }
  .col-lg-6 {
    width: 50%;
  }
  .col-lg-5 {
    width: 41.66666667%;
  }
  .col-lg-4 {
    width: 33.33333333%;
  }
  .col-lg-3 {
    width: 25%;
  }
  .col-lg-2 {
    width: 16.66666667%;
  }
  .col-lg-1 {
    width: 8.33333333%;
  }
  .col-lg-pull-12 {
    right: 100%;
  }
  .col-lg-pull-11 {
    right: 91.66666667%;
  }
  .col-lg-pull-10 {
    right: 83.33333333%;
  }
  .col-lg-pull-9 {
    right: 75%;
  }
  .col-lg-pull-8 {
    right: 66.66666667%;
  }
  .col-lg-pull-7 {
    right: 58.33333333%;
  }
  .col-lg-pull-6 {
    right: 50%;
  }
  .col-lg-pull-5 {
    right: 41.66666667%;
  }
  .col-lg-pull-4 {
    right: 33.33333333%;
  }
  .col-lg-pull-3 {
    right: 25%;
  }
  .col-lg-pull-2 {
    right: 16.66666667%;
  }
  .col-lg-pull-1 {
    right: 8.33333333%;
  }
  .col-lg-pull-0 {
    right: auto;
  }
  .col-lg-push-12 {
    left: 100%;
  }
  .col-lg-push-11 {
    left: 91.66666667%;
  }
  .col-lg-push-10 {
    left: 83.33333333%;
  }
  .col-lg-push-9 {
    left: 75%;
  }
  .col-lg-push-8 {
    left: 66.66666667%;
  }
  .col-lg-push-7 {
    left: 58.33333333%;
  }
  .col-lg-push-6 {
    left: 50%;
  }
  .col-lg-push-5 {
    left: 41.66666667%;
  }
  .col-lg-push-4 {
    left: 33.33333333%;
  }
  .col-lg-push-3 {
    left: 25%;
  }
  .col-lg-push-2 {
    left: 16.66666667%;
  }
  .col-lg-push-1 {
    left: 8.33333333%;
  }
  .col-lg-push-0 {
    left: auto;
  }
  .col-lg-offset-12 {
    margin-left: 100%;
  }
  .col-lg-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-lg-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-lg-offset-9 {
    margin-left: 75%;
  }
  .col-lg-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-lg-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-lg-offset-6 {
    margin-left: 50%;
  }
  .col-lg-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-lg-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-lg-offset-3 {
    margin-left: 25%;
  }
  .col-lg-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-lg-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-lg-offset-0 {
    margin-left: 0%;
  }
}
table {
  background-color: transparent;
}
caption {
  padding-top: 8px;
  padding-bottom: 8px;
  color: #777777;
  text-align: left;
}
th {
  text-align: left;
}
.table {
  width: 100%;
  max-width: 100%;
  margin-bottom: 18px;
}
.table > thead > tr > th,
.table > tbody > tr > th,
.table > tfoot > tr > th,
.table > thead > tr > td,
.table > tbody > tr > td,
.table > tfoot > tr > td {
  padding: 8px;
  line-height: 1.42857143;
  vertical-align: top;
  border-top: 1px solid #ddd;
}
.table > thead > tr > th {
  vertical-align: bottom;
  border-bottom: 2px solid #ddd;
}
.table > caption + thead > tr:first-child > th,
.table > colgroup + thead > tr:first-child > th,
.table > thead:first-child > tr:first-child > th,
.table > caption + thead > tr:first-child > td,
.table > colgroup + thead > tr:first-child > td,
.table > thead:first-child > tr:first-child > td {
  border-top: 0;
}
.table > tbody + tbody {
  border-top: 2px solid #ddd;
}
.table .table {
  background-color: #fff;
}
.table-condensed > thead > tr > th,
.table-condensed > tbody > tr > th,
.table-condensed > tfoot > tr > th,
.table-condensed > thead > tr > td,
.table-condensed > tbody > tr > td,
.table-condensed > tfoot > tr > td {
  padding: 5px;
}
.table-bordered {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > tbody > tr > th,
.table-bordered > tfoot > tr > th,
.table-bordered > thead > tr > td,
.table-bordered > tbody > tr > td,
.table-bordered > tfoot > tr > td {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > thead > tr > td {
  border-bottom-width: 2px;
}
.table-striped > tbody > tr:nth-of-type(odd) {
  background-color: #f9f9f9;
}
.table-hover > tbody > tr:hover {
  background-color: #f5f5f5;
}
table col[class*="col-"] {
  position: static;
  float: none;
  display: table-column;
}
table td[class*="col-"],
table th[class*="col-"] {
  position: static;
  float: none;
  display: table-cell;
}
.table > thead > tr > td.active,
.table > tbody > tr > td.active,
.table > tfoot > tr > td.active,
.table > thead > tr > th.active,
.table > tbody > tr > th.active,
.table > tfoot > tr > th.active,
.table > thead > tr.active > td,
.table > tbody > tr.active > td,
.table > tfoot > tr.active > td,
.table > thead > tr.active > th,
.table > tbody > tr.active > th,
.table > tfoot > tr.active > th {
  background-color: #f5f5f5;
}
.table-hover > tbody > tr > td.active:hover,
.table-hover > tbody > tr > th.active:hover,
.table-hover > tbody > tr.active:hover > td,
.table-hover > tbody > tr:hover > .active,
.table-hover > tbody > tr.active:hover > th {
  background-color: #e8e8e8;
}
.table > thead > tr > td.success,
.table > tbody > tr > td.success,
.table > tfoot > tr > td.success,
.table > thead > tr > th.success,
.table > tbody > tr > th.success,
.table > tfoot > tr > th.success,
.table > thead > tr.success > td,
.table > tbody > tr.success > td,
.table > tfoot > tr.success > td,
.table > thead > tr.success > th,
.table > tbody > tr.success > th,
.table > tfoot > tr.success > th {
  background-color: #dff0d8;
}
.table-hover > tbody > tr > td.success:hover,
.table-hover > tbody > tr > th.success:hover,
.table-hover > tbody > tr.success:hover > td,
.table-hover > tbody > tr:hover > .success,
.table-hover > tbody > tr.success:hover > th {
  background-color: #d0e9c6;
}
.table > thead > tr > td.info,
.table > tbody > tr > td.info,
.table > tfoot > tr > td.info,
.table > thead > tr > th.info,
.table > tbody > tr > th.info,
.table > tfoot > tr > th.info,
.table > thead > tr.info > td,
.table > tbody > tr.info > td,
.table > tfoot > tr.info > td,
.table > thead > tr.info > th,
.table > tbody > tr.info > th,
.table > tfoot > tr.info > th {
  background-color: #d9edf7;
}
.table-hover > tbody > tr > td.info:hover,
.table-hover > tbody > tr > th.info:hover,
.table-hover > tbody > tr.info:hover > td,
.table-hover > tbody > tr:hover > .info,
.table-hover > tbody > tr.info:hover > th {
  background-color: #c4e3f3;
}
.table > thead > tr > td.warning,
.table > tbody > tr > td.warning,
.table > tfoot > tr > td.warning,
.table > thead > tr > th.warning,
.table > tbody > tr > th.warning,
.table > tfoot > tr > th.warning,
.table > thead > tr.warning > td,
.table > tbody > tr.warning > td,
.table > tfoot > tr.warning > td,
.table > thead > tr.warning > th,
.table > tbody > tr.warning > th,
.table > tfoot > tr.warning > th {
  background-color: #fcf8e3;
}
.table-hover > tbody > tr > td.warning:hover,
.table-hover > tbody > tr > th.warning:hover,
.table-hover > tbody > tr.warning:hover > td,
.table-hover > tbody > tr:hover > .warning,
.table-hover > tbody > tr.warning:hover > th {
  background-color: #faf2cc;
}
.table > thead > tr > td.danger,
.table > tbody > tr > td.danger,
.table > tfoot > tr > td.danger,
.table > thead > tr > th.danger,
.table > tbody > tr > th.danger,
.table > tfoot > tr > th.danger,
.table > thead > tr.danger > td,
.table > tbody > tr.danger > td,
.table > tfoot > tr.danger > td,
.table > thead > tr.danger > th,
.table > tbody > tr.danger > th,
.table > tfoot > tr.danger > th {
  background-color: #f2dede;
}
.table-hover > tbody > tr > td.danger:hover,
.table-hover > tbody > tr > th.danger:hover,
.table-hover > tbody > tr.danger:hover > td,
.table-hover > tbody > tr:hover > .danger,
.table-hover > tbody > tr.danger:hover > th {
  background-color: #ebcccc;
}
.table-responsive {
  overflow-x: auto;
  min-height: 0.01%;
}
@media screen and (max-width: 767px) {
  .table-responsive {
    width: 100%;
    margin-bottom: 13.5px;
    overflow-y: hidden;
    -ms-overflow-style: -ms-autohiding-scrollbar;
    border: 1px solid #ddd;
  }
  .table-responsive > .table {
    margin-bottom: 0;
  }
  .table-responsive > .table > thead > tr > th,
  .table-responsive > .table > tbody > tr > th,
  .table-responsive > .table > tfoot > tr > th,
  .table-responsive > .table > thead > tr > td,
  .table-responsive > .table > tbody > tr > td,
  .table-responsive > .table > tfoot > tr > td {
    white-space: nowrap;
  }
  .table-responsive > .table-bordered {
    border: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:first-child,
  .table-responsive > .table-bordered > tbody > tr > th:first-child,
  .table-responsive > .table-bordered > tfoot > tr > th:first-child,
  .table-responsive > .table-bordered > thead > tr > td:first-child,
  .table-responsive > .table-bordered > tbody > tr > td:first-child,
  .table-responsive > .table-bordered > tfoot > tr > td:first-child {
    border-left: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:last-child,
  .table-responsive > .table-bordered > tbody > tr > th:last-child,
  .table-responsive > .table-bordered > tfoot > tr > th:last-child,
  .table-responsive > .table-bordered > thead > tr > td:last-child,
  .table-responsive > .table-bordered > tbody > tr > td:last-child,
  .table-responsive > .table-bordered > tfoot > tr > td:last-child {
    border-right: 0;
  }
  .table-responsive > .table-bordered > tbody > tr:last-child > th,
  .table-responsive > .table-bordered > tfoot > tr:last-child > th,
  .table-responsive > .table-bordered > tbody > tr:last-child > td,
  .table-responsive > .table-bordered > tfoot > tr:last-child > td {
    border-bottom: 0;
  }
}
fieldset {
  padding: 0;
  margin: 0;
  border: 0;
  min-width: 0;
}
legend {
  display: block;
  width: 100%;
  padding: 0;
  margin-bottom: 18px;
  font-size: 19.5px;
  line-height: inherit;
  color: #333333;
  border: 0;
  border-bottom: 1px solid #e5e5e5;
}
label {
  display: inline-block;
  max-width: 100%;
  margin-bottom: 5px;
  font-weight: bold;
}
input[type="search"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
input[type="radio"],
input[type="checkbox"] {
  margin: 4px 0 0;
  margin-top: 1px \9;
  line-height: normal;
}
input[type="file"] {
  display: block;
}
input[type="range"] {
  display: block;
  width: 100%;
}
select[multiple],
select[size] {
  height: auto;
}
input[type="file"]:focus,
input[type="radio"]:focus,
input[type="checkbox"]:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
output {
  display: block;
  padding-top: 7px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
}
.form-control {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
}
.form-control:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.form-control::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.form-control:-ms-input-placeholder {
  color: #999;
}
.form-control::-webkit-input-placeholder {
  color: #999;
}
.form-control::-ms-expand {
  border: 0;
  background-color: transparent;
}
.form-control[disabled],
.form-control[readonly],
fieldset[disabled] .form-control {
  background-color: #eeeeee;
  opacity: 1;
}
.form-control[disabled],
fieldset[disabled] .form-control {
  cursor: not-allowed;
}
textarea.form-control {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: none;
}
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  input[type="date"].form-control,
  input[type="time"].form-control,
  input[type="datetime-local"].form-control,
  input[type="month"].form-control {
    line-height: 32px;
  }
  input[type="date"].input-sm,
  input[type="time"].input-sm,
  input[type="datetime-local"].input-sm,
  input[type="month"].input-sm,
  .input-group-sm input[type="date"],
  .input-group-sm input[type="time"],
  .input-group-sm input[type="datetime-local"],
  .input-group-sm input[type="month"] {
    line-height: 30px;
  }
  input[type="date"].input-lg,
  input[type="time"].input-lg,
  input[type="datetime-local"].input-lg,
  input[type="month"].input-lg,
  .input-group-lg input[type="date"],
  .input-group-lg input[type="time"],
  .input-group-lg input[type="datetime-local"],
  .input-group-lg input[type="month"] {
    line-height: 45px;
  }
}
.form-group {
  margin-bottom: 15px;
}
.radio,
.checkbox {
  position: relative;
  display: block;
  margin-top: 10px;
  margin-bottom: 10px;
}
.radio label,
.checkbox label {
  min-height: 18px;
  padding-left: 20px;
  margin-bottom: 0;
  font-weight: normal;
  cursor: pointer;
}
.radio input[type="radio"],
.radio-inline input[type="radio"],
.checkbox input[type="checkbox"],
.checkbox-inline input[type="checkbox"] {
  position: absolute;
  margin-left: -20px;
  margin-top: 4px \9;
}
.radio + .radio,
.checkbox + .checkbox {
  margin-top: -5px;
}
.radio-inline,
.checkbox-inline {
  position: relative;
  display: inline-block;
  padding-left: 20px;
  margin-bottom: 0;
  vertical-align: middle;
  font-weight: normal;
  cursor: pointer;
}
.radio-inline + .radio-inline,
.checkbox-inline + .checkbox-inline {
  margin-top: 0;
  margin-left: 10px;
}
input[type="radio"][disabled],
input[type="checkbox"][disabled],
input[type="radio"].disabled,
input[type="checkbox"].disabled,
fieldset[disabled] input[type="radio"],
fieldset[disabled] input[type="checkbox"] {
  cursor: not-allowed;
}
.radio-inline.disabled,
.checkbox-inline.disabled,
fieldset[disabled] .radio-inline,
fieldset[disabled] .checkbox-inline {
  cursor: not-allowed;
}
.radio.disabled label,
.checkbox.disabled label,
fieldset[disabled] .radio label,
fieldset[disabled] .checkbox label {
  cursor: not-allowed;
}
.form-control-static {
  padding-top: 7px;
  padding-bottom: 7px;
  margin-bottom: 0;
  min-height: 31px;
}
.form-control-static.input-lg,
.form-control-static.input-sm {
  padding-left: 0;
  padding-right: 0;
}
.input-sm {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-sm {
  height: 30px;
  line-height: 30px;
}
textarea.input-sm,
select[multiple].input-sm {
  height: auto;
}
.form-group-sm .form-control {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.form-group-sm select.form-control {
  height: 30px;
  line-height: 30px;
}
.form-group-sm textarea.form-control,
.form-group-sm select[multiple].form-control {
  height: auto;
}
.form-group-sm .form-control-static {
  height: 30px;
  min-height: 30px;
  padding: 6px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.input-lg {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-lg {
  height: 45px;
  line-height: 45px;
}
textarea.input-lg,
select[multiple].input-lg {
  height: auto;
}
.form-group-lg .form-control {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.form-group-lg select.form-control {
  height: 45px;
  line-height: 45px;
}
.form-group-lg textarea.form-control,
.form-group-lg select[multiple].form-control {
  height: auto;
}
.form-group-lg .form-control-static {
  height: 45px;
  min-height: 35px;
  padding: 11px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.has-feedback {
  position: relative;
}
.has-feedback .form-control {
  padding-right: 40px;
}
.form-control-feedback {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 2;
  display: block;
  width: 32px;
  height: 32px;
  line-height: 32px;
  text-align: center;
  pointer-events: none;
}
.input-lg + .form-control-feedback,
.input-group-lg + .form-control-feedback,
.form-group-lg .form-control + .form-control-feedback {
  width: 45px;
  height: 45px;
  line-height: 45px;
}
.input-sm + .form-control-feedback,
.input-group-sm + .form-control-feedback,
.form-group-sm .form-control + .form-control-feedback {
  width: 30px;
  height: 30px;
  line-height: 30px;
}
.has-success .help-block,
.has-success .control-label,
.has-success .radio,
.has-success .checkbox,
.has-success .radio-inline,
.has-success .checkbox-inline,
.has-success.radio label,
.has-success.checkbox label,
.has-success.radio-inline label,
.has-success.checkbox-inline label {
  color: #3c763d;
}
.has-success .form-control {
  border-color: #3c763d;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-success .form-control:focus {
  border-color: #2b542c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
}
.has-success .input-group-addon {
  color: #3c763d;
  border-color: #3c763d;
  background-color: #dff0d8;
}
.has-success .form-control-feedback {
  color: #3c763d;
}
.has-warning .help-block,
.has-warning .control-label,
.has-warning .radio,
.has-warning .checkbox,
.has-warning .radio-inline,
.has-warning .checkbox-inline,
.has-warning.radio label,
.has-warning.checkbox label,
.has-warning.radio-inline label,
.has-warning.checkbox-inline label {
  color: #8a6d3b;
}
.has-warning .form-control {
  border-color: #8a6d3b;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-warning .form-control:focus {
  border-color: #66512c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
}
.has-warning .input-group-addon {
  color: #8a6d3b;
  border-color: #8a6d3b;
  background-color: #fcf8e3;
}
.has-warning .form-control-feedback {
  color: #8a6d3b;
}
.has-error .help-block,
.has-error .control-label,
.has-error .radio,
.has-error .checkbox,
.has-error .radio-inline,
.has-error .checkbox-inline,
.has-error.radio label,
.has-error.checkbox label,
.has-error.radio-inline label,
.has-error.checkbox-inline label {
  color: #a94442;
}
.has-error .form-control {
  border-color: #a94442;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-error .form-control:focus {
  border-color: #843534;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
}
.has-error .input-group-addon {
  color: #a94442;
  border-color: #a94442;
  background-color: #f2dede;
}
.has-error .form-control-feedback {
  color: #a94442;
}
.has-feedback label ~ .form-control-feedback {
  top: 23px;
}
.has-feedback label.sr-only ~ .form-control-feedback {
  top: 0;
}
.help-block {
  display: block;
  margin-top: 5px;
  margin-bottom: 10px;
  color: #404040;
}
@media (min-width: 768px) {
  .form-inline .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .form-inline .form-control-static {
    display: inline-block;
  }
  .form-inline .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .form-inline .input-group .input-group-addon,
  .form-inline .input-group .input-group-btn,
  .form-inline .input-group .form-control {
    width: auto;
  }
  .form-inline .input-group > .form-control {
    width: 100%;
  }
  .form-inline .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio,
  .form-inline .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio label,
  .form-inline .checkbox label {
    padding-left: 0;
  }
  .form-inline .radio input[type="radio"],
  .form-inline .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .form-inline .has-feedback .form-control-feedback {
    top: 0;
  }
}
.form-horizontal .radio,
.form-horizontal .checkbox,
.form-horizontal .radio-inline,
.form-horizontal .checkbox-inline {
  margin-top: 0;
  margin-bottom: 0;
  padding-top: 7px;
}
.form-horizontal .radio,
.form-horizontal .checkbox {
  min-height: 25px;
}
.form-horizontal .form-group {
  margin-left: 0px;
  margin-right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .control-label {
    text-align: right;
    margin-bottom: 0;
    padding-top: 7px;
  }
}
.form-horizontal .has-feedback .form-control-feedback {
  right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .form-group-lg .control-label {
    padding-top: 11px;
    font-size: 17px;
  }
}
@media (min-width: 768px) {
  .form-horizontal .form-group-sm .control-label {
    padding-top: 6px;
    font-size: 12px;
  }
}
.btn {
  display: inline-block;
  margin-bottom: 0;
  font-weight: normal;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  white-space: nowrap;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  border-radius: 2px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.btn:focus,
.btn:active:focus,
.btn.active:focus,
.btn.focus,
.btn:active.focus,
.btn.active.focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
.btn:hover,
.btn:focus,
.btn.focus {
  color: #333;
  text-decoration: none;
}
.btn:active,
.btn.active {
  outline: 0;
  background-image: none;
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn.disabled,
.btn[disabled],
fieldset[disabled] .btn {
  cursor: not-allowed;
  opacity: 0.65;
  filter: alpha(opacity=65);
  -webkit-box-shadow: none;
  box-shadow: none;
}
a.btn.disabled,
fieldset[disabled] a.btn {
  pointer-events: none;
}
.btn-default {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.btn-default:focus,
.btn-default.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.btn-default:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active:hover,
.btn-default.active:hover,
.open > .dropdown-toggle.btn-default:hover,
.btn-default:active:focus,
.btn-default.active:focus,
.open > .dropdown-toggle.btn-default:focus,
.btn-default:active.focus,
.btn-default.active.focus,
.open > .dropdown-toggle.btn-default.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  background-image: none;
}
.btn-default.disabled:hover,
.btn-default[disabled]:hover,
fieldset[disabled] .btn-default:hover,
.btn-default.disabled:focus,
.btn-default[disabled]:focus,
fieldset[disabled] .btn-default:focus,
.btn-default.disabled.focus,
.btn-default[disabled].focus,
fieldset[disabled] .btn-default.focus {
  background-color: #fff;
  border-color: #ccc;
}
.btn-default .badge {
  color: #fff;
  background-color: #333;
}
.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary:focus,
.btn-primary.focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active:hover,
.btn-primary.active:hover,
.open > .dropdown-toggle.btn-primary:hover,
.btn-primary:active:focus,
.btn-primary.active:focus,
.open > .dropdown-toggle.btn-primary:focus,
.btn-primary:active.focus,
.btn-primary.active.focus,
.open > .dropdown-toggle.btn-primary.focus {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.btn-primary.disabled:hover,
.btn-primary[disabled]:hover,
fieldset[disabled] .btn-primary:hover,
.btn-primary.disabled:focus,
.btn-primary[disabled]:focus,
fieldset[disabled] .btn-primary:focus,
.btn-primary.disabled.focus,
.btn-primary[disabled].focus,
fieldset[disabled] .btn-primary.focus {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary .badge {
  color: #337ab7;
  background-color: #fff;
}
.btn-success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success:focus,
.btn-success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.btn-success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active:hover,
.btn-success.active:hover,
.open > .dropdown-toggle.btn-success:hover,
.btn-success:active:focus,
.btn-success.active:focus,
.open > .dropdown-toggle.btn-success:focus,
.btn-success:active.focus,
.btn-success.active.focus,
.open > .dropdown-toggle.btn-success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  background-image: none;
}
.btn-success.disabled:hover,
.btn-success[disabled]:hover,
fieldset[disabled] .btn-success:hover,
.btn-success.disabled:focus,
.btn-success[disabled]:focus,
fieldset[disabled] .btn-success:focus,
.btn-success.disabled.focus,
.btn-success[disabled].focus,
fieldset[disabled] .btn-success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.btn-info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info:focus,
.btn-info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.btn-info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active:hover,
.btn-info.active:hover,
.open > .dropdown-toggle.btn-info:hover,
.btn-info:active:focus,
.btn-info.active:focus,
.open > .dropdown-toggle.btn-info:focus,
.btn-info:active.focus,
.btn-info.active.focus,
.open > .dropdown-toggle.btn-info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  background-image: none;
}
.btn-info.disabled:hover,
.btn-info[disabled]:hover,
fieldset[disabled] .btn-info:hover,
.btn-info.disabled:focus,
.btn-info[disabled]:focus,
fieldset[disabled] .btn-info:focus,
.btn-info.disabled.focus,
.btn-info[disabled].focus,
fieldset[disabled] .btn-info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.btn-warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning:focus,
.btn-warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.btn-warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active:hover,
.btn-warning.active:hover,
.open > .dropdown-toggle.btn-warning:hover,
.btn-warning:active:focus,
.btn-warning.active:focus,
.open > .dropdown-toggle.btn-warning:focus,
.btn-warning:active.focus,
.btn-warning.active.focus,
.open > .dropdown-toggle.btn-warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  background-image: none;
}
.btn-warning.disabled:hover,
.btn-warning[disabled]:hover,
fieldset[disabled] .btn-warning:hover,
.btn-warning.disabled:focus,
.btn-warning[disabled]:focus,
fieldset[disabled] .btn-warning:focus,
.btn-warning.disabled.focus,
.btn-warning[disabled].focus,
fieldset[disabled] .btn-warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.btn-danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger:focus,
.btn-danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.btn-danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active:hover,
.btn-danger.active:hover,
.open > .dropdown-toggle.btn-danger:hover,
.btn-danger:active:focus,
.btn-danger.active:focus,
.open > .dropdown-toggle.btn-danger:focus,
.btn-danger:active.focus,
.btn-danger.active.focus,
.open > .dropdown-toggle.btn-danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  background-image: none;
}
.btn-danger.disabled:hover,
.btn-danger[disabled]:hover,
fieldset[disabled] .btn-danger:hover,
.btn-danger.disabled:focus,
.btn-danger[disabled]:focus,
fieldset[disabled] .btn-danger:focus,
.btn-danger.disabled.focus,
.btn-danger[disabled].focus,
fieldset[disabled] .btn-danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger .badge {
  color: #d9534f;
  background-color: #fff;
}
.btn-link {
  color: #337ab7;
  font-weight: normal;
  border-radius: 0;
}
.btn-link,
.btn-link:active,
.btn-link.active,
.btn-link[disabled],
fieldset[disabled] .btn-link {
  background-color: transparent;
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn-link,
.btn-link:hover,
.btn-link:focus,
.btn-link:active {
  border-color: transparent;
}
.btn-link:hover,
.btn-link:focus {
  color: #23527c;
  text-decoration: underline;
  background-color: transparent;
}
.btn-link[disabled]:hover,
fieldset[disabled] .btn-link:hover,
.btn-link[disabled]:focus,
fieldset[disabled] .btn-link:focus {
  color: #777777;
  text-decoration: none;
}
.btn-lg,
.btn-group-lg > .btn {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.btn-sm,
.btn-group-sm > .btn {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-xs,
.btn-group-xs > .btn {
  padding: 1px 5px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-block {
  display: block;
  width: 100%;
}
.btn-block + .btn-block {
  margin-top: 5px;
}
input[type="submit"].btn-block,
input[type="reset"].btn-block,
input[type="button"].btn-block {
  width: 100%;
}
.fade {
  opacity: 0;
  -webkit-transition: opacity 0.15s linear;
  -o-transition: opacity 0.15s linear;
  transition: opacity 0.15s linear;
}
.fade.in {
  opacity: 1;
}
.collapse {
  display: none;
}
.collapse.in {
  display: block;
}
tr.collapse.in {
  display: table-row;
}
tbody.collapse.in {
  display: table-row-group;
}
.collapsing {
  position: relative;
  height: 0;
  overflow: hidden;
  -webkit-transition-property: height, visibility;
  transition-property: height, visibility;
  -webkit-transition-duration: 0.35s;
  transition-duration: 0.35s;
  -webkit-transition-timing-function: ease;
  transition-timing-function: ease;
}
.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px dashed;
  border-top: 4px solid \9;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}
.dropup,
.dropdown {
  position: relative;
}
.dropdown-toggle:focus {
  outline: 0;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1000;
  display: none;
  float: left;
  min-width: 160px;
  padding: 5px 0;
  margin: 2px 0 0;
  list-style: none;
  font-size: 13px;
  text-align: left;
  background-color: #fff;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.15);
  border-radius: 2px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  background-clip: padding-box;
}
.dropdown-menu.pull-right {
  right: 0;
  left: auto;
}
.dropdown-menu .divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.dropdown-menu > li > a {
  display: block;
  padding: 3px 20px;
  clear: both;
  font-weight: normal;
  line-height: 1.42857143;
  color: #333333;
  white-space: nowrap;
}
.dropdown-menu > li > a:hover,
.dropdown-menu > li > a:focus {
  text-decoration: none;
  color: #262626;
  background-color: #f5f5f5;
}
.dropdown-menu > .active > a,
.dropdown-menu > .active > a:hover,
.dropdown-menu > .active > a:focus {
  color: #fff;
  text-decoration: none;
  outline: 0;
  background-color: #337ab7;
}
.dropdown-menu > .disabled > a,
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  color: #777777;
}
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  text-decoration: none;
  background-color: transparent;
  background-image: none;
  filter: progid:DXImageTransform.Microsoft.gradient(enabled = false);
  cursor: not-allowed;
}
.open > .dropdown-menu {
  display: block;
}
.open > a {
  outline: 0;
}
.dropdown-menu-right {
  left: auto;
  right: 0;
}
.dropdown-menu-left {
  left: 0;
  right: auto;
}
.dropdown-header {
  display: block;
  padding: 3px 20px;
  font-size: 12px;
  line-height: 1.42857143;
  color: #777777;
  white-space: nowrap;
}
.dropdown-backdrop {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 990;
}
.pull-right > .dropdown-menu {
  right: 0;
  left: auto;
}
.dropup .caret,
.navbar-fixed-bottom .dropdown .caret {
  border-top: 0;
  border-bottom: 4px dashed;
  border-bottom: 4px solid \9;
  content: "";
}
.dropup .dropdown-menu,
.navbar-fixed-bottom .dropdown .dropdown-menu {
  top: auto;
  bottom: 100%;
  margin-bottom: 2px;
}
@media (min-width: 541px) {
  .navbar-right .dropdown-menu {
    left: auto;
    right: 0;
  }
  .navbar-right .dropdown-menu-left {
    left: 0;
    right: auto;
  }
}
.btn-group,
.btn-group-vertical {
  position: relative;
  display: inline-block;
  vertical-align: middle;
}
.btn-group > .btn,
.btn-group-vertical > .btn {
  position: relative;
  float: left;
}
.btn-group > .btn:hover,
.btn-group-vertical > .btn:hover,
.btn-group > .btn:focus,
.btn-group-vertical > .btn:focus,
.btn-group > .btn:active,
.btn-group-vertical > .btn:active,
.btn-group > .btn.active,
.btn-group-vertical > .btn.active {
  z-index: 2;
}
.btn-group .btn + .btn,
.btn-group .btn + .btn-group,
.btn-group .btn-group + .btn,
.btn-group .btn-group + .btn-group {
  margin-left: -1px;
}
.btn-toolbar {
  margin-left: -5px;
}
.btn-toolbar .btn,
.btn-toolbar .btn-group,
.btn-toolbar .input-group {
  float: left;
}
.btn-toolbar > .btn,
.btn-toolbar > .btn-group,
.btn-toolbar > .input-group {
  margin-left: 5px;
}
.btn-group > .btn:not(:first-child):not(:last-child):not(.dropdown-toggle) {
  border-radius: 0;
}
.btn-group > .btn:first-child {
  margin-left: 0;
}
.btn-group > .btn:first-child:not(:last-child):not(.dropdown-toggle) {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn:last-child:not(:first-child),
.btn-group > .dropdown-toggle:not(:first-child) {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group > .btn-group {
  float: left;
}
.btn-group > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group .dropdown-toggle:active,
.btn-group.open .dropdown-toggle {
  outline: 0;
}
.btn-group > .btn + .dropdown-toggle {
  padding-left: 8px;
  padding-right: 8px;
}
.btn-group > .btn-lg + .dropdown-toggle {
  padding-left: 12px;
  padding-right: 12px;
}
.btn-group.open .dropdown-toggle {
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn-group.open .dropdown-toggle.btn-link {
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn .caret {
  margin-left: 0;
}
.btn-lg .caret {
  border-width: 5px 5px 0;
  border-bottom-width: 0;
}
.dropup .btn-lg .caret {
  border-width: 0 5px 5px;
}
.btn-group-vertical > .btn,
.btn-group-vertical > .btn-group,
.btn-group-vertical > .btn-group > .btn {
  display: block;
  float: none;
  width: 100%;
  max-width: 100%;
}
.btn-group-vertical > .btn-group > .btn {
  float: none;
}
.btn-group-vertical > .btn + .btn,
.btn-group-vertical > .btn + .btn-group,
.btn-group-vertical > .btn-group + .btn,
.btn-group-vertical > .btn-group + .btn-group {
  margin-top: -1px;
  margin-left: 0;
}
.btn-group-vertical > .btn:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.btn-group-vertical > .btn:first-child:not(:last-child) {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn:last-child:not(:first-child) {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
.btn-group-vertical > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.btn-group-justified {
  display: table;
  width: 100%;
  table-layout: fixed;
  border-collapse: separate;
}
.btn-group-justified > .btn,
.btn-group-justified > .btn-group {
  float: none;
  display: table-cell;
  width: 1%;
}
.btn-group-justified > .btn-group .btn {
  width: 100%;
}
.btn-group-justified > .btn-group .dropdown-menu {
  left: auto;
}
[data-toggle="buttons"] > .btn input[type="radio"],
[data-toggle="buttons"] > .btn-group > .btn input[type="radio"],
[data-toggle="buttons"] > .btn input[type="checkbox"],
[data-toggle="buttons"] > .btn-group > .btn input[type="checkbox"] {
  position: absolute;
  clip: rect(0, 0, 0, 0);
  pointer-events: none;
}
.input-group {
  position: relative;
  display: table;
  border-collapse: separate;
}
.input-group[class*="col-"] {
  float: none;
  padding-left: 0;
  padding-right: 0;
}
.input-group .form-control {
  position: relative;
  z-index: 2;
  float: left;
  width: 100%;
  margin-bottom: 0;
}
.input-group .form-control:focus {
  z-index: 3;
}
.input-group-lg > .form-control,
.input-group-lg > .input-group-addon,
.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-group-lg > .form-control,
select.input-group-lg > .input-group-addon,
select.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  line-height: 45px;
}
textarea.input-group-lg > .form-control,
textarea.input-group-lg > .input-group-addon,
textarea.input-group-lg > .input-group-btn > .btn,
select[multiple].input-group-lg > .form-control,
select[multiple].input-group-lg > .input-group-addon,
select[multiple].input-group-lg > .input-group-btn > .btn {
  height: auto;
}
.input-group-sm > .form-control,
.input-group-sm > .input-group-addon,
.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-group-sm > .form-control,
select.input-group-sm > .input-group-addon,
select.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  line-height: 30px;
}
textarea.input-group-sm > .form-control,
textarea.input-group-sm > .input-group-addon,
textarea.input-group-sm > .input-group-btn > .btn,
select[multiple].input-group-sm > .form-control,
select[multiple].input-group-sm > .input-group-addon,
select[multiple].input-group-sm > .input-group-btn > .btn {
  height: auto;
}
.input-group-addon,
.input-group-btn,
.input-group .form-control {
  display: table-cell;
}
.input-group-addon:not(:first-child):not(:last-child),
.input-group-btn:not(:first-child):not(:last-child),
.input-group .form-control:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.input-group-addon,
.input-group-btn {
  width: 1%;
  white-space: nowrap;
  vertical-align: middle;
}
.input-group-addon {
  padding: 6px 12px;
  font-size: 13px;
  font-weight: normal;
  line-height: 1;
  color: #555555;
  text-align: center;
  background-color: #eeeeee;
  border: 1px solid #ccc;
  border-radius: 2px;
}
.input-group-addon.input-sm {
  padding: 5px 10px;
  font-size: 12px;
  border-radius: 1px;
}
.input-group-addon.input-lg {
  padding: 10px 16px;
  font-size: 17px;
  border-radius: 3px;
}
.input-group-addon input[type="radio"],
.input-group-addon input[type="checkbox"] {
  margin-top: 0;
}
.input-group .form-control:first-child,
.input-group-addon:first-child,
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group > .btn,
.input-group-btn:first-child > .dropdown-toggle,
.input-group-btn:last-child > .btn:not(:last-child):not(.dropdown-toggle),
.input-group-btn:last-child > .btn-group:not(:last-child) > .btn {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.input-group-addon:first-child {
  border-right: 0;
}
.input-group .form-control:last-child,
.input-group-addon:last-child,
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group > .btn,
.input-group-btn:last-child > .dropdown-toggle,
.input-group-btn:first-child > .btn:not(:first-child),
.input-group-btn:first-child > .btn-group:not(:first-child) > .btn {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.input-group-addon:last-child {
  border-left: 0;
}
.input-group-btn {
  position: relative;
  font-size: 0;
  white-space: nowrap;
}
.input-group-btn > .btn {
  position: relative;
}
.input-group-btn > .btn + .btn {
  margin-left: -1px;
}
.input-group-btn > .btn:hover,
.input-group-btn > .btn:focus,
.input-group-btn > .btn:active {
  z-index: 2;
}
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group {
  margin-right: -1px;
}
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group {
  z-index: 2;
  margin-left: -1px;
}
.nav {
  margin-bottom: 0;
  padding-left: 0;
  list-style: none;
}
.nav > li {
  position: relative;
  display: block;
}
.nav > li > a {
  position: relative;
  display: block;
  padding: 10px 15px;
}
.nav > li > a:hover,
.nav > li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.nav > li.disabled > a {
  color: #777777;
}
.nav > li.disabled > a:hover,
.nav > li.disabled > a:focus {
  color: #777777;
  text-decoration: none;
  background-color: transparent;
  cursor: not-allowed;
}
.nav .open > a,
.nav .open > a:hover,
.nav .open > a:focus {
  background-color: #eeeeee;
  border-color: #337ab7;
}
.nav .nav-divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.nav > li > a > img {
  max-width: none;
}
.nav-tabs {
  border-bottom: 1px solid #ddd;
}
.nav-tabs > li {
  float: left;
  margin-bottom: -1px;
}
.nav-tabs > li > a {
  margin-right: 2px;
  line-height: 1.42857143;
  border: 1px solid transparent;
  border-radius: 2px 2px 0 0;
}
.nav-tabs > li > a:hover {
  border-color: #eeeeee #eeeeee #ddd;
}
.nav-tabs > li.active > a,
.nav-tabs > li.active > a:hover,
.nav-tabs > li.active > a:focus {
  color: #555555;
  background-color: #fff;
  border: 1px solid #ddd;
  border-bottom-color: transparent;
  cursor: default;
}
.nav-tabs.nav-justified {
  width: 100%;
  border-bottom: 0;
}
.nav-tabs.nav-justified > li {
  float: none;
}
.nav-tabs.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-tabs.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-tabs.nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs.nav-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs.nav-justified > .active > a,
.nav-tabs.nav-justified > .active > a:hover,
.nav-tabs.nav-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs.nav-justified > .active > a,
  .nav-tabs.nav-justified > .active > a:hover,
  .nav-tabs.nav-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.nav-pills > li {
  float: left;
}
.nav-pills > li > a {
  border-radius: 2px;
}
.nav-pills > li + li {
  margin-left: 2px;
}
.nav-pills > li.active > a,
.nav-pills > li.active > a:hover,
.nav-pills > li.active > a:focus {
  color: #fff;
  background-color: #337ab7;
}
.nav-stacked > li {
  float: none;
}
.nav-stacked > li + li {
  margin-top: 2px;
  margin-left: 0;
}
.nav-justified {
  width: 100%;
}
.nav-justified > li {
  float: none;
}
.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs-justified {
  border-bottom: 0;
}
.nav-tabs-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs-justified > .active > a,
.nav-tabs-justified > .active > a:hover,
.nav-tabs-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs-justified > .active > a,
  .nav-tabs-justified > .active > a:hover,
  .nav-tabs-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.tab-content > .tab-pane {
  display: none;
}
.tab-content > .active {
  display: block;
}
.nav-tabs .dropdown-menu {
  margin-top: -1px;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar {
  position: relative;
  min-height: 30px;
  margin-bottom: 18px;
  border: 1px solid transparent;
}
@media (min-width: 541px) {
  .navbar {
    border-radius: 2px;
  }
}
@media (min-width: 541px) {
  .navbar-header {
    float: left;
  }
}
.navbar-collapse {
  overflow-x: visible;
  padding-right: 0px;
  padding-left: 0px;
  border-top: 1px solid transparent;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
  -webkit-overflow-scrolling: touch;
}
.navbar-collapse.in {
  overflow-y: auto;
}
@media (min-width: 541px) {
  .navbar-collapse {
    width: auto;
    border-top: 0;
    box-shadow: none;
  }
  .navbar-collapse.collapse {
    display: block !important;
    height: auto !important;
    padding-bottom: 0;
    overflow: visible !important;
  }
  .navbar-collapse.in {
    overflow-y: visible;
  }
  .navbar-fixed-top .navbar-collapse,
  .navbar-static-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    padding-left: 0;
    padding-right: 0;
  }
}
.navbar-fixed-top .navbar-collapse,
.navbar-fixed-bottom .navbar-collapse {
  max-height: 340px;
}
@media (max-device-width: 540px) and (orientation: landscape) {
  .navbar-fixed-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    max-height: 200px;
  }
}
.container > .navbar-header,
.container-fluid > .navbar-header,
.container > .navbar-collapse,
.container-fluid > .navbar-collapse {
  margin-right: 0px;
  margin-left: 0px;
}
@media (min-width: 541px) {
  .container > .navbar-header,
  .container-fluid > .navbar-header,
  .container > .navbar-collapse,
  .container-fluid > .navbar-collapse {
    margin-right: 0;
    margin-left: 0;
  }
}
.navbar-static-top {
  z-index: 1000;
  border-width: 0 0 1px;
}
@media (min-width: 541px) {
  .navbar-static-top {
    border-radius: 0;
  }
}
.navbar-fixed-top,
.navbar-fixed-bottom {
  position: fixed;
  right: 0;
  left: 0;
  z-index: 1030;
}
@media (min-width: 541px) {
  .navbar-fixed-top,
  .navbar-fixed-bottom {
    border-radius: 0;
  }
}
.navbar-fixed-top {
  top: 0;
  border-width: 0 0 1px;
}
.navbar-fixed-bottom {
  bottom: 0;
  margin-bottom: 0;
  border-width: 1px 0 0;
}
.navbar-brand {
  float: left;
  padding: 6px 0px;
  font-size: 17px;
  line-height: 18px;
  height: 30px;
}
.navbar-brand:hover,
.navbar-brand:focus {
  text-decoration: none;
}
.navbar-brand > img {
  display: block;
}
@media (min-width: 541px) {
  .navbar > .container .navbar-brand,
  .navbar > .container-fluid .navbar-brand {
    margin-left: 0px;
  }
}
.navbar-toggle {
  position: relative;
  float: right;
  margin-right: 0px;
  padding: 9px 10px;
  margin-top: -2px;
  margin-bottom: -2px;
  background-color: transparent;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 2px;
}
.navbar-toggle:focus {
  outline: 0;
}
.navbar-toggle .icon-bar {
  display: block;
  width: 22px;
  height: 2px;
  border-radius: 1px;
}
.navbar-toggle .icon-bar + .icon-bar {
  margin-top: 4px;
}
@media (min-width: 541px) {
  .navbar-toggle {
    display: none;
  }
}
.navbar-nav {
  margin: 3px 0px;
}
.navbar-nav > li > a {
  padding-top: 10px;
  padding-bottom: 10px;
  line-height: 18px;
}
@media (max-width: 540px) {
  .navbar-nav .open .dropdown-menu {
    position: static;
    float: none;
    width: auto;
    margin-top: 0;
    background-color: transparent;
    border: 0;
    box-shadow: none;
  }
  .navbar-nav .open .dropdown-menu > li > a,
  .navbar-nav .open .dropdown-menu .dropdown-header {
    padding: 5px 15px 5px 25px;
  }
  .navbar-nav .open .dropdown-menu > li > a {
    line-height: 18px;
  }
  .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-nav .open .dropdown-menu > li > a:focus {
    background-image: none;
  }
}
@media (min-width: 541px) {
  .navbar-nav {
    float: left;
    margin: 0;
  }
  .navbar-nav > li {
    float: left;
  }
  .navbar-nav > li > a {
    padding-top: 6px;
    padding-bottom: 6px;
  }
}
.navbar-form {
  margin-left: 0px;
  margin-right: 0px;
  padding: 10px 0px;
  border-top: 1px solid transparent;
  border-bottom: 1px solid transparent;
  -webkit-box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  margin-top: -1px;
  margin-bottom: -1px;
}
@media (min-width: 768px) {
  .navbar-form .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .navbar-form .form-control-static {
    display: inline-block;
  }
  .navbar-form .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .navbar-form .input-group .input-group-addon,
  .navbar-form .input-group .input-group-btn,
  .navbar-form .input-group .form-control {
    width: auto;
  }
  .navbar-form .input-group > .form-control {
    width: 100%;
  }
  .navbar-form .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio,
  .navbar-form .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio label,
  .navbar-form .checkbox label {
    padding-left: 0;
  }
  .navbar-form .radio input[type="radio"],
  .navbar-form .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .navbar-form .has-feedback .form-control-feedback {
    top: 0;
  }
}
@media (max-width: 540px) {
  .navbar-form .form-group {
    margin-bottom: 5px;
  }
  .navbar-form .form-group:last-child {
    margin-bottom: 0;
  }
}
@media (min-width: 541px) {
  .navbar-form {
    width: auto;
    border: 0;
    margin-left: 0;
    margin-right: 0;
    padding-top: 0;
    padding-bottom: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
  }
}
.navbar-nav > li > .dropdown-menu {
  margin-top: 0;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar-fixed-bottom .navbar-nav > li > .dropdown-menu {
  margin-bottom: 0;
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.navbar-btn {
  margin-top: -1px;
  margin-bottom: -1px;
}
.navbar-btn.btn-sm {
  margin-top: 0px;
  margin-bottom: 0px;
}
.navbar-btn.btn-xs {
  margin-top: 4px;
  margin-bottom: 4px;
}
.navbar-text {
  margin-top: 6px;
  margin-bottom: 6px;
}
@media (min-width: 541px) {
  .navbar-text {
    float: left;
    margin-left: 0px;
    margin-right: 0px;
  }
}
@media (min-width: 541px) {
  .navbar-left {
    float: left !important;
    float: left;
  }
  .navbar-right {
    float: right !important;
    float: right;
    margin-right: 0px;
  }
  .navbar-right ~ .navbar-right {
    margin-right: 0;
  }
}
.navbar-default {
  background-color: #f8f8f8;
  border-color: #e7e7e7;
}
.navbar-default .navbar-brand {
  color: #777;
}
.navbar-default .navbar-brand:hover,
.navbar-default .navbar-brand:focus {
  color: #5e5e5e;
  background-color: transparent;
}
.navbar-default .navbar-text {
  color: #777;
}
.navbar-default .navbar-nav > li > a {
  color: #777;
}
.navbar-default .navbar-nav > li > a:hover,
.navbar-default .navbar-nav > li > a:focus {
  color: #333;
  background-color: transparent;
}
.navbar-default .navbar-nav > .active > a,
.navbar-default .navbar-nav > .active > a:hover,
.navbar-default .navbar-nav > .active > a:focus {
  color: #555;
  background-color: #e7e7e7;
}
.navbar-default .navbar-nav > .disabled > a,
.navbar-default .navbar-nav > .disabled > a:hover,
.navbar-default .navbar-nav > .disabled > a:focus {
  color: #ccc;
  background-color: transparent;
}
.navbar-default .navbar-toggle {
  border-color: #ddd;
}
.navbar-default .navbar-toggle:hover,
.navbar-default .navbar-toggle:focus {
  background-color: #ddd;
}
.navbar-default .navbar-toggle .icon-bar {
  background-color: #888;
}
.navbar-default .navbar-collapse,
.navbar-default .navbar-form {
  border-color: #e7e7e7;
}
.navbar-default .navbar-nav > .open > a,
.navbar-default .navbar-nav > .open > a:hover,
.navbar-default .navbar-nav > .open > a:focus {
  background-color: #e7e7e7;
  color: #555;
}
@media (max-width: 540px) {
  .navbar-default .navbar-nav .open .dropdown-menu > li > a {
    color: #777;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #333;
    background-color: transparent;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #555;
    background-color: #e7e7e7;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #ccc;
    background-color: transparent;
  }
}
.navbar-default .navbar-link {
  color: #777;
}
.navbar-default .navbar-link:hover {
  color: #333;
}
.navbar-default .btn-link {
  color: #777;
}
.navbar-default .btn-link:hover,
.navbar-default .btn-link:focus {
  color: #333;
}
.navbar-default .btn-link[disabled]:hover,
fieldset[disabled] .navbar-default .btn-link:hover,
.navbar-default .btn-link[disabled]:focus,
fieldset[disabled] .navbar-default .btn-link:focus {
  color: #ccc;
}
.navbar-inverse {
  background-color: #222;
  border-color: #080808;
}
.navbar-inverse .navbar-brand {
  color: #9d9d9d;
}
.navbar-inverse .navbar-brand:hover,
.navbar-inverse .navbar-brand:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-text {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a:hover,
.navbar-inverse .navbar-nav > li > a:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-nav > .active > a,
.navbar-inverse .navbar-nav > .active > a:hover,
.navbar-inverse .navbar-nav > .active > a:focus {
  color: #fff;
  background-color: #080808;
}
.navbar-inverse .navbar-nav > .disabled > a,
.navbar-inverse .navbar-nav > .disabled > a:hover,
.navbar-inverse .navbar-nav > .disabled > a:focus {
  color: #444;
  background-color: transparent;
}
.navbar-inverse .navbar-toggle {
  border-color: #333;
}
.navbar-inverse .navbar-toggle:hover,
.navbar-inverse .navbar-toggle:focus {
  background-color: #333;
}
.navbar-inverse .navbar-toggle .icon-bar {
  background-color: #fff;
}
.navbar-inverse .navbar-collapse,
.navbar-inverse .navbar-form {
  border-color: #101010;
}
.navbar-inverse .navbar-nav > .open > a,
.navbar-inverse .navbar-nav > .open > a:hover,
.navbar-inverse .navbar-nav > .open > a:focus {
  background-color: #080808;
  color: #fff;
}
@media (max-width: 540px) {
  .navbar-inverse .navbar-nav .open .dropdown-menu > .dropdown-header {
    border-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu .divider {
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a {
    color: #9d9d9d;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #fff;
    background-color: transparent;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #fff;
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #444;
    background-color: transparent;
  }
}
.navbar-inverse .navbar-link {
  color: #9d9d9d;
}
.navbar-inverse .navbar-link:hover {
  color: #fff;
}
.navbar-inverse .btn-link {
  color: #9d9d9d;
}
.navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link:focus {
  color: #fff;
}
.navbar-inverse .btn-link[disabled]:hover,
fieldset[disabled] .navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link[disabled]:focus,
fieldset[disabled] .navbar-inverse .btn-link:focus {
  color: #444;
}
.breadcrumb {
  padding: 8px 15px;
  margin-bottom: 18px;
  list-style: none;
  background-color: #f5f5f5;
  border-radius: 2px;
}
.breadcrumb > li {
  display: inline-block;
}
.breadcrumb > li + li:before {
  content: "/\00a0";
  padding: 0 5px;
  color: #5e5e5e;
}
.breadcrumb > .active {
  color: #777777;
}
.pagination {
  display: inline-block;
  padding-left: 0;
  margin: 18px 0;
  border-radius: 2px;
}
.pagination > li {
  display: inline;
}
.pagination > li > a,
.pagination > li > span {
  position: relative;
  float: left;
  padding: 6px 12px;
  line-height: 1.42857143;
  text-decoration: none;
  color: #337ab7;
  background-color: #fff;
  border: 1px solid #ddd;
  margin-left: -1px;
}
.pagination > li:first-child > a,
.pagination > li:first-child > span {
  margin-left: 0;
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.pagination > li:last-child > a,
.pagination > li:last-child > span {
  border-bottom-right-radius: 2px;
  border-top-right-radius: 2px;
}
.pagination > li > a:hover,
.pagination > li > span:hover,
.pagination > li > a:focus,
.pagination > li > span:focus {
  z-index: 2;
  color: #23527c;
  background-color: #eeeeee;
  border-color: #ddd;
}
.pagination > .active > a,
.pagination > .active > span,
.pagination > .active > a:hover,
.pagination > .active > span:hover,
.pagination > .active > a:focus,
.pagination > .active > span:focus {
  z-index: 3;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
  cursor: default;
}
.pagination > .disabled > span,
.pagination > .disabled > span:hover,
.pagination > .disabled > span:focus,
.pagination > .disabled > a,
.pagination > .disabled > a:hover,
.pagination > .disabled > a:focus {
  color: #777777;
  background-color: #fff;
  border-color: #ddd;
  cursor: not-allowed;
}
.pagination-lg > li > a,
.pagination-lg > li > span {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.pagination-lg > li:first-child > a,
.pagination-lg > li:first-child > span {
  border-bottom-left-radius: 3px;
  border-top-left-radius: 3px;
}
.pagination-lg > li:last-child > a,
.pagination-lg > li:last-child > span {
  border-bottom-right-radius: 3px;
  border-top-right-radius: 3px;
}
.pagination-sm > li > a,
.pagination-sm > li > span {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.pagination-sm > li:first-child > a,
.pagination-sm > li:first-child > span {
  border-bottom-left-radius: 1px;
  border-top-left-radius: 1px;
}
.pagination-sm > li:last-child > a,
.pagination-sm > li:last-child > span {
  border-bottom-right-radius: 1px;
  border-top-right-radius: 1px;
}
.pager {
  padding-left: 0;
  margin: 18px 0;
  list-style: none;
  text-align: center;
}
.pager li {
  display: inline;
}
.pager li > a,
.pager li > span {
  display: inline-block;
  padding: 5px 14px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 15px;
}
.pager li > a:hover,
.pager li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.pager .next > a,
.pager .next > span {
  float: right;
}
.pager .previous > a,
.pager .previous > span {
  float: left;
}
.pager .disabled > a,
.pager .disabled > a:hover,
.pager .disabled > a:focus,
.pager .disabled > span {
  color: #777777;
  background-color: #fff;
  cursor: not-allowed;
}
.label {
  display: inline;
  padding: .2em .6em .3em;
  font-size: 75%;
  font-weight: bold;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: .25em;
}
a.label:hover,
a.label:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.label:empty {
  display: none;
}
.btn .label {
  position: relative;
  top: -1px;
}
.label-default {
  background-color: #777777;
}
.label-default[href]:hover,
.label-default[href]:focus {
  background-color: #5e5e5e;
}
.label-primary {
  background-color: #337ab7;
}
.label-primary[href]:hover,
.label-primary[href]:focus {
  background-color: #286090;
}
.label-success {
  background-color: #5cb85c;
}
.label-success[href]:hover,
.label-success[href]:focus {
  background-color: #449d44;
}
.label-info {
  background-color: #5bc0de;
}
.label-info[href]:hover,
.label-info[href]:focus {
  background-color: #31b0d5;
}
.label-warning {
  background-color: #f0ad4e;
}
.label-warning[href]:hover,
.label-warning[href]:focus {
  background-color: #ec971f;
}
.label-danger {
  background-color: #d9534f;
}
.label-danger[href]:hover,
.label-danger[href]:focus {
  background-color: #c9302c;
}
.badge {
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  font-size: 12px;
  font-weight: bold;
  color: #fff;
  line-height: 1;
  vertical-align: middle;
  white-space: nowrap;
  text-align: center;
  background-color: #777777;
  border-radius: 10px;
}
.badge:empty {
  display: none;
}
.btn .badge {
  position: relative;
  top: -1px;
}
.btn-xs .badge,
.btn-group-xs > .btn .badge {
  top: 0;
  padding: 1px 5px;
}
a.badge:hover,
a.badge:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.list-group-item.active > .badge,
.nav-pills > .active > a > .badge {
  color: #337ab7;
  background-color: #fff;
}
.list-group-item > .badge {
  float: right;
}
.list-group-item > .badge + .badge {
  margin-right: 5px;
}
.nav-pills > li > a > .badge {
  margin-left: 3px;
}
.jumbotron {
  padding-top: 30px;
  padding-bottom: 30px;
  margin-bottom: 30px;
  color: inherit;
  background-color: #eeeeee;
}
.jumbotron h1,
.jumbotron .h1 {
  color: inherit;
}
.jumbotron p {
  margin-bottom: 15px;
  font-size: 20px;
  font-weight: 200;
}
.jumbotron > hr {
  border-top-color: #d5d5d5;
}
.container .jumbotron,
.container-fluid .jumbotron {
  border-radius: 3px;
  padding-left: 0px;
  padding-right: 0px;
}
.jumbotron .container {
  max-width: 100%;
}
@media screen and (min-width: 768px) {
  .jumbotron {
    padding-top: 48px;
    padding-bottom: 48px;
  }
  .container .jumbotron,
  .container-fluid .jumbotron {
    padding-left: 60px;
    padding-right: 60px;
  }
  .jumbotron h1,
  .jumbotron .h1 {
    font-size: 59px;
  }
}
.thumbnail {
  display: block;
  padding: 4px;
  margin-bottom: 18px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: border 0.2s ease-in-out;
  -o-transition: border 0.2s ease-in-out;
  transition: border 0.2s ease-in-out;
}
.thumbnail > img,
.thumbnail a > img {
  margin-left: auto;
  margin-right: auto;
}
a.thumbnail:hover,
a.thumbnail:focus,
a.thumbnail.active {
  border-color: #337ab7;
}
.thumbnail .caption {
  padding: 9px;
  color: #000;
}
.alert {
  padding: 15px;
  margin-bottom: 18px;
  border: 1px solid transparent;
  border-radius: 2px;
}
.alert h4 {
  margin-top: 0;
  color: inherit;
}
.alert .alert-link {
  font-weight: bold;
}
.alert > p,
.alert > ul {
  margin-bottom: 0;
}
.alert > p + p {
  margin-top: 5px;
}
.alert-dismissable,
.alert-dismissible {
  padding-right: 35px;
}
.alert-dismissable .close,
.alert-dismissible .close {
  position: relative;
  top: -2px;
  right: -21px;
  color: inherit;
}
.alert-success {
  background-color: #dff0d8;
  border-color: #d6e9c6;
  color: #3c763d;
}
.alert-success hr {
  border-top-color: #c9e2b3;
}
.alert-success .alert-link {
  color: #2b542c;
}
.alert-info {
  background-color: #d9edf7;
  border-color: #bce8f1;
  color: #31708f;
}
.alert-info hr {
  border-top-color: #a6e1ec;
}
.alert-info .alert-link {
  color: #245269;
}
.alert-warning {
  background-color: #fcf8e3;
  border-color: #faebcc;
  color: #8a6d3b;
}
.alert-warning hr {
  border-top-color: #f7e1b5;
}
.alert-warning .alert-link {
  color: #66512c;
}
.alert-danger {
  background-color: #f2dede;
  border-color: #ebccd1;
  color: #a94442;
}
.alert-danger hr {
  border-top-color: #e4b9c0;
}
.alert-danger .alert-link {
  color: #843534;
}
@-webkit-keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
@keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
.progress {
  overflow: hidden;
  height: 18px;
  margin-bottom: 18px;
  background-color: #f5f5f5;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
}
.progress-bar {
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 18px;
  color: #fff;
  text-align: center;
  background-color: #337ab7;
  -webkit-box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  -webkit-transition: width 0.6s ease;
  -o-transition: width 0.6s ease;
  transition: width 0.6s ease;
}
.progress-striped .progress-bar,
.progress-bar-striped {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-size: 40px 40px;
}
.progress.active .progress-bar,
.progress-bar.active {
  -webkit-animation: progress-bar-stripes 2s linear infinite;
  -o-animation: progress-bar-stripes 2s linear infinite;
  animation: progress-bar-stripes 2s linear infinite;
}
.progress-bar-success {
  background-color: #5cb85c;
}
.progress-striped .progress-bar-success {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-info {
  background-color: #5bc0de;
}
.progress-striped .progress-bar-info {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-warning {
  background-color: #f0ad4e;
}
.progress-striped .progress-bar-warning {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-danger {
  background-color: #d9534f;
}
.progress-striped .progress-bar-danger {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.media {
  margin-top: 15px;
}
.media:first-child {
  margin-top: 0;
}
.media,
.media-body {
  zoom: 1;
  overflow: hidden;
}
.media-body {
  width: 10000px;
}
.media-object {
  display: block;
}
.media-object.img-thumbnail {
  max-width: none;
}
.media-right,
.media > .pull-right {
  padding-left: 10px;
}
.media-left,
.media > .pull-left {
  padding-right: 10px;
}
.media-left,
.media-right,
.media-body {
  display: table-cell;
  vertical-align: top;
}
.media-middle {
  vertical-align: middle;
}
.media-bottom {
  vertical-align: bottom;
}
.media-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.media-list {
  padding-left: 0;
  list-style: none;
}
.list-group {
  margin-bottom: 20px;
  padding-left: 0;
}
.list-group-item {
  position: relative;
  display: block;
  padding: 10px 15px;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid #ddd;
}
.list-group-item:first-child {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
}
.list-group-item:last-child {
  margin-bottom: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
a.list-group-item,
button.list-group-item {
  color: #555;
}
a.list-group-item .list-group-item-heading,
button.list-group-item .list-group-item-heading {
  color: #333;
}
a.list-group-item:hover,
button.list-group-item:hover,
a.list-group-item:focus,
button.list-group-item:focus {
  text-decoration: none;
  color: #555;
  background-color: #f5f5f5;
}
button.list-group-item {
  width: 100%;
  text-align: left;
}
.list-group-item.disabled,
.list-group-item.disabled:hover,
.list-group-item.disabled:focus {
  background-color: #eeeeee;
  color: #777777;
  cursor: not-allowed;
}
.list-group-item.disabled .list-group-item-heading,
.list-group-item.disabled:hover .list-group-item-heading,
.list-group-item.disabled:focus .list-group-item-heading {
  color: inherit;
}
.list-group-item.disabled .list-group-item-text,
.list-group-item.disabled:hover .list-group-item-text,
.list-group-item.disabled:focus .list-group-item-text {
  color: #777777;
}
.list-group-item.active,
.list-group-item.active:hover,
.list-group-item.active:focus {
  z-index: 2;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.list-group-item.active .list-group-item-heading,
.list-group-item.active:hover .list-group-item-heading,
.list-group-item.active:focus .list-group-item-heading,
.list-group-item.active .list-group-item-heading > small,
.list-group-item.active:hover .list-group-item-heading > small,
.list-group-item.active:focus .list-group-item-heading > small,
.list-group-item.active .list-group-item-heading > .small,
.list-group-item.active:hover .list-group-item-heading > .small,
.list-group-item.active:focus .list-group-item-heading > .small {
  color: inherit;
}
.list-group-item.active .list-group-item-text,
.list-group-item.active:hover .list-group-item-text,
.list-group-item.active:focus .list-group-item-text {
  color: #c7ddef;
}
.list-group-item-success {
  color: #3c763d;
  background-color: #dff0d8;
}
a.list-group-item-success,
button.list-group-item-success {
  color: #3c763d;
}
a.list-group-item-success .list-group-item-heading,
button.list-group-item-success .list-group-item-heading {
  color: inherit;
}
a.list-group-item-success:hover,
button.list-group-item-success:hover,
a.list-group-item-success:focus,
button.list-group-item-success:focus {
  color: #3c763d;
  background-color: #d0e9c6;
}
a.list-group-item-success.active,
button.list-group-item-success.active,
a.list-group-item-success.active:hover,
button.list-group-item-success.active:hover,
a.list-group-item-success.active:focus,
button.list-group-item-success.active:focus {
  color: #fff;
  background-color: #3c763d;
  border-color: #3c763d;
}
.list-group-item-info {
  color: #31708f;
  background-color: #d9edf7;
}
a.list-group-item-info,
button.list-group-item-info {
  color: #31708f;
}
a.list-group-item-info .list-group-item-heading,
button.list-group-item-info .list-group-item-heading {
  color: inherit;
}
a.list-group-item-info:hover,
button.list-group-item-info:hover,
a.list-group-item-info:focus,
button.list-group-item-info:focus {
  color: #31708f;
  background-color: #c4e3f3;
}
a.list-group-item-info.active,
button.list-group-item-info.active,
a.list-group-item-info.active:hover,
button.list-group-item-info.active:hover,
a.list-group-item-info.active:focus,
button.list-group-item-info.active:focus {
  color: #fff;
  background-color: #31708f;
  border-color: #31708f;
}
.list-group-item-warning {
  color: #8a6d3b;
  background-color: #fcf8e3;
}
a.list-group-item-warning,
button.list-group-item-warning {
  color: #8a6d3b;
}
a.list-group-item-warning .list-group-item-heading,
button.list-group-item-warning .list-group-item-heading {
  color: inherit;
}
a.list-group-item-warning:hover,
button.list-group-item-warning:hover,
a.list-group-item-warning:focus,
button.list-group-item-warning:focus {
  color: #8a6d3b;
  background-color: #faf2cc;
}
a.list-group-item-warning.active,
button.list-group-item-warning.active,
a.list-group-item-warning.active:hover,
button.list-group-item-warning.active:hover,
a.list-group-item-warning.active:focus,
button.list-group-item-warning.active:focus {
  color: #fff;
  background-color: #8a6d3b;
  border-color: #8a6d3b;
}
.list-group-item-danger {
  color: #a94442;
  background-color: #f2dede;
}
a.list-group-item-danger,
button.list-group-item-danger {
  color: #a94442;
}
a.list-group-item-danger .list-group-item-heading,
button.list-group-item-danger .list-group-item-heading {
  color: inherit;
}
a.list-group-item-danger:hover,
button.list-group-item-danger:hover,
a.list-group-item-danger:focus,
button.list-group-item-danger:focus {
  color: #a94442;
  background-color: #ebcccc;
}
a.list-group-item-danger.active,
button.list-group-item-danger.active,
a.list-group-item-danger.active:hover,
button.list-group-item-danger.active:hover,
a.list-group-item-danger.active:focus,
button.list-group-item-danger.active:focus {
  color: #fff;
  background-color: #a94442;
  border-color: #a94442;
}
.list-group-item-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.list-group-item-text {
  margin-bottom: 0;
  line-height: 1.3;
}
.panel {
  margin-bottom: 18px;
  background-color: #fff;
  border: 1px solid transparent;
  border-radius: 2px;
  -webkit-box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
.panel-body {
  padding: 15px;
}
.panel-heading {
  padding: 10px 15px;
  border-bottom: 1px solid transparent;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel-heading > .dropdown .dropdown-toggle {
  color: inherit;
}
.panel-title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 15px;
  color: inherit;
}
.panel-title > a,
.panel-title > small,
.panel-title > .small,
.panel-title > small > a,
.panel-title > .small > a {
  color: inherit;
}
.panel-footer {
  padding: 10px 15px;
  background-color: #f5f5f5;
  border-top: 1px solid #ddd;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .list-group,
.panel > .panel-collapse > .list-group {
  margin-bottom: 0;
}
.panel > .list-group .list-group-item,
.panel > .panel-collapse > .list-group .list-group-item {
  border-width: 1px 0;
  border-radius: 0;
}
.panel > .list-group:first-child .list-group-item:first-child,
.panel > .panel-collapse > .list-group:first-child .list-group-item:first-child {
  border-top: 0;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .list-group:last-child .list-group-item:last-child,
.panel > .panel-collapse > .list-group:last-child .list-group-item:last-child {
  border-bottom: 0;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .panel-heading + .panel-collapse > .list-group .list-group-item:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.panel-heading + .list-group .list-group-item:first-child {
  border-top-width: 0;
}
.list-group + .panel-footer {
  border-top-width: 0;
}
.panel > .table,
.panel > .table-responsive > .table,
.panel > .panel-collapse > .table {
  margin-bottom: 0;
}
.panel > .table caption,
.panel > .table-responsive > .table caption,
.panel > .panel-collapse > .table caption {
  padding-left: 15px;
  padding-right: 15px;
}
.panel > .table:first-child,
.panel > .table-responsive:first-child > .table:first-child {
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child {
  border-top-left-radius: 1px;
  border-top-right-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:first-child {
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:last-child {
  border-top-right-radius: 1px;
}
.panel > .table:last-child,
.panel > .table-responsive:last-child > .table:last-child {
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child {
  border-bottom-left-radius: 1px;
  border-bottom-right-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:first-child {
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:last-child {
  border-bottom-right-radius: 1px;
}
.panel > .panel-body + .table,
.panel > .panel-body + .table-responsive,
.panel > .table + .panel-body,
.panel > .table-responsive + .panel-body {
  border-top: 1px solid #ddd;
}
.panel > .table > tbody:first-child > tr:first-child th,
.panel > .table > tbody:first-child > tr:first-child td {
  border-top: 0;
}
.panel > .table-bordered,
.panel > .table-responsive > .table-bordered {
  border: 0;
}
.panel > .table-bordered > thead > tr > th:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:first-child,
.panel > .table-bordered > tbody > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:first-child,
.panel > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-bordered > thead > tr > td:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:first-child,
.panel > .table-bordered > tbody > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:first-child,
.panel > .table-bordered > tfoot > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:first-child {
  border-left: 0;
}
.panel > .table-bordered > thead > tr > th:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:last-child,
.panel > .table-bordered > tbody > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:last-child,
.panel > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-bordered > thead > tr > td:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:last-child,
.panel > .table-bordered > tbody > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:last-child,
.panel > .table-bordered > tfoot > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:last-child {
  border-right: 0;
}
.panel > .table-bordered > thead > tr:first-child > td,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > td,
.panel > .table-bordered > tbody > tr:first-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > td,
.panel > .table-bordered > thead > tr:first-child > th,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > th,
.panel > .table-bordered > tbody > tr:first-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > th {
  border-bottom: 0;
}
.panel > .table-bordered > tbody > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > td,
.panel > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-bordered > tbody > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > th,
.panel > .table-bordered > tfoot > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > th {
  border-bottom: 0;
}
.panel > .table-responsive {
  border: 0;
  margin-bottom: 0;
}
.panel-group {
  margin-bottom: 18px;
}
.panel-group .panel {
  margin-bottom: 0;
  border-radius: 2px;
}
.panel-group .panel + .panel {
  margin-top: 5px;
}
.panel-group .panel-heading {
  border-bottom: 0;
}
.panel-group .panel-heading + .panel-collapse > .panel-body,
.panel-group .panel-heading + .panel-collapse > .list-group {
  border-top: 1px solid #ddd;
}
.panel-group .panel-footer {
  border-top: 0;
}
.panel-group .panel-footer + .panel-collapse .panel-body {
  border-bottom: 1px solid #ddd;
}
.panel-default {
  border-color: #ddd;
}
.panel-default > .panel-heading {
  color: #333333;
  background-color: #f5f5f5;
  border-color: #ddd;
}
.panel-default > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ddd;
}
.panel-default > .panel-heading .badge {
  color: #f5f5f5;
  background-color: #333333;
}
.panel-default > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ddd;
}
.panel-primary {
  border-color: #337ab7;
}
.panel-primary > .panel-heading {
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.panel-primary > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #337ab7;
}
.panel-primary > .panel-heading .badge {
  color: #337ab7;
  background-color: #fff;
}
.panel-primary > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #337ab7;
}
.panel-success {
  border-color: #d6e9c6;
}
.panel-success > .panel-heading {
  color: #3c763d;
  background-color: #dff0d8;
  border-color: #d6e9c6;
}
.panel-success > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #d6e9c6;
}
.panel-success > .panel-heading .badge {
  color: #dff0d8;
  background-color: #3c763d;
}
.panel-success > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #d6e9c6;
}
.panel-info {
  border-color: #bce8f1;
}
.panel-info > .panel-heading {
  color: #31708f;
  background-color: #d9edf7;
  border-color: #bce8f1;
}
.panel-info > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #bce8f1;
}
.panel-info > .panel-heading .badge {
  color: #d9edf7;
  background-color: #31708f;
}
.panel-info > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #bce8f1;
}
.panel-warning {
  border-color: #faebcc;
}
.panel-warning > .panel-heading {
  color: #8a6d3b;
  background-color: #fcf8e3;
  border-color: #faebcc;
}
.panel-warning > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #faebcc;
}
.panel-warning > .panel-heading .badge {
  color: #fcf8e3;
  background-color: #8a6d3b;
}
.panel-warning > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #faebcc;
}
.panel-danger {
  border-color: #ebccd1;
}
.panel-danger > .panel-heading {
  color: #a94442;
  background-color: #f2dede;
  border-color: #ebccd1;
}
.panel-danger > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ebccd1;
}
.panel-danger > .panel-heading .badge {
  color: #f2dede;
  background-color: #a94442;
}
.panel-danger > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ebccd1;
}
.embed-responsive {
  position: relative;
  display: block;
  height: 0;
  padding: 0;
  overflow: hidden;
}
.embed-responsive .embed-responsive-item,
.embed-responsive iframe,
.embed-responsive embed,
.embed-responsive object,
.embed-responsive video {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
  border: 0;
}
.embed-responsive-16by9 {
  padding-bottom: 56.25%;
}
.embed-responsive-4by3 {
  padding-bottom: 75%;
}
.well {
  min-height: 20px;
  padding: 19px;
  margin-bottom: 20px;
  background-color: #f5f5f5;
  border: 1px solid #e3e3e3;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
}
.well blockquote {
  border-color: #ddd;
  border-color: rgba(0, 0, 0, 0.15);
}
.well-lg {
  padding: 24px;
  border-radius: 3px;
}
.well-sm {
  padding: 9px;
  border-radius: 1px;
}
.close {
  float: right;
  font-size: 19.5px;
  font-weight: bold;
  line-height: 1;
  color: #000;
  text-shadow: 0 1px 0 #fff;
  opacity: 0.2;
  filter: alpha(opacity=20);
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
  opacity: 0.5;
  filter: alpha(opacity=50);
}
button.close {
  padding: 0;
  cursor: pointer;
  background: transparent;
  border: 0;
  -webkit-appearance: none;
}
.modal-open {
  overflow: hidden;
}
.modal {
  display: none;
  overflow: hidden;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1050;
  -webkit-overflow-scrolling: touch;
  outline: 0;
}
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, -25%);
  -ms-transform: translate(0, -25%);
  -o-transform: translate(0, -25%);
  transform: translate(0, -25%);
  -webkit-transition: -webkit-transform 0.3s ease-out;
  -moz-transition: -moz-transform 0.3s ease-out;
  -o-transition: -o-transform 0.3s ease-out;
  transition: transform 0.3s ease-out;
}
.modal.in .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
.modal-open .modal {
  overflow-x: hidden;
  overflow-y: auto;
}
.modal-dialog {
  position: relative;
  width: auto;
  margin: 10px;
}
.modal-content {
  position: relative;
  background-color: #fff;
  border: 1px solid #999;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  background-clip: padding-box;
  outline: 0;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1040;
  background-color: #000;
}
.modal-backdrop.fade {
  opacity: 0;
  filter: alpha(opacity=0);
}
.modal-backdrop.in {
  opacity: 0.5;
  filter: alpha(opacity=50);
}
.modal-header {
  padding: 15px;
  border-bottom: 1px solid #e5e5e5;
}
.modal-header .close {
  margin-top: -2px;
}
.modal-title {
  margin: 0;
  line-height: 1.42857143;
}
.modal-body {
  position: relative;
  padding: 15px;
}
.modal-footer {
  padding: 15px;
  text-align: right;
  border-top: 1px solid #e5e5e5;
}
.modal-footer .btn + .btn {
  margin-left: 5px;
  margin-bottom: 0;
}
.modal-footer .btn-group .btn + .btn {
  margin-left: -1px;
}
.modal-footer .btn-block + .btn-block {
  margin-left: 0;
}
.modal-scrollbar-measure {
  position: absolute;
  top: -9999px;
  width: 50px;
  height: 50px;
  overflow: scroll;
}
@media (min-width: 768px) {
  .modal-dialog {
    width: 600px;
    margin: 30px auto;
  }
  .modal-content {
    -webkit-box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
  }
  .modal-sm {
    width: 300px;
  }
}
@media (min-width: 992px) {
  .modal-lg {
    width: 900px;
  }
}
.tooltip {
  position: absolute;
  z-index: 1070;
  display: block;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 12px;
  opacity: 0;
  filter: alpha(opacity=0);
}
.tooltip.in {
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.tooltip.top {
  margin-top: -3px;
  padding: 5px 0;
}
.tooltip.right {
  margin-left: 3px;
  padding: 0 5px;
}
.tooltip.bottom {
  margin-top: 3px;
  padding: 5px 0;
}
.tooltip.left {
  margin-left: -3px;
  padding: 0 5px;
}
.tooltip-inner {
  max-width: 200px;
  padding: 3px 8px;
  color: #fff;
  text-align: center;
  background-color: #000;
  border-radius: 2px;
}
.tooltip-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.tooltip.top .tooltip-arrow {
  bottom: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-left .tooltip-arrow {
  bottom: 0;
  right: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-right .tooltip-arrow {
  bottom: 0;
  left: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.right .tooltip-arrow {
  top: 50%;
  left: 0;
  margin-top: -5px;
  border-width: 5px 5px 5px 0;
  border-right-color: #000;
}
.tooltip.left .tooltip-arrow {
  top: 50%;
  right: 0;
  margin-top: -5px;
  border-width: 5px 0 5px 5px;
  border-left-color: #000;
}
.tooltip.bottom .tooltip-arrow {
  top: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-left .tooltip-arrow {
  top: 0;
  right: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-right .tooltip-arrow {
  top: 0;
  left: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.popover {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1060;
  display: none;
  max-width: 276px;
  padding: 1px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 13px;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
.popover.top {
  margin-top: -10px;
}
.popover.right {
  margin-left: 10px;
}
.popover.bottom {
  margin-top: 10px;
}
.popover.left {
  margin-left: -10px;
}
.popover-title {
  margin: 0;
  padding: 8px 14px;
  font-size: 13px;
  background-color: #f7f7f7;
  border-bottom: 1px solid #ebebeb;
  border-radius: 2px 2px 0 0;
}
.popover-content {
  padding: 9px 14px;
}
.popover > .arrow,
.popover > .arrow:after {
  position: absolute;
  display: block;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.popover > .arrow {
  border-width: 11px;
}
.popover > .arrow:after {
  border-width: 10px;
  content: "";
}
.popover.top > .arrow {
  left: 50%;
  margin-left: -11px;
  border-bottom-width: 0;
  border-top-color: #999999;
  border-top-color: rgba(0, 0, 0, 0.25);
  bottom: -11px;
}
.popover.top > .arrow:after {
  content: " ";
  bottom: 1px;
  margin-left: -10px;
  border-bottom-width: 0;
  border-top-color: #fff;
}
.popover.right > .arrow {
  top: 50%;
  left: -11px;
  margin-top: -11px;
  border-left-width: 0;
  border-right-color: #999999;
  border-right-color: rgba(0, 0, 0, 0.25);
}
.popover.right > .arrow:after {
  content: " ";
  left: 1px;
  bottom: -10px;
  border-left-width: 0;
  border-right-color: #fff;
}
.popover.bottom > .arrow {
  left: 50%;
  margin-left: -11px;
  border-top-width: 0;
  border-bottom-color: #999999;
  border-bottom-color: rgba(0, 0, 0, 0.25);
  top: -11px;
}
.popover.bottom > .arrow:after {
  content: " ";
  top: 1px;
  margin-left: -10px;
  border-top-width: 0;
  border-bottom-color: #fff;
}
.popover.left > .arrow {
  top: 50%;
  right: -11px;
  margin-top: -11px;
  border-right-width: 0;
  border-left-color: #999999;
  border-left-color: rgba(0, 0, 0, 0.25);
}
.popover.left > .arrow:after {
  content: " ";
  right: 1px;
  border-right-width: 0;
  border-left-color: #fff;
  bottom: -10px;
}
.carousel {
  position: relative;
}
.carousel-inner {
  position: relative;
  overflow: hidden;
  width: 100%;
}
.carousel-inner > .item {
  display: none;
  position: relative;
  -webkit-transition: 0.6s ease-in-out left;
  -o-transition: 0.6s ease-in-out left;
  transition: 0.6s ease-in-out left;
}
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  line-height: 1;
}
@media all and (transform-3d), (-webkit-transform-3d) {
  .carousel-inner > .item {
    -webkit-transition: -webkit-transform 0.6s ease-in-out;
    -moz-transition: -moz-transform 0.6s ease-in-out;
    -o-transition: -o-transform 0.6s ease-in-out;
    transition: transform 0.6s ease-in-out;
    -webkit-backface-visibility: hidden;
    -moz-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-perspective: 1000px;
    -moz-perspective: 1000px;
    perspective: 1000px;
  }
  .carousel-inner > .item.next,
  .carousel-inner > .item.active.right {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.prev,
  .carousel-inner > .item.active.left {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.next.left,
  .carousel-inner > .item.prev.right,
  .carousel-inner > .item.active {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    left: 0;
  }
}
.carousel-inner > .active,
.carousel-inner > .next,
.carousel-inner > .prev {
  display: block;
}
.carousel-inner > .active {
  left: 0;
}
.carousel-inner > .next,
.carousel-inner > .prev {
  position: absolute;
  top: 0;
  width: 100%;
}
.carousel-inner > .next {
  left: 100%;
}
.carousel-inner > .prev {
  left: -100%;
}
.carousel-inner > .next.left,
.carousel-inner > .prev.right {
  left: 0;
}
.carousel-inner > .active.left {
  left: -100%;
}
.carousel-inner > .active.right {
  left: 100%;
}
.carousel-control {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 15%;
  opacity: 0.5;
  filter: alpha(opacity=50);
  font-size: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
  background-color: rgba(0, 0, 0, 0);
}
.carousel-control.left {
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#80000000', endColorstr='#00000000', GradientType=1);
}
.carousel-control.right {
  left: auto;
  right: 0;
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#00000000', endColorstr='#80000000', GradientType=1);
}
.carousel-control:hover,
.carousel-control:focus {
  outline: 0;
  color: #fff;
  text-decoration: none;
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.carousel-control .icon-prev,
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-left,
.carousel-control .glyphicon-chevron-right {
  position: absolute;
  top: 50%;
  margin-top: -10px;
  z-index: 5;
  display: inline-block;
}
.carousel-control .icon-prev,
.carousel-control .glyphicon-chevron-left {
  left: 50%;
  margin-left: -10px;
}
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-right {
  right: 50%;
  margin-right: -10px;
}
.carousel-control .icon-prev,
.carousel-control .icon-next {
  width: 20px;
  height: 20px;
  line-height: 1;
  font-family: serif;
}
.carousel-control .icon-prev:before {
  content: '\2039';
}
.carousel-control .icon-next:before {
  content: '\203a';
}
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  z-index: 15;
  width: 60%;
  margin-left: -30%;
  padding-left: 0;
  list-style: none;
  text-align: center;
}
.carousel-indicators li {
  display: inline-block;
  width: 10px;
  height: 10px;
  margin: 1px;
  text-indent: -999px;
  border: 1px solid #fff;
  border-radius: 10px;
  cursor: pointer;
  background-color: #000 \9;
  background-color: rgba(0, 0, 0, 0);
}
.carousel-indicators .active {
  margin: 0;
  width: 12px;
  height: 12px;
  background-color: #fff;
}
.carousel-caption {
  position: absolute;
  left: 15%;
  right: 15%;
  bottom: 20px;
  z-index: 10;
  padding-top: 20px;
  padding-bottom: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
}
.carousel-caption .btn {
  text-shadow: none;
}
@media screen and (min-width: 768px) {
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-prev,
  .carousel-control .icon-next {
    width: 30px;
    height: 30px;
    margin-top: -10px;
    font-size: 30px;
  }
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .icon-prev {
    margin-left: -10px;
  }
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-next {
    margin-right: -10px;
  }
  .carousel-caption {
    left: 20%;
    right: 20%;
    padding-bottom: 30px;
  }
  .carousel-indicators {
    bottom: 20px;
  }
}
.clearfix:before,
.clearfix:after,
.dl-horizontal dd:before,
.dl-horizontal dd:after,
.container:before,
.container:after,
.container-fluid:before,
.container-fluid:after,
.row:before,
.row:after,
.form-horizontal .form-group:before,
.form-horizontal .form-group:after,
.btn-toolbar:before,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:before,
.btn-group-vertical > .btn-group:after,
.nav:before,
.nav:after,
.navbar:before,
.navbar:after,
.navbar-header:before,
.navbar-header:after,
.navbar-collapse:before,
.navbar-collapse:after,
.pager:before,
.pager:after,
.panel-body:before,
.panel-body:after,
.modal-header:before,
.modal-header:after,
.modal-footer:before,
.modal-footer:after,
.item_buttons:before,
.item_buttons:after {
  content: " ";
  display: table;
}
.clearfix:after,
.dl-horizontal dd:after,
.container:after,
.container-fluid:after,
.row:after,
.form-horizontal .form-group:after,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:after,
.nav:after,
.navbar:after,
.navbar-header:after,
.navbar-collapse:after,
.pager:after,
.panel-body:after,
.modal-header:after,
.modal-footer:after,
.item_buttons:after {
  clear: both;
}
.center-block {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.pull-right {
  float: right !important;
}
.pull-left {
  float: left !important;
}
.hide {
  display: none !important;
}
.show {
  display: block !important;
}
.invisible {
  visibility: hidden;
}
.text-hide {
  font: 0/0 a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
.hidden {
  display: none !important;
}
.affix {
  position: fixed;
}
@-ms-viewport {
  width: device-width;
}
.visible-xs,
.visible-sm,
.visible-md,
.visible-lg {
  display: none !important;
}
.visible-xs-block,
.visible-xs-inline,
.visible-xs-inline-block,
.visible-sm-block,
.visible-sm-inline,
.visible-sm-inline-block,
.visible-md-block,
.visible-md-inline,
.visible-md-inline-block,
.visible-lg-block,
.visible-lg-inline,
.visible-lg-inline-block {
  display: none !important;
}
@media (max-width: 767px) {
  .visible-xs {
    display: block !important;
  }
  table.visible-xs {
    display: table !important;
  }
  tr.visible-xs {
    display: table-row !important;
  }
  th.visible-xs,
  td.visible-xs {
    display: table-cell !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-block {
    display: block !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline {
    display: inline !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm {
    display: block !important;
  }
  table.visible-sm {
    display: table !important;
  }
  tr.visible-sm {
    display: table-row !important;
  }
  th.visible-sm,
  td.visible-sm {
    display: table-cell !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-block {
    display: block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline {
    display: inline !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md {
    display: block !important;
  }
  table.visible-md {
    display: table !important;
  }
  tr.visible-md {
    display: table-row !important;
  }
  th.visible-md,
  td.visible-md {
    display: table-cell !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-block {
    display: block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline {
    display: inline !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg {
    display: block !important;
  }
  table.visible-lg {
    display: table !important;
  }
  tr.visible-lg {
    display: table-row !important;
  }
  th.visible-lg,
  td.visible-lg {
    display: table-cell !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-block {
    display: block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline {
    display: inline !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline-block {
    display: inline-block !important;
  }
}
@media (max-width: 767px) {
  .hidden-xs {
    display: none !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .hidden-sm {
    display: none !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .hidden-md {
    display: none !important;
  }
}
@media (min-width: 1200px) {
  .hidden-lg {
    display: none !important;
  }
}
.visible-print {
  display: none !important;
}
@media print {
  .visible-print {
    display: block !important;
  }
  table.visible-print {
    display: table !important;
  }
  tr.visible-print {
    display: table-row !important;
  }
  th.visible-print,
  td.visible-print {
    display: table-cell !important;
  }
}
.visible-print-block {
  display: none !important;
}
@media print {
  .visible-print-block {
    display: block !important;
  }
}
.visible-print-inline {
  display: none !important;
}
@media print {
  .visible-print-inline {
    display: inline !important;
  }
}
.visible-print-inline-block {
  display: none !important;
}
@media print {
  .visible-print-inline-block {
    display: inline-block !important;
  }
}
@media print {
  .hidden-print {
    display: none !important;
  }
}
/*!
*
* Font Awesome
*
*/
/*!
 *  Font Awesome 4.2.0 by @davegandy - http://fontawesome.io - @fontawesome
 *  License - http://fontawesome.io/license (Font: SIL OFL 1.1, CSS: MIT License)
 */
/* FONT PATH
 * -------------------------- */
@font-face {
  font-family: 'FontAwesome';
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?v=4.2.0');
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?#iefix&v=4.2.0') format('embedded-opentype'), url('../components/font-awesome/fonts/fontawesome-webfont.woff?v=4.2.0') format('woff'), url('../components/font-awesome/fonts/fontawesome-webfont.ttf?v=4.2.0') format('truetype'), url('../components/font-awesome/fonts/fontawesome-webfont.svg?v=4.2.0#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
.fa {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
/* makes the font 33% larger relative to the icon container */
.fa-lg {
  font-size: 1.33333333em;
  line-height: 0.75em;
  vertical-align: -15%;
}
.fa-2x {
  font-size: 2em;
}
.fa-3x {
  font-size: 3em;
}
.fa-4x {
  font-size: 4em;
}
.fa-5x {
  font-size: 5em;
}
.fa-fw {
  width: 1.28571429em;
  text-align: center;
}
.fa-ul {
  padding-left: 0;
  margin-left: 2.14285714em;
  list-style-type: none;
}
.fa-ul > li {
  position: relative;
}
.fa-li {
  position: absolute;
  left: -2.14285714em;
  width: 2.14285714em;
  top: 0.14285714em;
  text-align: center;
}
.fa-li.fa-lg {
  left: -1.85714286em;
}
.fa-border {
  padding: .2em .25em .15em;
  border: solid 0.08em #eee;
  border-radius: .1em;
}
.pull-right {
  float: right;
}
.pull-left {
  float: left;
}
.fa.pull-left {
  margin-right: .3em;
}
.fa.pull-right {
  margin-left: .3em;
}
.fa-spin {
  -webkit-animation: fa-spin 2s infinite linear;
  animation: fa-spin 2s infinite linear;
}
@-webkit-keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
@keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
.fa-rotate-90 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=1);
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}
.fa-rotate-180 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=2);
  -webkit-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  transform: rotate(180deg);
}
.fa-rotate-270 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=3);
  -webkit-transform: rotate(270deg);
  -ms-transform: rotate(270deg);
  transform: rotate(270deg);
}
.fa-flip-horizontal {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1);
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
.fa-flip-vertical {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=2, mirror=1);
  -webkit-transform: scale(1, -1);
  -ms-transform: scale(1, -1);
  transform: scale(1, -1);
}
:root .fa-rotate-90,
:root .fa-rotate-180,
:root .fa-rotate-270,
:root .fa-flip-horizontal,
:root .fa-flip-vertical {
  filter: none;
}
.fa-stack {
  position: relative;
  display: inline-block;
  width: 2em;
  height: 2em;
  line-height: 2em;
  vertical-align: middle;
}
.fa-stack-1x,
.fa-stack-2x {
  position: absolute;
  left: 0;
  width: 100%;
  text-align: center;
}
.fa-stack-1x {
  line-height: inherit;
}
.fa-stack-2x {
  font-size: 2em;
}
.fa-inverse {
  color: #fff;
}
/* Font Awesome uses the Unicode Private Use Area (PUA) to ensure screen
   readers do not read off random characters that represent icons */
.fa-glass:before {
  content: "\f000";
}
.fa-music:before {
  content: "\f001";
}
.fa-search:before {
  content: "\f002";
}
.fa-envelope-o:before {
  content: "\f003";
}
.fa-heart:before {
  content: "\f004";
}
.fa-star:before {
  content: "\f005";
}
.fa-star-o:before {
  content: "\f006";
}
.fa-user:before {
  content: "\f007";
}
.fa-film:before {
  content: "\f008";
}
.fa-th-large:before {
  content: "\f009";
}
.fa-th:before {
  content: "\f00a";
}
.fa-th-list:before {
  content: "\f00b";
}
.fa-check:before {
  content: "\f00c";
}
.fa-remove:before,
.fa-close:before,
.fa-times:before {
  content: "\f00d";
}
.fa-search-plus:before {
  content: "\f00e";
}
.fa-search-minus:before {
  content: "\f010";
}
.fa-power-off:before {
  content: "\f011";
}
.fa-signal:before {
  content: "\f012";
}
.fa-gear:before,
.fa-cog:before {
  content: "\f013";
}
.fa-trash-o:before {
  content: "\f014";
}
.fa-home:before {
  content: "\f015";
}
.fa-file-o:before {
  content: "\f016";
}
.fa-clock-o:before {
  content: "\f017";
}
.fa-road:before {
  content: "\f018";
}
.fa-download:before {
  content: "\f019";
}
.fa-arrow-circle-o-down:before {
  content: "\f01a";
}
.fa-arrow-circle-o-up:before {
  content: "\f01b";
}
.fa-inbox:before {
  content: "\f01c";
}
.fa-play-circle-o:before {
  content: "\f01d";
}
.fa-rotate-right:before,
.fa-repeat:before {
  content: "\f01e";
}
.fa-refresh:before {
  content: "\f021";
}
.fa-list-alt:before {
  content: "\f022";
}
.fa-lock:before {
  content: "\f023";
}
.fa-flag:before {
  content: "\f024";
}
.fa-headphones:before {
  content: "\f025";
}
.fa-volume-off:before {
  content: "\f026";
}
.fa-volume-down:before {
  content: "\f027";
}
.fa-volume-up:before {
  content: "\f028";
}
.fa-qrcode:before {
  content: "\f029";
}
.fa-barcode:before {
  content: "\f02a";
}
.fa-tag:before {
  content: "\f02b";
}
.fa-tags:before {
  content: "\f02c";
}
.fa-book:before {
  content: "\f02d";
}
.fa-bookmark:before {
  content: "\f02e";
}
.fa-print:before {
  content: "\f02f";
}
.fa-camera:before {
  content: "\f030";
}
.fa-font:before {
  content: "\f031";
}
.fa-bold:before {
  content: "\f032";
}
.fa-italic:before {
  content: "\f033";
}
.fa-text-height:before {
  content: "\f034";
}
.fa-text-width:before {
  content: "\f035";
}
.fa-align-left:before {
  content: "\f036";
}
.fa-align-center:before {
  content: "\f037";
}
.fa-align-right:before {
  content: "\f038";
}
.fa-align-justify:before {
  content: "\f039";
}
.fa-list:before {
  content: "\f03a";
}
.fa-dedent:before,
.fa-outdent:before {
  content: "\f03b";
}
.fa-indent:before {
  content: "\f03c";
}
.fa-video-camera:before {
  content: "\f03d";
}
.fa-photo:before,
.fa-image:before,
.fa-picture-o:before {
  content: "\f03e";
}
.fa-pencil:before {
  content: "\f040";
}
.fa-map-marker:before {
  content: "\f041";
}
.fa-adjust:before {
  content: "\f042";
}
.fa-tint:before {
  content: "\f043";
}
.fa-edit:before,
.fa-pencil-square-o:before {
  content: "\f044";
}
.fa-share-square-o:before {
  content: "\f045";
}
.fa-check-square-o:before {
  content: "\f046";
}
.fa-arrows:before {
  content: "\f047";
}
.fa-step-backward:before {
  content: "\f048";
}
.fa-fast-backward:before {
  content: "\f049";
}
.fa-backward:before {
  content: "\f04a";
}
.fa-play:before {
  content: "\f04b";
}
.fa-pause:before {
  content: "\f04c";
}
.fa-stop:before {
  content: "\f04d";
}
.fa-forward:before {
  content: "\f04e";
}
.fa-fast-forward:before {
  content: "\f050";
}
.fa-step-forward:before {
  content: "\f051";
}
.fa-eject:before {
  content: "\f052";
}
.fa-chevron-left:before {
  content: "\f053";
}
.fa-chevron-right:before {
  content: "\f054";
}
.fa-plus-circle:before {
  content: "\f055";
}
.fa-minus-circle:before {
  content: "\f056";
}
.fa-times-circle:before {
  content: "\f057";
}
.fa-check-circle:before {
  content: "\f058";
}
.fa-question-circle:before {
  content: "\f059";
}
.fa-info-circle:before {
  content: "\f05a";
}
.fa-crosshairs:before {
  content: "\f05b";
}
.fa-times-circle-o:before {
  content: "\f05c";
}
.fa-check-circle-o:before {
  content: "\f05d";
}
.fa-ban:before {
  content: "\f05e";
}
.fa-arrow-left:before {
  content: "\f060";
}
.fa-arrow-right:before {
  content: "\f061";
}
.fa-arrow-up:before {
  content: "\f062";
}
.fa-arrow-down:before {
  content: "\f063";
}
.fa-mail-forward:before,
.fa-share:before {
  content: "\f064";
}
.fa-expand:before {
  content: "\f065";
}
.fa-compress:before {
  content: "\f066";
}
.fa-plus:before {
  content: "\f067";
}
.fa-minus:before {
  content: "\f068";
}
.fa-asterisk:before {
  content: "\f069";
}
.fa-exclamation-circle:before {
  content: "\f06a";
}
.fa-gift:before {
  content: "\f06b";
}
.fa-leaf:before {
  content: "\f06c";
}
.fa-fire:before {
  content: "\f06d";
}
.fa-eye:before {
  content: "\f06e";
}
.fa-eye-slash:before {
  content: "\f070";
}
.fa-warning:before,
.fa-exclamation-triangle:before {
  content: "\f071";
}
.fa-plane:before {
  content: "\f072";
}
.fa-calendar:before {
  content: "\f073";
}
.fa-random:before {
  content: "\f074";
}
.fa-comment:before {
  content: "\f075";
}
.fa-magnet:before {
  content: "\f076";
}
.fa-chevron-up:before {
  content: "\f077";
}
.fa-chevron-down:before {
  content: "\f078";
}
.fa-retweet:before {
  content: "\f079";
}
.fa-shopping-cart:before {
  content: "\f07a";
}
.fa-folder:before {
  content: "\f07b";
}
.fa-folder-open:before {
  content: "\f07c";
}
.fa-arrows-v:before {
  content: "\f07d";
}
.fa-arrows-h:before {
  content: "\f07e";
}
.fa-bar-chart-o:before,
.fa-bar-chart:before {
  content: "\f080";
}
.fa-twitter-square:before {
  content: "\f081";
}
.fa-facebook-square:before {
  content: "\f082";
}
.fa-camera-retro:before {
  content: "\f083";
}
.fa-key:before {
  content: "\f084";
}
.fa-gears:before,
.fa-cogs:before {
  content: "\f085";
}
.fa-comments:before {
  content: "\f086";
}
.fa-thumbs-o-up:before {
  content: "\f087";
}
.fa-thumbs-o-down:before {
  content: "\f088";
}
.fa-star-half:before {
  content: "\f089";
}
.fa-heart-o:before {
  content: "\f08a";
}
.fa-sign-out:before {
  content: "\f08b";
}
.fa-linkedin-square:before {
  content: "\f08c";
}
.fa-thumb-tack:before {
  content: "\f08d";
}
.fa-external-link:before {
  content: "\f08e";
}
.fa-sign-in:before {
  content: "\f090";
}
.fa-trophy:before {
  content: "\f091";
}
.fa-github-square:before {
  content: "\f092";
}
.fa-upload:before {
  content: "\f093";
}
.fa-lemon-o:before {
  content: "\f094";
}
.fa-phone:before {
  content: "\f095";
}
.fa-square-o:before {
  content: "\f096";
}
.fa-bookmark-o:before {
  content: "\f097";
}
.fa-phone-square:before {
  content: "\f098";
}
.fa-twitter:before {
  content: "\f099";
}
.fa-facebook:before {
  content: "\f09a";
}
.fa-github:before {
  content: "\f09b";
}
.fa-unlock:before {
  content: "\f09c";
}
.fa-credit-card:before {
  content: "\f09d";
}
.fa-rss:before {
  content: "\f09e";
}
.fa-hdd-o:before {
  content: "\f0a0";
}
.fa-bullhorn:before {
  content: "\f0a1";
}
.fa-bell:before {
  content: "\f0f3";
}
.fa-certificate:before {
  content: "\f0a3";
}
.fa-hand-o-right:before {
  content: "\f0a4";
}
.fa-hand-o-left:before {
  content: "\f0a5";
}
.fa-hand-o-up:before {
  content: "\f0a6";
}
.fa-hand-o-down:before {
  content: "\f0a7";
}
.fa-arrow-circle-left:before {
  content: "\f0a8";
}
.fa-arrow-circle-right:before {
  content: "\f0a9";
}
.fa-arrow-circle-up:before {
  content: "\f0aa";
}
.fa-arrow-circle-down:before {
  content: "\f0ab";
}
.fa-globe:before {
  content: "\f0ac";
}
.fa-wrench:before {
  content: "\f0ad";
}
.fa-tasks:before {
  content: "\f0ae";
}
.fa-filter:before {
  content: "\f0b0";
}
.fa-briefcase:before {
  content: "\f0b1";
}
.fa-arrows-alt:before {
  content: "\f0b2";
}
.fa-group:before,
.fa-users:before {
  content: "\f0c0";
}
.fa-chain:before,
.fa-link:before {
  content: "\f0c1";
}
.fa-cloud:before {
  content: "\f0c2";
}
.fa-flask:before {
  content: "\f0c3";
}
.fa-cut:before,
.fa-scissors:before {
  content: "\f0c4";
}
.fa-copy:before,
.fa-files-o:before {
  content: "\f0c5";
}
.fa-paperclip:before {
  content: "\f0c6";
}
.fa-save:before,
.fa-floppy-o:before {
  content: "\f0c7";
}
.fa-square:before {
  content: "\f0c8";
}
.fa-navicon:before,
.fa-reorder:before,
.fa-bars:before {
  content: "\f0c9";
}
.fa-list-ul:before {
  content: "\f0ca";
}
.fa-list-ol:before {
  content: "\f0cb";
}
.fa-strikethrough:before {
  content: "\f0cc";
}
.fa-underline:before {
  content: "\f0cd";
}
.fa-table:before {
  content: "\f0ce";
}
.fa-magic:before {
  content: "\f0d0";
}
.fa-truck:before {
  content: "\f0d1";
}
.fa-pinterest:before {
  content: "\f0d2";
}
.fa-pinterest-square:before {
  content: "\f0d3";
}
.fa-google-plus-square:before {
  content: "\f0d4";
}
.fa-google-plus:before {
  content: "\f0d5";
}
.fa-money:before {
  content: "\f0d6";
}
.fa-caret-down:before {
  content: "\f0d7";
}
.fa-caret-up:before {
  content: "\f0d8";
}
.fa-caret-left:before {
  content: "\f0d9";
}
.fa-caret-right:before {
  content: "\f0da";
}
.fa-columns:before {
  content: "\f0db";
}
.fa-unsorted:before,
.fa-sort:before {
  content: "\f0dc";
}
.fa-sort-down:before,
.fa-sort-desc:before {
  content: "\f0dd";
}
.fa-sort-up:before,
.fa-sort-asc:before {
  content: "\f0de";
}
.fa-envelope:before {
  content: "\f0e0";
}
.fa-linkedin:before {
  content: "\f0e1";
}
.fa-rotate-left:before,
.fa-undo:before {
  content: "\f0e2";
}
.fa-legal:before,
.fa-gavel:before {
  content: "\f0e3";
}
.fa-dashboard:before,
.fa-tachometer:before {
  content: "\f0e4";
}
.fa-comment-o:before {
  content: "\f0e5";
}
.fa-comments-o:before {
  content: "\f0e6";
}
.fa-flash:before,
.fa-bolt:before {
  content: "\f0e7";
}
.fa-sitemap:before {
  content: "\f0e8";
}
.fa-umbrella:before {
  content: "\f0e9";
}
.fa-paste:before,
.fa-clipboard:before {
  content: "\f0ea";
}
.fa-lightbulb-o:before {
  content: "\f0eb";
}
.fa-exchange:before {
  content: "\f0ec";
}
.fa-cloud-download:before {
  content: "\f0ed";
}
.fa-cloud-upload:before {
  content: "\f0ee";
}
.fa-user-md:before {
  content: "\f0f0";
}
.fa-stethoscope:before {
  content: "\f0f1";
}
.fa-suitcase:before {
  content: "\f0f2";
}
.fa-bell-o:before {
  content: "\f0a2";
}
.fa-coffee:before {
  content: "\f0f4";
}
.fa-cutlery:before {
  content: "\f0f5";
}
.fa-file-text-o:before {
  content: "\f0f6";
}
.fa-building-o:before {
  content: "\f0f7";
}
.fa-hospital-o:before {
  content: "\f0f8";
}
.fa-ambulance:before {
  content: "\f0f9";
}
.fa-medkit:before {
  content: "\f0fa";
}
.fa-fighter-jet:before {
  content: "\f0fb";
}
.fa-beer:before {
  content: "\f0fc";
}
.fa-h-square:before {
  content: "\f0fd";
}
.fa-plus-square:before {
  content: "\f0fe";
}
.fa-angle-double-left:before {
  content: "\f100";
}
.fa-angle-double-right:before {
  content: "\f101";
}
.fa-angle-double-up:before {
  content: "\f102";
}
.fa-angle-double-down:before {
  content: "\f103";
}
.fa-angle-left:before {
  content: "\f104";
}
.fa-angle-right:before {
  content: "\f105";
}
.fa-angle-up:before {
  content: "\f106";
}
.fa-angle-down:before {
  content: "\f107";
}
.fa-desktop:before {
  content: "\f108";
}
.fa-laptop:before {
  content: "\f109";
}
.fa-tablet:before {
  content: "\f10a";
}
.fa-mobile-phone:before,
.fa-mobile:before {
  content: "\f10b";
}
.fa-circle-o:before {
  content: "\f10c";
}
.fa-quote-left:before {
  content: "\f10d";
}
.fa-quote-right:before {
  content: "\f10e";
}
.fa-spinner:before {
  content: "\f110";
}
.fa-circle:before {
  content: "\f111";
}
.fa-mail-reply:before,
.fa-reply:before {
  content: "\f112";
}
.fa-github-alt:before {
  content: "\f113";
}
.fa-folder-o:before {
  content: "\f114";
}
.fa-folder-open-o:before {
  content: "\f115";
}
.fa-smile-o:before {
  content: "\f118";
}
.fa-frown-o:before {
  content: "\f119";
}
.fa-meh-o:before {
  content: "\f11a";
}
.fa-gamepad:before {
  content: "\f11b";
}
.fa-keyboard-o:before {
  content: "\f11c";
}
.fa-flag-o:before {
  content: "\f11d";
}
.fa-flag-checkered:before {
  content: "\f11e";
}
.fa-terminal:before {
  content: "\f120";
}
.fa-code:before {
  content: "\f121";
}
.fa-mail-reply-all:before,
.fa-reply-all:before {
  content: "\f122";
}
.fa-star-half-empty:before,
.fa-star-half-full:before,
.fa-star-half-o:before {
  content: "\f123";
}
.fa-location-arrow:before {
  content: "\f124";
}
.fa-crop:before {
  content: "\f125";
}
.fa-code-fork:before {
  content: "\f126";
}
.fa-unlink:before,
.fa-chain-broken:before {
  content: "\f127";
}
.fa-question:before {
  content: "\f128";
}
.fa-info:before {
  content: "\f129";
}
.fa-exclamation:before {
  content: "\f12a";
}
.fa-superscript:before {
  content: "\f12b";
}
.fa-subscript:before {
  content: "\f12c";
}
.fa-eraser:before {
  content: "\f12d";
}
.fa-puzzle-piece:before {
  content: "\f12e";
}
.fa-microphone:before {
  content: "\f130";
}
.fa-microphone-slash:before {
  content: "\f131";
}
.fa-shield:before {
  content: "\f132";
}
.fa-calendar-o:before {
  content: "\f133";
}
.fa-fire-extinguisher:before {
  content: "\f134";
}
.fa-rocket:before {
  content: "\f135";
}
.fa-maxcdn:before {
  content: "\f136";
}
.fa-chevron-circle-left:before {
  content: "\f137";
}
.fa-chevron-circle-right:before {
  content: "\f138";
}
.fa-chevron-circle-up:before {
  content: "\f139";
}
.fa-chevron-circle-down:before {
  content: "\f13a";
}
.fa-html5:before {
  content: "\f13b";
}
.fa-css3:before {
  content: "\f13c";
}
.fa-anchor:before {
  content: "\f13d";
}
.fa-unlock-alt:before {
  content: "\f13e";
}
.fa-bullseye:before {
  content: "\f140";
}
.fa-ellipsis-h:before {
  content: "\f141";
}
.fa-ellipsis-v:before {
  content: "\f142";
}
.fa-rss-square:before {
  content: "\f143";
}
.fa-play-circle:before {
  content: "\f144";
}
.fa-ticket:before {
  content: "\f145";
}
.fa-minus-square:before {
  content: "\f146";
}
.fa-minus-square-o:before {
  content: "\f147";
}
.fa-level-up:before {
  content: "\f148";
}
.fa-level-down:before {
  content: "\f149";
}
.fa-check-square:before {
  content: "\f14a";
}
.fa-pencil-square:before {
  content: "\f14b";
}
.fa-external-link-square:before {
  content: "\f14c";
}
.fa-share-square:before {
  content: "\f14d";
}
.fa-compass:before {
  content: "\f14e";
}
.fa-toggle-down:before,
.fa-caret-square-o-down:before {
  content: "\f150";
}
.fa-toggle-up:before,
.fa-caret-square-o-up:before {
  content: "\f151";
}
.fa-toggle-right:before,
.fa-caret-square-o-right:before {
  content: "\f152";
}
.fa-euro:before,
.fa-eur:before {
  content: "\f153";
}
.fa-gbp:before {
  content: "\f154";
}
.fa-dollar:before,
.fa-usd:before {
  content: "\f155";
}
.fa-rupee:before,
.fa-inr:before {
  content: "\f156";
}
.fa-cny:before,
.fa-rmb:before,
.fa-yen:before,
.fa-jpy:before {
  content: "\f157";
}
.fa-ruble:before,
.fa-rouble:before,
.fa-rub:before {
  content: "\f158";
}
.fa-won:before,
.fa-krw:before {
  content: "\f159";
}
.fa-bitcoin:before,
.fa-btc:before {
  content: "\f15a";
}
.fa-file:before {
  content: "\f15b";
}
.fa-file-text:before {
  content: "\f15c";
}
.fa-sort-alpha-asc:before {
  content: "\f15d";
}
.fa-sort-alpha-desc:before {
  content: "\f15e";
}
.fa-sort-amount-asc:before {
  content: "\f160";
}
.fa-sort-amount-desc:before {
  content: "\f161";
}
.fa-sort-numeric-asc:before {
  content: "\f162";
}
.fa-sort-numeric-desc:before {
  content: "\f163";
}
.fa-thumbs-up:before {
  content: "\f164";
}
.fa-thumbs-down:before {
  content: "\f165";
}
.fa-youtube-square:before {
  content: "\f166";
}
.fa-youtube:before {
  content: "\f167";
}
.fa-xing:before {
  content: "\f168";
}
.fa-xing-square:before {
  content: "\f169";
}
.fa-youtube-play:before {
  content: "\f16a";
}
.fa-dropbox:before {
  content: "\f16b";
}
.fa-stack-overflow:before {
  content: "\f16c";
}
.fa-instagram:before {
  content: "\f16d";
}
.fa-flickr:before {
  content: "\f16e";
}
.fa-adn:before {
  content: "\f170";
}
.fa-bitbucket:before {
  content: "\f171";
}
.fa-bitbucket-square:before {
  content: "\f172";
}
.fa-tumblr:before {
  content: "\f173";
}
.fa-tumblr-square:before {
  content: "\f174";
}
.fa-long-arrow-down:before {
  content: "\f175";
}
.fa-long-arrow-up:before {
  content: "\f176";
}
.fa-long-arrow-left:before {
  content: "\f177";
}
.fa-long-arrow-right:before {
  content: "\f178";
}
.fa-apple:before {
  content: "\f179";
}
.fa-windows:before {
  content: "\f17a";
}
.fa-android:before {
  content: "\f17b";
}
.fa-linux:before {
  content: "\f17c";
}
.fa-dribbble:before {
  content: "\f17d";
}
.fa-skype:before {
  content: "\f17e";
}
.fa-foursquare:before {
  content: "\f180";
}
.fa-trello:before {
  content: "\f181";
}
.fa-female:before {
  content: "\f182";
}
.fa-male:before {
  content: "\f183";
}
.fa-gittip:before {
  content: "\f184";
}
.fa-sun-o:before {
  content: "\f185";
}
.fa-moon-o:before {
  content: "\f186";
}
.fa-archive:before {
  content: "\f187";
}
.fa-bug:before {
  content: "\f188";
}
.fa-vk:before {
  content: "\f189";
}
.fa-weibo:before {
  content: "\f18a";
}
.fa-renren:before {
  content: "\f18b";
}
.fa-pagelines:before {
  content: "\f18c";
}
.fa-stack-exchange:before {
  content: "\f18d";
}
.fa-arrow-circle-o-right:before {
  content: "\f18e";
}
.fa-arrow-circle-o-left:before {
  content: "\f190";
}
.fa-toggle-left:before,
.fa-caret-square-o-left:before {
  content: "\f191";
}
.fa-dot-circle-o:before {
  content: "\f192";
}
.fa-wheelchair:before {
  content: "\f193";
}
.fa-vimeo-square:before {
  content: "\f194";
}
.fa-turkish-lira:before,
.fa-try:before {
  content: "\f195";
}
.fa-plus-square-o:before {
  content: "\f196";
}
.fa-space-shuttle:before {
  content: "\f197";
}
.fa-slack:before {
  content: "\f198";
}
.fa-envelope-square:before {
  content: "\f199";
}
.fa-wordpress:before {
  content: "\f19a";
}
.fa-openid:before {
  content: "\f19b";
}
.fa-institution:before,
.fa-bank:before,
.fa-university:before {
  content: "\f19c";
}
.fa-mortar-board:before,
.fa-graduation-cap:before {
  content: "\f19d";
}
.fa-yahoo:before {
  content: "\f19e";
}
.fa-google:before {
  content: "\f1a0";
}
.fa-reddit:before {
  content: "\f1a1";
}
.fa-reddit-square:before {
  content: "\f1a2";
}
.fa-stumbleupon-circle:before {
  content: "\f1a3";
}
.fa-stumbleupon:before {
  content: "\f1a4";
}
.fa-delicious:before {
  content: "\f1a5";
}
.fa-digg:before {
  content: "\f1a6";
}
.fa-pied-piper:before {
  content: "\f1a7";
}
.fa-pied-piper-alt:before {
  content: "\f1a8";
}
.fa-drupal:before {
  content: "\f1a9";
}
.fa-joomla:before {
  content: "\f1aa";
}
.fa-language:before {
  content: "\f1ab";
}
.fa-fax:before {
  content: "\f1ac";
}
.fa-building:before {
  content: "\f1ad";
}
.fa-child:before {
  content: "\f1ae";
}
.fa-paw:before {
  content: "\f1b0";
}
.fa-spoon:before {
  content: "\f1b1";
}
.fa-cube:before {
  content: "\f1b2";
}
.fa-cubes:before {
  content: "\f1b3";
}
.fa-behance:before {
  content: "\f1b4";
}
.fa-behance-square:before {
  content: "\f1b5";
}
.fa-steam:before {
  content: "\f1b6";
}
.fa-steam-square:before {
  content: "\f1b7";
}
.fa-recycle:before {
  content: "\f1b8";
}
.fa-automobile:before,
.fa-car:before {
  content: "\f1b9";
}
.fa-cab:before,
.fa-taxi:before {
  content: "\f1ba";
}
.fa-tree:before {
  content: "\f1bb";
}
.fa-spotify:before {
  content: "\f1bc";
}
.fa-deviantart:before {
  content: "\f1bd";
}
.fa-soundcloud:before {
  content: "\f1be";
}
.fa-database:before {
  content: "\f1c0";
}
.fa-file-pdf-o:before {
  content: "\f1c1";
}
.fa-file-word-o:before {
  content: "\f1c2";
}
.fa-file-excel-o:before {
  content: "\f1c3";
}
.fa-file-powerpoint-o:before {
  content: "\f1c4";
}
.fa-file-photo-o:before,
.fa-file-picture-o:before,
.fa-file-image-o:before {
  content: "\f1c5";
}
.fa-file-zip-o:before,
.fa-file-archive-o:before {
  content: "\f1c6";
}
.fa-file-sound-o:before,
.fa-file-audio-o:before {
  content: "\f1c7";
}
.fa-file-movie-o:before,
.fa-file-video-o:before {
  content: "\f1c8";
}
.fa-file-code-o:before {
  content: "\f1c9";
}
.fa-vine:before {
  content: "\f1ca";
}
.fa-codepen:before {
  content: "\f1cb";
}
.fa-jsfiddle:before {
  content: "\f1cc";
}
.fa-life-bouy:before,
.fa-life-buoy:before,
.fa-life-saver:before,
.fa-support:before,
.fa-life-ring:before {
  content: "\f1cd";
}
.fa-circle-o-notch:before {
  content: "\f1ce";
}
.fa-ra:before,
.fa-rebel:before {
  content: "\f1d0";
}
.fa-ge:before,
.fa-empire:before {
  content: "\f1d1";
}
.fa-git-square:before {
  content: "\f1d2";
}
.fa-git:before {
  content: "\f1d3";
}
.fa-hacker-news:before {
  content: "\f1d4";
}
.fa-tencent-weibo:before {
  content: "\f1d5";
}
.fa-qq:before {
  content: "\f1d6";
}
.fa-wechat:before,
.fa-weixin:before {
  content: "\f1d7";
}
.fa-send:before,
.fa-paper-plane:before {
  content: "\f1d8";
}
.fa-send-o:before,
.fa-paper-plane-o:before {
  content: "\f1d9";
}
.fa-history:before {
  content: "\f1da";
}
.fa-circle-thin:before {
  content: "\f1db";
}
.fa-header:before {
  content: "\f1dc";
}
.fa-paragraph:before {
  content: "\f1dd";
}
.fa-sliders:before {
  content: "\f1de";
}
.fa-share-alt:before {
  content: "\f1e0";
}
.fa-share-alt-square:before {
  content: "\f1e1";
}
.fa-bomb:before {
  content: "\f1e2";
}
.fa-soccer-ball-o:before,
.fa-futbol-o:before {
  content: "\f1e3";
}
.fa-tty:before {
  content: "\f1e4";
}
.fa-binoculars:before {
  content: "\f1e5";
}
.fa-plug:before {
  content: "\f1e6";
}
.fa-slideshare:before {
  content: "\f1e7";
}
.fa-twitch:before {
  content: "\f1e8";
}
.fa-yelp:before {
  content: "\f1e9";
}
.fa-newspaper-o:before {
  content: "\f1ea";
}
.fa-wifi:before {
  content: "\f1eb";
}
.fa-calculator:before {
  content: "\f1ec";
}
.fa-paypal:before {
  content: "\f1ed";
}
.fa-google-wallet:before {
  content: "\f1ee";
}
.fa-cc-visa:before {
  content: "\f1f0";
}
.fa-cc-mastercard:before {
  content: "\f1f1";
}
.fa-cc-discover:before {
  content: "\f1f2";
}
.fa-cc-amex:before {
  content: "\f1f3";
}
.fa-cc-paypal:before {
  content: "\f1f4";
}
.fa-cc-stripe:before {
  content: "\f1f5";
}
.fa-bell-slash:before {
  content: "\f1f6";
}
.fa-bell-slash-o:before {
  content: "\f1f7";
}
.fa-trash:before {
  content: "\f1f8";
}
.fa-copyright:before {
  content: "\f1f9";
}
.fa-at:before {
  content: "\f1fa";
}
.fa-eyedropper:before {
  content: "\f1fb";
}
.fa-paint-brush:before {
  content: "\f1fc";
}
.fa-birthday-cake:before {
  content: "\f1fd";
}
.fa-area-chart:before {
  content: "\f1fe";
}
.fa-pie-chart:before {
  content: "\f200";
}
.fa-line-chart:before {
  content: "\f201";
}
.fa-lastfm:before {
  content: "\f202";
}
.fa-lastfm-square:before {
  content: "\f203";
}
.fa-toggle-off:before {
  content: "\f204";
}
.fa-toggle-on:before {
  content: "\f205";
}
.fa-bicycle:before {
  content: "\f206";
}
.fa-bus:before {
  content: "\f207";
}
.fa-ioxhost:before {
  content: "\f208";
}
.fa-angellist:before {
  content: "\f209";
}
.fa-cc:before {
  content: "\f20a";
}
.fa-shekel:before,
.fa-sheqel:before,
.fa-ils:before {
  content: "\f20b";
}
.fa-meanpath:before {
  content: "\f20c";
}
/*!
*
* IPython base
*
*/
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
code {
  color: #000;
}
pre {
  font-size: inherit;
  line-height: inherit;
}
label {
  font-weight: normal;
}
/* Make the page background atleast 100% the height of the view port */
/* Make the page itself atleast 70% the height of the view port */
.border-box-sizing {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.corner-all {
  border-radius: 2px;
}
.no-padding {
  padding: 0px;
}
/* Flexible box model classes */
/* Taken from Alex Russell http://infrequently.org/2009/08/css-3-progress/ */
/* This file is a compatability layer.  It allows the usage of flexible box 
model layouts accross multiple browsers, including older browsers.  The newest,
universal implementation of the flexible box model is used when available (see
`Modern browsers` comments below).  Browsers that are known to implement this 
new spec completely include:

    Firefox 28.0+
    Chrome 29.0+
    Internet Explorer 11+ 
    Opera 17.0+

Browsers not listed, including Safari, are supported via the styling under the
`Old browsers` comments below.
*/
.hbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
.hbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.vbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
.vbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.hbox.reverse,
.vbox.reverse,
.reverse {
  /* Old browsers */
  -webkit-box-direction: reverse;
  -moz-box-direction: reverse;
  box-direction: reverse;
  /* Modern browsers */
  flex-direction: row-reverse;
}
.hbox.box-flex0,
.vbox.box-flex0,
.box-flex0 {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
  width: auto;
}
.hbox.box-flex1,
.vbox.box-flex1,
.box-flex1 {
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex,
.vbox.box-flex,
.box-flex {
  /* Old browsers */
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex2,
.vbox.box-flex2,
.box-flex2 {
  /* Old browsers */
  -webkit-box-flex: 2;
  -moz-box-flex: 2;
  box-flex: 2;
  /* Modern browsers */
  flex: 2;
}
.box-group1 {
  /*  Deprecated */
  -webkit-box-flex-group: 1;
  -moz-box-flex-group: 1;
  box-flex-group: 1;
}
.box-group2 {
  /* Deprecated */
  -webkit-box-flex-group: 2;
  -moz-box-flex-group: 2;
  box-flex-group: 2;
}
.hbox.start,
.vbox.start,
.start {
  /* Old browsers */
  -webkit-box-pack: start;
  -moz-box-pack: start;
  box-pack: start;
  /* Modern browsers */
  justify-content: flex-start;
}
.hbox.end,
.vbox.end,
.end {
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
}
.hbox.center,
.vbox.center,
.center {
  /* Old browsers */
  -webkit-box-pack: center;
  -moz-box-pack: center;
  box-pack: center;
  /* Modern browsers */
  justify-content: center;
}
.hbox.baseline,
.vbox.baseline,
.baseline {
  /* Old browsers */
  -webkit-box-pack: baseline;
  -moz-box-pack: baseline;
  box-pack: baseline;
  /* Modern browsers */
  justify-content: baseline;
}
.hbox.stretch,
.vbox.stretch,
.stretch {
  /* Old browsers */
  -webkit-box-pack: stretch;
  -moz-box-pack: stretch;
  box-pack: stretch;
  /* Modern browsers */
  justify-content: stretch;
}
.hbox.align-start,
.vbox.align-start,
.align-start {
  /* Old browsers */
  -webkit-box-align: start;
  -moz-box-align: start;
  box-align: start;
  /* Modern browsers */
  align-items: flex-start;
}
.hbox.align-end,
.vbox.align-end,
.align-end {
  /* Old browsers */
  -webkit-box-align: end;
  -moz-box-align: end;
  box-align: end;
  /* Modern browsers */
  align-items: flex-end;
}
.hbox.align-center,
.vbox.align-center,
.align-center {
  /* Old browsers */
  -webkit-box-align: center;
  -moz-box-align: center;
  box-align: center;
  /* Modern browsers */
  align-items: center;
}
.hbox.align-baseline,
.vbox.align-baseline,
.align-baseline {
  /* Old browsers */
  -webkit-box-align: baseline;
  -moz-box-align: baseline;
  box-align: baseline;
  /* Modern browsers */
  align-items: baseline;
}
.hbox.align-stretch,
.vbox.align-stretch,
.align-stretch {
  /* Old browsers */
  -webkit-box-align: stretch;
  -moz-box-align: stretch;
  box-align: stretch;
  /* Modern browsers */
  align-items: stretch;
}
div.error {
  margin: 2em;
  text-align: center;
}
div.error > h1 {
  font-size: 500%;
  line-height: normal;
}
div.error > p {
  font-size: 200%;
  line-height: normal;
}
div.traceback-wrapper {
  text-align: left;
  max-width: 800px;
  margin: auto;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
body {
  background-color: #fff;
  /* This makes sure that the body covers the entire window and needs to
       be in a different element than the display: box in wrapper below */
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  overflow: visible;
}
body > #header {
  /* Initially hidden to prevent FLOUC */
  display: none;
  background-color: #fff;
  /* Display over codemirror */
  position: relative;
  z-index: 100;
}
body > #header #header-container {
  padding-bottom: 5px;
  padding-top: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
body > #header .header-bar {
  width: 100%;
  height: 1px;
  background: #e7e7e7;
  margin-bottom: -1px;
}
@media print {
  body > #header {
    display: none !important;
  }
}
#header-spacer {
  width: 100%;
  visibility: hidden;
}
@media print {
  #header-spacer {
    display: none;
  }
}
#ipython_notebook {
  padding-left: 0px;
  padding-top: 1px;
  padding-bottom: 1px;
}
@media (max-width: 991px) {
  #ipython_notebook {
    margin-left: 10px;
  }
}
[dir="rtl"] #ipython_notebook {
  float: right !important;
}
#noscript {
  width: auto;
  padding-top: 16px;
  padding-bottom: 16px;
  text-align: center;
  font-size: 22px;
  color: red;
  font-weight: bold;
}
#ipython_notebook img {
  height: 28px;
}
#site {
  width: 100%;
  display: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  overflow: auto;
}
@media print {
  #site {
    height: auto !important;
  }
}
/* Smaller buttons */
.ui-button .ui-button-text {
  padding: 0.2em 0.8em;
  font-size: 77%;
}
input.ui-button {
  padding: 0.3em 0.9em;
}
span#login_widget {
  float: right;
}
span#login_widget > .button,
#logout {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button:focus,
#logout:focus,
span#login_widget > .button.focus,
#logout.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
span#login_widget > .button:hover,
#logout:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active:hover,
#logout:active:hover,
span#login_widget > .button.active:hover,
#logout.active:hover,
.open > .dropdown-togglespan#login_widget > .button:hover,
.open > .dropdown-toggle#logout:hover,
span#login_widget > .button:active:focus,
#logout:active:focus,
span#login_widget > .button.active:focus,
#logout.active:focus,
.open > .dropdown-togglespan#login_widget > .button:focus,
.open > .dropdown-toggle#logout:focus,
span#login_widget > .button:active.focus,
#logout:active.focus,
span#login_widget > .button.active.focus,
#logout.active.focus,
.open > .dropdown-togglespan#login_widget > .button.focus,
.open > .dropdown-toggle#logout.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  background-image: none;
}
span#login_widget > .button.disabled:hover,
#logout.disabled:hover,
span#login_widget > .button[disabled]:hover,
#logout[disabled]:hover,
fieldset[disabled] span#login_widget > .button:hover,
fieldset[disabled] #logout:hover,
span#login_widget > .button.disabled:focus,
#logout.disabled:focus,
span#login_widget > .button[disabled]:focus,
#logout[disabled]:focus,
fieldset[disabled] span#login_widget > .button:focus,
fieldset[disabled] #logout:focus,
span#login_widget > .button.disabled.focus,
#logout.disabled.focus,
span#login_widget > .button[disabled].focus,
#logout[disabled].focus,
fieldset[disabled] span#login_widget > .button.focus,
fieldset[disabled] #logout.focus {
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button .badge,
#logout .badge {
  color: #fff;
  background-color: #333;
}
.nav-header {
  text-transform: none;
}
#header > span {
  margin-top: 10px;
}
.modal_stretch .modal-dialog {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  min-height: 80vh;
}
.modal_stretch .modal-dialog .modal-body {
  max-height: calc(100vh - 200px);
  overflow: auto;
  flex: 1;
}
@media (min-width: 768px) {
  .modal .modal-dialog {
    width: 700px;
  }
}
@media (min-width: 768px) {
  select.form-control {
    margin-left: 12px;
    margin-right: 12px;
  }
}
/*!
*
* IPython auth
*
*/
.center-nav {
  display: inline-block;
  margin-bottom: -4px;
}
/*!
*
* IPython tree view
*
*/
/* We need an invisible input field on top of the sentense*/
/* "Drag file onto the list ..." */
.alternate_upload {
  background-color: none;
  display: inline;
}
.alternate_upload.form {
  padding: 0;
  margin: 0;
}
.alternate_upload input.fileinput {
  text-align: center;
  vertical-align: middle;
  display: inline;
  opacity: 0;
  z-index: 2;
  width: 12ex;
  margin-right: -12ex;
}
.alternate_upload .btn-upload {
  height: 22px;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
[dir="rtl"] #tabs li {
  float: right;
}
ul#tabs {
  margin-bottom: 4px;
}
[dir="rtl"] ul#tabs {
  margin-right: 0px;
}
ul#tabs a {
  padding-top: 6px;
  padding-bottom: 4px;
}
ul.breadcrumb a:focus,
ul.breadcrumb a:hover {
  text-decoration: none;
}
ul.breadcrumb i.icon-home {
  font-size: 16px;
  margin-right: 4px;
}
ul.breadcrumb span {
  color: #5e5e5e;
}
.list_toolbar {
  padding: 4px 0 4px 0;
  vertical-align: middle;
}
.list_toolbar .tree-buttons {
  padding-top: 1px;
}
[dir="rtl"] .list_toolbar .tree-buttons {
  float: left !important;
}
[dir="rtl"] .list_toolbar .pull-right {
  padding-top: 1px;
  float: left !important;
}
[dir="rtl"] .list_toolbar .pull-left {
  float: right !important;
}
.dynamic-buttons {
  padding-top: 3px;
  display: inline-block;
}
.list_toolbar [class*="span"] {
  min-height: 24px;
}
.list_header {
  font-weight: bold;
  background-color: #EEE;
}
.list_placeholder {
  font-weight: bold;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
}
.list_container {
  margin-top: 4px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 2px;
}
.list_container > div {
  border-bottom: 1px solid #ddd;
}
.list_container > div:hover .list-item {
  background-color: red;
}
.list_container > div:last-child {
  border: none;
}
.list_item:hover .list_item {
  background-color: #ddd;
}
.list_item a {
  text-decoration: none;
}
.list_item:hover {
  background-color: #fafafa;
}
.list_header > div,
.list_item > div {
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
.list_header > div input,
.list_item > div input {
  margin-right: 7px;
  margin-left: 14px;
  vertical-align: baseline;
  line-height: 22px;
  position: relative;
  top: -1px;
}
.list_header > div .item_link,
.list_item > div .item_link {
  margin-left: -1px;
  vertical-align: baseline;
  line-height: 22px;
}
.new-file input[type=checkbox] {
  visibility: hidden;
}
.item_name {
  line-height: 22px;
  height: 24px;
}
.item_icon {
  font-size: 14px;
  color: #5e5e5e;
  margin-right: 7px;
  margin-left: 7px;
  line-height: 22px;
  vertical-align: baseline;
}
.item_buttons {
  line-height: 1em;
  margin-left: -5px;
}
.item_buttons .btn,
.item_buttons .btn-group,
.item_buttons .input-group {
  float: left;
}
.item_buttons > .btn,
.item_buttons > .btn-group,
.item_buttons > .input-group {
  margin-left: 5px;
}
.item_buttons .btn {
  min-width: 13ex;
}
.item_buttons .running-indicator {
  padding-top: 4px;
  color: #5cb85c;
}
.item_buttons .kernel-name {
  padding-top: 4px;
  color: #5bc0de;
  margin-right: 7px;
  float: left;
}
.toolbar_info {
  height: 24px;
  line-height: 24px;
}
.list_item input:not([type=checkbox]) {
  padding-top: 3px;
  padding-bottom: 3px;
  height: 22px;
  line-height: 14px;
  margin: 0px;
}
.highlight_text {
  color: blue;
}
#project_name {
  display: inline-block;
  padding-left: 7px;
  margin-left: -2px;
}
#project_name > .breadcrumb {
  padding: 0px;
  margin-bottom: 0px;
  background-color: transparent;
  font-weight: bold;
}
#tree-selector {
  padding-right: 0px;
}
[dir="rtl"] #tree-selector a {
  float: right;
}
#button-select-all {
  min-width: 50px;
}
#select-all {
  margin-left: 7px;
  margin-right: 2px;
}
.menu_icon {
  margin-right: 2px;
}
.tab-content .row {
  margin-left: 0px;
  margin-right: 0px;
}
.folder_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f114";
}
.folder_icon:before.pull-left {
  margin-right: .3em;
}
.folder_icon:before.pull-right {
  margin-left: .3em;
}
.notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
}
.notebook_icon:before.pull-left {
  margin-right: .3em;
}
.notebook_icon:before.pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
  color: #5cb85c;
}
.running_notebook_icon:before.pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.pull-right {
  margin-left: .3em;
}
.file_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f016";
  position: relative;
  top: -2px;
}
.file_icon:before.pull-left {
  margin-right: .3em;
}
.file_icon:before.pull-right {
  margin-left: .3em;
}
#notebook_toolbar .pull-right {
  padding-top: 0px;
  margin-right: -1px;
}
ul#new-menu {
  left: auto;
  right: 0;
}
[dir="rtl"] #new-menu {
  text-align: right;
}
.kernel-menu-icon {
  padding-right: 12px;
  width: 24px;
  content: "\f096";
}
.kernel-menu-icon:before {
  content: "\f096";
}
.kernel-menu-icon-current:before {
  content: "\f00c";
}
#tab_content {
  padding-top: 20px;
}
#running .panel-group .panel {
  margin-top: 3px;
  margin-bottom: 1em;
}
#running .panel-group .panel .panel-heading {
  background-color: #EEE;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
#running .panel-group .panel .panel-heading a:focus,
#running .panel-group .panel .panel-heading a:hover {
  text-decoration: none;
}
#running .panel-group .panel .panel-body {
  padding: 0px;
}
#running .panel-group .panel .panel-body .list_container {
  margin-top: 0px;
  margin-bottom: 0px;
  border: 0px;
  border-radius: 0px;
}
#running .panel-group .panel .panel-body .list_container .list_item {
  border-bottom: 1px solid #ddd;
}
#running .panel-group .panel .panel-body .list_container .list_item:last-child {
  border-bottom: 0px;
}
[dir="rtl"] #running .col-sm-8 {
  float: right !important;
}
.delete-button {
  display: none;
}
.duplicate-button {
  display: none;
}
.rename-button {
  display: none;
}
.shutdown-button {
  display: none;
}
.dynamic-instructions {
  display: inline-block;
  padding-top: 4px;
}
/*!
*
* IPython text editor webapp
*
*/
.selected-keymap i.fa {
  padding: 0px 5px;
}
.selected-keymap i.fa:before {
  content: "\f00c";
}
#mode-menu {
  overflow: auto;
  max-height: 20em;
}
.edit_app #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.edit_app #menubar .navbar {
  /* Use a negative 1 bottom margin, so the border overlaps the border of the
    header */
  margin-bottom: -1px;
}
.dirty-indicator {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator.pull-left {
  margin-right: .3em;
}
.dirty-indicator.pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-dirty.pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-clean.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f00c";
}
.dirty-indicator-clean:before.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.pull-right {
  margin-left: .3em;
}
#filename {
  font-size: 16pt;
  display: table;
  padding: 0px 5px;
}
#current-mode {
  padding-left: 5px;
  padding-right: 5px;
}
#texteditor-backdrop {
  padding-top: 20px;
  padding-bottom: 20px;
}
@media not print {
  #texteditor-backdrop {
    background-color: #EEE;
  }
}
@media print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container {
    padding: 0px;
    background-color: #fff;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
/*!
*
* IPython notebook
*
*/
/* CSS font colors for translated ANSI colors. */
.ansibold {
  font-weight: bold;
}
/* use dark versions for foreground, to improve visibility */
.ansiblack {
  color: black;
}
.ansired {
  color: darkred;
}
.ansigreen {
  color: darkgreen;
}
.ansiyellow {
  color: #c4a000;
}
.ansiblue {
  color: darkblue;
}
.ansipurple {
  color: darkviolet;
}
.ansicyan {
  color: steelblue;
}
.ansigray {
  color: gray;
}
/* and light for background, for the same reason */
.ansibgblack {
  background-color: black;
}
.ansibgred {
  background-color: red;
}
.ansibggreen {
  background-color: green;
}
.ansibgyellow {
  background-color: yellow;
}
.ansibgblue {
  background-color: blue;
}
.ansibgpurple {
  background-color: magenta;
}
.ansibgcyan {
  background-color: cyan;
}
.ansibggray {
  background-color: gray;
}
div.cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-radius: 2px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border-width: 1px;
  border-style: solid;
  border-color: transparent;
  width: 100%;
  padding: 5px;
  /* This acts as a spacer between cells, that is outside the border */
  margin: 0px;
  outline: none;
  border-left-width: 1px;
  padding-left: 5px;
  background: linear-gradient(to right, transparent -40px, transparent 1px, transparent 1px, transparent 100%);
}
div.cell.jupyter-soft-selected {
  border-left-color: #90CAF9;
  border-left-color: #E3F2FD;
  border-left-width: 1px;
  padding-left: 5px;
  border-right-color: #E3F2FD;
  border-right-width: 1px;
  background: #E3F2FD;
}
@media print {
  div.cell.jupyter-soft-selected {
    border-color: transparent;
  }
}
div.cell.selected {
  border-color: #ababab;
  border-left-width: 0px;
  padding-left: 6px;
  background: linear-gradient(to right, #42A5F5 -40px, #42A5F5 5px, transparent 5px, transparent 100%);
}
@media print {
  div.cell.selected {
    border-color: transparent;
  }
}
div.cell.selected.jupyter-soft-selected {
  border-left-width: 0;
  padding-left: 6px;
  background: linear-gradient(to right, #42A5F5 -40px, #42A5F5 7px, #E3F2FD 7px, #E3F2FD 100%);
}
.edit_mode div.cell.selected {
  border-color: #66BB6A;
  border-left-width: 0px;
  padding-left: 6px;
  background: linear-gradient(to right, #66BB6A -40px, #66BB6A 5px, transparent 5px, transparent 100%);
}
@media print {
  .edit_mode div.cell.selected {
    border-color: transparent;
  }
}
.prompt {
  /* This needs to be wide enough for 3 digit prompt numbers: In[100]: */
  min-width: 14ex;
  /* This padding is tuned to match the padding on the CodeMirror editor. */
  padding: 0.4em;
  margin: 0px;
  font-family: monospace;
  text-align: right;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
  /* Don't highlight prompt number selection */
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  /* Use default cursor */
  cursor: default;
}
@media (max-width: 540px) {
  .prompt {
    text-align: left;
  }
}
div.inner_cell {
  min-width: 0;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_area {
  border: 1px solid #cfcfcf;
  border-radius: 2px;
  background: #f7f7f7;
  line-height: 1.21429em;
}
/* This is needed so that empty prompt areas can collapse to zero height when there
   is no content in the output_subarea and the prompt. The main purpose of this is
   to make sure that empty JavaScript output_subareas have no height. */
div.prompt:empty {
  padding-top: 0;
  padding-bottom: 0;
}
div.unrecognized_cell {
  padding: 5px 5px 5px 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.unrecognized_cell .inner_cell {
  border-radius: 2px;
  padding: 5px;
  font-weight: bold;
  color: red;
  border: 1px solid #cfcfcf;
  background: #eaeaea;
}
div.unrecognized_cell .inner_cell a {
  color: inherit;
  text-decoration: none;
}
div.unrecognized_cell .inner_cell a:hover {
  color: inherit;
  text-decoration: none;
}
@media (max-width: 540px) {
  div.unrecognized_cell > div.prompt {
    display: none;
  }
}
div.code_cell {
  /* avoid page breaking on code cells when printing */
}
@media print {
  div.code_cell {
    page-break-inside: avoid;
  }
}
/* any special styling for code cells that are currently running goes here */
div.input {
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.input {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_prompt {
  color: #303F9F;
  border-top: 1px solid transparent;
}
div.input_area > div.highlight {
  margin: 0.4em;
  border: none;
  padding: 0px;
  background-color: transparent;
}
div.input_area > div.highlight > pre {
  margin: 0px;
  border: none;
  padding: 0px;
  background-color: transparent;
}
/* The following gets added to the <head> if it is detected that the user has a
 * monospace font with inconsistent normal/bold/italic height.  See
 * notebookmain.js.  Such fonts will have keywords vertically offset with
 * respect to the rest of the text.  The user should select a better font.
 * See: https://github.com/ipython/ipython/issues/1503
 *
 * .CodeMirror span {
 *      vertical-align: bottom;
 * }
 */
.CodeMirror {
  line-height: 1.21429em;
  /* Changed from 1em to our global default */
  font-size: 14px;
  height: auto;
  /* Changed to auto to autogrow */
  background: none;
  /* Changed from white to allow our bg to show through */
}
.CodeMirror-scroll {
  /*  The CodeMirror docs are a bit fuzzy on if overflow-y should be hidden or visible.*/
  /*  We have found that if it is visible, vertical scrollbars appear with font size changes.*/
  overflow-y: hidden;
  overflow-x: auto;
}
.CodeMirror-lines {
  /* In CM2, this used to be 0.4em, but in CM3 it went to 4px. We need the em value because */
  /* we have set a different line-height and want this to scale with that. */
  padding: 0.4em;
}
.CodeMirror-linenumber {
  padding: 0 8px 0 4px;
}
.CodeMirror-gutters {
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.CodeMirror pre {
  /* In CM3 this went to 4px from 0 in CM2. We need the 0 value because of how we size */
  /* .CodeMirror-lines */
  padding: 0;
  border: 0;
  border-radius: 0;
}
/*

Original style from softwaremaniacs.org (c) Ivan Sagalaev <Maniac@SoftwareManiacs.Org>
Adapted from GitHub theme

*/
.highlight-base {
  color: #000;
}
.highlight-variable {
  color: #000;
}
.highlight-variable-2 {
  color: #1a1a1a;
}
.highlight-variable-3 {
  color: #333333;
}
.highlight-string {
  color: #BA2121;
}
.highlight-comment {
  color: #408080;
  font-style: italic;
}
.highlight-number {
  color: #080;
}
.highlight-atom {
  color: #88F;
}
.highlight-keyword {
  color: #008000;
  font-weight: bold;
}
.highlight-builtin {
  color: #008000;
}
.highlight-error {
  color: #f00;
}
.highlight-operator {
  color: #AA22FF;
  font-weight: bold;
}
.highlight-meta {
  color: #AA22FF;
}
/* previously not defined, copying from default codemirror */
.highlight-def {
  color: #00f;
}
.highlight-string-2 {
  color: #f50;
}
.highlight-qualifier {
  color: #555;
}
.highlight-bracket {
  color: #997;
}
.highlight-tag {
  color: #170;
}
.highlight-attribute {
  color: #00c;
}
.highlight-header {
  color: blue;
}
.highlight-quote {
  color: #090;
}
.highlight-link {
  color: #00c;
}
/* apply the same style to codemirror */
.cm-s-ipython span.cm-keyword {
  color: #008000;
  font-weight: bold;
}
.cm-s-ipython span.cm-atom {
  color: #88F;
}
.cm-s-ipython span.cm-number {
  color: #080;
}
.cm-s-ipython span.cm-def {
  color: #00f;
}
.cm-s-ipython span.cm-variable {
  color: #000;
}
.cm-s-ipython span.cm-operator {
  color: #AA22FF;
  font-weight: bold;
}
.cm-s-ipython span.cm-variable-2 {
  color: #1a1a1a;
}
.cm-s-ipython span.cm-variable-3 {
  color: #333333;
}
.cm-s-ipython span.cm-comment {
  color: #408080;
  font-style: italic;
}
.cm-s-ipython span.cm-string {
  color: #BA2121;
}
.cm-s-ipython span.cm-string-2 {
  color: #f50;
}
.cm-s-ipython span.cm-meta {
  color: #AA22FF;
}
.cm-s-ipython span.cm-qualifier {
  color: #555;
}
.cm-s-ipython span.cm-builtin {
  color: #008000;
}
.cm-s-ipython span.cm-bracket {
  color: #997;
}
.cm-s-ipython span.cm-tag {
  color: #170;
}
.cm-s-ipython span.cm-attribute {
  color: #00c;
}
.cm-s-ipython span.cm-header {
  color: blue;
}
.cm-s-ipython span.cm-quote {
  color: #090;
}
.cm-s-ipython span.cm-link {
  color: #00c;
}
.cm-s-ipython span.cm-error {
  color: #f00;
}
.cm-s-ipython span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}
div.output_wrapper {
  /* this position must be relative to enable descendents to be absolute within it */
  position: relative;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  z-index: 1;
}
/* class for the output area when it should be height-limited */
div.output_scroll {
  /* ideally, this would be max-height, but FF barfs all over that */
  height: 24em;
  /* FF needs this *and the wrapper* to specify full width, or it will shrinkwrap */
  width: 100%;
  overflow: auto;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  display: block;
}
/* output div while it is collapsed */
div.output_collapsed {
  margin: 0px;
  padding: 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
div.out_prompt_overlay {
  height: 100%;
  padding: 0px 0.4em;
  position: absolute;
  border-radius: 2px;
}
div.out_prompt_overlay:hover {
  /* use inner shadow to get border that is computed the same on WebKit/FF */
  -webkit-box-shadow: inset 0 0 1px #000;
  box-shadow: inset 0 0 1px #000;
  background: rgba(240, 240, 240, 0.5);
}
div.output_prompt {
  color: #D84315;
}
/* This class is the outer container of all output sections. */
div.output_area {
  padding: 0px;
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.output_area .MathJax_Display {
  text-align: left !important;
}
div.output_area .rendered_html table {
  margin-left: 0;
  margin-right: 0;
}
div.output_area .rendered_html img {
  margin-left: 0;
  margin-right: 0;
}
div.output_area img,
div.output_area svg {
  max-width: 100%;
  height: auto;
}
div.output_area img.unconfined,
div.output_area svg.unconfined {
  max-width: none;
}
/* This is needed to protect the pre formating from global settings such
   as that of bootstrap */
.output {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.output_area {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
div.output_area pre {
  margin: 0;
  padding: 0;
  border: 0;
  vertical-align: baseline;
  color: black;
  background-color: transparent;
  border-radius: 0;
}
/* This class is for the output subarea inside the output_area and after
   the prompt div. */
div.output_subarea {
  overflow-x: auto;
  padding: 0.4em;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
  max-width: calc(100% - 14ex);
}
div.output_scroll div.output_subarea {
  overflow-x: visible;
}
/* The rest of the output_* classes are for special styling of the different
   output types */
/* all text output has this class: */
div.output_text {
  text-align: left;
  color: #000;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
}
/* stdout/stderr are 'text' as well as 'stream', but execute_result/error are *not* streams */
div.output_stderr {
  background: #fdd;
  /* very light red background for stderr */
}
div.output_latex {
  text-align: left;
}
/* Empty output_javascript divs should have no height */
div.output_javascript:empty {
  padding: 0;
}
.js-error {
  color: darkred;
}
/* raw_input styles */
div.raw_input_container {
  line-height: 1.21429em;
  padding-top: 5px;
}
pre.raw_input_prompt {
  /* nothing needed here. */
}
input.raw_input {
  font-family: monospace;
  font-size: inherit;
  color: inherit;
  width: auto;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
}
input.raw_input:focus {
  box-shadow: none;
}
p.p-space {
  margin-bottom: 10px;
}
div.output_unrecognized {
  padding: 5px;
  font-weight: bold;
  color: red;
}
div.output_unrecognized a {
  color: inherit;
  text-decoration: none;
}
div.output_unrecognized a:hover {
  color: inherit;
  text-decoration: none;
}
.rendered_html {
  color: #000;
  /* any extras will just be numbers: */
}
.rendered_html em {
  font-style: italic;
}
.rendered_html strong {
  font-weight: bold;
}
.rendered_html u {
  text-decoration: underline;
}
.rendered_html :link {
  text-decoration: underline;
}
.rendered_html :visited {
  text-decoration: underline;
}
.rendered_html h1 {
  font-size: 185.7%;
  margin: 1.08em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h2 {
  font-size: 157.1%;
  margin: 1.27em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h3 {
  font-size: 128.6%;
  margin: 1.55em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h4 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h5 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h6 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h1:first-child {
  margin-top: 0.538em;
}
.rendered_html h2:first-child {
  margin-top: 0.636em;
}
.rendered_html h3:first-child {
  margin-top: 0.777em;
}
.rendered_html h4:first-child {
  margin-top: 1em;
}
.rendered_html h5:first-child {
  margin-top: 1em;
}
.rendered_html h6:first-child {
  margin-top: 1em;
}
.rendered_html ul {
  list-style: disc;
  margin: 0em 2em;
  padding-left: 0px;
}
.rendered_html ul ul {
  list-style: square;
  margin: 0em 2em;
}
.rendered_html ul ul ul {
  list-style: circle;
  margin: 0em 2em;
}
.rendered_html ol {
  list-style: decimal;
  margin: 0em 2em;
  padding-left: 0px;
}
.rendered_html ol ol {
  list-style: upper-alpha;
  margin: 0em 2em;
}
.rendered_html ol ol ol {
  list-style: lower-alpha;
  margin: 0em 2em;
}
.rendered_html ol ol ol ol {
  list-style: lower-roman;
  margin: 0em 2em;
}
.rendered_html ol ol ol ol ol {
  list-style: decimal;
  margin: 0em 2em;
}
.rendered_html * + ul {
  margin-top: 1em;
}
.rendered_html * + ol {
  margin-top: 1em;
}
.rendered_html hr {
  color: black;
  background-color: black;
}
.rendered_html pre {
  margin: 1em 2em;
}
.rendered_html pre,
.rendered_html code {
  border: 0;
  background-color: #fff;
  color: #000;
  font-size: 100%;
  padding: 0px;
}
.rendered_html blockquote {
  margin: 1em 2em;
}
.rendered_html table {
  margin-left: auto;
  margin-right: auto;
  border: 1px solid black;
  border-collapse: collapse;
}
.rendered_html tr,
.rendered_html th,
.rendered_html td {
  border: 1px solid black;
  border-collapse: collapse;
  margin: 1em 2em;
}
.rendered_html td,
.rendered_html th {
  text-align: left;
  vertical-align: middle;
  padding: 4px;
}
.rendered_html th {
  font-weight: bold;
}
.rendered_html * + table {
  margin-top: 1em;
}
.rendered_html p {
  text-align: left;
}
.rendered_html * + p {
  margin-top: 1em;
}
.rendered_html img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.rendered_html * + img {
  margin-top: 1em;
}
.rendered_html img,
.rendered_html svg {
  max-width: 100%;
  height: auto;
}
.rendered_html img.unconfined,
.rendered_html svg.unconfined {
  max-width: none;
}
div.text_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.text_cell > div.prompt {
    display: none;
  }
}
div.text_cell_render {
  /*font-family: "Helvetica Neue", Arial, Helvetica, Geneva, sans-serif;*/
  outline: none;
  resize: none;
  width: inherit;
  border-style: none;
  padding: 0.5em 0.5em 0.5em 0.4em;
  color: #000;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
a.anchor-link:link {
  text-decoration: none;
  padding: 0px 20px;
  visibility: hidden;
}
h1:hover .anchor-link,
h2:hover .anchor-link,
h3:hover .anchor-link,
h4:hover .anchor-link,
h5:hover .anchor-link,
h6:hover .anchor-link {
  visibility: visible;
}
.text_cell.rendered .input_area {
  display: none;
}
.text_cell.rendered .rendered_html {
  overflow-x: auto;
  overflow-y: hidden;
}
.text_cell.unrendered .text_cell_render {
  display: none;
}
.cm-header-1,
.cm-header-2,
.cm-header-3,
.cm-header-4,
.cm-header-5,
.cm-header-6 {
  font-weight: bold;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
.cm-header-1 {
  font-size: 185.7%;
}
.cm-header-2 {
  font-size: 157.1%;
}
.cm-header-3 {
  font-size: 128.6%;
}
.cm-header-4 {
  font-size: 110%;
}
.cm-header-5 {
  font-size: 100%;
  font-style: italic;
}
.cm-header-6 {
  font-size: 100%;
  font-style: italic;
}
/*!
*
* IPython notebook webapp
*
*/
@media (max-width: 767px) {
  .notebook_app {
    padding-left: 0px;
    padding-right: 0px;
  }
}
#ipython-main-app {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook_panel {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook {
  font-size: 14px;
  line-height: 20px;
  overflow-y: hidden;
  overflow-x: auto;
  width: 100%;
  /* This spaces the page away from the edge of the notebook area */
  padding-top: 20px;
  margin: 0px;
  outline: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  min-height: 100%;
}
@media not print {
  #notebook-container {
    padding: 15px;
    background-color: #fff;
    min-height: 0;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
@media print {
  #notebook-container {
    width: 100%;
  }
}
div.ui-widget-content {
  border: 1px solid #ababab;
  outline: none;
}
pre.dialog {
  background-color: #f7f7f7;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0.4em;
  padding-left: 2em;
}
p.dialog {
  padding: 0.2em;
}
/* Word-wrap output correctly.  This is the CSS3 spelling, though Firefox seems
   to not honor it correctly.  Webkit browsers (Chrome, rekonq, Safari) do.
 */
pre,
code,
kbd,
samp {
  white-space: pre-wrap;
}
#fonttest {
  font-family: monospace;
}
p {
  margin-bottom: 0;
}
.end_space {
  min-height: 100px;
  transition: height .2s ease;
}
.notebook_app > #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
@media not print {
  .notebook_app {
    background-color: #EEE;
  }
}
kbd {
  border-style: solid;
  border-width: 1px;
  box-shadow: none;
  margin: 2px;
  padding-left: 2px;
  padding-right: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
/* CSS for the cell toolbar */
.celltoolbar {
  border: thin solid #CFCFCF;
  border-bottom: none;
  background: #EEE;
  border-radius: 2px 2px 0px 0px;
  width: 100%;
  height: 29px;
  padding-right: 4px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
  display: -webkit-flex;
}
@media print {
  .celltoolbar {
    display: none;
  }
}
.ctb_hideshow {
  display: none;
  vertical-align: bottom;
}
/* ctb_show is added to the ctb_hideshow div to show the cell toolbar.
   Cell toolbars are only shown when the ctb_global_show class is also set.
*/
.ctb_global_show .ctb_show.ctb_hideshow {
  display: block;
}
.ctb_global_show .ctb_show + .input_area,
.ctb_global_show .ctb_show + div.text_cell_input,
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border-top-right-radius: 0px;
  border-top-left-radius: 0px;
}
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border: 1px solid #cfcfcf;
}
.celltoolbar {
  font-size: 87%;
  padding-top: 3px;
}
.celltoolbar select {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  width: inherit;
  font-size: inherit;
  height: 22px;
  padding: 0px;
  display: inline-block;
}
.celltoolbar select:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.celltoolbar select::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.celltoolbar select:-ms-input-placeholder {
  color: #999;
}
.celltoolbar select::-webkit-input-placeholder {
  color: #999;
}
.celltoolbar select::-ms-expand {
  border: 0;
  background-color: transparent;
}
.celltoolbar select[disabled],
.celltoolbar select[readonly],
fieldset[disabled] .celltoolbar select {
  background-color: #eeeeee;
  opacity: 1;
}
.celltoolbar select[disabled],
fieldset[disabled] .celltoolbar select {
  cursor: not-allowed;
}
textarea.celltoolbar select {
  height: auto;
}
select.celltoolbar select {
  height: 30px;
  line-height: 30px;
}
textarea.celltoolbar select,
select[multiple].celltoolbar select {
  height: auto;
}
.celltoolbar label {
  margin-left: 5px;
  margin-right: 5px;
}
.completions {
  position: absolute;
  z-index: 110;
  overflow: hidden;
  border: 1px solid #ababab;
  border-radius: 2px;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  line-height: 1;
}
.completions select {
  background: white;
  outline: none;
  border: none;
  padding: 0px;
  margin: 0px;
  overflow: auto;
  font-family: monospace;
  font-size: 110%;
  color: #000;
  width: auto;
}
.completions select option.context {
  color: #286090;
}
#kernel_logo_widget {
  float: right !important;
  float: right;
}
#kernel_logo_widget .current_kernel_logo {
  display: none;
  margin-top: -1px;
  margin-bottom: -1px;
  width: 32px;
  height: 32px;
}
#menubar {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  margin-top: 1px;
}
#menubar .navbar {
  border-top: 1px;
  border-radius: 0px 0px 2px 2px;
  margin-bottom: 0px;
}
#menubar .navbar-toggle {
  float: left;
  padding-top: 7px;
  padding-bottom: 7px;
  border: none;
}
#menubar .navbar-collapse {
  clear: left;
}
.nav-wrapper {
  border-bottom: 1px solid #e7e7e7;
}
i.menu-icon {
  padding-top: 4px;
}
ul#help_menu li a {
  overflow: hidden;
  padding-right: 2.2em;
}
ul#help_menu li a i {
  margin-right: -1.2em;
}
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu > .dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
}
.dropdown-submenu:hover > .dropdown-menu {
  display: block;
}
.dropdown-submenu > a:after {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  content: "\f0da";
  float: right;
  color: #333333;
  margin-top: 2px;
  margin-right: -10px;
}
.dropdown-submenu > a:after.pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.pull-right {
  margin-left: .3em;
}
.dropdown-submenu:hover > a:after {
  color: #262626;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left > .dropdown-menu {
  left: -100%;
  margin-left: 10px;
}
#notification_area {
  float: right !important;
  float: right;
  z-index: 10;
}
.indicator_area {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
#kernel_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  border-left: 1px solid;
}
#kernel_indicator .kernel_indicator_name {
  padding-left: 5px;
  padding-right: 5px;
}
#modal_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
#readonly-indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  margin-top: 2px;
  margin-bottom: 0px;
  margin-left: 0px;
  margin-right: 0px;
  display: none;
}
.modal_indicator:before {
  width: 1.28571429em;
  text-align: center;
}
.edit_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f040";
}
.edit_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: ' ';
}
.command_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f10c";
}
.kernel_idle_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f111";
}
.kernel_busy_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f1e2";
}
.kernel_dead_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f127";
}
.kernel_disconnected_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.pull-right {
  margin-left: .3em;
}
.notification_widget {
  color: #777;
  z-index: 10;
  background: rgba(240, 240, 240, 0.5);
  margin-right: 4px;
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget:focus,
.notification_widget.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.notification_widget:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active:hover,
.notification_widget.active:hover,
.open > .dropdown-toggle.notification_widget:hover,
.notification_widget:active:focus,
.notification_widget.active:focus,
.open > .dropdown-toggle.notification_widget:focus,
.notification_widget:active.focus,
.notification_widget.active.focus,
.open > .dropdown-toggle.notification_widget.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  background-image: none;
}
.notification_widget.disabled:hover,
.notification_widget[disabled]:hover,
fieldset[disabled] .notification_widget:hover,
.notification_widget.disabled:focus,
.notification_widget[disabled]:focus,
fieldset[disabled] .notification_widget:focus,
.notification_widget.disabled.focus,
.notification_widget[disabled].focus,
fieldset[disabled] .notification_widget.focus {
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget .badge {
  color: #fff;
  background-color: #333;
}
.notification_widget.warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning:focus,
.notification_widget.warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.notification_widget.warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active:hover,
.notification_widget.warning.active:hover,
.open > .dropdown-toggle.notification_widget.warning:hover,
.notification_widget.warning:active:focus,
.notification_widget.warning.active:focus,
.open > .dropdown-toggle.notification_widget.warning:focus,
.notification_widget.warning:active.focus,
.notification_widget.warning.active.focus,
.open > .dropdown-toggle.notification_widget.warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  background-image: none;
}
.notification_widget.warning.disabled:hover,
.notification_widget.warning[disabled]:hover,
fieldset[disabled] .notification_widget.warning:hover,
.notification_widget.warning.disabled:focus,
.notification_widget.warning[disabled]:focus,
fieldset[disabled] .notification_widget.warning:focus,
.notification_widget.warning.disabled.focus,
.notification_widget.warning[disabled].focus,
fieldset[disabled] .notification_widget.warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.notification_widget.success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success:focus,
.notification_widget.success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.notification_widget.success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active:hover,
.notification_widget.success.active:hover,
.open > .dropdown-toggle.notification_widget.success:hover,
.notification_widget.success:active:focus,
.notification_widget.success.active:focus,
.open > .dropdown-toggle.notification_widget.success:focus,
.notification_widget.success:active.focus,
.notification_widget.success.active.focus,
.open > .dropdown-toggle.notification_widget.success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  background-image: none;
}
.notification_widget.success.disabled:hover,
.notification_widget.success[disabled]:hover,
fieldset[disabled] .notification_widget.success:hover,
.notification_widget.success.disabled:focus,
.notification_widget.success[disabled]:focus,
fieldset[disabled] .notification_widget.success:focus,
.notification_widget.success.disabled.focus,
.notification_widget.success[disabled].focus,
fieldset[disabled] .notification_widget.success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.notification_widget.info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info:focus,
.notification_widget.info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.notification_widget.info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active:hover,
.notification_widget.info.active:hover,
.open > .dropdown-toggle.notification_widget.info:hover,
.notification_widget.info:active:focus,
.notification_widget.info.active:focus,
.open > .dropdown-toggle.notification_widget.info:focus,
.notification_widget.info:active.focus,
.notification_widget.info.active.focus,
.open > .dropdown-toggle.notification_widget.info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  background-image: none;
}
.notification_widget.info.disabled:hover,
.notification_widget.info[disabled]:hover,
fieldset[disabled] .notification_widget.info:hover,
.notification_widget.info.disabled:focus,
.notification_widget.info[disabled]:focus,
fieldset[disabled] .notification_widget.info:focus,
.notification_widget.info.disabled.focus,
.notification_widget.info[disabled].focus,
fieldset[disabled] .notification_widget.info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.notification_widget.danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger:focus,
.notification_widget.danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.notification_widget.danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active:hover,
.notification_widget.danger.active:hover,
.open > .dropdown-toggle.notification_widget.danger:hover,
.notification_widget.danger:active:focus,
.notification_widget.danger.active:focus,
.open > .dropdown-toggle.notification_widget.danger:focus,
.notification_widget.danger:active.focus,
.notification_widget.danger.active.focus,
.open > .dropdown-toggle.notification_widget.danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  background-image: none;
}
.notification_widget.danger.disabled:hover,
.notification_widget.danger[disabled]:hover,
fieldset[disabled] .notification_widget.danger:hover,
.notification_widget.danger.disabled:focus,
.notification_widget.danger[disabled]:focus,
fieldset[disabled] .notification_widget.danger:focus,
.notification_widget.danger.disabled.focus,
.notification_widget.danger[disabled].focus,
fieldset[disabled] .notification_widget.danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger .badge {
  color: #d9534f;
  background-color: #fff;
}
div#pager {
  background-color: #fff;
  font-size: 14px;
  line-height: 20px;
  overflow: hidden;
  display: none;
  position: fixed;
  bottom: 0px;
  width: 100%;
  max-height: 50%;
  padding-top: 8px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  /* Display over codemirror */
  z-index: 100;
  /* Hack which prevents jquery ui resizable from changing top. */
  top: auto !important;
}
div#pager pre {
  line-height: 1.21429em;
  color: #000;
  background-color: #f7f7f7;
  padding: 0.4em;
}
div#pager #pager-button-area {
  position: absolute;
  top: 8px;
  right: 20px;
}
div#pager #pager-contents {
  position: relative;
  overflow: auto;
  width: 100%;
  height: 100%;
}
div#pager #pager-contents #pager-container {
  position: relative;
  padding: 15px 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
div#pager .ui-resizable-handle {
  top: 0px;
  height: 8px;
  background: #f7f7f7;
  border-top: 1px solid #cfcfcf;
  border-bottom: 1px solid #cfcfcf;
  /* This injects handle bars (a short, wide = symbol) for 
        the resize handle. */
}
div#pager .ui-resizable-handle::after {
  content: '';
  top: 2px;
  left: 50%;
  height: 3px;
  width: 30px;
  margin-left: -15px;
  position: absolute;
  border-top: 1px solid #cfcfcf;
}
.quickhelp {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  line-height: 1.8em;
}
.shortcut_key {
  display: inline-block;
  width: 21ex;
  text-align: right;
  font-family: monospace;
}
.shortcut_descr {
  display: inline-block;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
span.save_widget {
  margin-top: 6px;
}
span.save_widget span.filename {
  height: 1em;
  line-height: 1em;
  padding: 3px;
  margin-left: 16px;
  border: none;
  font-size: 146.5%;
  border-radius: 2px;
}
span.save_widget span.filename:hover {
  background-color: #e6e6e6;
}
span.checkpoint_status,
span.autosave_status {
  font-size: small;
}
@media (max-width: 767px) {
  span.save_widget {
    font-size: small;
  }
  span.checkpoint_status,
  span.autosave_status {
    display: none;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  span.checkpoint_status {
    display: none;
  }
  span.autosave_status {
    font-size: x-small;
  }
}
.toolbar {
  padding: 0px;
  margin-left: -5px;
  margin-top: 2px;
  margin-bottom: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.toolbar select,
.toolbar label {
  width: auto;
  vertical-align: middle;
  margin-right: 2px;
  margin-bottom: 0px;
  display: inline;
  font-size: 92%;
  margin-left: 0.3em;
  margin-right: 0.3em;
  padding: 0px;
  padding-top: 3px;
}
.toolbar .btn {
  padding: 2px 8px;
}
.toolbar .btn-group {
  margin-top: 0px;
  margin-left: 5px;
}
#maintoolbar {
  margin-bottom: -3px;
  margin-top: -8px;
  border: 0px;
  min-height: 27px;
  margin-left: 0px;
  padding-top: 11px;
  padding-bottom: 3px;
}
#maintoolbar .navbar-text {
  float: none;
  vertical-align: middle;
  text-align: right;
  margin-left: 5px;
  margin-right: 0px;
  margin-top: 0px;
}
.select-xs {
  height: 24px;
}
.pulse,
.dropdown-menu > li > a.pulse,
li.pulse > a.dropdown-toggle,
li.pulse.open > a.dropdown-toggle {
  background-color: #F37626;
  color: white;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
/** WARNING IF YOU ARE EDITTING THIS FILE, if this is a .css file, It has a lot
 * of chance of beeing generated from the ../less/[samename].less file, you can
 * try to get back the less file by reverting somme commit in history
 **/
/*
 * We'll try to get something pretty, so we
 * have some strange css to have the scroll bar on
 * the left with fix button on the top right of the tooltip
 */
@-moz-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-webkit-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-moz-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/*properties of tooltip after "expand"*/
.bigtooltip {
  overflow: auto;
  height: 200px;
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
}
/*properties of tooltip before "expand"*/
.smalltooltip {
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
  text-overflow: ellipsis;
  overflow: hidden;
  height: 80px;
}
.tooltipbuttons {
  position: absolute;
  padding-right: 15px;
  top: 0px;
  right: 0px;
}
.tooltiptext {
  /*avoid the button to overlap on some docstring*/
  padding-right: 30px;
}
.ipython_tooltip {
  max-width: 700px;
  /*fade-in animation when inserted*/
  -webkit-animation: fadeOut 400ms;
  -moz-animation: fadeOut 400ms;
  animation: fadeOut 400ms;
  -webkit-animation: fadeIn 400ms;
  -moz-animation: fadeIn 400ms;
  animation: fadeIn 400ms;
  vertical-align: middle;
  background-color: #f7f7f7;
  overflow: visible;
  border: #ababab 1px solid;
  outline: none;
  padding: 3px;
  margin: 0px;
  padding-left: 7px;
  font-family: monospace;
  min-height: 50px;
  -moz-box-shadow: 0px 6px 10px -1px #adadad;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  border-radius: 2px;
  position: absolute;
  z-index: 1000;
}
.ipython_tooltip a {
  float: right;
}
.ipython_tooltip .tooltiptext pre {
  border: 0;
  border-radius: 0;
  font-size: 100%;
  background-color: #f7f7f7;
}
.pretooltiparrow {
  left: 0px;
  margin: 0px;
  top: -16px;
  width: 40px;
  height: 16px;
  overflow: hidden;
  position: absolute;
}
.pretooltiparrow:before {
  background-color: #f7f7f7;
  border: 1px #ababab solid;
  z-index: 11;
  content: "";
  position: absolute;
  left: 15px;
  top: 10px;
  width: 25px;
  height: 25px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
}
ul.typeahead-list i {
  margin-left: -10px;
  width: 18px;
}
ul.typeahead-list {
  max-height: 80vh;
  overflow: auto;
}
ul.typeahead-list > li > a {
  /** Firefox bug **/
  /* see https://github.com/jupyter/notebook/issues/559 */
  white-space: normal;
}
.cmd-palette .modal-body {
  padding: 7px;
}
.cmd-palette form {
  background: white;
}
.cmd-palette input {
  outline: none;
}
.no-shortcut {
  display: none;
}
.command-shortcut:before {
  content: "(command)";
  padding-right: 3px;
  color: #777777;
}
.edit-shortcut:before {
  content: "(edit)";
  padding-right: 3px;
  color: #777777;
}
#find-and-replace #replace-preview .match,
#find-and-replace #replace-preview .insert {
  background-color: #BBDEFB;
  border-color: #90CAF9;
  border-style: solid;
  border-width: 1px;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .match {
  background-color: #FFCDD2;
  border-color: #EF9A9A;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .insert {
  background-color: #C8E6C9;
  border-color: #A5D6A7;
  border-radius: 0px;
}
#find-and-replace #replace-preview {
  max-height: 60vh;
  overflow: auto;
}
#find-and-replace #replace-preview pre {
  padding: 5px 10px;
}
.terminal-app {
  background: #EEE;
}
.terminal-app #header {
  background: #fff;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.terminal-app .terminal {
  width: 100%;
  float: left;
  font-family: monospace;
  color: white;
  background: black;
  padding: 0.4em;
  border-radius: 2px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
}
.terminal-app .terminal,
.terminal-app .terminal dummy-screen {
  line-height: 1em;
  font-size: 14px;
}
.terminal-app .terminal .xterm-rows {
  padding: 10px;
}
.terminal-app .terminal-cursor {
  color: black;
  background: white;
}
.terminal-app #terminado-container {
  margin-top: 20px;
}
/*# sourceMappingURL=style.min.css.map */
    </style>
<style type="text/css">
    .highlight .hll { background-color: #ffffcc }
.highlight  { background: #f8f8f8; }
.highlight .c { color: #408080; font-style: italic } /* Comment */
.highlight .err { border: 1px solid #FF0000 } /* Error */
.highlight .k { color: #008000; font-weight: bold } /* Keyword */
.highlight .o { color: #666666 } /* Operator */
.highlight .ch { color: #408080; font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: #408080; font-style: italic } /* Comment.Multiline */
.highlight .cp { color: #BC7A00 } /* Comment.Preproc */
.highlight .cpf { color: #408080; font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: #408080; font-style: italic } /* Comment.Single */
.highlight .cs { color: #408080; font-style: italic } /* Comment.Special */
.highlight .gd { color: #A00000 } /* Generic.Deleted */
.highlight .ge { font-style: italic } /* Generic.Emph */
.highlight .gr { color: #FF0000 } /* Generic.Error */
.highlight .gh { color: #000080; font-weight: bold } /* Generic.Heading */
.highlight .gi { color: #00A000 } /* Generic.Inserted */
.highlight .go { color: #888888 } /* Generic.Output */
.highlight .gp { color: #000080; font-weight: bold } /* Generic.Prompt */
.highlight .gs { font-weight: bold } /* Generic.Strong */
.highlight .gu { color: #800080; font-weight: bold } /* Generic.Subheading */
.highlight .gt { color: #0044DD } /* Generic.Traceback */
.highlight .kc { color: #008000; font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: #008000; font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: #008000; font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: #008000 } /* Keyword.Pseudo */
.highlight .kr { color: #008000; font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: #B00040 } /* Keyword.Type */
.highlight .m { color: #666666 } /* Literal.Number */
.highlight .s { color: #BA2121 } /* Literal.String */
.highlight .na { color: #7D9029 } /* Name.Attribute */
.highlight .nb { color: #008000 } /* Name.Builtin */
.highlight .nc { color: #0000FF; font-weight: bold } /* Name.Class */
.highlight .no { color: #880000 } /* Name.Constant */
.highlight .nd { color: #AA22FF } /* Name.Decorator */
.highlight .ni { color: #999999; font-weight: bold } /* Name.Entity */
.highlight .ne { color: #D2413A; font-weight: bold } /* Name.Exception */
.highlight .nf { color: #0000FF } /* Name.Function */
.highlight .nl { color: #A0A000 } /* Name.Label */
.highlight .nn { color: #0000FF; font-weight: bold } /* Name.Namespace */
.highlight .nt { color: #008000; font-weight: bold } /* Name.Tag */
.highlight .nv { color: #19177C } /* Name.Variable */
.highlight .ow { color: #AA22FF; font-weight: bold } /* Operator.Word */
.highlight .w { color: #bbbbbb } /* Text.Whitespace */
.highlight .mb { color: #666666 } /* Literal.Number.Bin */
.highlight .mf { color: #666666 } /* Literal.Number.Float */
.highlight .mh { color: #666666 } /* Literal.Number.Hex */
.highlight .mi { color: #666666 } /* Literal.Number.Integer */
.highlight .mo { color: #666666 } /* Literal.Number.Oct */
.highlight .sa { color: #BA2121 } /* Literal.String.Affix */
.highlight .sb { color: #BA2121 } /* Literal.String.Backtick */
.highlight .sc { color: #BA2121 } /* Literal.String.Char */
.highlight .dl { color: #BA2121 } /* Literal.String.Delimiter */
.highlight .sd { color: #BA2121; font-style: italic } /* Literal.String.Doc */
.highlight .s2 { color: #BA2121 } /* Literal.String.Double */
.highlight .se { color: #BB6622; font-weight: bold } /* Literal.String.Escape */
.highlight .sh { color: #BA2121 } /* Literal.String.Heredoc */
.highlight .si { color: #BB6688; font-weight: bold } /* Literal.String.Interpol */
.highlight .sx { color: #008000 } /* Literal.String.Other */
.highlight .sr { color: #BB6688 } /* Literal.String.Regex */
.highlight .s1 { color: #BA2121 } /* Literal.String.Single */
.highlight .ss { color: #19177C } /* Literal.String.Symbol */
.highlight .bp { color: #008000 } /* Name.Builtin.Pseudo */
.highlight .fm { color: #0000FF } /* Name.Function.Magic */
.highlight .vc { color: #19177C } /* Name.Variable.Class */
.highlight .vg { color: #19177C } /* Name.Variable.Global */
.highlight .vi { color: #19177C } /* Name.Variable.Instance */
.highlight .vm { color: #19177C } /* Name.Variable.Magic */
.highlight .il { color: #666666 } /* Literal.Number.Integer.Long */
    </style>
<style type="text/css">
    
/* Temporary definitions which will become obsolete with Notebook release 5.0 */
.ansi-black-fg { color: #3E424D; }
.ansi-black-bg { background-color: #3E424D; }
.ansi-black-intense-fg { color: #282C36; }
.ansi-black-intense-bg { background-color: #282C36; }
.ansi-red-fg { color: #E75C58; }
.ansi-red-bg { background-color: #E75C58; }
.ansi-red-intense-fg { color: #B22B31; }
.ansi-red-intense-bg { background-color: #B22B31; }
.ansi-green-fg { color: #00A250; }
.ansi-green-bg { background-color: #00A250; }
.ansi-green-intense-fg { color: #007427; }
.ansi-green-intense-bg { background-color: #007427; }
.ansi-yellow-fg { color: #DDB62B; }
.ansi-yellow-bg { background-color: #DDB62B; }
.ansi-yellow-intense-fg { color: #B27D12; }
.ansi-yellow-intense-bg { background-color: #B27D12; }
.ansi-blue-fg { color: #208FFB; }
.ansi-blue-bg { background-color: #208FFB; }
.ansi-blue-intense-fg { color: #0065CA; }
.ansi-blue-intense-bg { background-color: #0065CA; }
.ansi-magenta-fg { color: #D160C4; }
.ansi-magenta-bg { background-color: #D160C4; }
.ansi-magenta-intense-fg { color: #A03196; }
.ansi-magenta-intense-bg { background-color: #A03196; }
.ansi-cyan-fg { color: #60C6C8; }
.ansi-cyan-bg { background-color: #60C6C8; }
.ansi-cyan-intense-fg { color: #258F8F; }
.ansi-cyan-intense-bg { background-color: #258F8F; }
.ansi-white-fg { color: #C5C1B4; }
.ansi-white-bg { background-color: #C5C1B4; }
.ansi-white-intense-fg { color: #A1A6B2; }
.ansi-white-intense-bg { background-color: #A1A6B2; }

.ansi-bold { font-weight: bold; }

    </style>


<style type="text/css">
/* Overrides of notebook CSS for static HTML export */
body {
  overflow: visible;
  padding: 8px;
}

div#notebook {
  overflow: visible;
  border-top: none;
}@media print {
  div.cell {
    display: block;
    page-break-inside: avoid;
  } 
  div.output_wrapper { 
    display: block;
    page-break-inside: avoid; 
  }
  div.output { 
    display: block;
    page-break-inside: avoid; 
  }
}
</style>

<!-- Custom stylesheet, it must be in the same directory as the html file -->
<link rel="stylesheet" href="custom.css">

<!-- Loading mathjax macro -->
<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS_HTML"></script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
            processEscapes: true,
            processEnvironments: true
        },
        // Center justify equations in code and markdown cells. Elsewhere
        // we use CSS to left justify single line equations in code cells.
        displayAlign: 'center',
        "HTML-CSS": {
            styles: {'.MathJax_Display': {"margin": 0}},
            linebreaks: { automatic: true }
        }
    });
    </script>
    <!-- End of mathjax configuration --></head>
<body>
  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>I came across an odd problem that I had never really explored before in The Practice of Statistics, 5th Edition Annotated Teacher's Edition.  In a sidebar alternative activity, there was mention of a "random baby" applet that simulated a stork delivering babies to homes.  It was then suggested that the concept of a derangement be researched.  I was intrigued, so I looked up what a derangement was.  According to Wikipedia:</p>
<blockquote><p>A derangement is a permutation of the elements of a set, such that no element appears in its original position.</p>
</blockquote>
<p>I decided to write a quick Python simulation to see how this particular scenario played out.</p>
<p>For the four homes/babies scenario, the probability of a derangement (every home receiving the wrong baby) looks to be approaching 0.375.</p>
<p>I explored a few other scenarios, increasing the number of deliveries to see how the long-run probability behaved.  The Wikipedia article includes an explanation of how as the number of possible deliveries increases, the long-run probability approaches $\frac{1}{e}$ which is equal to approximately 0.368.  The simulations I ran with 1,000,000 trials end with probabilities of 0.368094 and 0.367922 which shows that these simulations accurately portray the scenario.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="o">%</span><span class="k">matplotlib</span> inline

<span class="n">np</span><span class="o">.</span><span class="n">random</span><span class="o">.</span><span class="n">seed</span><span class="p">(</span><span class="mi">123</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">compare_lists</span><span class="p">(</span><span class="n">list_a</span><span class="p">,</span> <span class="n">list_b</span><span class="p">):</span>
    <span class="n">result_list</span> <span class="o">=</span> <span class="p">[]</span>
    
    <span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">element</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">list_a</span><span class="p">):</span>
        <span class="k">if</span> <span class="n">element</span> <span class="o">==</span> <span class="n">list_b</span><span class="p">[</span><span class="n">i</span><span class="p">]:</span>
            <span class="n">result_list</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span>
            
        <span class="k">else</span><span class="p">:</span>
            <span class="n">result_list</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="mi">0</span><span class="p">)</span>
            
    <span class="k">return</span> <span class="n">result_list</span>

<span class="k">def</span> <span class="nf">simulate_derangements</span><span class="p">(</span><span class="n">deliveries</span> <span class="o">=</span> <span class="mi">4</span><span class="p">,</span> <span class="n">trials</span> <span class="o">=</span> <span class="mi">100</span><span class="p">):</span>
    <span class="n">homes_list</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="n">deliveries</span><span class="p">))</span>
    
    <span class="n">derangement_probs</span> <span class="o">=</span> <span class="p">[]</span>
    
    <span class="n">number_of_derangements_total</span><span class="o">=</span> <span class="mf">0.0</span>
    
    <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="n">trials</span> <span class="o">+</span> <span class="mi">1</span><span class="p">):</span>
        <span class="n">babies_list</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">random</span><span class="o">.</span><span class="n">choice</span><span class="p">(</span><span class="n">deliveries</span><span class="p">,</span> <span class="n">deliveries</span><span class="p">,</span> <span class="n">replace</span> <span class="o">=</span> <span class="kc">False</span><span class="p">))</span>
        
        <span class="k">if</span> <span class="nb">sum</span><span class="p">(</span><span class="n">compare_lists</span><span class="p">(</span><span class="n">homes_list</span><span class="p">,</span> <span class="n">babies_list</span><span class="p">))</span> <span class="o">==</span> <span class="mi">0</span><span class="p">:</span>
            <span class="n">number_of_derangements_total</span> <span class="o">+=</span> <span class="mf">1.0</span>
        
        <span class="n">derangement_probs</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">number_of_derangements_total</span> <span class="o">/</span> <span class="nb">float</span><span class="p">(</span><span class="n">i</span><span class="p">))</span>
        
    <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">derangement_probs</span><span class="p">)</span>
    
    <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Probability of Randomly Delivering &#39;</span> 
              <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">deliveries</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; Babies All to the Wrong Homes (&#39;</span> 
              <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">trials</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; trials)&#39;</span><span class="p">)</span>
    
    <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
    <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Probability After Last Trial: &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">derangement_probs</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">]))</span>
    

<span class="n">simulate_derangements</span><span class="p">()</span>
<span class="n">simulate_derangements</span><span class="p">(</span><span class="n">trials</span> <span class="o">=</span> <span class="mi">1000</span><span class="p">)</span>
<span class="n">simulate_derangements</span><span class="p">(</span><span class="n">trials</span> <span class="o">=</span> <span class="mi">1000000</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Probability After Last Trial: 0.43
</pre>
</div>
</div>

<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAfgAAAEICAYAAACzuuZmAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADl0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uIDIuMS4xLCBodHRwOi8vbWF0cGxvdGxpYi5vcmcvAOZPmwAAIABJREFUeJzt3XmcHFW5//HPM/tMMkuSmewhC1kg7BL2XVADKqAXFRRZBb2AXhEvF5cfm3pduPeCKIoggoiA7AYF2XdIIGEJ2QiTfc8kmSWTyezn98epntR0umdLT6Yy/X2/XvOa7qrq6lNVp+up89SpKnPOISIiIv1LRl8XQERERFJPAV5ERKQfUoAXERHphxTgRURE+iEFeBERkX5IAV5ERKQf2q0B3syuN7P7evjZC8zs9Q7GP21m5yea1sxqzWxCT763m2XMN7MnzazazB7u7e/rQnmWm9kpvTDfHm/HVH63me0VbNvMXvie48zso1TPd3czs3vM7KcdjN8tv42473zZzL4RvO7wd90L391ndVd6xsy+aWa39HU5esLMvmZmz3Zx2i7VTTN7zMymd2WenQb4IEhsD3YEG8zsbjMb2JWZ707OuVOdc39OMm6gc24pdL7D20VnAcOAIc65L8WPDDZgU7Auq8zsTTM7qpfKEjlmNs7MXLD8sfr0DzP7VE/m55xbGWzbllSX1Tn3mnNuSqrnG2Zmg82sopMD1wvMrCW0zpaa2b+nqgzh30YqmbfUzBbswjxi9SWrh58/0cxW9/T7O5n3UWZWEz64NLM7kwy7vTfK0B3JDqR6qxGQKmaWA/wYuCk07A4z+8jMWs3sggSfudLM1gcNrT+ZWW5o3Dgze8nM6sxsUfyyd/TZuOm6VDedc391zn26m4vdmV8AP+vKhF1twX/eOTcQ+ARwGH6FtxP8oNM95T8WWOyca+5gmr8F67IUeAno85Z+HygJ1sFBwHPA44l+qH2lpwGlB34JLOzCdG8FgXgg/iDyV2Z2SO8WbZcdDwwFJpjZYX1dmF4wG8jE7xNjjgPWxg07Hng1/sPaX3bZGcAi59ya0LAPgMuAd+MnNrPPANcAJwPjgAnADaFJHgDeA4YAPwIeMbOyLn62W3prP+KcexsoMrNpnU3brQoWrOSngf2hLdX2MzN7A6jD/5hHmtkMM9tiZuVmdkncbPLM7G9mttXM3jWzg2IjzOwaM1sSjFtgZl+I+6yZ2W+Co6tFZnZyaERb2i9ecKQ10cwuBb4GXB20hp40s/80s0fjpv+NJUkJmdm+wXdVmdl8Mzs9GH4DcC3wlWDeF3eyLpuBvwKjQhVsUNCirTCzyuD16Lhl/ImZvRGso2fNrDQ0/utmtsLMNpvZj+LKnWtmt5jZ2uDvltjRaaylY2ZXm9lGM1tnZmea2WlmtjjYlj9Msj7+aWbfjhs218zO7Gj5g3Ww3jn3a+B64JexHV5Qhx4N1sMyM/tOku9uO4o2s7PNbHbc+CvNbEZo+f/HzFaazxzcbmb5ccv/X2a2Hrjb4lp/5ls63w+WrTqow3mh8VcH622tmX0jVueSLbv5zM3+wN2drae4dfYu/qBg39C8HrYdrY5XzWy/uI+VmtlzQZ15xczGhj7bVs5O1lFpUB+rgvrwmnUcoM4H/g48FbzuiVhgrAp+U0eZWYaZ/Tio5xvN7F4zK47/oJkNwO+rRtqO7MfIYHRO8LmtwW94WuhzXap7zrkmYCY+gGNmQ4Ec4G9xwybHlsO6ub80n/F7qIOyfsLM3gvGPRzUyR5nJztat6Hf2oVmtsr8/ulbZnZY8JuoMrPfxs3vIjNbGEz7TKzemXdz8B3Vwef3T1KsU4FX4tb9bc65F4D6BNOfD9zlnJvvnKsEfgJcEHzvZPzB13XOue3OuUeBD4F/6+yzCSSqmxeY3zffbGZbgOtt59PFvw7WX42ZzTGz4xLN3MzyzOw+8/vyKjN7x8yGhSZ5GfhskrK16VaAN7MxwGn4I6CYrwOXAoXACvwR0mpgJL618d8WCsT4I7KHgcHA/cATZpYdjFuCPwouxh853WdmI0KfPQJYim/9Xgc8ZmaDu1p+59wd+KD6q6BF9HngPmC6mZUEy5gFfAX4S4LlzwaeBJ7Ft06+DfzVzKY4564D/pughe6cu6ujsphPPZ0HbAYqg8EZ+B3+WGAvYDvw27iPfhW4MPj+HOD7wfymAr/Hb4+R+CPU0aHP/Qg4EjgY33I+nPaZmOFAHjAKf6ByJ3AucCh+m1xric/V/jmYLrZcBwXzeKqj5Y/zWLA8U4Kg8ST+KH0U/mj6u+aPrjsyI/j8pNCwr+LrGPjW8mT88k9kx3LGDMfXybH4+pzIl4HpwHjgQHbsOKYD3wNOCeZ9QkcFNZ/CvQ24AujWvaLNt4Yn41uQMU8Dk/Dr8F18HQ/7Gn5nVQq8n2B8TEfr6Cr877oMfxrqh8nKbmYF+N/+X4O/s4P63l3HB/9Lgt/UW/h1fgFwEr6FNZCdfyM457bhg8PaWPbDObc2GH068CBQgq83vw3K3d2692qojMcDrwd/4WHLnHPh0wTd3V8mK2sO8DhwD77ePgDEN4i66wI6X7dH4OvaV4Bb8PuVU4D9gC+b2QlB+c7E15Ev4uvMa0EZAT6NXzeTg+X6Cn4/mMgBQHf6wuyH334xHwDDzGxIMG6pc25r3Pj9uvDZeInqJuyIUUNJnEZ/B//7isW/hy3UUAg5Hx8Hx+D35d/Cx4OYhfj9eMeccx3+AcuBWqAKXyF/B+QH414GbgxNOwZoAQpDw34O3BO8vh6YGRqXAawDjkvy3e8DZwSvL8Cnvyw0/m3g66GyfCM07euh6RwwMXh9D/DTuO95GrgkeP05YEGS8hwHrAcyQsMeAK4PLd99HazL64HGYF224Cv1iR1MfzBQGXr/MvDj0PvLgH8Fr68FHgyNGxB81ynB+yXAaaHxnwGWB69PxFeezOB9YbDOjghNPwc4M345gVxgCzApeP8/wO+SLM+4YL5ZccPzguHH4H8gK+PG/wC4O8F3t5sf/mDt2uD1JGArUAAYsA3YOzTPo/A739jyNwJ5ofEnAqvjfgfnht7/Crg9eP0n4OehcRMJ1bkE6+FK4PeJ6mqCaS8AmoM6UxvM9zeEfgdx05cE0xSH6nu4XgzE170x4d9GF9bRjfgWecJliivDuUAFkBXUjyrgC3H1OOFvtbP6ArwAXBZ6PwVoiq9TibZhqP48H3o/FdgevO6w7iWZ/+Zg3f0auCRYvxtCw+6OW+7u7i+TlfV4YA3t94evE7dvS1KPwn+t7NhHJF23oW0xKjR+M/CV0PtHge8Gr58GLg6Ny8BnLcYCnwQW4xscGYnKG/rcx8D0JONeBy6IG7YkPD2QHZR7HP7gambc9D8Lre+kn+1i3bwgQf25gI5/35XAQaHtHdu3XQS8CRyY5HOXAC929lvsagv+TOdciXNurHPuMudc+EhiVej1SGCLa3+EtAJ/NLzT9M65VnYcvWJm55nZ+0FKogqfwiwNfXaNC5YuNO+R7LpwK/RcErTeAyOBVUG5w2UYlWT6RB5yzpXgW0Hz8C1kwLd8zOwPQYqsBt9CKLH2vcTXh17X4XcobWWLjXC+BRM+Kh4ZlDVc7vC62+x2dFaLbd8NofHbQ9/VxjnXADwEnBu0gM4h+fpLJrb+tuB3ACNjdSCoBz/Er6/O3B98P/jW+xPOuTp8C6IAmBOa57+C4TEVzrlEKb+wLq37uNftmE8Tfwff8umqmcHvbyA+07AfPluEmWWa2S/Mn9qqwR+IQPvfTbhe1OLXc/zvprN1dBNQDjxrvvPcNR2U93x8PW8O6sdj9DxNHy9RPc6ia/UjJn475gWZu+7WvZn4OrA/PuC+FqzfVaFh8effu7u/TFbWkey8P0xa72LlDepR2x+wMq48na3b+H1Csn3EWODXofW4BX/QM8o59yI+M3AbsMF8p7miJGWuxDc4uqoWCM8r9nprgnGx8bH139Fnu6rDbWBmVwWnLaqD9VJM+99qzF+AZ4AHzZ/2+1Uo0w1+nVR1VphUdPIIV7C1wGAzC2+QvfBHmjFjYi+CgDAaWBucn7kTn7YcElS+efhKETPKzMLv9wq+s6fljXkCODA4D/Q5kqcw1wJjrP25x/jl61ohnNsEfBN/niZ2GuIq/FHzEc65InakgSzBLOKto/26LcCndsJlHxtX7u6uu2T+jE8DnwzUuR3pqq76ArARn4pbhW81hndEhc6507own2fx55sPxgf6WHp+E37ns19onsVBwIzpVqo8zjranw4Zk2xC/KmREcAC8+f7fw0cbv4ceqeX+znnNuBbSp8PBn0Vf9rrFPzOYlwwPFxnwvViID49GL/tO1xHzrmtzrmrnHMTgu/+XlwqOTb/0fgW2rnBMq3Hp55Ps1B/kS5KtE0S1eNm2geajj7fkW7VveCA8B38PmOEc25RMOq1YNiB7Bzgu7u/TGYdO+8PO6p3XdGddduZVcA349ZlvnPuTQDn3K3OuUPxB6uTgf9MMp+5wfiumk/71PVBwAbn3OZg3IS49X1QMLyzz8ZLVreS1rngfPt/4U/1DQpiXDUJ9u/OuSbn3A3OuanA0fj6dF5okn1pfzohoZT24nTOrcKnFX4edBI4ELiY9gHzUDP7YnAU+l2gAX8kPAC/cioAzOxCgs58IUOB75hZtpl9Cb+Q3TnXC76ytjuXHPxQH8EHhLedcysTfRCYhU9jXh2U4UT8zu7BbpYh9r2L8EdpVweDCvE72aqgb8F13ZjdI8DnzOzY4PzcjbTfvg8APzazsmBHey0+pb3LgoDeCvwv3Wi9m9kwM7sCv5w/CDIjbwM15ju85Qct1P2tCz2xne+4+Ai+tTkY30M/lim6E7jZfMcnzGxUF87rd9VDwIXmO2AW0P7cfryn8UH44ODvWnyfloNdFy73C84HfoEdO6VC/G9oM74F/t8JPnZaqF78BJgV/FbbdLaOzOxz5juqGlCDTy0nKu/X8enXKaFlnIzP1J2TYPqOVODrVfj3+gBwpZmNDw5WYv1eEl25sgEYYgk64SXRk7r3Kn4/9mZo2OvBsPXOuSXJPtjF/WUyb+HX/xXmO5megT943BXdWbeduR34gQUdPs2sONhnY75j3hFBi3QbvrNcsrr/FHF9WswsJzhvbUB2sO5i+7p7gYvNbKqZDcL3M7oHwDm3GH/a97rgM1/AH4Q92tlnE0hUNztTiD9gqgCyzOxads4oxJbxJDM7IDjor8GfKgmvoxPw+5IO9cZlGufgd2Br8Z1ArnPOPRca/3d8p4pK/M7gi8HRygJ8gHgL/8M8AHgjbt6z8OdWN+HPnZyV5OiqI3cBU4PU0ROh4X8OvjNpgHLONeI7vZwalOF3wHmhI/eeuAm4NNip3gLkB/OeiU+Rdolzbj5wOf4gZR1+/YY79/wU3zFrLr7n6LvBsFS5F7/+unLQUGVm24JynAZ8yTn3J4AgyH0eHxiW4dfFH/Gt0664H9+afThux/Rf+BTzzCCV/Tw+CO0y59zTwK34yx7L8XUYfOCNn7bB+asH1jvn1uOP4JuC18kcZUFPcHznmgp8B0/w630FvtW3AF9v4t2PP4jagj8l9LUk39PROpoUvK8Nlu93zrmXE8zj/GDc+rjlvJ1upumD0ys/A94Ifq9H4vs7/AUfWJfhg8O3k3x+ET5oLQ0+3+HpvB7WvVfwDY/wNeavB8N2ujwugc72l8nK2ojvwHYxPlV7LvAPEtS5bujyuu1C+R7Hd9p8MKhL8/D7TfBB7U78PmoF/uD0f5LM6klgn7ht9yy+IXQ0cEfw+vjge/+F7x/zUjDvFbRvKJ0NTAu++xf4GFLRxc+Gly9R3ezMM/igvDiYdz3JU/rD8Y2VGvxv/hWCfWtwwLnN+cvlOmTtT+GkLzPbC1gEDHfO1fR1efY0ZnYecKlz7ti+LktfM7N98Tu03B62fkS6zcxm4Tt+3t3XZUkl85c3T3XOfbevyxIF5i/rvss512n2WgGetr4A/wcUOecu6uvy7GmCtPSL+JbbvX1dnr4QpPv+iT/V9Geg1TnX6b0ARHrK/CVpH+EzDV/DZ0kmOOfW9WnBJDLS/k5K5m+IUQN8iu6d8xba7v5UgT+tcn8nk/dn38SvhyX4c2Upu52sSBJT8B2tqvEddM9ScJcwteBFRET6obRvwYuIiPRHu+uhGmmltLTUjRs3rq+LISKyx5gzZ84m51xZ51NKVynA94Jx48Yxe/bszicUEREAzGxF51NJdyhFLyIi0g8pwIuIiPRDCvAiIiL9kAK8iIhIP6QALyIi0g+ldYA3sz+Z2UYzm5dkvJnZrWZWbmZzzewTu7uMIiIiPZHWAR7/KMDpHYw/Ff8UrUnApcDvd0OZREREdllaB3jn3Kv4R2gmcwZwr/NmAiVmNqK3ynPX68t46kPdSlpERHZdWgf4LhhF++f1rg6G7cTMLjWz2WY2u6Kiokdfdu9by3lmfkePBRcREekaBfiOWYJhCZ/O45y7wzk3zTk3raysZ3dbTPRlIiIiPaEA37HVwJjQ+9HA2t78Qj3cT0REUkEBvmMzgPOC3vRHAtW9+bxlM0ucHhAREemmtH7YjJk9AJwIlJrZauA6IBvAOXc78BRwGlAO1AEX9mp5enPmIiKSVtI6wDvnzulkvAMu303FiX3n7vw6ERHpp5SijxJL0oNPRESkmxTgI0QpehERSRUF+KhRE15ERFJAAT5CfC96RXgREdl1CvARohS9iIikigJ8xKgTvYiIpIICfISYKcCLiEhqKMBHiClJLyIiKaIAHzHqZCciIqmgAB8hStGLiEiqKMCLiIj0QwrwEaMGvIiIpIICfISYmVL0IiKSEgrwEaI+9CIikioK8JGjJryIiOw6BfgIUS96ERFJFQX4CDE9D15ERFJEAV5ERKQfUoCPEMNwytGLiEgKKMBHiFL0IiKSKgrwEaLL5EREJFUU4CNGGXoREUkFBfgoMVOKXkREUkIBPkKUohcRkVRRgI8Y9aIXEZFUUICPEFMTXkREUkQBPkIU30VEJFUU4CNGGXoREUkFBfgIMTOc+tGLiEgKKMBHiFL0IiKSKgrwEaMUvYiIpIICfIToefAiIpIqCvARYkrSi4hIiijAR4w62YmISCoowEeJUvQiIpIiCvARogS9iIikigJ8xKgBLyIiqZD2Ad7MppvZR2ZWbmbXJBi/l5m9ZGbvmdlcMzut98qCIryIiKREWgd4M8sEbgNOBaYC55jZ1LjJfgw85Jw7BDgb+F2vlUdJehERSZG0DvDA4UC5c26pc64ReBA4I24aBxQFr4uBtb1ZIPWiFxGRVEj3AD8KWBV6vzoYFnY9cK6ZrQaeAr6daEZmdqmZzTaz2RUVFT0qjG50IyIiqZLuAT5RTjw+xJ4D3OOcGw2cBvzFzHZab865O5xz05xz08rKynpWGNMpeBERSY10D/CrgTGh96PZOQV/MfAQgHPuLSAPKO2NwugcvIiIpEq6B/h3gElmNt7McvCd6GbETbMSOBnAzPbFB/ie5eC7wClHLyIiKZDWAd451wxcATwDLMT3lp9vZjea2enBZFcBl5jZB8ADwAWul6KwUvQiIpIqWX1dgL7mnHsK33kuPOza0OsFwDG7u1wiIiK7Iq1b8FGkDL2IiKSCAnyEmJlS9CIikhIK8BGiPvQiIpIqCvBRoxy9iIikgAJ8hKgXvYiIpIoCfIQoRS8iIqmiAB8xytCLiEgqKMBHiO9FrwgvIiK7TgE+QpSiFxGRVFGAjxil6EVEJBUU4CNEz4MXEZFUUYCPFCXpRUQkNRTgI0YNeBERSQUF+AjxKXqFeBER2XUK8BGiBL2IiKSKAryIiEg/pAAfIepFLyIiqaIAHyGmJL2IiKSIAnzE6Fa1IiKSCgrwEaIUvYiIpIoCfIToefAiIpIqCvARonPwIiKSKgrwEaMb3YiISCoowEeJUvQiIpIiCvARogS9iIikigJ81KgJLyIiKaAAHyFmpvguIiIpoQAfIUrRi4hIqijAR4x60YuISCoowEeIbnQjIiKpogAfIUrRi4hIqijAR4wy9CIikgoK8BHie9ErwouIyK5TgI8QpehFRCRVFOAjRil6ERFJBQX4KNHz4EVEJEUU4CNEj4sVEZFUSesAb2bTzewjMys3s2uSTPNlM1tgZvPN7P7dXUYREZGeyOrrAvQVM8sEbgM+BawG3jGzGc65BaFpJgE/AI5xzlWa2dDeLZPuZCciIqmRzi34w4Fy59xS51wj8CBwRtw0lwC3OecqAZxzG3uzQErQi4hIqqRzgB8FrAq9Xx0MC5sMTDazN8xspplNTzYzM7vUzGab2eyKiooeF0rtdxERSYV0DvCJGszx8TULmAScCJwD/NHMShLNzDl3h3NumnNuWllZWc8KpF70IiKSIukc4FcDY0LvRwNrE0zzd+dck3NuGfARPuD3CkN3shMRkdRI5wD/DjDJzMabWQ5wNjAjbpongJMAzKwUn7Jf2lsFMp2EFxGRFEnbAO+cawauAJ4BFgIPOefmm9mNZnZ6MNkzwGYzWwC8BPync25z75arN+cuIiLpIm0vkwNwzj0FPBU37NrQawd8L/jrdXoevIiIpEratuCjSTl6ERFJDQX4iFGKXkREUkEBPkJ8JztFeBER2XUK8BGiBL2IiKSKAnzEKEUvIiKpoAAfIepFLyIiqaIAHyF6HryIiKSKAnzE6HGxIiKSCgrwEaIUvYiIpIoCfIQoQS8iIqmiAB8xytCLiEgqKMBHiJnpHLyIiKSEAryIiEg/pAAfMWq/i4hIKijAR4gZivAiIpISCvARohvdiIhIqijAR4wa8CIikgoK8BFipjvZiYhIaijAR0iG7mQnIiIpogAfIRlmtKoFLyIiKaAAHyFmRmtrX5dCRET6AwX4CMkw1IIXEZGUUICPkMwMpehFRCQ1FOAjxMxoVXwXEZEUUICPkIzgPje6VE5ERHaVAnyEZJiP8GrFi4jIrlKAj5BYC17n4UVEZFcpwEeItbXgFeBFRGTXKMBHSCxFr/guIiK7SgE+QpSiFxGRVFGAjxB1shMRkVRRgI8Qi2vBb6pt4PL732VrfVMflkpERPZECvAR0nYOPrgf/W0vlfPPuet4ePbqPiyViIjsiRTgIyT+HHxOpt88jS16Ao2IiHSPAnyEZGS0v0wuOwjwTc0K8CIi0j0K8BFicZ3s2gK8WvAiItJNCvAREr4X/T1vLOPm5xcD0NiibvUiItI9aR/gzWy6mX1kZuVmdk0H051lZs7MpvVWWcKXyV3/5IK24Y1K0YuISDeldYA3s0zgNuBUYCpwjplNTTBdIfAdYFZvlifcyS4r9gaob27pza8VEZF+KK0DPHA4UO6cW+qcawQeBM5IMN1PgF8B9b1ZmPC96GPn3wG2NTT35teKiEg/lO4BfhSwKvR+dTCsjZkdAoxxzv2jtwsTvhd9duaOFvzWegV4ERHpnnQP8JZgWFuPNjPLAG4Grup0RmaXmtlsM5tdUVHRo8KEU/Q5WTs2je5kJyIi3ZXuAX41MCb0fjSwNvS+ENgfeNnMlgNHAjMSdbRzzt3hnJvmnJtWVlbWo8KEO9llZYQDvFrwIiLSPeke4N8BJpnZeDPLAc4GZsRGOueqnXOlzrlxzrlxwEzgdOfc7N4oTPhe9FlK0YuIyC5I6wDvnGsGrgCeARYCDznn5pvZjWZ2+u4uz45z8K7tNrUAa6q289i7uh99f9bS6nB6TLCIpFBWXxegrznnngKeiht2bZJpT+zNsoRT9OFe9ADfe+gDvviJ0b359dJHFq6r4dsPvEd2ZgY3nXUg+48q7usiiUg/kPYBPkoykqTopf9pbmnluhnzaWhu5ZE5PjtTOjCXM297g8tOmsi5R+xFWWFu26WT8Zxz7cYt37SN0sJcBubu/JNesXkbD76zirMPG8PYIQN6Z4GkWyq3NbKkopahhXls2FrP6EH5DBmQS1aGYUbS7d4d2xtbmLu6ipEl+QwakMOayu3kZ2cyelA+GRnG2qrt/Pmt5WyorqesMJfCvGy2bGsE/GnBA0cX09LqyMww1tfUs6xiG9ubWmh1juYWR31zC9kZGew3qogTJpdx8JgSFq7bylF7D9nlsktqKMBHSNt18K07t+Blz7amajvvrazEOZi7uoo7X1vWNi4rw7jz/GkcMqaEG55cwK0vfMytL3zMcZNKuerTU1iysZaDxhRzxf3vkWHGgnU1FORkcsCoYorzs9lU28C7K6sAmDqiiKunTyEzw/hgVRUvLtrYNu6Pry3l2ImllA7Mpa6phTGDCgA4eEwJR00YQnFBdttpgvqmVrIzjawk9TA23YwP1vLCwo2cMnUY+40sYvyQAW0PTXLOUbO9maL8LFpaHW8s2cz66u1MGlbIIWNKUhLEomjxhq1s2trAviOKWFO1nU21DWyubWR7UwuPvbuagpws3ltZybbGxDewGjIgh0/vN4wjxg+htqGZw8cPZmLZQDIyjEXra9iyrZGt9c2sq9rOyi3b2bKtgcaWVg4aXUJzq+P1jzexrno762vqqW/a+S6YOVkZjCzOY21VPY0treRnZ7K9qWWnaR6NOy1YnJ9NblYGWRlGTlZGW924f9ZK7n5juf9cZgZv/uCTlA7MTcGalF2lAB8h4RZ8on1ffVMLedmZu7dQ0qaqrpEn567juImlDCvKIy87o8MgNW9NNZf99V2OmTiEB95etdP4/zh5Ep/ebxijBxVQnJ8NwM1fOZjPHjCCW15YzOzllZx52xuA74AZPkXf2NzKrGVb2t4fOLqYvOxM3l62hQvufqfd9wwryuX/vnwwf39/DQ/NTtyXoygvi72HDmTemmqagmcf5Gdn8s0TJnDRseOprW/muhnz+XjDVoYV5bFgbQ1DBuawfHMd4AN9zD7DCzlkr0G8vWwzSyq2UZibxda4mzUdOLqYYyaWAjCyJJ99hxdSWdfEkRMGU5iXnXSd9jbnHLUNzaytqmfysIE0tbS/ZDVszopKnv5wHWurtzNmcAEbqut5Z3kla6q2J53/hNIBLN9cx1F7l/L5g0awpmo7RXnZbGtoZl11PQ3NLWyqbWTG+2t3qjMTygawtGLbTvM0g4E5WTz14XoAygpzGVmSz36jijltEEyoAAAUg0lEQVR2YinbGprZvK2RwQU5tDpH+cZaNmxt4JiJpVx20kRGFufR2NLKxpoGRhTn0dzq+wAtqail1fn+IUX5WYwODgjj1Te1MGvZFuYs38LRE0sZMiCnq6tbepmpY0/qTZs2zc2e3f2O9s8v2MA37p3Nk1ccyw8f/5AP11S3G//mNZ9kZEl+qoqZNqrqGsnMMPKzM5O2SDvS3NLK9x/+gCfeX9tu+OHjBvO/Xz6Iqrom9hlRyNvLtjB/bTX3zVxJY3Mr62vqycvOaGtFnXnwSPYaXMDKLXVc9ekpjBmceIcZs7ZqO799qZzBBTnMW1vNladMZtSgfDLNKCnIZuWWOqrqmmhobuXgMSXkZGXQ0NzCX95awfy1NYwdUsCxE0s5dOygtgORlZvrWFe9nSEDc/hwTTUlBTnMWV7J3DXVvLrY379hfOkASgqy2VrfTPnG2qTlG1WSz5EThnDlpyYxd3U1r3xUwdJNtXy0fis19c3kZWdw+PghrK/2qeF9RxQxeVghVXWN/GPuOpZu2jlYDcjJ5KxDR/OZ/YczcehA1lbVs2VbA7UNLdw3cwXF+dkcNWEIQwbmUL29icptTZwwpYzi/GzeKN9EbUMzU4YXcvykMjJDt3t2zvHyRxXc8OR8MswYUZJHQ1Mrza2O/UcVsXDdVuasqEy4nPnZmeRkZdDU0sqgghw+NXUYM5duZtH6rYA/MI89AXKf4YWcOGUo44b47Zyfncnw4jxGFOeTkQFHTRjSpcxFfVMLc1ZUUpSXzfurKlm0fivLNm1j2rjBTB42kJZWx8ShAykrzGVoYR7gT8XUNbawz/DCPTI7YmZznHO99qyPdKQA3wt6GuBfXLSBi+6Zzd8vP4b/enRu2w4k5h/fPrbfd8BataWOax6by9ePHMvUEcV+R9zcyrw11UwdWcRdry3jjINHMqFsYLvPvbBwA+NLB7Qb/t7KSl5ctJHfvFjeNuyiY8bz48/u25ZG7kxNfRP3vLGc/3vOP9nvsHGD2FrfvNO2SeaJy49hW0Mzk4YNbNsRR1XltkZKCrLbBYd5a6q57aVyVldu5xf/dgD7jSympr6JwtyspEGktdVRU9+EczAoSWuutdUxd001o0rymbemmtWVdbQEw/7xwToaW1rJyjBanGvLXAwvymN9TdfuFl2cn8340gHUN7XQ2NzadjAxcehABuRmsbSiluzMDLIzjS3bGsnPzuTovUspyMlkQG4WZYW5LN+8jdysTNZXb6epxfeLqW9qYfbySgYPyOGcw/fivKPGUlKQQ1VdIwNys5Rh2wUK8KmnFH2EhO9F39TSypETBvOj06by+d++DsCm2oa+LF5KXPv3eQwqyOG4SaUU52czelAB+TmZbK5tYN7aGi65dzaNza28Ub456Tx+/cLHPP+9E3h3ZSVFeVm8Xr6J+2aupDg/mxHFeZQV5vLjz07lC797c6fP/umNZWyqbeDnXzyAAQk6pIX9/KmF/OHVpQAcNLqYey8+oi2VDlC+cStXPfQBizfUkplh1DU2c95R4/jytDHkZGUwelD+HrXDTxSM9x9VzO/PPbTdsKJOUugZGUZJQcdp2owM4+AxJQCctM/QduN+cOq+PL9wA4vW1VCQm8VBo0uorGvkrENHk52ZwYerq1m8YSvF+dlMGV7IG+WbWFtdzwGjihlVks/STbU8/u4aFq3fSmNLK0V5WZwwuYzjJpVy7pFjd9omdY3NZGVkJE3Fx6trbCYnM6NdNmiIzjlLBKkF3wt62oJ/ZXEF5//pbR7996O58m/vc+jYQfzi3w7ggOuepbGllbzsDGb98JR2QSaR2oZmquoak54z64qVm+v44u/f4PZzD2XauMHd+qxzrq33beygpamllYvueYfXPt7Ubtq87Az++Z3jOPl/X2kbttfgAlZV1rU755ydaTS1OArzsmhtdTQ0+/RqWGyasGMnlnLJ8RM4YXIZzjluf2Upv/zXIgC+eMgoLjp2PFNHFOGADTX1DMjJorggm5lLN3P2HTMB3wntngsP6zBoNTS3kJPZ8Tl5EUlOLfjUUws+QmJZYxe04LMyjNysTN758SkcdMOz1De18vuXl3DNqft0OJ9L753Nm0s2U/6zU7t0znlTbQNNLa2MKN5xfv+VjyvYVNvILc9/zH3fOKJL5d9a30RNfTN3vbaMP73he4mfvM9Qrp6+Dz98/MO2c5xDBuSwObgcp76plS/d/lbbPEoH5vKv7x5HQY6vmvPWVLNxaz1H7+07ZOVlZzJnRSXn/nEWza0tDBmQw4DcLB649EhaWx2Pvrua0YMK+P7DH3DFSRP5/memtM3bzPj3E/emrDCX7z/8AY+9t4bH3luz03LkZ2cyeEAOew0uaFeWjuRm7TktdRFJDwrwERK70U1Lq6OpxZEdpAyL8nZspsogMCazaksdby7x6e35a2s4aEwJ/5y7jhuenM+lx0/gG8dN2Okz1zw6l482bOW+i49g6aZtnDRlKHOW+x7ar5dv4v1VVW3p1I58/a63eX9VVbthLyzayAuLNra9f/hbR3FYKCPwmxc+5n+fW8zJ+wzljvOmUVvf3C6g+j4H7fsdHDp2EK/854kU5WeTl53Z7prw754yGYCzDk1+U6CzDh3NWYeO5qkP13Hl396nobn9pUTbm1pYU7WdBy45skvBXUQkirT3ipBYdnfxxlo21TaQGQwIp31rOnmy3Pcf/qDt9VtLNzOudACX3/8uAD/950K+esRe7YLWTc8s4vmFPgCfcNPLALx29UnMXlHJCZPLeH9VFb97qZw7zkueOXtlcQWPzFndLrhfcPQ4po0bxPUzFrT1HfjD1w9tF9wBLj9pIgW5WZy8z1AyM4zigq5dIjW0aEeHtZ6mxU87YASnHTCCVVvqaGhuYUKpv9a4tqGZVVvq2HdEUY/mKyISBQrwERJ7gtz/e2IeACu21O00TWcPnglfG/2Lpxcxd3X7FvXLH1Vw2gEjAPjrrBXc9tKSneZx3K9eAuDCY8Zz0JgSbn3hYxZv2MrkYYUJv/PqRz5gQ40P4rd85WAmDytk3xH+Up0TpwxlffV2Jg5N/NmMDOPiY8d3uEy9Lf5ytYG5WQruIrLH0+3SIiQz7tKtRB0gO3o2fHj6rx6xF0DbzS9itzB9et56Wlsda6u286PH57VNP27Izh3ypo0dxIVHj2NATia/fv7jhN9Z29DcdnvLgpxMzjh4JFNHFrW1qgfmZiUN7iIi0nvUgo+QrC5cm705yTn41lbHOXf6Xt/Xfm4qw4ryuH/Wyrbx8274DD94bC4z3l/Lt+6bw7MLNrSNm3HFMUwdUcTmbY1U1TVx7l2zmDZ2EPuNLCIrM4OLjx3PrS+W89ZPnuPxy47mzSWbuePVpTxx2TG8tXQzTS2Ouy88jANHFasXuYhIRCjAR0h8Cz7s7gsO48J73mFjTQOtrW6nG7Wsqdrelp4fUZyX8NK26fuP4IG3V7UL7rN+eDLDgvPZw4ryGFaUxzs/OqXd575x/ARufbGcLdsaufz+d9m0tZH1NfUcdOOzABTmZXHsxFLdP19EJEK0R46Q+CfIhTP0J+0zlBtO34/GltaErfhP3bzjOvLhwc1eZv7gZP/ZKWWAv01mYdzNXYYVdX53taK8bG4660AA5q2p2eluYvuNLFJwFxGJGO2VIyQ+Rd8adw4+dh/6RA+zCD81KnY9+/DiPD766XTuDHrA52T5RzuCvxb9e5+a3OWyfWnaGBbeOL3t/eOXHc1lJ+7NlGGFfOuEvbs8HxER2T2Uoo+QzIz2x1stcXdq2yvo7f3lP7zFU985jolDd9x3fVhRLhtqGnjssqMZXryjVR5/A5bvnDyJmUtn8cClRybtFZ9Mfk4mL151Aq3OMXGof2LY1dM7vumOiIj0DbXgIyS+BT++dEC797EA39jcyrfum9NuXEur45zD9+ITew3q8DuO3ruUZT8/rdvBPWZC2UD1ihcR2QMowEdIrJNdSXCzl+tP36/d+PycHa3x9dU7zoPHniFdVti1B16op7uISP+nAB8hsRZ8Q1MrA3IyO3wSWW3DjhveXHH/e4A/ry4iIgIK8JESa8E3trQmvWSuINSKbw3O0T8XXPbWGHdPdRERSV8K8BESu1Vt7FGriQwNpeHXVG1nY+iStS9NS/6AFRERSS8K8BGSGboOPr5Hfcwfz5/GPsN9J7ePN25l2aZtbeM6el65iIikFwX4CAn3ok9235iJQwv526VHAVC+sZbfvewfFnPeUWN7vXwiIrLnUICPkHBaPitJCx6guCCbssJcFm+o5ZXFFQBckuA57yIikr4U4CMkM3T5WgfxHfC3h523prrtfVcvkRMRkfSgAB8hGRlGrBHfUQse4IBRxXy8sRYzOP+osR1eUiciIulHAT5iYoG9syfH7j+qmJZWh3MwtAsPjBERkfSiAB8xsSfKddaCP3B0cdvrQeo9LyIicRTgIybWk76jZ8MDDA+12gcFt7YVERGJUYCPmNzgXHpnAd7MyM3ym2+QblErIiJxFOAjJha0OwvwAPuO8M92D9++VkREBBTgI6c7Af62r32CC44e1xboRUREYrL6ugDSXm5W11L0AKNK8nd6pKyIiAioBR85udlBC17PbBcRkV2gAB8xsRR9VqYCvIiI9JwCfMTEUvQZasGLiMguUICPmLwgRZ/VhXPwIiIiyaR1gDez6Wb2kZmVm9k1CcZ/z8wWmNlcM3vBzHr9maxtLXgFeBER2QVpG+DNLBO4DTgVmAqcY2ZT4yZ7D5jmnDsQeAT4VW+Xq+0cvAK8iIjsgrQN8MDhQLlzbqlzrhF4EDgjPIFz7iXnXF3wdiYwurcL1daLXgFeRER2QToH+FHAqtD71cGwZC4Gnk420swuNbPZZja7oqKix4XqznXwIiIiyaRzgE8UQV3CCc3OBaYBNyWbmXPuDufcNOfctLKysh4Xqjt3shMREUkmne9ktxoYE3o/GlgbP5GZnQL8CDjBOdfQ24WKteAt4fGHiIhI16RzC/4dYJKZjTezHOBsYEZ4AjM7BPgDcLpzbuPuKFTsHHxLa+vu+DoREemn0jbAO+eagSuAZ4CFwEPOuflmdqOZnR5MdhMwEHjYzN43sxlJZpcysRR9U2vCswUiIiJdks4pepxzTwFPxQ27NvT6lN1dprzgefAtLQrwIiLSc2nbgo+qWAu+WSl6ERHZBQrwERPrZNeoFryIiOwCBfiIGZjnz5rUN7X0cUlERGRPpgAfMQNzfYDf3qgALyIiPacAHzGFQQu+rrG5j0siIiJ7MgX4iCnI8efg1YIXEZFdoQAfMQNyfAs+M1N3shMRkZ5L6+vgo6ikIJurp09h+n7D+7ooIiKyB1OAjxgz47ITJ/Z1MUREZA+nFL2IiEg/pAAvIiLSDynAi4iI9EMK8CIiIv2QAryIiEg/pAAvIiLSDynAi4iI9EMK8CIiIv2QOafnjqeamVUAK3r48VJgUwqLsyfQMqcHLXN66Okyj3XOlaW6MOlMAT5izGy2c25aX5djd9Iypwctc3pIx2WOKqXoRURE+iEFeBERkX5IAT567ujrAvQBLXN60DKnh3Rc5kjSOXgREZF+SC14ERGRfkgBXkREpB9SgI8IM5tuZh+ZWbmZXdPX5UkVMxtjZi+Z2UIzm29m/xEMH2xmz5nZx8H/QcFwM7Nbg/Uw18w+0bdL0HNmlmlm75nZP4L3481sVrDMfzOznGB4bvC+PBg/ri/L3VNmVmJmj5jZomB7H9Xft7OZXRnU63lm9oCZ5fW37WxmfzKzjWY2LzSs29vVzM4Ppv/YzM7vi2VJNwrwEWBmmcBtwKnAVOAcM5vat6VKmWbgKufcvsCRwOXBsl0DvOCcmwS8ELwHvw4mBX+XAr/f/UVOmf8AFobe/xK4OVjmSuDiYPjFQKVzbiJwczDdnujXwL+cc/sAB+GXvd9uZzMbBXwHmOac2x/IBM6m/23ne4DpccO6tV3NbDBwHXAEcDhwXeygQHqPAnw0HA6UO+eWOucagQeBM/q4TCnhnFvnnHs3eL0Vv9MfhV++PweT/Rk4M3h9BnCv82YCJWY2YjcXe5eZ2Wjgs8Afg/cGfBJ4JJgkfplj6+IR4ORg+j2GmRUBxwN3ATjnGp1zVfTz7QxkAflmlgUUAOvoZ9vZOfcqsCVucHe362eA55xzW5xzlcBz7HzQICmmAB8No4BVoferg2H9SpCSPASYBQxzzq0DfxAADA0m6y/r4hbgaqA1eD8EqHLONQfvw8vVtszB+Opg+j3JBKACuDs4LfFHMxtAP97Ozrk1wP8AK/GBvRqYQ//ezjHd3a57/PbeEynAR0Oio/h+df2imQ0EHgW+65yr6WjSBMP2qHVhZp8DNjrn5oQHJ5jUdWHcniIL+ATwe+fcIcA2dqRtE9njlzlIMZ8BjAdGAgPwKep4/Wk7dybZMqbDskeOAnw0rAbGhN6PBtb2UVlSzsyy8cH9r865x4LBG2Ip2eD/xmB4f1gXxwCnm9ly/OmWT+Jb9CVBKhfaL1fbMgfji9k5JRp1q4HVzrlZwftH8AG/P2/nU4BlzrkK51wT8BhwNP17O8d0d7v2h+29x1GAj4Z3gElB79scfEedGX1cppQIzjHeBSx0zv1faNQMINaT9nzg76Hh5wW9cY8EqmOpwD2Fc+4HzrnRzrlx+G35onPua8BLwFnBZPHLHFsXZwXT71GtG+fcemCVmU0JBp0MLKAfb2d8av5IMysI6nlsmfvtdg7p7nZ9Bvi0mQ0KMh+fDoZJb3LO6S8Cf8BpwGJgCfCjvi5PCpfrWHwqbi7wfvB3Gv7c4wvAx8H/wcH0hr+iYAnwIb6Hcp8vxy4s/4nAP4LXE4C3gXLgYSA3GJ4XvC8Pxk/o63L3cFkPBmYH2/oJYFB/387ADcAiYB7wFyC3v21n4AF8H4MmfEv84p5sV+CiYNnLgQv7ernS4U+3qhUREemHlKIXERHphxTgRURE+iEFeBERkX5IAV5ERKQfUoAXERHphxTgRURE+iEFeBERkX7o/wPijhndMePkdgAAAABJRU5ErkJggg==
"
>
</div>

</div>

<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Probability After Last Trial: 0.37
</pre>
</div>
</div>

<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Probability After Last Trial: 0.375201
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">simulate_derangements</span><span class="p">(</span><span class="n">deliveries</span> <span class="o">=</span> <span class="mi">25</span><span class="p">,</span> <span class="n">trials</span> <span class="o">=</span> <span class="mi">1000</span><span class="p">)</span>
<span class="n">simulate_derangements</span><span class="p">(</span><span class="n">deliveries</span> <span class="o">=</span> <span class="mi">25</span><span class="p">,</span> <span class="n">trials</span> <span class="o">=</span> <span class="mi">1000000</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Probability After Last Trial: 0.375
</pre>
</div>
</div>

<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Probability After Last Trial: 0.368094
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">simulate_derangements</span><span class="p">(</span><span class="n">deliveries</span> <span class="o">=</span> <span class="mi">100</span><span class="p">,</span> <span class="n">trials</span> <span class="o">=</span> <span class="mi">1000</span><span class="p">)</span>
<span class="n">simulate_derangements</span><span class="p">(</span><span class="n">deliveries</span> <span class="o">=</span> <span class="mi">100</span><span class="p">,</span> <span class="n">trials</span> <span class="o">=</span> <span class="mi">1000000</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Probability After Last Trial: 0.359
</pre>
</div>
</div>

<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Probability After Last Trial: 0.367922
</pre>
</div>
</div>

</div>
</div>

</div>
    </div>
  </div>
</body>

 


</html>
