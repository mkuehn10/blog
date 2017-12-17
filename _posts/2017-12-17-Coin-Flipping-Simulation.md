---
layout: post
title: Coin Flipping Simulation
excerpt: When teaching anyone about probability, one of the most accessible and obvious examples of a random event is a coin flip.  I created a coin flipping simulation to show how the short-run and long-run behavior differs and forms the basis of the concept of probability.
---

<html>
<head><meta charset="utf-8" />
<title>coin_flipping_simulation</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
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
<p>When teaching anyone about probability, one of the most accessible and obvious examples of a random event is a coin flip.  I created a coin flipping simulation to show how the short-run and long-run behavior differs and forms the basis of the concept of probability.  The definition of probability according to the Annotated Teacher's Edition: The Practice of Statistics textbook is</p>
<blockquote><p>The probability of any outcome of a chance process is a number between 0 and 1 that describes the proportion of times the outcome would occur in a very long series of repetitions (Tabor, 2014).</p>
</blockquote>
<p>Using the example of a coin flip, I will create several simulations in Python to show differences between short-run and long-run probability.</p>

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
<span class="n">plt</span><span class="o">.</span><span class="n">rcParams</span><span class="p">[</span><span class="s1">&#39;figure.figsize&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="mi">9</span><span class="p">,</span> <span class="mi">6</span>
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
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">coin_flip_simulation</span><span class="p">(</span><span class="n">simulations</span> <span class="o">=</span> <span class="mi">5</span><span class="p">,</span> <span class="n">trials</span> <span class="o">=</span> <span class="mi">10</span><span class="p">):</span>
    <span class="n">final_probabilities</span> <span class="o">=</span> <span class="p">[]</span>
    <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">simulations</span><span class="p">):</span>
        <span class="n">heads_probabilities</span> <span class="o">=</span> <span class="p">[]</span>
        
        <span class="n">number_of_heads_total</span> <span class="o">=</span> <span class="mf">0.0</span>
        
        <span class="k">for</span> <span class="n">j</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="n">trials</span> <span class="o">+</span> <span class="mi">1</span><span class="p">):</span>
            <span class="k">if</span> <span class="n">np</span><span class="o">.</span><span class="n">random</span><span class="o">.</span><span class="n">randint</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">2</span><span class="p">)</span> <span class="o">==</span> <span class="mi">0</span><span class="p">:</span>
                <span class="n">number_of_heads_total</span> <span class="o">+=</span> <span class="mf">1.0</span>
                
            <span class="n">heads_probabilities</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">number_of_heads_total</span> <span class="o">/</span> <span class="nb">float</span><span class="p">(</span><span class="n">j</span><span class="p">))</span>
        
        <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">heads_probabilities</span><span class="p">)</span>
        <span class="n">final_probabilities</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">heads_probabilities</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">])</span>
        
    <span class="n">plt</span><span class="o">.</span><span class="n">axhline</span><span class="p">(</span><span class="n">y</span><span class="o">=</span><span class="mf">0.5</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;black&#39;</span><span class="p">,</span> <span class="n">linestyle</span><span class="o">=</span><span class="s1">&#39;dotted&#39;</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="nb">str</span><span class="p">(</span><span class="n">simulations</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; Runs of &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">trials</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; Coin Flips&#39;</span><span class="p">)</span>    
    <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
    <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Largest probability after &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">trials</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; flips: &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="nb">max</span><span class="p">(</span><span class="n">final_probabilities</span><span class="p">)))</span>
    <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Smallest probability after &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">trials</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; flips: &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="nb">min</span><span class="p">(</span><span class="n">final_probabilities</span><span class="p">)))</span>
    <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Median probability after &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">trials</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; flips: &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">median</span><span class="p">(</span><span class="n">final_probabilities</span><span class="p">)))</span>
    
<span class="n">np</span><span class="o">.</span><span class="n">random</span><span class="o">.</span><span class="n">seed</span><span class="p">(</span><span class="mi">123</span><span class="p">)</span>

<span class="n">coin_flip_simulation</span><span class="p">()</span>
<span class="n">coin_flip_simulation</span><span class="p">(</span><span class="n">simulations</span> <span class="o">=</span> <span class="mi">1000</span><span class="p">,</span> <span class="n">trials</span> <span class="o">=</span> <span class="mi">10</span><span class="p">)</span>
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
<pre>Largest probability after 10 flips: 0.7
Smallest probability after 10 flips: 0.4
Median probability after 10 flips: 0.6
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
<pre>Largest probability after 10 flips: 1.0
Smallest probability after 10 flips: 0.0
Median probability after 10 flips: 0.5
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The preceding code creates a function that runs 5 total simulations of flipping a coin 10 times.  The function keeps a running probability of the number of heads after each coin flip.  The plot shows how the running probability total varies over the 5 simulations and 10 coin flips in each simulation.  In the short-run of only flipping the coin 10 times, a wide array of probabilities result (from 0.4 to 0.7).  This shows that probability in the short-run has much more variability than the long-run probability. The second run of the simulation shows how a small number of trials can be likely to show extreme results.  Notice that with 1000 simulations, the results include both trials in which all heads were tossed and no heads were tossed.</p>
<p>The following are the results of conducting the same simulation using more coin flips per simulation.  With 100 coin flips, there is still variation; however, it is apparent that the probabilities are converging on what one would expect (0.5) especially compared to the simulation with 10 coin flips.  Increasing the number of coin flips by a factor of 10 all the way up to 100,000 shows that the long-run probability of flipping a coin does converge on 0.50.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">coin_flip_simulation</span><span class="p">(</span><span class="n">trials</span> <span class="o">=</span> <span class="mi">100</span><span class="p">)</span>
<span class="n">coin_flip_simulation</span><span class="p">(</span><span class="n">simulations</span> <span class="o">=</span> <span class="mi">1000</span><span class="p">,</span> <span class="n">trials</span> <span class="o">=</span> <span class="mi">100</span><span class="p">)</span>
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
<pre>Largest probability after 100 flips: 0.56
Smallest probability after 100 flips: 0.4
Median probability after 100 flips: 0.47
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
<pre>Largest probability after 100 flips: 0.66
Smallest probability after 100 flips: 0.3
Median probability after 100 flips: 0.5
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
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">coin_flip_simulation</span><span class="p">(</span><span class="n">trials</span> <span class="o">=</span> <span class="mi">1000</span><span class="p">)</span>
<span class="n">coin_flip_simulation</span><span class="p">(</span><span class="n">simulations</span> <span class="o">=</span> <span class="mi">1000</span><span class="p">,</span> <span class="n">trials</span> <span class="o">=</span> <span class="mi">1000</span><span class="p">)</span>
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
<pre>Largest probability after 1000 flips: 0.514
Smallest probability after 1000 flips: 0.482
Median probability after 1000 flips: 0.505
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
<pre>Largest probability after 1000 flips: 0.545
Smallest probability after 1000 flips: 0.449
Median probability after 1000 flips: 0.5005
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
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">coin_flip_simulation</span><span class="p">(</span><span class="n">trials</span> <span class="o">=</span> <span class="mi">10000</span><span class="p">)</span>
<span class="n">coin_flip_simulation</span><span class="p">(</span><span class="n">simulations</span> <span class="o">=</span> <span class="mi">1000</span><span class="p">,</span> <span class="n">trials</span> <span class="o">=</span> <span class="mi">10000</span><span class="p">)</span>
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
<pre>Largest probability after 10000 flips: 0.5062
Smallest probability after 10000 flips: 0.4958
Median probability after 10000 flips: 0.4972
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
<pre>Largest probability after 10000 flips: 0.5197
Smallest probability after 10000 flips: 0.486
Median probability after 10000 flips: 0.4997
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">coin_flip_simulation</span><span class="p">(</span><span class="n">trials</span> <span class="o">=</span> <span class="mi">100000</span><span class="p">)</span>
<span class="n">coin_flip_simulation</span><span class="p">(</span><span class="n">simulations</span> <span class="o">=</span> <span class="mi">1000</span><span class="p">,</span> <span class="n">trials</span> <span class="o">=</span> <span class="mi">100000</span><span class="p">)</span>
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
<pre>Largest probability after 100000 flips: 0.50032
Smallest probability after 100000 flips: 0.49688
Median probability after 100000 flips: 0.49805
</pre>
</div>
</div>

<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAXcAAAEICAYAAACktLTqAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADl0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uIDIuMS4xLCBodHRwOi8vbWF0cGxvdGxpYi5vcmcvAOZPmwAAIABJREFUeJzt3XmcHGW59vHfXdXds2cPIQuQAAEMKqA5HNwRAYGjcBQV8KCiIIryuqAouACCKyooigviEZEji4gKGsUFEBVBgigkIYEQlgwJyWSbzN7dVff7R9WEZjKdmYQZZmpyfT+fztTyVNdTXZ2rq596usrcHRERGVuCka6AiIgMPYW7iMgYpHAXERmDFO4iImOQwl1EZAxSuIuIjEEKdxkTzGxfM7vfzNrM7EMjXZ/Rxsx2N7N2MwuH+HkvMLNrhnMdsmMU7qOYmZ1pZgvNrMfMrupn/uvMbKmZdZrZ7Wa2R8W8GjP7XzPbbGZPm9lZg122n/U8bmZd6X/cp83sKjNrHNKNfe4+Adzh7k3uflnfmWb2NjO7K93eO/qZf6CZ3ZfOv8/MDqyYZ2b2FTNbnz4uNjMb7mX7Y2avN7M70w+xFjP7s5kdO9CL4+5Punuju0cDle1nnYeaWZzu/97HLUO5Dhl6CvfRbRXweeB/+84wsynATcBngUnAQuD6iiIXAHOBPYDXAp8ws6MGuWx/3ujujcCBwEHAuTu6UcNkD2DxNuZvAL4BfLnvDDMrAL8CrgEmAj8GfpVOBzgd+G/gAODFwBuA9z0Py/at51uAnwFXA7OAacB5wBu3sd1DZVUa3L2P52Od8ly4ux6j/EES8Ff1mXY6cFfFeAPQBeyXjj8FHFkx/yLgusEs28/6HwcOrxi/GPhNxfgdwGkV46cAf60Yd+D9wCPARuBywNJ5ewN/BlqBdcD123gdjiUJ8E3pOl+QTr8NiIBuoB3YZxvPcRrJEX7ltCPT18sqpj0JHJUO3wWcXjHvVODu4V62Tx0tnXf2NrYtAD4DPAGsJfkQGJ/Om53uh1zFPrsI+BvQBvwemFLleQ8FmqvMuwC4Zhvr+BLwj3T//gqYlM6rJflQW5/uz3uBaSP9f20sPXTknl37A//uHXH3DuBRYH8zmwjMqJyfDu8/0LIDrdTMZgFHA8u3s75vAP6D5Aj2bcDr0+kXkQTLRJKj0W9VWe8+wLXAR4CpwALgFjMruPthwF+AMz05qnx4O+u2P/CAp6mTeoAqrxdbv5bDtWylfYHdgBu3sR2npI/XAnsCjcC3t1H+7cC7gV2AAvDxbZTdUe8E3kPyfiwDvU1m7wLGk2zTZJIP/65hWP9OS+GeXY0kR0OVWoGmdB595vfOG2jZan5pZm3ASpKjwvO3s75fdvdN7v4kcDtJ8w5AiaRJZYa7d7v7X6ssfwLJt4U/uHsJ+BpQB7x8O+vRn4Fej77zW4HGtO18OJetNDn9u3ob2/E/wCXuvsLd20mazk40s1yV8j9y94fdvQu4gWf2SX9mmNmmisfbtlG20k/cfVF6APFZ4G3pCddSuk17u3vk7ve5++ZBPqcMgsI9u9qBcX2mjSP5it1eMd533kDLVvPf7t5E8hV9P2DKdtb36YrhTp75APoESZPDP8xssZm9p8ryM0iaGwBw95jkg2bmdtajPwO9Hn3njwPa0yPu4Vy20vr07/RtbMezXqN0OEfSNt+favukP6vcfULF44ZtlK20sk998iTvnZ8AtwLXmdmq9ERzfpDPKYOgcM+uxSRNHACYWQOwF7DY3TeSHOEdUFH+AJ454Vh12YFW6u5/Bq4iOXLu1QHUV4zvOtiNcPen3f297j6D5ETjd8xs736KriI5wu+ts5F8pX9qsOvahsXAiyt7sZCc/Oz39WLr13K4lq20jCQoj9/GdjzrNQJ2J2kKWbONZYbbbhXDu5Mcsa9z95K7f87d55F8+3oDSROODBGF+yhmZjkzqwVCIDSz2oqv2L8AXmhmx6dlziNpv12azr8a+IyZTTSz/YD3koTyYJYdyDeAIyq67f0LeLOZ1afBfOp2bONb03Z8SE62OsnJ0b5uAP4r7cKZBz4G9JCcsBzMesJ0W3NAkL6WvUeKd6Tr/JAlXUjPTKfflv69GjjLzGaa2Yx03Vc9D8tukR7pnwV81szebWbjzCwws1ea2RVpsWuBj5rZHEu6qn6R5AR1eTCv0TA52czmmVk9cCFwo7tHZvZaM3tR2kSzmST01YVyKI30GV09qj9IeiJ4n8cFFfMPB5aSnIi6A5hdMa+GpAvlZpIjt7P6PHfVZfupx+NU9JZJp30X+Hk6PIXkpGgbSe+LC9i6t8zeFeNXAZ9Phy8mOfpuJzmpe/o26vEmYAlJu/Sfgf0r5t1BRY+dfpY9pZ/X8qqK+QcB96Wvxz+BgyrmWVrPDenjYp7dw2VYlq2yHUeRnDxuB1rS7f6vdF5A8kG9Mp13DTAxnTebrXuyVO3h1Gedh/Lce8tsBm4h7ZEDnETybaSD5P15We9yegzNo7c7mojIkLLkx2LXuPuVI12XnZGaZURExiCFu4jIGKRmGRGRMUhH7iIiY1C1X64NuylTpvjs2bNHavUiIpl03333rXP3qQOVG7Fwnz17NgsXLhyp1YuIZJKZPTFwKTXLiIiMSQp3EZExSOEuIjIGKdxFRMYghbuIyBg0YLhbcpPltWa2qMp8M7PLzGy5mT1gZi8Z+mqKiMj2GMyR+1UkV6Kr5miSGzHPJbk353efe7VEROS5GLCfu7vfaWazt1HkOOBqT65jcLeZTTCz6e6+rduB7bD3X/5pNk2bypzb7+RLl980HKsQEcm8oWhzn8mzb6XVTJVbn5nZ6Wa20MwWtrS07NDKuqaM547Jh1JqmLFDy4uI7AyGItytn2n9Xo3M3a9w9/nuPn/q1AF/PduvuPeZrb/ViogIDE24N/Ps+yTOIrmXo4iIjJChCPebgXemvWYOAVqHq71dREQGZ8ATqmZ2Lck9FKeYWTNwPpAHcPfvAQuAY4DlQCfw7uGqbJ+aPT+rERHJoMH0ljlpgPkOfHDIajRIusWIiEh1mf2FqineRUSqymy4i4hIddkNd3WFFBGpKrvhLiIiVWU33F1t7iIi1WQ23F3NMiIiVSncRUTGoMyGu4iIVJfZcNdxu4hIdZkNd8W7iEh1mQ13V7iLiFSV2XDX1WVERKrLbLibjtxFRKrKbLiLiEh1CncRkTFI4S4iMgZlNtx1OlVEpLrMhruIiFSX4XBXbxkRkWoyG+7qCikiUl1mw13ZLiJSXWbDXZcfEBGpLrPhLiIi1SncRUTGIIW7iMgYpHAXERmDFO4iImNQhsNdvWVERKrJcLjr6jIiItVkN9x14C4iUlVmwz30zFZdRGTYDSohzewoM1tmZsvN7Jx+5u9uZreb2f1m9oCZHTP0VRURkcEaMNzNLAQuB44G5gEnmdm8PsU+A9zg7gcBJwLfGeqKblWv4V6BiEiGDebI/WBgubuvcPcicB1wXJ8yDoxLh8cDq4auiiIisr0GE+4zgZUV483ptEoXACebWTOwAPh//T2RmZ1uZgvNbGFLS8sOVPcZsZrcRUSqGkxE9tcC0rcf4knAVe4+CzgG+ImZbfXc7n6Fu8939/lTp07d/tqKiMigDCbcm4HdKsZnsXWzy6nADQDu/negFpgyFBUUEZHtN5hwvxeYa2ZzzKxAcsL05j5lngReB2BmLyAJ9+fW7iIiIjtswHB39zJwJnAr8BBJr5jFZnahmR2bFvsY8F4z+zdwLXCKuw/rT0gLnh/OpxcRybTcYAq5+wKSE6WV086rGF4CvGJoqzYQdYYUEakmw31OFO4iItVkONx14TARkWoyG+6mI3cRkaoyG+6xwl1EpKrMhruiXUSkusyGu4iIVKdwFxEZgxTuIiJjUObCPUhb28thNMI1EREZvTIX7k1WD8B46ka4JiIio1fmwt3SbjKWvaqLiDxvMpyQ6gwpIlJNhsNdRESqyWy467hdRKS6zIa7K95FRKrKbLiLiEh1mQ13XfBXRKS6zIZ7HcWRroKIyKiV2XDXsbuISHWZDXedUBURqS6z4W6ma8uIiFST4XDXkbuISDWZDfeefH6kqyAiMmplNtzbahpGugoiIqNWZsO9Rl0hRUSqymy46+oyIiLVZTbcXd3cRUSqyly4W5rqhWL7CNdERGT0yly49/4yNejpGeF6iIiMXhkM915qcxcRqWZQ4W5mR5nZMjNbbmbnVCnzNjNbYmaLzeynQ1tNERHZHrmBCphZCFwOHAE0A/ea2c3uvqSizFzgXOAV7r7RzHYZrgqLiMjABnPkfjCw3N1XuHsRuA44rk+Z9wKXu/tGAHdfO7TVrJS0uZuuCikiUtVgwn0msLJivDmdVmkfYB8z+5uZ3W1mR/X3RGZ2upktNLOFLS0tO1bhSU8CUL/r0zu0vIjIzmAw4d7fmcu+h805YC5wKHAScKWZTdhqIfcr3H2+u8+fOnXq9tYVgCAsAxDm9AtVEZFqBhPuzcBuFeOzgFX9lPmVu5fc/TFgGUnYD5tSMODpAhGRndZgwv1eYK6ZzTGzAnAicHOfMr8EXgtgZlNImmlWDGVF+8pHRdo3qq+7iEh/Bgx3dy8DZwK3Ag8BN7j7YjO70MyOTYvdCqw3syXA7cDZ7r5+uCoNUMrnWf7AMJ63FRHJsEG1bbj7AmBBn2nnVQw7cFb6GFYdNAFw6+TX8cCqZq58VouRiIhABn+huooZANw37kAeXbd0hGsjIjI6ZS7cH604T9u9zHBdHlJEZCuZC/dKZ678NRef8+mRroaIyKiTuXD3im73Sw96Ed/nEDZeMGMEayQiMvpkLtw32uQtwyHOLTefy8lrPqLmGRGRCpkL92dxuOM13+KDD/6cvc7/Da8/63fEsUJeRCTT4b6kYRVOTIPVsKznHdw67gT2/NQC7l4xrF3sRURGvUyH+2tWnMj3X/ZRbj/sUB751a5csvs7YWLAZ792Hb/57JEjXT0RkRGTuQu07O8PsNheDIDH7UzumAkWcOObTmefm//A/6u5nGjOLB57dCqLPrI3rcGL+UXhNdz6gitZ8OYF7NakHz2JyNiXuXDPU9oyPO0lF/DGv8+kbQ7sVrOIEw/8G9c+fTEtj99COf8ifr+mBo/XMCdYwMlr9ue6BWfQXTue+u7WLc8xY7/DOOG8DxOE4UhsjojIsMhcuFd2hZy0TyuT9mnlL3e+lCfSyxCctOsnuCb4Gcsn3AGF3ZmcqyHYtIY/7nMkh9/+S+q6N7P/0ctZtGAvxnUXWf3Qn7j07bcBEBQiZr/uKcbt3gHAqrt3oenfEdODNprudyxd9+baAk8cUMPKmZ3s+oqQRzfNY2bDanZvagZ3crlGXvqSn0I8iXxuHE8u2czDd69hn/0Dpj1xOU3eTBg47P8mfOZ8yuP3IairIQiSDxizZ7bR3Z8Zd4fe4TiGINOtaiIyjDId7lfzHk7mR1vGL11/PGdMuYW79lzCTS9921bLPjj3Jc+MnPHsedZeonDXGsKlTrw04JjGvzM5B7ec+FqiIKDl9InM2rCGeR2PMOWJp7i7cx9yhQD/e8ATNbtgkeOhYd0RXp/D73uaA+N7GVdT5E8vOhheBBDDnGdWPO2RNXQ83kr71Ee2TCuUuqnr6KCULzBjzZOUc3kaO9uYsfoJegq1NHZtZreNjzGufTNPx1Opsx5wY01uMk1RBzli1tRMYf2EmbRZnrguT2NHB142ZnatJIpzrK3dhdoQClaiLijiboSxsyk3HotjGuihNT+Rrvx4GkLHgoBJgVNLQFfczYa4lmlBRBwYjaFRH0Tk4jJuBZrMmRzG4CGBGSGQD0LK7oT5AGKnPsjRGQU0WYGa+lqs1uiyAPIQEZPLFbDYyedyNDXlCcOAUrFEYAHEIV1BQJAzuoplYgsohCH5yCnU5gjyObpyAflcSF0YkLOQ2tpaLHa6ussUyzF5C6iJnMa6HOMn1ZGrCfFCQJAPITRKDrU1IV6K8cix0LB8iIX27A/b58Ddk7sipH89diwXPPMBbsmHvLtDnD4gmRfYs++y0Ds/nWeBPbMOGJL6SvbYSPUPnz9/vi9cuHC7lzvitqt40A589rRH/8b0NZu5+uVHD1X1MsPc8Yr/vFPaO0j+55fJB0WK5Trc8rTVhQQO+ZJTKJdoLHYRekzkIbXlEliRps6IUs6o7XG6a0JKYUA+ishFZYo5oxCVCcplugo1RAY1UZFcnN48JY4JcII4JoidmlIRDwIKUZFSkCMKQ+IgAE/qjEE5CIjdyHmZOAixMIZcTDEsQOCUyZMrR1gUE0QGQUy+GOFumDtB7NQVuwmJCOMyNVEp+aAqO24BoZcxj/Ec5LxEWHTycZkcEYQOHpAjoq5UwhzccsQGVgLciT0EizGPCUolDJJyntzmMQqMACfvJSwGN4gtIHDHwhg3JwpDSkGeoBwRkaOUy5GzMkHs4EZ3rga3HMVcnlJo5OMy7o5HRmQhURDigRHEjnlMLorAktcbd3J48nqS7Pbeg58gjrDeDw+z5C9OGEMUGJbuK9wJ3IkDiOKAXBzhgRG7ERNgkRN4RNkCYnJEBhZBSAT+zPK5uEx9qYfAIApDjBhiiAgIo3L64WQYcVLfINmewJOKB5EnX0pDww3Cchm3gCgGCDB3yrkcFsXEQUBMAAF4DvJxGTwmyEc4IRY5Zk4UB0QeQuh4DKHFWBwTY+SthANxkCcfRwSlmGRVIXEAFAyLnZCI2APcjCgIsJIRBVAmT5xzwtiT930xppTLU86HxBbipeT1doMoCClbmNTZwCMoNfTwhW9duWP/583uc/f5A5UbsSP3ZcuWcdVVV3HKKadQKpU44ogjOO200zj55JPp7OzkmGOO4YwzzuCEE06gtbWV4447jg996EO0jZ9IvHkjmy44m4a3voOal7+G303cl9Zvn0NDbhw1B7+CaO3TtH7pMzScfBqfbrqPaQ238rWvtfCud03kgAPqWLmyyKWXruONp+7Ln/c/h42PreXhb11N0/s+Sn6//SktX0bb5V+l6YNnk997X0pLF9P2/UsZ96FzyM3Zm+Kif9H+w28z7qOfIbf7bIr/Xkj7Vd9j3NkXkJsxi5777qbjmisZf+7nCXfZFb/nT+Su+yanfOal7DWplV/e1cQdNy6n/vzLYMJkuu/8E5N+cTFvuPC/Wdp4CG2338bGW37NqV98JWtq5/DgH5bz4G8X84qLP0iQC1n7u9u56/ered0l7yMix99//Tg9d9zKrK9+jXWNTXT+6gZ67voz+375s0zlcVb9/LeU7/838z//QTwHf71hCdGS+5lzwadZa1OIf/ptupavoOG8SwBo/8kVxE8+xsRPXURkOdp/9B3itU8z7pMXYh6z+cpvY5s30PixCwBo++4leLGHcR8+Nxn/9lcBaDrzbAA2f/NLWKGGpjOSi4Zu/vpF2LjxNL33QwC0fuV8wl2m0fjuDyTjX/gU+d32YMI7TqFoNWy66JPk99qXhre/B4BN53+M/LwDaDjhnQBs/PSHqXnJf1J//NuT8XM+SM3LXkP9ccm3t40ffx81h76e+jccD8CGj55G3euPpe6oY/FyiY1nn0HdMW+i7oj/wru72HTumTS98U00vfYwOttLbDzvY9S/6SQaXvUaotZNbPjcOVvee9GGdbRedA5NJ76T8Qe/FF+7iqe//EWa/uc9BPNfRXlVM5u/egGNp7yfwgHzKT/5OJsv/TyNp55J4YUHUn5sOZsv+/Jzfu9N/PhnqJ0+g+J9f6f1/65i1ifOJZi2K+333sOG637Kbp/6LEyeSuvdf6f1Z9ey6/mfJ5owlc6/3E77Tdcz4aJLscYmSrctoOOWn7P7F75MoTbHpj/+gQ2//S1zvvIV8qGx8fe3su73f2K/r32JHGXWL/gN6//8N+Z/5ZN0WS3NN/+BDXffx55fvpAyOVp+fjOd9y9m9ufPJyRizQ030bFkKbMv+AyO8fS1N1Jcvpw9PvtJzJ211/wfPSubmf2pjxMQs/pH19DTsp69zj4TDJp/8BPKm9uYe9Z7ic144ntXE/cU2fPDp1Imx+OX/wgnYK8PvpOQMo9+84eENQX2fP//UCLPiku+TziuiT1PO4EcZR66+AcUpk5h99PfRkzA8i9+k8bdprHXyW/EgcUXfYdxe89i35MOJyTmngt+yPh5e7LH2w7DgH9+5ltMOugF7PGOZP6953yTaS97MTOPex0xAQvP/jrTDj2Y3f/rEAznH2d9lV2PfBVv3XvaduXem9/8ZtatW8db3vKWQWds5pplHg/2ADZus8xb/Kf8LV7Cyf45Dppbz6q+941K7UILF/BpHqPIN6ONHPno9ezaPptHHy1y66Z1nHXPwxzz6BTub3uIL3Wv4gz/KHO8wGK6+SEbOGXRFwjunc4T7e38sbyUs/0DzPA8f1nRxC3da/m4v49dyjX8gzZ+1h7ynxs6aHjkjRz9rzZaNjzBt+5+jImN6/jjoo1cuX4CJ903j8k+gevXP8lNxZCXrs3B5H8Qrp7A0x0xpz75b6Lxa7l103pWdz/J25fdg9etZ+6mx/lrzyo+/MTXmdwzjd+tfph7Op/g/Y9cjQcRd69/jH93reeUx/5KZ66Nhk2P8FhbJ59cdhNRWORX6x/giY4NfGLtJ+iK67m+bRnrulv5yNPnU4qN6zcvY11HD6ev/CxYyM/aFtHR1cWpaz9OFOe5rnMJpbjEaZ0rieICPyqvoOQFTmi/gCIFbireS50HvH3TWsKgyA9KD9NUCnl31xJiAi6LVjC5WMvbWh8jFxT5VukhZnQ+xFs3LIZCia+XHmG37kd444bFRLmQy0qL2KunmcPbltFuTfwgepQ9e7qY376J0CKuKq9kn66/Mb+tFQeuKT/Fvj1/Y15bN0XLc1O0jhd0LeQFm4v0lANuLm9k767F7NVWIO7u5g9RK3v2LGdm5wSCzo3cWd7APp2LmNkWUuxo42/RBub1/JPZ7R10tLdzR7SRF3QvYkpHSFtXK+1RO/OKS5jT0UaxazW3R+uY3/UXpnc009G9mtujFg7uuYNdO1ewqWs1d0YtHNq1gD3a76a5eyO3R2t4VfcCpnb/k3XdzfwlfprDen7JLt2TebzUwl3xGl5TWsDE0iSeLK/iXl/HK6I7qY+nstIfYxFt7GlLafTVrIkfpYd29mIpDfFK1kRLWUobB5T/SVOpwJPlRSz1Vg4r/ZGanloeiR7iYW9j3/ISvNzAyriFLu9idrSCOChQjjfR5t1MitdSJs96h8hDNvl4aqIe8lGZfFxmatd6Qo+JixvwqJsZnWuICOkodhKVi+zasQ7DKRY30Rp1Mb1zLbEZbaUe4ihiYlcrTsDackwuiqntSTpSWATE4MVc8o2jHBJHId6VpxDHhCUnoETYCbEViKMclPMUu+vJeQRlIyhB3FVDp9Uny5ZD6MoR4ngUUizXsrE7uQ1od1wH5Qk8VtyHyALa40a8PIna4kwcozuuo608gTXFWThGl9ezIZpCvjgT85hynKer3Mi6nl1xM0pxnq5yAx2lyf2H0hDKXLPMrrf/a5vz/8+P73f6tC/8J+FT/wKc2vmnkZ918FZlOm77HPHmp+jK5yjmAsyhqbvIvXtOpzuf44UrW7hvzq7ko5hdW9vZZ/WGAX8o4BZgHg9y6ypYiBUaISyQm7oPXuoinDwXy9US97RBqQNytVi+DqubRG7KfpSeuhfiEqXH/5J8ZQ5rCCfuQbx5FdHmp0gaeQ08xsJCMhzmkvWUe/AwTxDWJEU8xiyAQh1mBTwq4l0bwGPifC1BkCeOeogaxgMBQU8HAQFERSh34uUuHCPO1xJbDg9ITgAHThBFEOQgX0+pYTwexURhDWaQix0jxAoFuuobKGN0BUZsUBNFhA5RWEMhMgphHguN2qhIFDj5ICAgxsvdhBQIcxFxAKWoTJyvgZyRyxWJiIlCIwohKJVwiuS9Czxp8gk8pBRERJY0tZQCp0RyAjs2II4IMDwMIIqTJhKLiAjIUSaMYkIzPE6OnopBnrKR/Ho6yCdNJ6WIUpinTEBsRhxEBETJ6x47eEwxH5DzGIsDuh0sLhMA5hGEQBQTxDGRW9L0YAGlMCAOnTCEQlSGckwUBAQWExKTKzuR5ZLmlCB5X5oZubhMFAREcbCl2ckJsQAKlLG0+cF7mxZ6m9kswEiaWGI3LE6aXiKDMjlKQQ2R5TECykFA4KWkbcsMLGmCcQuJkzYkzNKmHuL0Ts1G4BGYYR4QWNIMGZK+7m54EBBbSDksgJfJW5Q0jZE0k8UWJk0rBJh5WufktXOSJpcACC0i8BjzMhYYaY2ooUzOYsKgh8BKlAkJzJNmlqSxigAnF5fwwHAiAgIiN4ppM5mbEZsTkSf2HBuKEzj+c1dvfy6QgWaZofLmp//IsdN+QH7pmUzvKVLoOp8nDvnclvl73/ZtwnIj/AfJo4+O2uW033wZ9Z3dW6bVlcrUpT0un5r+ctp3ezt4RH5mF2+oqycf5rFg+7pODuXJrU3BJnqsm/VBF632GC9t3537uYO1e3dQKMVMm7gfj+SbmbKujcAeoW1cD/muBlrrA8ZtjphQLBI7eFCmpxZqyuvprAsp5mNiuom9Bw8a6W6oIfR2xnX3sCmsJ4zzlAoBLVMmsKG+iVxoNJY20u31BGETRpE4MDpDI4hgYrFMY1cHNeUi47pjsBy5oI4JxW6IY8aXisRhC5tq6igGETWBEdU00BD1UF90ar2bcURMaJhKOcwlpxLCBnJN48kXSli+FsvXYO3dWBRRspCOqItSXR1BUKAprKO+dhyNjZMIJ0wkCPJYTzdRdzdhGOL5mFxD8iGOlSl2dOJN48k3NEAck6uvpzBxIrnxTUkw5HJYTQ1xV3eyP/MBXu7GyxEelIA4acsP88QeARFR1E0ubCDMNREEOYKgbqv3gLvjxSKOY0FIkM8P7o0QlSEIt7Sre2/7ehThpRJeLifzgpCgkId8fstJ2qE6KeylEl58pnty73qS+kW9BYl7ilg+h/XOc8fCEI/jpJ5xjOVyEIY6ATxEMn3kfsiji/hl8wf546unUNc6h+5xj1Po2JU5d31pwOcpBz18YPcv0Fy7nlesfhf7tx7I3d7DX805hjyz5xTAAAANnUlEQVQvJmQDzsL2Zg6pKbEi2JXfhclx+uRiF68mx8vCOm6Z9WP2L+3O2vp9uG3cBCxs47AVq6grl+iICrSUa1nl4+nwKYyrybGpx2nBeRVwuG3iYBtHfdxISI7C3AnEG3sY9/o9KMxoJGgqEBTCIfvP+HxLeoQ8030zi9sgMtoM9sg9s+F+pP+GL/7+1bQecCJPT6utWn76BwpsOKNEzwudRXe9m1e3HcLfN8OFJ0wB4MRbfgmFaRzd1sFejQdSQwE3J06+VAINWz2nFUK8GD1rWmH3JiYeP5euxetp+3Mz3pPMz02rJz+tnvoXT6V2v0l4KcZySdc6EZHtNeabZTa1zKHt1x9izRE1/c5/4Ef7sLHxfTzw4WlsaghZGhTgldB7TH//f+zF9MYmeO2B/S7fy0tpu2R+cD8Yyk9rYNxhu1edbzn98EhEhl/mwj2Mk/7FJz+5B+adW/p4P3n7dCbsvZkVv9uN2vEnccvhc1myew1f3XcW75gxZYebNgYb6iIio0nmwn16W0zz+JBlG8ocf9wanmIyP158Ase+7Hd89M4vcfb4Os74zmt5vyW/m8gHau8VkZ1P5sK9lzuENc57b/0GsQXc+dQr+Fx7He/63mFbyoTKcxHZSWU23HtdY03cNCfk4tNfSaCjcxERIIM36+jbt+fBSbfw5bfMV7CLiFTI3pG7PfPnx1M+xiHFenKT60a0SiIio032wr2XQ2334cz7wLa7MoqI7Iwy2yxT27We2W2rydfXj2h9RERGo8yFexB1ATBt5S+4O9g8wrURERmdMtcsE8TJRYqemDieblaOcG1EREanzB25b+Fw+Iv3GOlaiIiMSoMKdzM7ysyWmdlyMztnG+XeYmZuZgNe1GZH9V5uwA3+44j+r90uIrKzGzDczSwELgeOBuYBJ5nZvH7KNQEfAu4Z6kr2JySisbHx+ViViEjmDObI/WBgubuvcPcicB1wXD/lLgIuBrr7mTdkem8AXJ/TyVQRkWoGE+4z4VlnLpvTaVuY2UHAbu7+6209kZmdbmYLzWxhS0vLdle2Ujk3rJ8hIiKZNphw7+93/VuuAmBmAXAp8LGBnsjdr3D3+e4+f+rUqYOvZeVzpLXJR2qSERGpZjDh3gzsVjE+C1hVMd4EvBC4w8weBw4Bbh7Ok6oAwcjcQEpEJBMGE+73AnPNbI6ZFYATgZt7Z7p7q7tPcffZ7j4buBs41t23/x56g9DbWwaPh+PpRUTGhAHD3d3LwJnArcBDwA3uvtjMLjSzY4e7gtXoIpAiItUN6heq7r4AWNBn2nlVyh763Ku1jbqkf0OibZYTEdmZZfAXqskhexiXR7geIiKjV+bCvbe3TByoXUZEpJrMhXuvpvbSSFdBRGTUyly4b7mee7eaZUREqsleuKfdZNbtolvriYhUk7lw72Vb3SpbRER6KdxFRMagzIX7V37xe45tLjK+rWOkqyIiMmplLtzntmzgvMU9mOnIXUSkmsyFu4iIDEzhLiIyBmU23ON+LzMvIiKQ4XDfch0CERHZSmbDXTfrEBGpLrPhXvDMVl1EZNhlLiE3TUjunbphStMI10REZPTKXLh3NCbXlOlqKIxwTURERq/MhbuIiAxM4S4iMgZlNtxdFw4TEakqs+GOesuIiFSV2YTUcbuISHWZDXf9PlVEpLrshXvvZQfika2GiMholtlwD2Olu4hINdkL9y3U6i4iUk2Gw11ERKrJbLi7TqmKiFSV2XBXfxkRkeoyF+6KdBGRgQ0q3M3sKDNbZmbLzeycfuafZWZLzOwBM/uTme0x9FXtw3VCVUSkmgHD3cxC4HLgaGAecJKZzetT7H5gvru/GLgRuHioK7o1hbuISDWDOXI/GFju7ivcvQhcBxxXWcDdb3f3znT0bmDW0FZTRES2x2DCfSawsmK8OZ1WzanAb/ubYWanm9lCM1vY0tIy+FpWaEx/mpoLoh1aXkRkZzCYcO/vHGa/bSJmdjIwH/hqf/Pd/Qp3n+/u86dOnTr4WlaYQBLquXCHFhcR2SnkBlGmGditYnwWsKpvITM7HPg08Bp37xma6omIyI4YzJH7vcBcM5tjZgXgRODmygJmdhDwfeBYd1879NXcmk6niohUN2C4u3sZOBO4FXgIuMHdF5vZhWZ2bFrsq0Aj8DMz+5eZ3Vzl6YaMLhsmIlLdYJplcPcFwII+086rGD58iOs1oMz9+kpE5HmUwYxUg4yIyEAyGO72rD8iIrK1DIZ7ItblB0REqspsuIuISHUKdxGRMSiz4R6r0V1EpKrMhruIiFSncBcRGYOyG+7qLSMiUlV2w11ERKrKYLjriF1EZCAZDPeEWmVERKrLYLinXSADdYUUEakmg+EuIiIDUbiLiIxBmQv33sYY1y9URUSqyly493JXuIuIVJPBcPeKf0VEpD8ZDPdeincRkWoyHO5qlhERqSbD4a4jdxGRajIb7op2EZHqMhvultmai4gMvwxGZNLWriN3EZHqMhjuaazrymEiIlVlMNwT+hGTiEh1mQ13ERGpLsPhrmYZEZFqMhvuinYRkeoyG+7qCykiUp0SUkRkDBpUuJvZUWa2zMyWm9k5/cyvMbPr0/n3mNnsoa6oiIgM3oDhbmYhcDlwNDAPOMnM5vUpdiqw0d33Bi4FvjLUFRURkcEbzJH7wcByd1/h7kXgOuC4PmWOA36cDt8IvM7MhqUjunV0DMfTioiMKYMJ95nAyorx5nRav2XcvQy0ApP7PpGZnW5mC81sYUtLyw5VuHM8xJsf5PHO9h1aXkRkZ5AbRJn+jsD79kQcTBnc/QrgCoD58+fvUG/Ged+9BIBL+MCOLC4islMYzJF7M7BbxfgsYFW1MmaWA8YDG4aigiIisv0GE+73AnPNbI6ZFYATgZv7lLkZeFc6/BbgNndd2UtEZKQM2Czj7mUzOxO4FQiB/3X3xWZ2IbDQ3W8Gfgj8xMyWkxyxnziclRYRkW0bTJs77r4AWNBn2nkVw93AW4e2aiIisqP0C1URkTFI4S4iMgYp3EVExiCFu4jIGGQj1WPRzFqAJ3Zw8SnAuiGsThZom3cO2uadw3PZ5j3cfepAhUYs3J8LM1vo7vNHuh7PJ23zzkHbvHN4PrZZzTIiImOQwl1EZAzKarhfMdIVGAHa5p2DtnnnMOzbnMk2dxER2basHrmLiMg2KNxFRMagzIX7QDfrHs3MbDczu93MHjKzxWb24XT6JDP7g5k9kv6dmE43M7ss3dYHzOwlFc/1rrT8I2b2rorpLzWzB9NlLhuu2x1uLzMLzex+M/t1Oj4nvZn6I+nN1Qvp9Ko3Wzezc9Ppy8zs9RXTR917wswmmNmNZrY03d8vG+v72cw+mr6vF5nZtWZWO9b2s5n9r5mtNbNFFdOGfb9WW8c2uXtmHiSXHH4U2BMoAP8G5o10vbaj/tOBl6TDTcDDJDcdvxg4J51+DvCVdPgY4Lckd7o6BLgnnT4JWJH+nZgOT0zn/QN4WbrMb4GjR3q703qdBfwU+HU6fgNwYjr8PeCMdPgDwPfS4ROB69Pheen+rgHmpO+DcLS+J0juKXxaOlwAJozl/Uxyq83HgLqK/XvKWNvPwKuBlwCLKqYN+36tto5t1nWk/xNs5wv7MuDWivFzgXNHul7PYXt+BRwBLAOmp9OmA8vS4e8DJ1WUX5bOPwn4fsX076fTpgNLK6Y/q9wIbucs4E/AYcCv0zfuOiDXd7+S3DfgZelwLi1nffd1b7nR+J4AxqVBZ32mj9n9zDP3UZ6U7rdfA68fi/sZmM2zw33Y92u1dWzrkbVmmcHcrDsT0q+hBwH3ANPcfTVA+neXtFi17d3W9OZ+po+0bwCfAOJ0fDKwyZObqcOz61ntZuvb+1qMpD2BFuBHaVPUlWbWwBjez+7+FPA14ElgNcl+u4+xvZ97PR/7tdo6qspauA/qRtyjnZk1Aj8HPuLum7dVtJ9pvgPTR4yZvQFY6+73VU7up6gPMC8z20xyJPoS4LvufhDQQfJVuprMb3PaBnwcSVPKDKABOLqfomNpPw9kRLcxa+E+mJt1j2pmlicJ9v9z95vSyWvMbHo6fzqwNp1ebXu3NX1WP9NH0iuAY83sceA6kqaZbwATLLmZOjy7ntVutr69r8VIagaa3f2edPxGkrAfy/v5cOAxd29x9xJwE/ByxvZ+7vV87Ndq66gqa+E+mJt1j1rpme8fAg+5+yUVsypvMP4ukrb43unvTM+6HwK0pl/JbgWONLOJ6RHTkSTtkauBNjM7JF3XOyuea0S4+7nuPsvdZ5Psr9vc/X+A20lupg5bb3N/N1u/GTgx7WUxB5hLcvJp1L0n3P1pYKWZ7ZtOeh2whDG8n0maYw4xs/q0Tr3bPGb3c4XnY79WW0d1I3kSZgdPZhxD0svkUeDTI12f7az7K0m+Zj0A/Ct9HEPS1vgn4JH076S0vAGXp9v6IDC/4rneAyxPH++umD4fWJQu8236nNQb4e0/lGd6y+xJ8p92OfAzoCadXpuOL0/n71mx/KfT7VpGRe+Q0fieAA4EFqb7+pckvSLG9H4GPgcsTev1E5IeL2NqPwPXkpxTKJEcaZ/6fOzXauvY1kOXHxARGYOy1iwjIiKDoHAXERmDFO4iImOQwl1EZAxSuIuIjEEKdxGRMUjhLiIyBv1/RXts5ZGVAbwAAAAASUVORK5CYII=
"
>
</div>

</div>

<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Largest probability after 100000 flips: 0.50479
Smallest probability after 100000 flips: 0.49579
Median probability after 100000 flips: 0.499955
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
