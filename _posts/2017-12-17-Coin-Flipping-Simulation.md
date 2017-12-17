---
layout: post
title: Coin Flipping Simulation
---
<!DOCTYPE html>
<html>
<head><meta charset="utf-8" />
<title>coin_flipping_simulation</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
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
<p>When teaching anyone about probability, one of the most accessible and obvious examples of a random event is a coin flip.  I created a coin flipping simulation to show how the short-run and long-run behavior differs and forms the basis of the concept of probability.  The definition of probability according to the Annotated Teacher's Editio: The Practice of Statistics textbook is</p>
<blockquote><p>The probability of any outcome of a chance process is a number between 0 and 1 that describes the proportion of times the outcome wuld occur in a very long series of repetitions (Tabor, 2014).</p>
</blockquote>
<p>Using the example of a coin flip, I will create several simulations in Python to show differences between short-run and long-run probability.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="o">%</span><span class="k">matplotlib</span> inline
<span class="n">plt</span><span class="o">.</span><span class="n">rcParams</span><span class="p">[</span><span class="s1">&#39;figure.figsize&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="mi">12</span><span class="p">,</span> <span class="mi">8</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[27]:</div>
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
        
    <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="nb">str</span><span class="p">(</span><span class="n">simulations</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; Runs of &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">trials</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; Coin Flips&#39;</span><span class="p">)</span>    
    <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
    <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Largest probability after &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">trials</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; flips: &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="nb">max</span><span class="p">(</span><span class="n">final_probabilities</span><span class="p">)))</span>
    <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Smallest probability after &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">trials</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; flips: &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="nb">min</span><span class="p">(</span><span class="n">final_probabilities</span><span class="p">)))</span>
    <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Median probability after &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">trials</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; flips: &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">median</span><span class="p">(</span><span class="n">final_probabilities</span><span class="p">)))</span>
    
<span class="n">np</span><span class="o">.</span><span class="n">random</span><span class="o">.</span><span class="n">seed</span><span class="p">(</span><span class="mi">123</span><span class="p">)</span>

<span class="n">coin_flip_simulation</span><span class="p">()</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The preceding code creates a function that runs 5 total simulations of flipping a coin 10 times.  The function keeps a running probability of the number of heads after each coin flip.  The plot shows how the running probability total varies over the 5 simulations and 10 coin flips in each simulation.  In the short-run of only flipping the coin 10 times, a wide array of probabilities result (from 0.4 to 0.7).  This shows that probability in the short-run has much more variability than the long-run probability.</p>
<p>The following is the result of conducting the same simulation using more coin flips per simulation.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[28]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">coin_flip_simulation</span><span class="p">(</span><span class="n">trials</span> <span class="o">=</span> <span class="mi">100</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAsYAAAHiCAYAAADrvQoIAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADl0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uIDIuMS4xLCBodHRwOi8vbWF0cGxvdGxpYi5vcmcvAOZPmwAAIABJREFUeJzs3XV4VFf+x/H3mXgyURISglNcS4vWbetOjZbaVnerW29367rtVrfK1oUade+vSqFYcHciBEKcuMyc3x83gYS4ldD5vJ6HZ5K5Z+49SSB88s33nmOstYiIiIiI+DrXnp6AiIiIiEhnoGAsIiIiIoKCsYiIiIgIoGAsIiIiIgIoGIuIiIiIAArGIiIiIiKAgrGISIcyjteMMbnGmHl7ej6tZYw52BizpgPO+7ox5oGOvIaISHMpGItIp2KM+cUYU2qMKaz602BQMsbcY4ypqBqXZ4z53Rgz8Y+cbzMcBPwF6GGtHbf7QWNMN2PM58aYdGOMNcb02e14kDHmVWPMDmPMNmPMDbsdP9IYs9oYU2yM+dkY07uxyRhjzjXGJFV9zrYaY74xxhzU1Adhrf3NWjuoOR9wPde8yBjjqfE1LTTGPNue1xARaQ8KxiLSGV1trXVX/WkqKL1vrXUDscDPwIcdP70W6Q1sttYWNXDcC3wLTGrg+D3AgKrzHA7cYow5FsAYEwt8DNwJxABJwPsNTaQqVD8FPATEA72A54FTWvQRtc7sGl9Tt7X26j/gmiIiLaJgLCJ/CtbaSuAdoLsxJg52Vipn1hxXVZXtX/X268aY54wxXxljCowxc40x+1QdM8aYJ40x240x+caYpcaY4fVd2xiTWFX1zTHGrDfGXFb1/CXAy8DEqirpvfXMO8Na+zwwv4EP7QLgfmttrrV2FfA/4KKqY6cDK6y1H1prS3FC9ChjzOB65hgJ3AdcZa392FpbZK2tsNZ+Ya29uWpMkDHmqarqdXrV20FVxw4zxqTVON9mY8xNVZ+XfGPM+8aY4AY+hmZp4Bq3G2NWVrWivFZ9DWNMrDHmy6rfFOQYY34zxuj/NBFpE30TEZHO6GFjTJYxZpYx5rDmvMAYE4gTIrOB3BZcazJwLxANrAcerHr+aOAQYCAQBZxdde76vAukAYnAGcBDxpgjrbWvAFeyq1p6dwvmhTEmuuqcS2o8vQQYVvX2sJrHqqrSG2ocr2kiEAx80sgl/wlMAPYFRgHjgH81Mv4s4FigLzCSXYG9PZ0HHAPsg/O1qJ7PjTif8zic6vcdgO2A64uID1EwFpHO5lagH9AdmAp8UV3FbcBZxpg8oAS4DDijqnrcXB9ba+fVqDjvW/V8BRAODAaMtXaVtXbr7i82xvTE6SO+1Vpbaq1djFMlPr8Fc2iIu+oxv8Zz+VXzqj6eT201j9fUBchq4nNzHnCftXa7tTYT5weGxj6OZ6y16dbaHOALdn3u6jOhqrpb/WdCI2NretZam1p1jQdxfpAB5+vTDehdVfn+zVqrYCwibaJgLCKdirV2rrW2wFpbZq19A5gFHN/ISz6w1kbhVA2XA/u38JLbarxdTFUYtdb+BDwLPAdkGGOmGmMi6nl9IpBjrS2o8VwyTrBvq8Kqx5rXjQAKahzffU41j9eUDcQaY/wbuV4iztyrJVc915B6P3cNmGOtjarxZ04jY2tKbWA+j+FU+L83xmw0xtzWzPOJiDRIwVhEOjsLmCYHWZsFXAHcY4zpVvV0ERBaPcYYk9CiC1v7jLV2f5zWhIHAzfUMSwdijDE1q7S9gC0tuVYD188FtuK0NVQbBayoentFzWPGmDCcloMV1DUbKAVObeSS6Tg3+VXrVfXcntSzxts751P1w9ON1tp+wEnADcaYI/fEBEXkz0PBWEQ6DWNMlDHmGGNMsDHG3xhzHk6f73fNeb21dnXV2FuqnloCDDPG7Ft109Y9LZjLWGPMeGNMAE7ALgU89VwzFfgdpy862BgzErgEpy2judcKBoKq3g3a7Sa2N4F/GWOiq26quwx4verYJ8BwY8ykqtfcBSyt+jzsPs/8quPPGWNONcaEGmMCjDHHGWMerRr2btW14qpWvLgLeLu5H0cHucoY08MYE4PTR/w+gDHmRGNMf2OMAXbgfG3qfH1ERFpCwVhEOpMA4AEgE8gCrgFOtda2ZNOHx4DLjTFdrbVrcVZi+AFYB8xs9JW1ReCsAJGL8yv8bOA/DYydDPTBqWZ+Atxtrf2/FlyrhF1tE6ur3q92N84NdcnAr8Bj1tpvAar6gCfh9N7mAuOBcxq6iLX2CeAGnBvYMnHaFK4GPq0a8gDOkm9LgWXAwqrn9qRpwPfAxqo/1fMZgPN1LcSphj9vrf1lT0xQRP48jO5VEBGRzsgYsxm41Fr7w56ei4j4BlWMRURERERQMBYRERERAdRKISIiIiICqGIsIiIiIgIoGIuIiIiIANDYDkgdKjY21vbp02dPXV5EREREfMSCBQuyrLVxTY3bY8G4T58+JCUl7anLi4iIiIiPMMYkNz1KrRQiIiIiIoCCsYiIiIgIoGAsIiIiIgIoGIuIiIiIAArGIiIiIiKAgrGIiIiICKBgLCIiIiICKBiLiIiIiAAKxiIiIiIigIKxiIiIiAigYCwiIiIiAigYi4iIiIgACsYiIiIiIoCCsYiIiIgI0IxgbIx51Riz3RizvIHjxhjzjDFmvTFmqTFmv/afpoiIiIhIx2pOxfh14NhGjh8HDKj6cznwQtunJSIiIiLyx2oyGFtrZwA5jQw5BXjTOuYAUcaYbu01wXblqYSSXKgs39MzEREREZFOpj16jLsDqTXeT6t6rvNJnQP/7uM8ioiIiIjU0B7B2NTznK13oDGXG2OSjDFJmZmZ7XDpFvIPdh4ry/74a4uIiIhIp9YewTgN6Fnj/R5Aen0DrbVTrbVjrLVj4uLi2uHSLeQf5DxWlv7x1xYRERGRTq09gvHnwAVVq1NMAPKttVvb4bztTxVjEREREWmAf1MDjDHvAocBscaYNOBuIADAWvsi8DVwPLAeKAYu7qjJtpkqxiIiIiLSgCaDsbV2chPHLXBVu82oI+2sGCsYi4iIiEhtvrXz3c6KsVopRERERKQ2HwvGqhiLiIiISP18Kxj7BTqPqhiLiIiIyG58KxgbA35BqhiLiIiISB2+FYzBaadQxVhEREREduODwVgVYxERERGpyweDsSrGIiIiIlKXDwZjVYxFREREpC4fDMaqGIuIiIhIXT4YjFUxFhEREZG6fDAYq2IsIiIiInX5YDBWxVhERERE6vLBYKyKsYiIiIjU5YPBOEjBWERERETq8MFgrIqxiIiIiNTlg8FYPcYiIiIiUpcPBmNVjEVERESkLh8MxqoYi4iIiEhdPhiMg8FTBtbu6ZmIiIiISCfig8E4yHlUO4WIiIiI1OCDwTjYeVQ7hYiIiIjU4IPBWBVjEREREanLB4OxKsYiIiIiUpcPBmNVjEVERESkLh8MxqoYi4iIiEhdPhyMVTEWERERkV18MBhXt1KoYiwiIiIiu/hgMFbFWERERETq8sFgrIqxiIiIiNSlYCwiIiIigk8HY7VSiIiIiMguPhiMtVybiIiIiNTlg8FYFWMRERERqcsHg7EqxiIiIiJSl+8FYz9VjEVERESkLt8Lxi4X+AWqYiwiIiIitfheMAannUIVYxERERGpwUeDcZAqxiIiIiJSi48GY1WMRURERKQ2Hw3GqhiLiIiISG0+GoyDwVO+p2chIiIiIp2IjwZjVYxFREREpDYfDcbqMRYRERGR2nw0GKtiLCIiIiK1+WgwDlYwFhEREZFafDQYB6mVQkRERERq8dFgrIqxiIiIiNTmo8FYFWMRERERqc1Hg7EqxiIiIiJSm48GY1WMRURERKQ2Hw3GVRVja/f0TERERESkk/DRYBzkPGpbaBERERGp4qPBONh5VJ+xiIiIiFTx0WBcVTFWn7GIiIiIVPHRYKyKsYiIiIjU5uPBWBVjEREREXH4ZjD2C3QeVTEWERERkSq+GYxVMRYRERGR3fhoMK6++U4VYxERERFx+Ggw1s13IiIiIlKbjwZjLdcmIiIiIrX5aDBWxVhEREREavPRYKyKsYiIiIjU5qPBWBVjEREREanNR4OxKsYiIiIiUpuPBmNVjEVERESkNh8NxqoYi4iIiEhtvhmMXX7gClAwFhEREZGdfDMYg9NOoWAsIiIiIlV8OBgHqcdYRERERHZqVjA2xhxrjFljjFlvjLmtnuO9jDE/G2MWGWOWGmOOb/+ptjNVjEVERESkhiaDsTHGD3gOOA4YCkw2xgzdbdi/gA+staOBc4Dn23ui7U4VYxERERGpoTkV43HAemvtRmttOfAecMpuYywQUfV2JJDeflPsIP7BCsYiIiIislNzgnF3ILXG+2lVz9V0DzDFGJMGfA1c0y6z60j+QR3SSjH3i41889Kydj+viIiIiHSs5gRjU89zdrf3JwOvW2t7AMcDbxlj6pzbGHO5MSbJGJOUmZnZ8tm2pw6oGFuvZcVv6aSuzMHa3T9FIiIiItKZNScYpwE9a7zfg7qtEpcAHwBYa2cDwUDs7iey1k611o6x1o6Ji4tr3YzbSwdUjDM276BkRzkVZR7KSyrb9dwiIiIi0rGaE4znAwOMMX2NMYE4N9d9vtuYFOBIAGPMEJxgvIdLwk3ogIrxxsW7PuSCHK14ISIiIrI3aTIYW2srgauB74BVOKtPrDDG3GeMOblq2I3AZcaYJcC7wEW2s/cSdEDFeNOSLELCAwAozNGNfSIiIiJ7E//mDLLWfo1zU13N5+6q8fZK4MD2nVoHa+eKce62IvIyihlzfB+Svt5MgYKxiIiIyF7Fx3e+a7+KcXUbxdCDEnH5GQpzFYxFRERE9iY+HIzbt2K8aUkWXXuHEx4TjDs6SD3GIiIiInsZHw7G7VcxLsovI2PTDvqOclbacEcHq8dYREREZC/jw8G4qmLcDvcIblqSBUDffZ0V6sJjgilQK4WIiIjIXsWHg3EgYMFT0eZTbVqSRURcCDHdwgBwxwRRlFeO1+Nt87lFRERE5I/hw8E42HlsY59xeWklaWty6DcqFmOcTQLDY4KxXktRfnlbZykiIiIifxAF4zb2GaesyMFbaXf2FwO4Y5xzq89YREREZO/hw8E4yHlsY8V44+JMgt0BJOwTufM5d7RzbvUZi4iIiOw9fDgYt71i7PF4SV6eTd+RsbhcZufz4dHVFWMt2SYiIiKyt/DhYNz2inH62jzKSyrpOyq21vOBIf4Ehfpr9zsRERGRvYgPB+O2V4w3Lc7EP9BFzyExdY65o4MpzFXFWERERGRv4cPBuG0VY2stm5Zm0XNIDP6BfnWOh8cEqWIsIiIishfx4WDctuXaMlMKKMwto9++cfUed8do9zsRERGRvYkPB+PqinHr2h02LcnCGOgzIrbe4+ExwZQVV1JeWtnaGYqIiIjIH8iHg3HbKsbJy7NJ2CeSYHdAvcfdMU7w1soUIiIiInsHHw7GVRVjT8t3p/NUeslOLyShb2SDY9xVS7ZpLWMRERGRvYMPB+PWV4xztxXjrbTE9nQ3OCZcu9+JiIiI7FUUjFvRY5ydVgBAbI/wBseERQZiDFqZQkRERGQv4cPBuPXLtWWmFeIX4CIqPqTBMS4/F2FRQVrLWERERGQv4bvB2K/1q1JkpRbSJTEMl1/jn75wLdkmIiIistfw4WDsDy7/FleMrbVkpRUQ26Ph/uJq7phgtVKIiIiI7CV8NxiD02fcwopxUV4ZZUWVxPZsuL+4WniM00phvba1MxQRERGRP4iPB+OgFleMs1ILAZpXMY4OxuuxFBe0fEk4EREREflj+XgwDm55MK5akaJLM1spQCtTiIiIiOwNfDwYB7W4lSIrtZDIuBACg/2bHBuu3e9ERERE9ho+HoxbXjHOTCtsVhsF1Nj9ThVjERERkU7Px4NxyyrG5aWV7MgsaXTHu5qCQv0JCPKjUNtCi4iIiHR6Ph6MW1Yxzk6rvvGu6RUpAIwxuGOC1UohIiIishfw8WDcsopxVnUwbmbFGJw+Y7VSiIiIiHR+Ph6MW1YxzkotIDgsgLCooGa/xh0TrFYKERERkb2Abwdjv8AWV4y79HBjjGn2a8KjgygpqKCy3NOaGYqIiIjIH8S3g3ELKsZej5fs9KIWtVHArrWMC3PVZywiIiLSmfl4MG5+j3FeRgmeCi9xzVyqrVq4lmwTERER2Sv4eDBufsW4ese72J7NW5Gi2q6KsYKxiIiISGfm48G4+RXjrNRCXP6GqITQFl3CHRUEBgq0ZJuIiIhIp+bjwbiqYmxtk0OzthQS0y0MP7+Wfcr8AlyERgRSqFYKERERkU5Nwdh6wVvZ6DBrLVmpBS1uo6gWHhOsHmMRERGRTs7Hg3HVesRN9BkX7yinpKCC2BbeeFfNHR2sVSlEREREOjkfD8bOjXFN9RlnpTo73sW1cKm2au6q3e9sM1o2RERERGTP8PFg3LyKcfWKFF16tLKVIjoYT4WX0sKKVr1eRERERDqejwfjZlaM0woJ7xJMUIh/qy4THqO1jEVEREQ6Ox8Pxs2sGKcWtrq/GJxWCtDudyIiIiKdmY8H46YrxhVlHvK2F7d6RQpQxVhERERkb+Djwbi6YtxwMM7eUgiWNlWMg90B+AW4tJaxiIiISCfm48G4umLccGDNSnNWpGhLMDbGVK1lrFYKERERkc7Kx4Nx0xXjrLRCAkP8Ce8S3KZLuaODKMxVxVhERESks/LxYNyMivHmbGK7h2CMadOl3FEBFGQVtekcIiIiItJxfDwYN10xzknNpQtr2nyp8IKFFBd4qCwqbPO5RERERKT9+XgwbrxiXL4jnwobgputbb5UdOlCAPLWrWvzuURERESk/SkYQ4MV45KMbQCEere37TqVZcQU/AZAzobUtp1LRERERDqEjwfjxjf4KN6eBUCoZ0vbrpO+mCizGYOH3LS8tp1LRERERDqEjwfjxivGxdlOiA0tT27bdVJm42cqiQzIJDersm3nEhEREZEO4dvB2M8fjF/DFeNc50a50MpUqGjDUmupcyFmH6IjSsnZEdL684iIiIhIh/HtYAxO1bihYJxfhsFDsKsAilrZZ+z1Qsoc6DWR6FgX+WVd8JRqPWMRERGRzkbB2D+o4VaKgkpCXPm4jBcKWxmMs9dBSQ70mkBMjyi8+JO/XitTiIiIiHQ2CsaNVYyLDKGufOedwozWnT9ljvPYawIx/XoAkLMhpXXnEhEREZEOo2DcWMW41J/QkArnnbYE49Au0KU/UYMGAV5y03Jady4RERER6TAKxv5BDVeMy0MIdfs777S2lSJlNvSaCMYQ4A4nPCCX3O0VrZysiIiIiHQUBeMGKsbW66W4MoLQcH+n4tuainFBBuRugl4Tdj4V4y4kJz+4LTMWERERkQ6gYNxAj3FZdhZe/AmNDAJ3fOsqxqlV/cU9dwXj6FjIK43BW6H1jEVEREQ6EwXjBirGxRlOhTg0OgzcXVtXMU6Z4wTvbqN2PhWTGIGHQHZsXN/qKYuIiIhI+1MwbqBiXJyVDUBol8iqinErg3H3MeAfuPOp6H7dAchdv7lV0xURERGRjqFg3FDFOHsHAKFxsVUV40ywtvnnLS+CrUug1/haT0cPHAhATmpW6+csIiIiIu1OwbihinFuEQChCfFOxbiyBMoKmn/etCSwHmdFihqComMI888lN6O80ZeXFlbw1fNL2ZFV0vxrioiIiEirKRg3VDHeUYYf5QRGxUBYV+fJltyAlzoXMNBjbJ1DMWEF5OQF1n1NDRsWbWfz0iw2Ls5s/jVFREREpNUUjBuqGBd6CfEvxLhcTisFtKzPOGU2xA+DkKg6h6K7WHJLY7CVngZfnrzc6XHetiG/+deUnUorPHy9bCsVHu+enoqIiIjsJRSM/YPrrxgXG0IDq9oY3PHOY3ODsacSUudBz/H1Ho5JdFNpgylI3Vz/yyu8pK3OBWDbxnxsS3qbBWstN09fyt/fWcirMzft6emIiIjIXkLBuIGd74pLg3ZtB70zGDezlWL7CigvrNNfXC26TzcActdtrPd4+vo8Kso89BoaQ1F+OYW59W9ZLfV74dcNfLEknVh3EM/+vJ7cosb7uUVERERAwdipGFuPU+WtobgilNCwqndCosHl3/yKccpc57HGjnc1xQyqWpkiuf7+4eTl2fj5u9j/uD6Ab7VTZKVlsHVDSqtf/+OqDB77bg0njUrknUvHU1RWyTM/rWvHGYqIiMiflYKxf5DzWKNq7C2voMTjdraDBnC5nBvwmlsxTpkNET0gqme9h4PjuhLit4PcjPpXnEhenk33QVHE94vAP8DFto2+EYx35OSz8tRJbDjrHMpK6lbxm7J+ewHXvbeYYYkRPDppJIMSwjl7bE/enpPM5qyiDpixiIiI/Jk0KxgbY441xqwxxqw3xtzWwJizjDErjTErjDHT2neaHcg/2Hn07Pp1e0lmBuAiLDJo17jm7n5nrbOxR6/6+4urxYTlk5Nbd2WK/Mxi8jKK6T28C35+Lrr2ifCZYPzz9f8irjCbLkW5/Prsmy16bX5xBZe+kURwgIup548hJNAPgH8cNZAAPxePfre6I6YsIiIifyJNBmNjjB/wHHAcMBSYbIwZutuYAcDtwIHW2mHA9R0w145RT8W4eLtTGQ6NDt81zh0PRc2oGOenQkF6g/3F1aJjPOQWR2O9tVdNqF6NotewLgAk9IskK7WQyvKGV7D4M5j93lcMnPcD6w47hbS43gR98DYVZc3rDa70eLn63YVsySvhxSn7kxgVsvNY14hgLj+kH18v28aC5NyOmr6IiIj8CTSnYjwOWG+t3WitLQfeA07ZbcxlwHPW2lwAa20LFvzdw6orxjWDcWYOAKGx0bvGuZvZSpEyx3lsoL+4WkxCGOU2lOItabWeT16eTVR8KFFdQwFI6BeB12vZntyCzUX2MrnbsvE++gBbo7tx1H/uIujiS+lakMmMqe816/WPfLOa39Zl8cCpwxnTJ6bO8csO7kdceBAPfrVSK3yIiIhIg5oTjLsDqTXeT6t6rqaBwEBjzCxjzBxjzLHtNcEOt7NivGvlh+Kc6u2gu+waVx2MvU2si5syBwLDoevQRodF93FWushZu37ncxVlHrasyaP38F3XTegXCdBkO4W1lq9fWMqyX9IaHdcZ/Xbd7USW7CDuwYcJdYdy4AWnkR6TiJn2Op5G1noG+HTRFl6euYmLDujD2WN71TsmLMifG/8ykIUpeXy7fFu7zNl6vWy7737Srv9Hnar/n9l3K7bxlyd+5f9WtmBNbxERkb1Ec4Kxqee53ctu/sAA4DBgMvCyMabOzhbGmMuNMUnGmKTMzE6yo1t9FeO8YgBCEhJ2jXPHO6tXlOQ0fr7tqyBhBLj8Gh0WPaA/ADnJu6rQW9bk4qn01grGIeGBRMaFNBmMs7cUsmlJFit+29L4/DqZX1/5kAFLfmPTsWcx4ginL9vP3w8z5WK65W5l5uvTG3ztxsxC7vhkGeP6xPDPE4Y0ep0zx/RkYLybR75dTXll24KstZaMBx4kd9o0Cr79lty33mrT+fYGFR4vD3y5kiveWkByTjFXvbOQ39dn7elpST0yUwpIX5e3p6chIrJXak4wTgNqLq/QA0ivZ8xn1toKa+0mYA1OUK7FWjvVWjvGWjsmLi6utXNuX/VVjHdUEGBKCHBH7BrX3N3vstZCbP8mLxvaLZEgVyG524p3Ppe8PBv/ID8S+9f+mSKhX2STG32snefMK3tLEYW5LV/RYU/ITN1K0DOPkhbbk2Mern1P5yGXnUNGRFfKX38Fbz0V2dIKD1dPW0SQv4unJ+9LgF/jf5X9XIbbjxtCcnYx78xNbtO8s/77X3KnTSPm4otxH3442594krKNf96NRLbklXDWS7N3VuZn3nI4fWJDufTNJBanNh7AsgvLuPGDJbw+68/7+eksstIK+PqFpXzw0Hw+eXwhM95fS2XFn/veBBGR9tacYDwfGGCM6WuMCQTOAT7fbcynwOEAxphYnNaK+nev6GzqqxgXWkIDCmuPa87ud8U5UJwFsQObvKxxuYgJzSM316ksW2tJXp5Nz8HR+AXU/rIk7BNJSUEFO7LqD7zWa1mXlEFUvNOXnLKiiap2J+D1eplz9a2EVpTQ89FHCQwOqnXcP8CfirPPp0dWKrOnfVnn9Q9/vYqVW3fwnzNH0S0ypM7x+hw2KI4D+3fh6R/XkV9S0ap5Z7/+OlnPv0DkGZPoesvNJNx7DyY4mK233471/PlCyM+rt3PCM7+xLqOQ587dj3tOHkbXiGDeumQ8se4gLnptHmu21d//Pmt9Fsc9/RsfLUzjni9W8uKvG/7g2fuG7PRCvp26jPcfmM+WtXmMO6kvIw/vwbKf05j+yAJytmqpQhGR5moyGFtrK4Grge+AVcAH1toVxpj7jDEnVw37Dsg2xqwEfgZuttZmd9Sk21V9FeMSP0KDdguhzdn9LqtqI4lmBGOA6OhKcoqc6nDO1iIKckprtVFUS+jnVK4baqfYujGfwpwyxhzfB3d0EMkrOv+n/pfn36b/mvmknno+gw/Yt94xh151Ptlh0RS8PLVW1fjb5dt4Y3YylxzUlyOHxDf7msY4VeP8kgqe+mFti+ec99FHbH/k34Qfcwzd7r0XYwwBXbuScOedlCxZQs5rr7X4nJ1VpcfLo9+u5uLX55MYGcIX1xzECSO77TweHxHM25eMJ9DPxfmvzCUle9dvPio8Xh75ZjVTXplLeLA/X15zECeNSuSRb1YzdYbCcXvJyyjm+1dW8N7980hZmcOY4/tw/gMTGXtCXw4+eyAnXDWSovwyPnxoPit+29JuN55uT97BjPfXsmmpWmlE5M/HvzmDrLVfA1/v9txdNd62wA1Vf/Yu9VWMy4LoElVce1xzWimyq4NxnS6SekXHh1CaGk5JxjaSlzvBvL5gHJPoJiDIj20b8xk0PqHO8XXzMvAPcNF3VCzp6/JYn5SBx+PFr4n2gj0lKy0D99SnSU7Yh2PuvbHBcYHBQRROOo/ebz5L0qc/MO70o0nLLeaW6UsY2SOSW48d3OJrD+8eyeRxvXjj982cuX9PhiZGNP0iYMd337P1zrsum+ESAAAgAElEQVQIO/BAEh97FOO3q4c84oTjKfjuOzKffgb3YYcR1L/pVprm8HotXyxN56D+sXRxBzX9gnaSU1TONe8uZNb6bCaP68XdJw0lOKBuz3yvLqG8dcl4znppNlNemcv0KydSUuHh2vcWsyQ1j8njenHXiUMJCfTjybNGYa3loa9X4zKGSw/u94d9PH82hbmlzP9yE6tmb8MvwMV+R/dm9F96EewOqDWuz4hYzrlzHD+8tpJf3llDysocDp8ymOCwgAbO3Lj0dbkkfZNM6socMLDs5zQGjovn4LMG1rl2p1CSB4vehmUfQs9xcNjtEFp31RoRkZqaFYz/1HYG4xoV4wo3PcN225Uu0A0BoU1UjNeCXyBE9W7WpWN6x0ES5KxZS8pyN126u3FHB9cZ53IZ4vvWv9GHx+Nl/cLt9BkZS2CwP72HdWHlzHS2bcin+8DoOuNrKiksp6SggphuYY2Oa2+zbruPfSpKiXzkAfwDGv8reMi1F7P4wzfJe+FFKk45imvfXYTXwn8njybQv3XB/5ZjBvHt8m3c+dlyPrxiIi5XffeX7lI4axbpN91EyKhR9PjvM7gCa2/MYowh4Z672XhiEum33U6f997F+Lftn1alx8vN05fyyaItjOoZxQdXTCDIv/EbOtvDyvQdXP5WEtsLynjsjJGcOab+3RurDUoI5/WLx3Ley3M566XZZBWW4zLwwnn7cdyIXRVmfz8XT529L9bCA1+tAlA4bqHSwgoWfLuZZb9swWIZcVh39j+2D6ERdTcKqhYWGcTJ1+7Loh9SmPvpRt7fPI8jLxxCj8HNC4jWWlJW5rDgm81sXZ9PSHgAE0/bh6EHJrL0lzQWfL2Z1NW5HHbuIPrt20nuG9m+Gua9BEveg4piiB8B81+GZdPhyLtgvwvqvzna64VNv0DSa8738cPvgC77/OHTF5E9q3OWFP9Iu23wUVlcTLkNJTRit2BjTNO732Wtg5h9mlyRolr0QOeb7ra129m6Pr/eanG1hH6RZG8pory0stbzaatyKS2sYMBYp6Wgx+BoXC5DSjPaKX56czUfP7bgD71BZ9F3vzEw6Sc2HHIigybU30JRU6g7lLwTz6Jv6irufeQ9Fqbk8fDpI+jdpfVhPio0kNuOHcyC5FymL2x8ebvS1avZcs21BPbrR88XX8AVGlrvOP8uXUi4+25Kly8n++WXWz03gLJKD1dNW8gni7ZwwshuLEnN465PV3T4GsyfL0nn9BdmUemxfHjFxCZDcbXRvaL53wVjSM8vZUi3cL65/pBaobiav5+Lp87Zl+NHJPDAV6t4daZuyGuO8tJK5n+1ibf+9TtLfkxlwLh4zrt3AgefNbDRUFzNuAz7Hd2bSbfuj3+gH589tZiZH65r9N+9tZaNizP58OEkvvzvEgqySzn47AGc/+AB7HdMb4LdAYw7sS9n3D6G0IhAvnlxGd+/soLSwtb17reZ1wOrv4Y3Tobnx8Oid2D46XDFb/C3mXDFDIgbDF9eD/87AlLn7XptSR7Mfh6eGwtvnQbJs2Dtt/DcePjun85xEfEZqhjvVjEuztgKQGhkPQHIHd90xbiJ9Ytrna5nbwLMSpavCMHrtfQe0XAwju8bga3a6KPHoF2V4HXzMwgKdSrFAIEh/nTrH0ny8hwmntbwtXdklbB5WRZYSFmeQ7/RHV/tqayoJOv++wkLieTwh+9o9usOufEyVn7+LgO+/5DJ193LSaMS2zyXM/bvwXvzU3jkm9UcPTSeqNC6AaMiI4PUK67EFRFBz6lT8YuMbPScEcceQ8Hxx5P53PO4DzuM4MEtb/UoKfdwxdsLmLE2k7tOHMpfD+pL3y5rePbn9YzsGcl545v324iWqPR4efS7NUydsZGxfaJ5/rz9iQtvWevGgf1jmX/HUYQH+zdagQ/wc/H0OaOxdhH3fbkSgL8e1LdN8/+z8ni8rJqZzrwvN1FSUEG/0XGMP6kfMYmt+6Gwa+8IzvrnWGZ/tJ4lP6aSuiqHoy4eSlzPXTt8WmvZtCSL+V9tIiu1kIi4EA4/fzCDxifgV89vaOJ6hnPm7WNY+G0ySV9tJm11DodOHsQ++3Vt9cfdImWFsPgdmPMC5G6CiO5VVeGLIKzG99OEEXDx107V+P/uhFf+AqMmO5XhZR86leUe4+C0qTDsVCcM/3Q/zH4OlrzrVI/3uwj89F+myJ+dKsa7VYyLtzvrK4fGhNcdGxbXcDCuLIecTc2+8Q6clSmiQ3IoLAkhKNSfhL4N97vWt9FHRbmHjYsz6Tc6rtZKFr2GdSF7SyGFuWV1zlNtxcx0DBAU6s/a+X/MZg0//PsFemSlUnbFtUTENB4ya3JHRVB86jmMy1jNLd0b/phawuUy3H/qcPKKy/nP92vqHPcWFZH6t7/hLSig54svEBDfvP/o4+/8F36RkaTfdjve8uZtaV2toLSCC1+dx2/rMvn3pBE7A+M//jKQwwbFcc/nK9p9W+u84nIufn0+U2ds5PwJvXnn0gktDsXVIkMDmmxLASccPzN5NMcNT+C+L1fy3M/rm3xNNa/3z79zYXW19r375vHru2uJTghj0q37c9wVI1odiqsFBPpxyORBnHjNKEoLK5j+SBILv0vG6/GycXEmHzw0n29eXEZFqYcjLxzCefeMZ+iBifWG4mp+fi7GntCXM+8YQ1hUEN9OXc43Ly6jKK+Jf6teD6z6wqnuelpYac5Pg+/vhCeGwje3QFgsnPEaXLcUDr6xdiiuZgyMPBOuToIDr3dC8tIPYPgkuPxXuPT/YNTZzv8J4fFwyrNOpbnrUPjqRnjxIFj/Q8vmKSJ7HQXj3W6+K85ygket7aCrueMbbqXI3eRsANKCYAwQE+38h9BzaAyuRm6WCw4LIDohlIwawTh5WTYVZR4Gjq29MkN1S0bKyvrbKTwVXlbNSqf3iFgGjo1n87KsOi0a7S1jczqx77/Kxt7DOPTyc1r8+kNu/Tt+cbHkP/N0u7UUDEuM5IKJfXhnbgpL03b9utR6PGy58SbKVq+h+1NPtqjy6x8dTbf776Ns9WoyH3+82a/LLSpnystzWZiSy9PnjK61i5+fy/D02aNJjArhb28vYPuO9lmnelNWEac9/ztzN+bw70kjuP/U4a3u226pAD8X/508mlP3TeSx79bw2HerG/265pdU8I/3F7PfA//3p95YJGPTDj59YhHfvLgMY+D4v43g1BtGk9C3+T9INkfvYV04565x9B0Zy+xPNvDqzTOdQFzm4aiLhnDuPeMZPLFbo9+TdhfbI5wzbhvDxNP2IXlFNtPumeOshrH7DzOVZbDwTXhuHLw/BT77O7x0KKTMbfoiWxbChxfDUyOdam7/I+CSH+DSH5zWieZUdIPc8Jd74cbVzp9TnoXEBtq6uo2EC7+As99x/o94e5LTbrFtedPXEZG9koKxyx8wu1opcpw1WUPrqxC6452d7yrrqQRmtWxFimpBcc6XoMeApnsF4/tFsm3jjp0BYu28bYRGBpK42012MYlhhEUFkbK8/mC8YfF2SgoqGH5od/qPjcdT4WXTko4NG3Nuu4fAygoGPXQPLlfL/9q5QkOJu+pqShYsoPDnX5ocX5CynV/uep/ijMbXdL7h6IHEuoO489PleKr+A8945N8U/vIL8f/6J+5DDmnxXMMPP5zoKVPIeeNNCn5peq7bU7by5qW3sXXzFl6csj8n19MqEhkawNTzx1BQWsnf3lnY5t375mzM5rTnZ5FfUsG0y8Y3uJ12R/L3c/H4WfsyeVxPnvt5A/d9ubLecDx7QzbHPTWDz5ekExboz4WvzeOLJbvvMbR325FdwvcvL2f6v5PI3VbEoecO4pw7x9F3VBzGNF2Fb40QdyDHXD6cIy8aQnzfSI66eCjn3j2eQRNaFohr8vNzsd8xvTnnX+OI6xXOL++s4dMnF5GXUQxlBfD7s/D0vvD5Nc7NzGe8Bme/DaX58OrR8MV1znrwNXm9sPY7eO0E+N/hTtV24t/huiVw5uvQc2zrPgFhsRBSZ4PWuoyBISfCVXPhmIeccP7iQfDpVbDjz/X3UETUY+x80/MP3lUxznceQ+LrLou2c8m2okyI7F77WFbVurgtDMZru6WTvrGM/KDNOPuiNKxbv0hW/76V/O0lhIQHkLwimxGH9Kjz62tjDL2HxbB+wfZ6l21b/usWImKD6TXEuTPdHR3EuqSMepeCaw8LvviJgYt/Y91Rkzh5/+GtPk/UpNPJee01Mp98Avehh9RaMq0mb6WHbx78nkyTSPG/v+b4J6Y0eM6I4AD+efwQrn9/Me/NT+G4tb+R+9ZbxFx4ITHnntvquXa9+SaKk5LYevsdBH/2KQFd62/FyErLYNk553N0zhYOL01jRP+GG8MHJYTz2JkjuXraIu77cgUPnDqiVXP7aEEat328lF4xobx60dg23cjYHN7ycoy/P6aeH4j8XIaHThtBSIA/r87aREm5hwdPG4Gfy1BW6eGJ79cy9beN9I4JZfqVE+kX6+bSN+dz7XuLyCos4+ID9+7+5PLSShZ9n8Ki/0vBAGOO78Poo3sRGPzHfGs2xjB4QjcGT6h7s2RbRMWHcso/RrNq1lZmTV/Le/f+zpiIjxkd9D5+fSc6Vdp9jnC+/wL0Oxx+edjpFV71JRzzIAw7zen//f2/kLna6R8++gHY70IIbt4yi+3KPwgmXgX7ngsz/gPzpsLyj+CAq+HA6yConvY7EdnrqGIMzje86opxQSXBrgL8Auvps2xs97usdRDercXfHFe4t/L5sGdZmTmjybHxNTb62LAoE2+l3bkaxe56De9CeamnVusFQPaWQrauz2fYwd0xLoNxGQaMiSd1RU6H3FFeXlpG3sMPkh0WzREP3NKmc5mAAOL+8Q/K1q0n/7PdN1/cZfajn5JpEnFXZLGpKIHUnxY3et5T9k1kQr8YfnjlIzIefhj3kUfS9Zab2zRXV1AQ3Z94HG9pKem33oqtZ1vrnK2ZLD7nfLrkZVBy2jkErFpGxqOPNXreE0cm8reJ3Ql/6Sm+efbtFs3J67U8/v0abvxwCWP7xPDx3w7s8FBcNHs26w8/gpSL/4qnsP4d2Iwx3HniEK45oj/vzU/lhg8WsyI9n1Of+52XZmxk8rhefH3dwYzuFU1kaABvXTKevwyJ594vVvLvbxtvweholaVlFKZltvh11mtZM2cr0+6eQ9LXm+m3bxzn3juB8Sf3+8NCcUczRVkMLXmJc7v8nT4Bc5ibdwbvez4i/cC3of+Ru0IxOO0Nxzzo9PTG9INProB/94HPrgLjB6e95FSID7hmz4TimkKinblePR8GHw8zHoNnRsO8/9X/20QR2asoGEPtinERhAY2sIVqY7vfZa1tcbUYYGnu6qrHdU2OjUkIIzDEn60b81k3P4OIuBC69qk/iPccHIPLZUheXvvXkitmbMHlbxhywK4K0YCx8Xi9lg2LGllxo5V+eOhZEnPS8fz9H7ij2v4fWvgxRxM8YgSZzzyDt7Rur23qT4tZsjmcBJPOmQ8dRaCnmBnTVuGtbHhpKmMM940K5erf3yQzoTfdd9vAo7WC+vUj4Z93UDx7Dtkvv1LrWO72bBacdT5dc9IpuesR9nv4bmIuuojct98m/7PPGjynt7iYsz9+ipM3/U6P5x5m3sffN2suJeWVXP/OfP7703rOHtOTN/46jsjQjtuUwXq9ZL34EimXXIorNJTipCRSL7kEz44d9Y43xnDj0YO45ZiBVH4ynS8uvYnc3AJevmAMD502gtDAXWExOMCPF6bsz7nje/HCLxu4efpSKjxtay1pjfWf/M7bV33OW/ctZOGzXzX7ddvWbmf6owv44fVVhEUFMemW/Tn6kmGEx9Rdw3yPyt3s9PHmJrfsdTvS4dvb4akRMOtpwoZM4Ng7TuOEv4+k0hvIJ48v5Kc3V1FSWE+ITBgOf/0OTnoaBp8IUz6Cv82CUeeAXyfbRCS6D5zxKlz6E8QOgq9vcpZ8Wzbdaf8Qkb2SgjHUrhiXBBAa1MBP/Q3tfmetUzFu4Y13GUUZbCvahj+GpZX59VYVazIuQ0LfCFKWZ7NlTS4Dx8Y32H8YGOJPwj6RtbaHLi+tZPXcbfTfrysh4bt6mmN7uomKD2VdUvuuTrE9ZSvxH7/Fhn4jOfjiSe1yTmMMXW+8kcpt28h9Z1qtY2U5O/jhnfUEeoo55p/HEBofw/6j/cjzj2fR8183cEbwFBTgd/dt+IUE848RU/glpaBd5goQOWkSEccfR+bTT1Oy2Klc52flMu/MC4jPSqPgjgeYeM4JAHS96UZCx41j6113U7pyZb3zTLn0Mkrmzyfy9jvIjIrH3H0b6xc0fiNQ7tYsfjn2dE5/4nruGd+FRyaNIKADd0X05OeT9veryHzqKSKOO45+n35C96eepGTlSpIvuojK3PpX1vDk5XHS9Ke5esnHnLJxJm+tmcbhPULqHevnMjx46nCuP2oA0xekcfmbSRSVdewNpNUKUrbz+TVv8913pXhxEWWzmb08hK+uf5vywpIGX1e8NZ0f73uFj55YTuG2TI48fwBn3Dpm54ozDfHmZ2Mr/5iPDYAdW+HLG+C/Y+C7O+D5iTDnRWcVicbkpzmrNzw9Cua+5LRCXD3fCY/xw+gzMpbJd49n9NG9WDNnG9Punsuq37fWrfi7XLD/RTDpf9D/qNqV5c6ox/5w0Zdw3nRnI6iPLoGph8L6H53/G0Rkr6JgDLUrxuXBhIY2EFB3BuPdKqtFmVCW3+JgvCxrGQDHRw4m28+QvjWpydfE94ukMLcMa2mwjaJa7+FdyE4r3Lls0rr5GVSUehh+aI9a44wxDBjTlS1r85peYqkFZt/3OEGV5Qy6985W3XDXkLAJ4wk76CCypk6tVYH8/p7PKfaP4vCT43H3cNZl3vdvxxFduY0FS6F4a92bEa3XS/rtt1OemkrfZ54mtk8Pbv94Gfkl7dNW4uyKdw8BCQlsufEm8lK2MPvMC0jcvpm8W+7hwCmn7hrr70/3J5/ALyqKtGuuxZO3a6UMT14eKRf/lZKlS+n+xOMkXng++/zvJTwuP7Zc+Xey0ur/oSZ9bTKLTj+b7ts2EkcZB//v/lrnbUjO1iJmfbSe0qKWfR5KVqxg06QzKJw1i/h//YvE/zyGKyyMiL/8hZ7PPUv5ho2kXHABlZm12w+KFyxg42mnUzhjBvG330bi4/+hcvlSkqecT0VG/b/JMMZw/VEDefC04fy6NpOzp84moxkrdlhrKZozh8rspjfBqclb6SHp6c959755pJV1ZXBMBlOePJaznj2TwTEZbC5N5P3rPiN7+ebaryuvYMmr7/HOfQtYm96T/boncV7ERQxecQEmb3O91wLwFuSSdet5rD3gQJKP3p/yZb+3aL4tVpTtbGjxzL6w8A3Y73y49EfofQB8eyu8eqyzq9zu8rc4gfiZ0bDgDWd94GsWwGkv1PktWkCQHwec3p+z/jmWqPhQfnpzFZ8+sYjsLYUd+7F1NGNgwF+cDUVOmwqlefD26fDmyZDW9Pd1Eek8FIxhZ8XYer2UVLoJdTfwafEPguCouhXjVt54tzRzKQGuAM4ceCYAyzZ80+RrEqr6jKMTg5vcyrlX1aYfySuysdayfMYWunR37zxHTQPGxoOF9Qvap50iecV6+v7+LRvGHM6Asa2/4a4hXW+8AW9+Ptn/c3aZW/ziN6SUJzI0Lot9Tpm4c5zL5eLQC0dQ4RfCr4/V/fxm/+9lCn/4kfhbbiZy4ngeO3MkWYXlPPhV3Ypta/lFRJD4n8co3Z7N0nOuovu2jeTccBeHXHxGnbH+XbrQ47/PULl9O1tuuhnr8VCZnU3yhRdRtmYNPZ55hohjjwWg9/ABBD3yOFFFucy/8HJKi2tXK9fNW8bGyZOJLMim9P7H6Tv1RSrS0ki98kq8xcUNzjd1dQ4fPbqAxf+XwhfPLKaspHnVyrUvf8qGKX/FVlbS5603iZlyXq3faLgPOYSeL71I+ZZ0J/Bu3Yr1eMh68UWSL7gQExBAn2nTiLnwQiJPOIFeLznzTT73XMo2NbxL3nnje/PyhWPYmFnEqc/NYtXW+ts1ACqzski75hpSLrqYTaedTsmyZc362LbNWcV7V77P3FVuws0OTv9rT458aDKBEWH4BQVw5EOTOexAKDbhTH9qOavf+wWA9Jkz+eCWD5k5ryvxkVmcc10PJt55C4HnTIXsDfDSIbD841rXsl4vO155gI1HHEDmZwsJ7eOmLLOMTZP/St5TtzT5m6UWK82Hnx6Ep0fCnOdh2OlOsD3xSegxBs770Al72evhpYPh18ecXtodW+Hrm50gveB1JxBfuxBOfgZiGr8pskt3N6fftB+HnTeI7PRC3n9wPjM/XEd5M/+udVoul7MW8tVJcOy/IWMlvHwkvDu58SXe8lLgx/vgyRHwzpmwZcEfN2cRqUXBGHZWjCt25FNpgxrfZtUdD0W7hcfqYNylhcE4aylDugxh2IATCPZalmQ0/c0wx66j3K+ETQHfNTm2S/eqZdtWZJOxaQdZqYUMP7R7ve0X0QlhxPZ0t9tmH4vvfxQvhjF3te0mtoYEDxlCxIknkvPmm2T8PJ85CyzRlRkccmfdlo3uB49gn/AMNhYlkPbLkp3PF86c5fy6//jjib7gAgBG9oji8kP68UFSGr+ubflNVQ3xGzaCXw/4J8tGXsvacx/g0MvObnBsyMiRxN91J0UzZ5Lx4IMkn38B5cnJ9HjxBcKPOLzW2NHHHULONbfRZ8tavr/4OrxVoWnxdzPJvfQi/DyVBD07lXGTjiF07Fi6P/kEpcuWk3btddh6NiBZOSudL59Zgjs6iMPOG0RWWiFfPLO40XWuK0vL+OaGt/m/pAgWjr2F+DfeI2Tf+teFDZswgV4vv+yE/fOmkHLJpWQ+9TQRxxxD348/ImTErh+iwg44gF5vvIG3pITkc89rNMQeMTieD6+ciNdaznjhd35ZU/cHvB3ffsvGk06maMZvdLnyCkxAAMnnTSH/84Zv5KwsLuWXu97n41dTKSSCCUOLOPuFs0mYMKTO2GHnH8HpVw8ixBbz48+VfHDla3zydjlllYEce3wJJz10IdFDqnbGHHoKXPkbxA2C6Rc7y5RVlFA68wtSjtmfLY+9gyvQj14PXU+vr5Lo9+E7BHcLYeuLX7DlzIPwbN3c4JybrbLM2Qr56X1hxqNO28Lf5ziV3ug+u8YZ44S9q+bBkJPg5wecNYifHgVJrzr9v9cscAJxVPOX/TMuw7CDuzPl3okMObAbS35K5Z2757Bm7rY9ekNlu/APgglXOjcMHvEv2DzLWeJt+iXOD0Tg9CGv+wGmneN8Lmc+CV32gbT5zrbV086G9EV79uMQ8UEKxrCzYly8bRsAoVH1bAddzd21bitF1jpnTc6I7vW/ph6V3kpWZK1gZOxIAgJCGWqCWFqY1uTrflz2Bm/tdzcLYj5pcqwxhl7DYkhdlcvSn9MICPJj4LiG2y8GjIln++Yd5Gc23CfZHKt+X0j/xTNJOfREug/s06ZzNSbuumvxWPj+5WUYazn2HxPxC6r/Bp1Dbj6OwMpifn17Jd5KD+VpW0i/8UaC+ven2wP31/ph4bojB9C/q5vbP1pKQWnbWyo8lV6eeGAOmBj8IvzZvi2q1g6G9Yk+80yizjyT3GnvUrltG73+NxX3gQfWO/bwv53HhhPPY8CS3/j6lof4fdrn2BuuoiQojIQ33mL4YeN2jg0/8ki63X8fRTNnkn7HP3dWH63XMufTDfz81mq6D4ri9Jv3Z9jB3Tnm0uFsTy7gy2eXUFFWt8e0IC2T6ddMZ2NxIr3c2ZQEdeHL1zY1uuti6H6j6fX663iLiihZvJiE++8j8fH/4Od21xkbMmI4faa9gys0lOQLL6Jw5qwGzzssMZLPrjqI3l3CuOSNJN6a49w0Vpmby5YbbmTL9f8goHt3+n78EV2vv54+0z8kZN99Sb/lVjIefQzrqf3xpfywkGnXfM6K7XEkBmQw+c4x7H/tSbj8G74xM25kP86+MJ9exbPJ9ibSv2AGZ924H/ucfELd5eqie8PF38CB11P5+xtsPWs/Nl12M2XbS0i48Ej6/pRE2OlXABAweH96fT2XrpPGU7Aqh40nHEvR9BcanEejvF5Y8j48Owa+ux26jYLLf4Gz3nCCekPccU6/8OT3IDhy1y5yJ/+3dpBuoWB3AIefN5gzbh2DOzqIH15b+edorwBntY1Dbobrl8BB/4A1X8OzY+HDi+C/o+GdSbAlyTl23RK44FNn974j/gUpc2DqYU61eeuSpq4kIu3E75577tkjF546deo9l19++R65dh3LP4ayHeSETGD1Mi/DxwQR2a+BXwWu/8H5leL4K3c9N+cFJ1yPvaTZl1yTs4Z317zLlKFTGBA9gI3rv+WnikwuHnI+fv4Nb8n78u/3kxpYSq6f5di4I4iOiG30Ol6PZc3cbeSkFzH0wET2Gd3w1sbumGCW/JhKSEQgiQOasfB9A+b+7UaCC3IZ9fLzhIR33HJgfpGRLN8UyhZ6cdB46HPMmAbHBrhDIHU967Oi8N+wlIqXHsGTn0/v117FPy6u1lh/PxfDu0fy6qxN5JVUcOSQxnu5G+P1ennqP/MI21KKHR7JX68fw/qkDNbNy2Dg+AQCghoOWWEHHQiVHrredBOho0c3ep3+Rx3EnJnL6P/blwTO+IntMd0Y9t7b9Bhc9+9x8NChmMAgct94A09BAUHjJ/LD66tYMSOdoQcl8pdLhhEQ6MwrulsYUfGhLP0xlW0b89ln/64718VOn7mcz59cRKErion7VnDoP08lcUAUy2dsYf3C7fQdFUtQAytfBHTtSsRJJxIzeTJhEyY0uomFX1QU4ccdS9GvM8h56y0CEroRPKRuxRbAHezPqaO7s3LrDl6duYmwOfOIuP9mSleuJO6aq0l86MGdX29XSAiRJ56IJz+f3Ap2mdYAACAASURBVDffpGTpUtyHHkpFWeX/s3ee4VGVWxu+p6X33ntvkNB7C703UZBmO/b6HRUPKpZzFHvBgqKIIAjSQWroPUBCeu+992SSKfv7sRGN6QiK5+S+Li5gsvbsmWTy7rXX+6xnceLV7VyIkiLRahg5UpcRK2aha9Y2cW9FSSJsuxd5zHp8w2R4uNig2LeZur370PXxQcfVtc0hAhKqr5ZTsCmRpkIV5sM9cPp2CwaTFyKRt7Ztk8hkGIybhVGgI/UnT1B54BLauEMYjJ6MRLf9JsXWJxPQpBxBun05XPkGzFxh9pcwZoVoNdldrLyh/3Lwmypal90ijMx0CRjmgKGZLqmXS4g9nk9TnQpbdxPkOn/cJeYvRaEPHqMhbAlomkXnCisfCF8F0z8RJ/jpXW/ClOuC6zDof59YcInfAZe+FKUYFp5gfHv85nvp5b+d1157rWjVqlVfdRXXWzGGGxXjhgqxKcnA2rLjWCPbdirGqT1uvIstiwUgxDpE/NtuACqJhJT0Qx0eo2xuJElej1sLCBIJP19c1+V5nPwtkFwfABI0qvOKtrGFHvaepqT9ATnF1f0n8EyPpnjKXVjYW3d9wB+gPL+OlHpnPHz0CL5/YpfxoQ9PwlxdwtU4KfWp2Ti8sxodN7d2Y8NczLl/uDubL+X+oRHEX669hl5WI42u+jz6aCh6hgomPxyMslHN4a/j0XZiMybV0cHmuWdbyQs6jJVKmbD+YzI8Qsj2CGbg7q3YurWdoPcLlg8+gMXSpZRs2cmOFYdJv1LKkDmejF7k22YgjHd/W8YtC6AgtZqDX8ahVmmIX3+UvRvy0CJl6nwrQh+ZAoCDtxkznuqLsl7FrvejqCnrWMussLND4di9XRaFjQ2umzZiOHAARS+9ROnHHY8GN9SVs2a6L6+Vl9CS78Al13sx/2YjVo88gkTROlGXKBTYvfIydq+9RsPFi1xc9Cw/PHOI1Bo73PSLWfjWKAIWj+38xbU0QsRrov62PA1mfQFL92G59GHct/+E3NKSvAcfovT99xFUv+5ANMXFk73gbopffRVd3wDc9+zB7usDyOzcOj2d/ujZuB86g/kwVypPZZA1fhhNEds6PSZt3zYSx/Yl464nKImqRDtnHTx0Shyy0QHalhYaLkW2a4t4u/itvCJwhAPxp/LZ9MoF4k7md/q70hM0Gi0pl4rZvvoKB7+Mo7KwA3vO31FT1kRxZs0fk3kY2cDk1bCyBO47CMHzQN6BdE/PFEY9L1aQR6+A7DOi28UPd/U29PXSy22kt2IMkHwAavLI1w4kt8CQgdM8ULSzrQtAcRykHYEhT4gLmqoJjr4CAbPAbXi3T7kleQtlTWU8EfoEEokEI11Tvk/fibdaQ4j3tHaP+fnseg7VXuZus0mkNaVCQwXT+t3X6Xlkcgn7TmTRpJAwZX4n26TXUbVoSblYjGeodeda63bQarXEPfwUaNQMWvcpOnodV77/KBqNlp8/i0WrFZjx3KBuVZQkUikWZgKJCSrkfQcS+MCUTuMHultwIK6IQwnFLBjgjI68Z/eR32+OpzmyglprBf/30pAbCaeBiS7GFrrEHM9H3aLBJaCTG7EeIFco8Fk0H59F89Az6LyCKJFI0PqFcTLThbomOUP9awi9d2iHlVsrJyOMzHWJOZZH2vEUUnN0MNVWMPulodj2b/25MjLXwyXAgqRzRaRcLMY12BJ9o559ltpDqquLyZQpqMpKqfp+Iy05ORiNHt3Gczo3Ipp9H16hQW6LsayMGh0nIhOasPAwwcaqfZmU2s2b3SUeFOuEIVE14RwqZdorc1EYdlGJzTgOm+dD6kGx+eyeH8Fl0A2LMbmFBaZzZqOpqqbq+400XLiAXkAAZZ99RvGqVQgaDfavrcLmxRdQWHW++/NbJHoGGM28F307CXWnIqncewIh/SQGo6YiUfz6vS6OvUrGP+Yj2XIAaYuaGhMLtMlKIq+Uoz+gP6ZWbSu+glZL7b59FDz+BFUbN1L78wF0PDzQcfnzxobLdWS4BVvhEWpNeV4d8acKyLxWhrmtASZW3aiOt0OLUk38qQKOrEsg+UIxOnoyKvLriT2eR12lEmsXY3T0W1fpBUGgOKOGs9vSOPVjCknnishPrsLURh9jy5t7HT1GoSdeW/rfBzqGkLgbItdCXqQoYTF16vIpeumll96Kcc+Q64ka4xolUtToWXZygfplyMcvDXgVGYAAVl49OmVsWSwh1iE3EhFb2xBsNAIxFR27IVzM3I9UEJgx9BH8VCYkyqpQqzvXwKaU1LFZ3sRGRSMpxV3783r1s0Ei4aY8jc9v2oNrUTo185fekmEenXHtaC7lefWMuscXPaPuG/87jgyh7zgnMqvMyUuq7DRWTyHjnXkhFFQ38dbBpB69vt3706k5XUK1iZSn/zUE2e+Sat/B9gSPcuRaRN4t94/uDhWF9ex8LwqVrilDdS6iu/ZlqrZ2XnX0629JH0Uctc16uOgUMP+jWZh6tl/xtXYxZtazoWi1Arvej6I8/9boRSUKBfZvvIH1M89Qu38/ucvvu+GLrFGpOf3aT+zfVo4GGRMnG7Dk87vxWeCJjlrg0EfXOBjR1t3i1IV8PltxFqr0aXRScKSvFY/nafnPgSTUHVUpm6pg92OwcTZI5bB0P8z6HAzb3uRI9fSwf20Vjh+8T3NaGllz5lL903YslizG8+ABTKdP71RKUlKrRKlq30PYaN5jeByKwDTMgYpDCWSNH4Ty7D7qy4qJun8W1fcsQie1guYwZ2z3HqTfyXNkL3oEh7wUyubN4dC/16C5PvxGEATqz5wha85cCp9/AamZKXarViGRych74AEK/u+fqMtvfvfkZrB0NGLm06FM+kcQqmYNez66xsG1cZ3uRPyextoWLu3N5PuXznP2pzRMrPSZ+lgI97wyiHvfHELIWGdSIovZ9MpFLuxKp7lRhVajJf1qKTveucrO96IoSKui3yRXRt7tQ215E7vej2bfJ9cozenYAeWWo2d6Xa8cB+GvQVEsfDsRvpsGGSe65ZlcU9ZE+tXSTptpe+nlf53eijGIRuwlCaQ2jaCxSULotMCOY+tLIHabaGlk6gTZZyFxj7hgGXVPi1rTXMMHVz9gptdMwmzDbjweE7+ZeFU194Y+2u5xn11+C0uNlAdHvURmZgzntTn4tljj6dTxVvv6c1lczqkCCZgZKBjq2XlVSqErIymhkJSEQgaGe3Tbf1itUpPx+JM0KfQY+dWHyOS3b6xtZVEDR75JwKOvNQOnefT4eAdvczKiysi8Vob/MPs2SWurWDN9GprVfHc+hyAHUzysu9CZAifP5ZGyPZN6fSmPvjIE4w6qpU7+FuQnV5Jwtgj3PlYYGP/xqmp3KMqoYe/H15DIJMx6JhS3OaNRJiZRuWEDCkdH9Pz92hyjrqoi7x8Pozi7jz4zAwhbuQS5buev18BEB7cQK1IjS0g8W4i9p2m3prvlJVaSHVuOrZtJuwmjRCLBoH8/dD08qNq8mbrDh1HZe7L/nXPkNNjgIC9i9qpwbAeIlWwvdzMsfM1IuFJCfVwVMcW1hPa1oUmpZs2nVyk7XohGIiFgvgdLlvZhZn9nahpVrD+XTWR2JaN8bDDU/c3nOWm/aKmVFwnDn4Z560U3gS7Q9fbGZPIkkEiwf20VZrNmIdXteFelvlnNO4eSeWJLND/HFhHsZIq9adsqpdTQBOO5S9Eza6b21BUqdx+lfvN3yLMq0LgZYfLeh/g+8yr6ZuZIpVK8Rw2iZdR4Mi9E4X76Z67uiQBjE+rfeYuKL75AqqeH3SuvYPevf6EfHIzZ/PlIZDKqt22jats2ZKam6Pn7d5rM30okEgkW9oYEjnBArpCRfKGI2BP5tDSpsXHtWH9cW9HEpb1ZRHyXSEFqFa6Bloxd4s+Aqe6Y2RogkUhQ6MhwCbTEd6AdjXUtxJ8uJOFMIQlnC0k8W4hMIWXQDA/ClwXgGmiJrZsJQaMc0TVQkH61lNjj+VQW1GPhYNRqaNJtRa4LLoNhwANgYAkpB+HKOnEn08AKLL1aDUXRaLRkxZRx9qc0zm5LIyOqlITTBaiaNVjYG3bc51AYDSdXw97HIee8qG02db7zB6700ksHdLdi3JsYA2SegoIoEhrGIhG0BE4K6Ti2pUG0KPKeANZ+kLhXTI4n/LvbI0uvlFzh58yfeSj4IRyNf624FeWd57CygAVO4RgYtK48ZRUk83nOVoZJvRgXejfmBvZsy9mFYUU5Y/rOb/c8giDw0q54gh1NcTY34GpOFUuHuHZ5Qfvo0iZcStxIlOUQ6tO5H+kvHF+zAcczh6h7+Fm8hnTeKPZH0GoFDnwRi6pZw7TH+3bavNYRUpkUK2cjYo7noWrW4BrUuZRhkIcFx5NK2XWtgNmhjq2TpN+RlFbJqa8SaJFLWLJiYIdb9wBSqQSXAEuSzxeSHVuB72A75Irbu4mTHVfOgc9iMTDVYfazYZjbGSKRyTCeMB5lTAyV33+Pjpsbej6/auZbcnLIXbqMlowMHN99B+uFC7qdFOkb6eDR15qM6DLiThbcmLLYHoJW4PL+LE5sSiY3sZKKwgbcQqzaaJ5/QdfbG4NBg0g9lsKZPFeUEn0G91Ex+pU56Ji0bvq0stAnaKg956KKUWQ0cDoymwv7czEobaHBQY8HXhpIsL+oiZdLpYz1s8HFwoAfLuWyMyqfMBczHOT1sOcxOPFvMPeAhVuvjyru/k2gzNQUoxEjkHcimxAEgX2xRTyw4TJn0sqZ1deR3MpGvj2bRbNaS383c+Tt3LAmmQfwscSNgPLL6MgEJE8/QeA7X2Hq0vbm0czGAq9F84hp0cfi3DHkRw/QUFWDzbPP4rj6LfR/k/hK5HIMBw3EeNJElHHxVP3wAw0XL6EfEozc8tbIgLqDVCbFwdsM/yH2KBtUxJ8uIPFsIXIdKVYuxkiv91JUFTdwfkc6JzemUJZTh+8gOybcH0jwaCeMzNu/MdM1UOAZaoN7Hytqy5UodGUMn+fNyLt9sHM3bXXzLJVJsfc0JWikIzKFlJTIYmKO51FT2oilg1GnO1iCViAnvoKrB7NpaVJj4WB4owekMyoK61G3aFo3s8p0wHkgDHxIdETKPCFemxL3gK4JdTI3rh3LJ+K7RJLOFaFVa+k73oV+k9xQ1qtIOFtI3Ml8GmqaMbczRM9QIXpaR28S7QNPrYayFHAfAXmX4PI6SDssTvez8hE9m3vp5W9EdxNjyV/lF9m/f3/hypU7pIEg4jU4/ylbqz7GUK+FaW8t7zi2vhTe84Yp78HAB0VfyvxIcXurm3xx7Qu+iPmCCwsvYKj49QIeFfM9S6+9y6e+yxg9+LlWx6zZ8X+srT/M257PMXX4MgCmfx2MgSBn60Pte13G5lczY805Vs8NRhDgxZ1x7H9iOEGOHY+gTSsvYv6eGSyJepVS81LefrNzDTNAc5OSyBHhKPUNGXviALJO7Kz+KNcicjm3PZ3w5QH4Dvpj3dmnt6YSdyKf2c+FdenCkV5az7RPzzDAzYINywfeuAj/lvKqJr5+9QI6KoEJT4bcSLS6ojCtij0fXsPJ35ypj4YgvU3jmlMuFnHs+2SsnIyY9nifNhpybVMTeQ8+RGN0NI4ffYjJ+PE0RkWT/6i4g+H0+WcYhIW199Rd0ljbwv41MZTn1zN2iR9+g1u7ICgbVBz9NpHchAr8Btth7mDIhV0Z2LqZMOWRkHb17mqVhnPb04k/VYC5Tj0THgjCKqTzHQSNSs3OtzdQWuCOjrQWx/EOTJk9sMP4pKJaHt54hdDaY7ytvwldbSOSUc/DsKe7fSPcE9JL63hlTwLnMyoIcjThjZlBhLqYU6dU8eb+JLZeycPPzpgP7upLgIMoVyqtVbL6UAo7ovKxNtblxUl+zA51bPcz2h7FGbls/XoPa1X2ODlZ85/ZwfR3s2g3VhAEanbtpnT1ajQNDVgsXozVY48hM7p97jMdUZZXx7nt6RSkVGFma0DoBBdyEyrJiC5FJpcSMNyB0PEu3dql+CM01bcQfSSXuJP5aFRafAfb0X+KO6bWv1b3W5RqUi7+kkA3IVdIUau0mFjp0W+yG76D7NrsXGnUWjKiS4k7kU9xZq04XG+ALWGTXLF0aGfnSqNGiN9F7sG9xBcFktPcHwEJrgHmBI52wTXQotXaUlXcQPTRXNE3WiPgaZtHqLAWG0kC2AVD2FIIng/6ZmIvTcwWuPCZ6Mpk6gyDH4HQxaB3e2VzvfRyq5BIJFcFQejYvuo6vRVjgNxLkHWKK3VzsbJQ4j6yk4qnXA9Ovwv2IeA+Ek6/J5rah3Q8sOH3fBP/DbpyXRYHLG71uJmJM98mrMehpZlB/ne1Pubs69RKmnh98hpk1ytU0df2c1lRxWznmRgZtF2c1p3JJK6ghtVzQ/CyMWLdmSwMdeWM8O44YVsR8SW5LVcxb/HAtcwDkxBdrE07X/iOf/Qt9peOo/nnv3Dt03Yb/lZRXdrI4a/icQmyZPAsjz+8lWvvJTpwZMeVEzDModOE1MJQBwtDXdafy8ZIV04/19ZNSy0taj554yJGjVoCFngydED3Pa2NLfUxMNEh5lg+zU3qLivYN0PMsTxObk7Bydec6U/0EatDv0OiUGA8YSKNly5RuWkTQmMDxa+9jtzKCtfvN3RokdYdFLoyvAfYUpJVS0xEHjp6Muw8xBu0stw69nwUTUV+PSPv8WXQDA8cvMywcjQi/lQB6VdLcAmwaNXAV13SyL5PY8iOraBvuDOTnhqMkX37ydwNagqQbruXwKqvsXVWM0TnawJqfgL7vh368FpL67i3+G2mVm0kVu3E186rCZ20FD2dW5sUN7aoef9IKs9ui6GqsYWV0wL4z+xgHMzE5EpXLmN8gC3Bjqbsiy3iu/NZSCUQnVvNoz9EkVRUx4MjPfh8URh9nc169LthZGHK4PBB+LlYciShhG/OZlFa10x/Nwv0FK1vciUSCXr+/pjOm4u2uoqqHzZTs3s3CltbdLy8/jR5BYChqS6+g+2wcTUhL6mS5PNFNFQp6RPuwsQHgvDqZ4Ou/u2TdP2CQkeGs78FAcMc0AoCyReKiT2eT32lEn1jHWKPi1XbzOgyTK30GTrPi/BlAdi4mVCaXUvC6UJSLhYjU0ixdDCiqb6FmGN5HF2fSMqFYmRyKQOmumPhYERKpGhjV55Xh4m1PkZmohRH2aAi/kwRxw5KiCsMolnXgRDLC4TrvUmwbCvmljIktgGibdx19BXNuGsOEdD0NZLGEtKrQ4irn0iB5SL0xj6BWehwJDrX42UKcAiFAQ+Kvy/lKeK0w8h10FAmyjf02y8uaFRign9+h3gTK5GAuZ3BbSsA9NJLR/RWjHvC2Y8Qjq7ii5KfCPMrZPDTSzuPf9cbfCfDtI/gLUfotwwmvdWtU2kFLSN+HMF41/GsGrqqzdfvWt8XE6mCdUsv33hMrVYxdkNffDQmrHvowo3Htx39hDcKv+Zpi7ncP731c2m1AsNXH8ff3oRvlg0AYPn6SFJL6jn7wph2L2BqjYZ+341DT2rBqoCVZK6vpsgvnzefXtLh+9Go1JweHo5aocO404e6rUnuKYJWYPeH0ZTn13PPK4MwMr81jhd5yZXs/egaoeNdGDq38wZKQRB4eNNVjieXsuvRYa0q7+++dQGDnCYMh1mzbHHwTb2Wsz+lEXMsj5F3+xA8+tZ1ml89lM3F3Zl4hloz/r5AZF3INTR1deQuvw9lfDz6/frhtOZT5Oa3xq9Wo9JydH0CGVFlhE10wczWgFNbUtE3UjDxoSDs3FvvZpRk1fLz5zFoNQKTHw7G0cec1MvFnNyUglQuIXxpAG4h3XBzSNwDe58EjUq0ywq9V7RW23ovVKTBuFdh2FOt9ZPJB2Dfk6CsQRj9Et9op/H24TTsTPVYs1BMQG8FJ1NKWbk7nvyqJub1c+LFyX5YGXX8+a5qaOGVvQnsiykEINzfhpVTA3Cz+uNV24ZmNR8eTeXbc1lYGOry6vQApoXYd5jwNl27RtHrr9OcmITh0CHYrnwZ3Y484G8jGo2WorRqrF2MO/TO/rNoqGnm6qEcEs4UoFULSCTgEWpD33BnbN1b6+YFQSA3oZLLP2dRklWLvokOzQ0qtBoBl0ALgkc74RpoeUNuoaxXEXsij9gT+TQ3qnH2N8fQXI+0yyVoVFpR4jHaEc++NsjkElEbfO4jUX+sMIR+S8VrV/xOiPsJWurBNhgG3EeL9xwSL9cScyyP+qpmzGwN6BvujO8gu/Z13AVXRQ//hF0gaMF3Cgx+FFyHgkRCeX49SecKSYksprlBjZG5LgpdGVXFjegZKQgY7kDQSMfbXtHvpZdf6G7FuDcxBrj4JU0H/s23pRsYMaiUkOV3dx7/xXCx8W7qe/BhIEz9oNvDPbJqspixewavD32d2d6z23z9za1T2N+Yy7nFUciu+1sevbiVZ1Pe5H790Tx916c3Yhsa6xi7dTAD1TZ8+uCJVs9zJbuSeV9e4MMFfZgdKiZZO6PyeXZbDDseGdqm4gmwNvIAa5JeYL7LC7wy5l5e+edG9Fr0+ed7s1Ao2q+8nFq3DZv3XqX4qZWMeWRRt74HN0P86QJObU5hzGI/AoZ17M97M5zYlEzSuULmvtAfW7fOq+NVDS1M/vgMBroy9j8xHAMdOd+sj0F5qQKlhwHPPT/4pl/HL/rp3IRKpj/eB+eALiqgXSAIApd/zuby/iy8B9gSvsy/21UaTU0NdRERmEyb1mmD2M2g1Qqc/jGVhNMFADj6mjPxgcAOm5dqy5vYvyaGmrImXDx1yE5txt7TlPH3B3Z9UW2uh0MviLpJhzCYu651o1xzHex5XLTA8p8OMz8HBDj4IsRsFpOGOWvBVmzIjcqt4onN0ZTUKnlxsh/3D3e/6SppWV0zr+9PZF9MIR7Whrw1O5hBHt3fLTieXIKuXMYwr+7bvHWX+IIaVuyMI66ghhHeVrw+Mwj3DhJvQaOh6scfKfngIzRNTWSNmcmoN57HxKJjydYvNCUkoKmsxHD48G5/H1UaLYq/QbWxvkpJTnwFzgEWmHRh7SYIAvlJVcSezMfYUo+Q0U4davHhuvXc6QKuReShUqrxGWRH8ChHrJyM2z+gJAHOfSwOFhE04s5n0FzRAs6xX5tmvYyoUq4dzaMstw59YwVBIx0JGuXUvoVnbaGoP77yLS0NSlJ17yFJOYnSMgVSuQSPPtb4D7UXPfUlUJAiTmLNji0HiQSPvlaEjHHC3qtnOx299NJTehPjnnBlPRW7PuDHio+ZOKkBr1nTO4/fOEe0axr3smjXtHS/2KDQDfZm7OVfZ//Frhm78DJvW6Hcd+JfvJS7l53D3sXbaxIAr2y4i10ksX3k9/i6t5Z5LFk7gCJZE4eXxyD9jZ/rqr0JbInM5crKcIz1xApKnVJFvzcjWDjQhVUz2jpvjN6wjApNMucXncBYV5+312/H+JIF8klq/jFrQpt4rVbL0THT0GusZ+jZCBRduBTcLE11Lfzw6kWsnI2Z+XTfW754Njep2fLaJXQN5Ny1YkCXFdXz6eUs+uYSdw9wZriREZk7s6gzk/PPN0eg6KHX8e9pUarZ+e5V6iqbmft8Pyzsb64KKAgCF/dkEnUoB78hdoxZ7N9tzemfgSAIxBzLQ63SEjbBpcuEXVmYwaEPTlJQ706YXx4DH1uErIObtRsUXoPt90FlJox4VhyS0J4uWBBE7eTRV8DCHVRKqCuE4c/CqBfaDGCoaVTxz+0xHEksIdzfhvfm98HMoPuffa1WYOuVPN46kIRSpeXRMZ48MtoT3duozb8ZNFqBjReyef9IKs1qLf8Y5cGjo73Q/131sKC6iQ+OpHLsYhIPJh5kbHYkVfomNC1/mDGPLWm1Lv1Cc1oaZZ98Qt3RCAD0+oRg+8KLGIR1LGO7mlPFh0dTOZdRzsw+Djw3wRdni46Tx/8FNBotglZArujmZ6c6F/Ivi4NduphaKAgChanVXIvIJTuuAqlcgs8AW/qMc26VgAuCQEl2LYmnckm7UoJaLcVSno2/6UV8hnuiP2wJmLSdrFhb3kT8qQISzxXS3KjG0tGQoFFO+Ay0RUfv1khgVM0aMq+VkX61FANjBQHDHbFxM+5NwP9H6W5ifPsFWH8H5Ho0asVFwqAdw/s2GNmK3brlaeL/ezD1LrYsFiOFER5m7TcJBXtMhNy9xGYdvZEYpzSn4SahTVIMEGAcQrQqkksJxxgSIiavGq3A/tgixvrZ3EiKAYz1FIzxteZAXBEvTwtA9ptEKaEkj3IhmgCjaRhfHy/70LxJfHv1BBWR5TCr7Wu9uucYLiVZ5Cx54rYlxQAX92SiUmoYucDntixouvpyRi/y5efPYrn8cxaDZ3VuvTXUy4qHR3my9Vgm1vW6KHUlPLJi0B9OigF09ORMeTSE7W9f4efPYpj3Yv8eD8cQBIFzO9KJicgjcIQDo+7x7Vbn+5+JRCKhb3g3B0akHUVvxwPMsJRQHzQJk+wtsP2wWMnVbadCJghiBevwS6J91bL9nQ/fkUhg6OOihvKnZWIz0f1Hwan99dPUQMHaxf347nw2/zmQxJSPz/DBgr4M7ka1N6OsnhU74ojMrmSQuwX/mROMZzcsAP8KZFIJy4a5MyXEnrcOJPPp8XR2RRewanog4QG21DSq+PxkOuvPZwOwPLwP9745l6wzl6j/979x/vwdjuzcgePL/yJ43BAAWvILKP/0U2r27kVqYIDVE4+jsLOj7ONPyFm4EOPJk7B57jl0nH6VEsXkVfNhRConU8qwNNRhbpgT+2IKORBXzOIhrjw+xgtzwz/JKu0OQyaTQk/up8xcxD/dQCKR4OhrjqOvOdUljcQezyPpQhHJF4px9DUjZIwz9VXNJJ4tpKKgHrmuDO9BjgQOd8BGA5LII3DpLbj8DgTMhIH/EF00rq/hJlb6DJ3rxYDp7qRdLiHuZD6nexAOCwAAIABJREFUNqdwfmc6foPtCRrleFOFAUErUJhWTfKlYjKulqJq1mBkrouyQUXiuSIsHY0IHOGAz0Dbv1x208udSW9iDCDXpVEr6gUNrLuxLWlkI/oZl6WArqn4/24SWxZLkFUQUkn7SZSr83BMtAKx5bHMBUoqCkjVURGuaX8xC++zmB+uRHI8dvONxPhSZgXl9c1MC2krOZjex4HDCSVEZlUyxPPXC/l75zcikWh5etCvDYEWxkaU2ZfhmO9MTEY2fTzdWj1X6Vdfo9YzZuSTy7r9/ntKaU4tiecK6TPWGQuH29f57hZshd9Qe64ezsEl0AIH785vkB4f7oHkQBEaiZZ5T4dibnrrdHImlvpMeSSE3R9Ec/DLOGY+FdplFfsXBK3Ama2pxJ0qIHiMEyPu8v77Vke0WrHR9eRbYBuEdMFGTMzdIDIUDq2AbybAPVtaN84pa2DvE6Km2HsCzPqy3aEb7eI2DJ6OBamiSws2iUTC8mHu9HM158kt0dzz9UUeHe3J0+E+7W7zqzVavj6TxYcRqegrZLwzN4T5/Z3+Fj8bG2M9PlzQlwUDnHl5dzwPfH+FIR6WJBbVUqtUMSfUiWcn+OB4vVGw78ThaMbt5/gn32H6/Vqkj93PnrBRhHjZody1Q5xAuXw5lg8+cEO7bjJ5MhXfrqfim2+ojziGxdIllM24hw8vFBGRVIKZgYIXJvmxdKgrBjpynpvgw4dHU1l/LottV/J4dLQXy4e5tWkW7OXWYGZrwMh7fBk4w4PEc4XEncjn4JeiE5O1izGjFvriM8D2N5MDx4LXWKjMEm9SozZC/A6w7yM28AXNBR2x2q/QkREwzAH/ofaUZNUSdyqfhLMFxJ3Mx9HXjKCRTrj3serUbx6gJi2F5KPRpGRbU1crQaEnw6ufDb6D7XDwMkPVrCH1suipfvrHVM7vSMeznw0Bwx2w9zT9W/wu9vLn0CulAEg+QNQ3W7lQt5QHV4ehY9pFU82Fz+HwCrALEb0kHzzWrdM0qZsYsnkI9wXdx5NhT3YY98iGwRRrm9i1PIZ1e1/l46qdvOzwIHeNb/+YieuCsNbosekf4vdzxc449lwr4OrK8W22PRtb1PR7I4I5YY78e7bYJNaiVtN/wxgMpfZcWN56+lnE1VhSvi6nwDuP/zz3a1NiwunLSB9aQsbMJUxbvaJb77+nCFqBHe9epbZCyaLXBt/2DvMWpZpt/76MRq1lwcqB7To3gFiRPfhlHNlx5Yx/LATvwFuv8QRIvVzM0W8S8R5gy/jlAV1WfQVB4OTmFBLPFNJ3vAtD53j+fRf7pirY+Q/RNzXkbpj24Y0LKSBO+vppKUhksGCjWBEuiBIrvjX5EP6qOLb9T/BabWhW89q+BLZdyaePkykf3x3aqhEuubiWf/4US1xBDRMDbXljVhA2xn/PhiOVRsv6c1l8cTKDECczXpzsh799x7r8mvIqTq1cjdup/UgRKBk+gUGv/hMjp/b7BFQlJWS8/R7agz9Tq2PAzqCJuCxdxNJR3q12v34hpbiO1YeSOZ5cir2pHk+N82ZePyfkXUhz6pvV7IrKx8JQl8lBdneUzOjvgEajJS+xEkNTXaxdOtA1/5bmeojdKibJpYmgZyY2wPa/r93hOI21LSSdLyThdCF1lUr0TXQIGGZPwHCHVnrtltoaMn6OIDmqnsI6Z0CLs04MfpZxuA8PQjFgIZi0/ayV5tSSeLaQ1MslqJQazGwN8B9qj+9gOwxNb21PRbepyhabIpP2ijthIQvAf0avHd4tpFdj3BPSj3H2870kNE3ioc8mIunqYhq3HXbcD0hEg//ZX3brNFdLrrLs0DLWjF3DKOdRHcZ9sXsRX1THcH7uUVb8uJBIeSnHF1zE0KD9Beipr8M5Jy/m2PzTGOibMeDfEYzysebju9vX6z2xJZpz6eVcemkcCpmUTy/s4avUlSx2f5nnR97VJn7l899jpDTi6fem37Cp2jvvPhyTo/A4fgxzm9tj8p98oYhjG5IYu8Qf/6FtNWq3g5LsWna+cxX3vtZMfDCw3cQy6nAOF3ZlMHy+N33GOd/W13PlYDaX9mTSJ9yZ4fO8O4wTBIEz29KIO5FP2CRXBs/843Z2twSVEo69Bta+ontLdyiOh62LoKYAJr8N/e9vf9pWRQZsuVvUEPe5G2K2ijKn+evFLds/mQNxRby4Ixa1VmDVjEBm9XXk85PpfHYiHRM9Ba/PDGJKsN2d8XP5k0lPyOCz4+nsKlDjaKbPi5P92rhdFFQ38XFEKtuv5uNfX8iK7KNYpsWhcHHB5umnMJ48ucPv3YWMCt4+lExMXjUeVoY8O8GHKUH2bRLeOqWKDeezWXc2i+pGFQA+tkY8E+7DxMDeBPm2IwiiU8blryFpH2jV4BUuVpG9x4O0dSFHqxXITagg4UwhOXHlCIBroCVerjUUXEsnvdAOtaCHqU4Z/v4qfCcNwqghDqI2QOZJkEjBZ5LoydzO87co1WRElZJ0roiijBokUgluwZYEDHPA5Xe+z7eF2iKx8TduOxRcz4cc+0NjBVRliU2SvpPF4oDXuNvinf6/RK/GuCfI9WjUmmEgr+86KYbfjH4WwKrjZOX3xJbFAhBs3bmdV4jjEISaWOJS95AkKcW3xaDDpBggzGE0x8u38vO59Ti4Laa6UdWujOIXpofYsy+mkPMZFYzysWZbyk+gNebxITPbjTcNNsbgnCnr9h7l8XlTyI5NxSP+IpljZtLvNiXFzU1qzu/KwNbdBL/Bf2yQR0+wdTNh4Ax3Lu7OJPmCBf5DW38f85Mrubg7A6/+NoSMvXWWah3Rb5IrjTUtxETkYWiqS+j4tpIaQRC4sCuDuBP59Al3vnOS4sZK+HEh5F63GCxLgQlvtrk4tSJpn1gp1jOB5Qc6T3AtPeGBCHHITvQm8JkMsz4Hgz/m5nGzTAm2p6+zGc9uu8bz22NZfTCZioYWZvV14JXpgVj8j+pgAbwCPfkw0JN56eW8+XMST2yJZv25LFZOC8DVwoDPTmSw6WIOAMuGuvPomHAsDR+g4cwZSt97n4Jnn0Nv/XfY/N//YTio7WdiiKclux8dyuGEEt4/ksLjm6MJdMjgnxN9GeVjTa1SzXfnsvnmbCa1SjVj/Wx4fKwXBVVNfBSRyiM/ROFvb8Kz430I97e5M35//huRSETJktswMSmM2gBX1sOWBeLQkLClELZYHD+NOB3ULdgKt2Ar6nLzSNx7hsTkWnLiTVBIbPF2LMZ/jB92Q+b/5trtDUFzxBvmqI3i2pByAIwdoO9CsVJtIVoK6ujJ8R/qgP9QB6qKG0g8V0TKxSKyYsoxMNXBd5Ad/kPtMbe7hTK+pipxYm7cT+LUXATR/SZ8FQTOAXNX8QYi/4pYZY/fIVriGViKXw+5C5wGdDqau0WpJju2nIqCBlyDLLD3NOt0x1EQBCoLG8hLqsTSyQhHb7OubwpaGsVpi3JdcB/1X5W091aMAfKvsued06gVlsx9v2PP3huUpcJnojcwCzaJNk/d4JkTz5BSlcKBOQc6jaupyWP47ilMkVpxQFvOIsVAXlz4TYfxFdXFjN8dzhi1I5i8w5HEYq6sDO+wy71ZraH/GxFMCrJj4TATFh+ZSYjRHDbPW9VufG1DE2tfPEKlURVvvbWMPcuexj0yAut9B7D37GYDVQ85+1MaMcfzmP9if2xc/9ytJK1WYO9H0ZTk1LHgpQE3bJPqq5Rs+89l9AwVzHux/y3rnO7O6zmyLoGMqNJ2J/5F7svk8s/ZBI10ZOQ9t6dBscdUZsKmeaKsYdbn4iJ/6QvwmwZzvm4tiwDxQnD6XXHcsmN/uPuHGxfHLtFqoChGbJ67A967Riuw9nQG+2KKeG68D+EBtl0f9D+ERiuw42o+7x5JoayuGT2FlBa1lvn9nHky3PuGVvkXBI2Gmj17KfvkE9TFxRiOGonNs8+i5+vb4fPvji7gw4hU8qua6ONsRmZZPXVKNeH+tjw1zptgJ9NW8XtjCvg4Io3sikZCnEx5JtyH0b7Wd8bv0n87GpWYuF75VqzySuXgN1WUWbgMhfSjYoKbdgQEDRrnEZQ5LcNy6AQUxt24NmhUkHoIor6H9AjRc9ltBIQtEa/ditafN41GS05sBUkXisiJr0DQCti6m+A/1B6v/rY3J+lTNYmvIW67+D40LWDhCcHzRL21dfufZQDULZBxDGJ+FJ9DrQQzV3EqYfB8sBGHaqmaNWTHlZN+pZSc+Ao0ai1IAAEMzXTx6m+Dd39bbFxFVw5BEKgoaCAjqpSMqFKqihtvnFLfWByR7tXPBntvs193UpS1kHoYkvZAWgSom8TH9czEtT1gJniMbuPkc6fQK6XoCcXxbHnzCmZmWiZ3YwQyTVWw2k3892ORnX+oryMIAuN+GscAuwGsHrm6y/gZ34aQK9WikUhY3/9T+geO7jT+nq/CqJWoyM1/j4lBdrw3v0+n8c9ti+FIYjFBgReIa9jJhvG76OfYsRvDi2+txzHHGb+7jbB+9EFywkYyc9NnXb6Pm6GysIGtb0biN9SeMffevkl6nVFfpeTHNyIxtdZnzvP9QIBd70dRWdjA/BX9b20FoRtoVFr2rblGUVoNUx8LwSVQrNT/IuvwG2rP2Hv97gz3ibxIUeIgCGJznMt1b+eLX4hNc4794J4fwej6BMaWRtjzqFgVCbkbpn8Mir+nBreX7lPfrObr05mU1il5YIRHl+4cWqWSyo0bqfjqa7T19ZhMnYr1k0+g49L+zXmzWsPWy3msP5eNj60RT4z1bjWU5/eoNVp2RhfwybE0MaF2MuXJcd6M9eutIP9pVGTA1fUQ/QM0VYJMFzTNYGQHfe8RR1C3o0nuNjUFoj959CZR06trKianoYtEn/Pf/ZwbappJvVRC0oUiqooakMu0eNgV4jfEEcfRo5DKO0mStRrIPgOx28QKcUud+D6C5ornvJkbeWUtJO8Xq82ZJ1Fr5eTozyZNmEROoTlqlYCBiQ6e/Wzw7meDpZMROXEVpF4uITehAq1GwMRchpNNFYXl5lRXaJBIwMHHDK8wG1yCLCnLqSP9ainZseWoVVoMjOV4utTgJY/AvmwLEu31n4f/dPGPqlFsdk4+AM01oGcKvlMhcNb1JPkv0my3Q29i3BPK0/jm5QS8XCoZtaIbibEgwJs24gf/X8Xdujsqbihm/PbxvDjwRRb5dz0IY+XmcPaoSnBQCRx+IL7L+Ne+X8h2IQ79tId5d8ldjPLpeOwzwImUUpavv4ih99uYy9w4u2xzp/Fn45K59lk+zc2XmHThB3R/+Amvfm29kP8ogiCw9+NrlOXWsei1wR0OffgzyIgq5dBX8YRNckWl1BB3Mp+JD4qjZv8KmpvU7Ho/ipqyJmY9E0pxZg1nt6WJwzuWB9wZ+sjEPbDzITC2h3t3tL2IJe2HHQ+ITi737hCrNT8uhKJYGP8aDH3yjqj69nLnoqmpoWLdN1Ru3IigVmM2by5WjzyKwvbW/F6qNFp2RuWz5kQ6eZVNBDma8ORYb8YH2PYmyH8WKqXYhJZzHnwmgtf4Lp1ieoRWCzlnxUp00l6xCmvtLybIIQt+dZpSt0DaEYRrWyhNSCe5cSRpTSNoFowwlFfh61GH74R+WAT9Rh5ZHC9KIOK2i37ouiYQMEOs7rqN6FxK1g00Gi35SVWkXcghM7YClUqGvrQGT93zeLlUYT9kENKgma3dskqTUUbvITMym/QybwpbArDTScbLKgOPga4Y9JsB1r+xnW2sRBV/kOxzcaTnmJKjDEWDDgZ6zXgGGuI1Mgg7b/PW1xx1s1jxT9gNyT+LSbKuifjz858hasl/v1P4J9ObGPcATXkOX67MINQvh6FPL+/WMQ0r/ZHo6GLwyrVuxe9OPcjLF55ny9QtBFkFdRm/5dBT/KfkOGNbbPn4wYgu409e2cUTCa/QrzyYr5/e1OVkKJVGy/g33sREbxtjRrzBM8PaTuH7PS//8zucK0ywrdzNzN3fdxkPUJBahaWjUYcOD7/nl2T0Vo9FvlmOb0wi6VwRQJcNcH8GDTXN7HjnKs0NKlqUGjz6WjPhwUDRz/RW0tIo6t+8xnV/IT+/Bo6sFPVv92wBww7cOvKvippCjUp0dVE1wbxvxAW0l166iaq0lIovv6Rq209I5HIs7l2Exf3337Lx5SqNlt3RBaw5kU5ORSMj9Zu4z0efEfMnIbvDhrH08gdoqoaEnWKVuuCK6HTjPUGcbpuwU2yEM7QRtb197kZt4kn20eOkXCojp9IJARk2BgX4ejfird6OfkWkKAfxGg99FojNf7+Ta6haNOQnVWJipY+lY9c+5oJWoCijmtTIEjKiylA2qNDRl+MZao13f1scrauQJu0S9ciliWLToftIsSqdelh8DIno3hM4W0zQs09D/C7IOQcIYBMorsFFMZB1SmyMNHOBgFm0eM0ku9yJjKgychIq0Ki0YmU61BrPsN/JLUC8ocg6db2S/DM0VSLIDSi3W0Cp0TgC5034SyrJvYlxD8hPjGXPJ+XYmJ5n/uqV3TomflgIaj1d+h673K34hdtfIbZ+LyfnncfKqOu7pkOX9vNS0os8Z/8PFk18ost4rUZD+HchuGkN+fbByG69pm0zhuCdVY3vqbMYWHTdRLflX+9SWdEPw8Bclj2xrMv4yqIGtrx2Cc8wayY91HnDIYBGrWXzqosodGXc9dKA298R3A1UzRq2r76CgYkO057oc+sT0JuguqSRXe9HYeNqzKR/BHfp79ljmutg8wJxwQycDbPXdr6ICQIcfRnOfypqzGavbXMhaENVNvxwl6i1u+fHGzq5XnrpKS15eZR9+im1+/YjNTDAYulSLJYtRWZya3oTGlJSiXv7I4wvnESKQJG5PcI9Sxj5j4W3dbBRL38BZSlw7QdRz9tUDX5ToM9CcVJgOxXrxqJC0g6cIjleS3mTPVKJBhcnJT6jA3Af4Ib8N3apWq1AQUoVqZeKyYguQ9WsAcDS0RCfgXZ4D7BtNeJe1ADXk3qphLQrJdRXNSPXkeLexxrv/ja4BFi2729fkigmyPHbxXXWZYjYtBcwE4zb6XeoLRKr5vE7Ie+i6AsfMEuMb0fu0aJUkxNXQXrUdS2zSou+sQL3PtZ4hlrj6Gd+4zopaAVKMqvIOBVDZkIDtY0GSFFx3zvD0DX58wcb9SbGPSD50iWOrW/AUv80d3+4qlvHXOg7CEEiYWj0xW7Fj9ywlPLmfNaO+ZER3p3LHAC+OJnBh4ejubRyRrenOq3eNoOtjZmcnH0QE9PObcSqyvLIHzUBuRZsX16JxaLO5R2CIJAxfQbHbRZSaSXl+bfnI+3CwePYhkSSLxQDMH9F1010cSfzOf1jKtMe74Nr0O1xu7gZNBotUonkztDvXkej0iKVS2791q6yRmyaK7gqVkhitoDHGLHJVLedhUyjFgdqxGwWLZcmv9N972CNGhD+q7qZe/nraE5Lo2zNZ9QdPozUxATL5cswX7wYmdHNXYCVqamUf/EFdYcOI9HXx+yee0jUtUL4cRMOlQWUGVnSNG8Ro55chp5BFzeCvfy90KjFimkPeh0qskpJia4lNbKEhupmdPRkeIbZ4BZiRVFGDWmRxTTUtKCjL8crzBqvfrZUlzaSGllMcWYtAPZepvgMsEXZqCY1soSqogakUgkugRZ4D7TFPcQahW43dysEAVoa2l+3O6K5HnQMuy1na1GqyU2oJCO6lJy4ClTNGnQN5LiFWKGjLyczuoyG6makMglOfhZ49rXE3aUefde/phDSa9fWA5QNYjempKGmW/FqlRpjZR0yBGorazCx6Lih4xdq1QVom62Jzq3uVmIcnVuFg4Vlj0adTg5cxKYrb3L8yhpmjeu8wS96+1rstSCYm1K9dRvmCxd2mmQ1RUejSk/HclAFqoIAjpw7x6QRIzqMr6tUkhpZgt9gO7LjKri4J5MZT/btMF7VrOHKgWzsvUxxCfxr7LY64k6oEv+e7k7C6xFNVbBxDhTHwvzvRF2c2wgx8f1+Biz8qfUUOVUTbL9P7CgfvQJGvdAzffCt1Az28j+Prrc3Th9/hDIpibJP11D28SdUfrcBiwfux2LhQqSG3WuYVaakUP7Z59QdOYLU0BDLhx7CYtlS5Obm2AGaRxdzftMemtavw+W7T4jauoHq6fMZ8cyDGJv3DmP4r0Am7/H6ZOluw1B3GwbP8qQwtYqUyBLSo0pJOl8kJrdBlgwfZIdbiCXy6xManQMsCB7tRE1ZE2mXS0iNLObUllRATJJHLfTFK8wGPaObKB5IJD1LiqHH8Tp6crz6ie4VapWGvMRKMqLLbjTuuQRY4DnLA7cQq7/V+O3eKxPQ0tgE6CGrr+tWfEVBKTLESntOdCLB44Z0Gt+oakYtK0Pb4k90blWXzy8IAtF51Qz36tlEtWD/+TheepND+SeZ1UVsy+HjlFvICXrqWYpffZWm6GsYhLU/EASg6scfkRoZMenxhXzx6hmuHWlgUsd5MTHH8hAEGDDNHQtHI87vSCc/pQon3/b1f7En8misbWHSQ0G9DS5/BQ0VsHGmuJW4YJNoKg9iM4q+OWxfDusnweJdovZOWQNb7hGbY6a8BwMf/Gtffy+9XEfP3x/nzz+jKS6esk8/oez9D6j8dj0Wy5djvnAhMqP2E+Tm9HSx4nzoEFIjI6wefQSLJUuQmbWehCqTyxixbA7aJbO4vOMI1WvX4r5tHcm7N1M8ZhqD/+9hrJ3/nIFEvdx5SKViddTJz4JRd/tQlFmDlZMR+kYdF7lMrfXpP8WNfpNdqSpqRKEnayWr+DsgV8hw72ONex9rNBotgla4cQPwd+POK4X9BTQ3KgFQ1Dd0K74ir/DGv0sTUrqMv5KfjkSiRUdrx7W8arqSrxRUN1FW10yoSxejqX+HRCploqkPF4UGqiozOowrL8zAKaWK2uHBmE6bitTQkOqtWzuMV1dVUXfoMKYzZmBoboFpfzXGZXZciGm/8VDZoCLhbCHeA2wwsdIneJQjRua6XNyd0e57VzaoiD6Si1uwJfZePXvPvdwC6kthwzQoT4O7t/yaFP+C3xS4dyfUFcM3EyHrDKyfKtqyzV3XmxT3ckeiHxyEy1df4fbjFvSCgij74AMyxo2j/Mu1aOrrb8Q1Z2VR8M/nyZw+g4bTp7F85GG8jkVg/eSTbZLi3yKVShk0fxJTInah/Pgrit388Tq8jYJJE9mz/Gly4tP+jLfZyx2MXEeGs59Fp0nxb5FIJFg4GP7tkuLfI5NJ/7ZJMfQmxgColC0A6NU3dhEpUlNQcuPfDemZXcZfLRST52EuAVQ1qsip6Pw81/KqAQh17nl39eSgpWgkEo5e+bTj59/2JTIBPOctRWpoiMmM6dQePIimurrd+JrdexBaWjBbsACAuTPDaZE1cXp/+zZycSfzUTdrCJvgCoiLw4Cp7pRk1ZIVU94mPvpIDs1NagbN/AP+lL3cHHXF8N1UqMyChVvBO7z9OLdhsOxnsVluwzSozBDjg+f9ua+3l156iH7fvrh8/RVu27ai37cvZR99RPq4cMrWfEbhipfInDqNuogILB+4H89jEdg89RQy067lcb8ldOIIpu/dhHzjT+T0GYb7xQjq5s9i77z7iT/ZvWboXnrp5c6gNzEGVE3NABg1tKDRqLuMry8SE+NmmQJJbnaX8UkVYvX2nrB+AETndS6niM6tRlcuxc++4zHQHeHrPQ03jYTDhWc7jNEcPUWptQKf/uMBMF+wAKGlhZo9e9rECoJA9dat6IeGoucr+hxamJoiD67DMM+O+PTUVvGqFg2xJ/JxDbZsZUPjN8QOM1sDLu3NRKv9tWrcUNNM7PF8fAbYYuX053ep/uloNd2P1ahFC7SKjqv/f4j6MtgwXTS9v3eHaMbeGfYhcP9hscN56T7Ryq2XXv4m6IeE4Lz2S9y2b8egXz/K16yh9sABLBYvxuvoEWyee+4PW715Dwhi5uYvsNyzn4yR03BKvors4aUcmDCHc5v3otVqb9G76aWXXm4XvYkxoG4Wk2GFRk11aV6X8c2lZQAUOnphUFrQZXxubTZojBnh6Yyhjoxrue1XZn8hOreKYEfTLr2I20MilTLJPJDLKCkrTWjz9eKcRJwy6mgYFXbDVULPzw/9Pn2o+nFrG6lD46VIWrKzMVtwV6vHZ88ZhUai4dCe1nZ1yeeLUNarblSLf0EqkzJohgeVhQ2kRhbfePzKz9loNQIDp7v3+L3+7Yj8Gla7Q9bp7sUfegGO/Ot6RbfrnYke0VgJG2dBdR4s2iZWhLuDhQfMXw9OXTb29tLLHYl+UCDOn3+G5+FDeB2LwHbFi8itetbP0RWOPm7MXLsa9+PHyJyzDNPyIixef4GTw8Zz9P11KBubbun5eunlVlBe34xG+9c4ld1J9CbGgLpZBYBUq6KioOvqnKa8nCa5LiovX6yrS1CrOq8yV7TkYyCxRyaVEOJkRnRex4lxi1pLfGFtj/XFv2VSyH0IEglHrrYd2Ry79UukgM/81oNMzO6+m5asLBovt050q7dtRWpqismkSa0ed7KxR+1Tjk66NbnFouZaq9ESfTQXOw9T7L3abkV6hlpj7WJM5L4sNGotNWWNJJ4tJGC4A6bWf+1EnNtOzgU49CKoGmDL9UlvnXHp/9k774Cqyv+Pv+5l7yV7iqC4BQeKA8StqLj3tvJXaWZWtixLLcv0a2lpqZl7goobJ4qCC3ABIqLsvbnAXef3xy3LGIKiYvH6j3Ofc57nXO4553M+z+d5v3+BK+tVFsnycvh9COQn1s1YygpgyzBVTfG47SrR9wYa+I+h6ehY5wHxPzGxMGPQ0g/pEHqGlP/7AKVYjN2v3xPR1YdD8xeTnZzx5IM0UO9JLygjKCqVjMKyGrW/nVrA8uOxbA9PJLdEWqdjKSmXE3A9mUkbwumwOJh3dkZw7FYapdLKZyvTC8pYf/4+g3+8QIdeWVytAAAgAElEQVTFJ/FcepKPAm5wJjaTcnktZjj/RTSoUgCKP34wYqWMgrQHT2wvysuhSNcQXWdnNE4rSLoTT+O2zSptq1QqKSMNRy0vANwdjPkl5D5lMgXalRSnR6cVIpUrcXd4+im9Jk364Boi5lhGGP9UJxadukiatTa+bb0f2244oD8ZX39N/s5d6HXqBIA8J4fC4JOYjh+HWLviYoBB/l0IXnafwIBzvPPmOO5dy6Qop4zuo10rVZYQiUV09ncm6Icobp9PJf1+AWI1ER0GOT31ub4SFKXDnikqF6Gx21U6wdtGwvTjYFpJpjzupCpb3Gwg+P8E6TdVcmm/D4ZpR8HQ5unHUl6k6j/jFozZphKub6CBBp4rWjra9H5nGsrZU7i89xi5v22iyaFtJB/ZRahHD9zefo1mnauWs2yg/iGVKzkVncGuq0mE3M1CKagU0jo3NmNwWxsGtLJ6TG41t0TK/ogU9l5L5k5aISKRSmr4swO38GpixuA2NvRtaYmxbu1NY+QKJefvZbM/IoUTtzMolSmwM9GhS5NGhNzN4kBkKjoaavg0M6d/Kys6OJlyIS6L/RGphCXkIAjQxs6I9/o0JTajiIORqey4nIS+ljo93Szo19ISn2YW6Gv9N0LG/8ZZPgGFVFX3JVbKKcxMfUJrUC/IQ6JvjFULVc1t6s3oKgPj+7kZoFaKk6EqAHJ3MEGuFLiVUkAHp4p6vX/KubWzfzZ1hgFmbfkhL4K01GtY26hqm5PvXsfuYQkPxlfMEIq1tTHyH0rejp1Y5uSgbmZGfkAAyGSPFt39E7fGzhx0uIjGbVOy83O5fjwRE2s9nFpXnYWxb26KbVNjLgfdp1wix6OfI3pGL94a8oWhkMGeaVBWqJI6s2gOkwJgYz/YOhymnwD9v+laZ0arpNEsWsLwX1V2zDbtVKoQm/1VmeNpR0DfovZjkUpg+1iVeceo36BZ/yfvU0MEQSA0NRQ3Uzca6Tw5C1ckLWL+ufmUyctY1mMZVnpWdTaWBhqor4jFYjqPHgijB3I3PIqHq9fjeO0syqmnOezYEuMpk+k8elCNLadvJOdTUCrDq0kj1OqRAdG/mbiMInZdSSIwIoWcEilWhtq86eOCdzNzLsRlExSVyseBN1l44BbdXBvh09ScS/dzOB2TiUwh0NrWiC+HtmRIWxtS8ks5dCONwzfS+GDfDT4OFNHNtRGDWlvTt4UVRtVo/wqCwO3UQgKup3AwKoXsYilGOhoM97BlmLst7R1NEIlEyBVKLifkcvRWOsdvp3P01l+ljI0b6THH15Wh7WxwNv9rjU+5XMHFezkcu5VOcHQGQVGpaKqJ6epiRt+WVvRqboGFwautnFEdDYExoJT9lTEuz0x/QmvQLsqnxMoeh7bNyQQKYu5V2TYsOQaAFuYqxYU/A97IpPzKA+OkfCwNtbA2erYfXX/3N/jh9CyOX/+ZqTbrAbi1+xccgRajKpfXMhkzhrzNWygIDMR0+nTyd+9Bt2NHtJydq+zHZ3AbrqzJZveaiwgpuvSa0rxahziRSERn/ybs+/YaWrrquPd1eKbzrPec/AISL6qCXMuWqm3mzWD8blWQu32UaiGblgGUZKusmDV0YPzOx8XW7TqoaoG3joDNQ2HKocfNNp6ErAx2TVDZPA//VWX3WUcIgsAPET+w/uZ6LHQsWOW7ilaNWlXZPrs0m1nBs4gviEdTrMnooNF86/0tna0719mYXkXu5NzB2cgZbfUnX/tF0iJ+jPgRLTUtXmvzGoaaDcYSrxpNPdvS1PNHspMzCPthA6bBBzD58kPOr/qe0kHD8XpzMkaNKs4cCoLAxfgcVp++x6X7OQDYmegwwdORMR3tMa2FKdS/idwSKcdvp9O4kR6dnEwR1+GLgkQq5/CNNHZeSeLawzzUxSJ6N7dkTEd7ejQ1f/RS0tHJlLm9XbmTVsjBqFQORaVxNjaLRvqaTOnixMgOdrhZ/XWtGutq0tLGiA/6NeNmSgGHb6Rx6EYa78fe4CPxTbq6/BEk/y2TnFFYxoHIFPZdSyE2owhNNTG+bhYM87DFp5k5Wv94qVJXE+Pl0ggvl0YsGtKS64l5XE/Mw7OxGW3sjCqd3dVSV6OnmwU93SxYqhS48iCX4DsZnLiTzpmAm4hE4G5nhL+pDK+mFri0b/nE71BZVkbxuRDKbt3C4r15z/LveO40BMaAQvZHsblShjyropzYPzGQFFJkYoqZrQVxWvrIHyRU2fZGhkrLspOtygLR3EALOxMdIqpYgBeRmI+7vckzm1zY23elpVKNo1lXmfrHNo0z4aQ46NK7eadK99Fq0gTdDh3I270HrWbNkCUlYT73nWr76dS6DacttmGQZI2esSauHSvxYv8HVs5GdBrcGGMLXbT1Xh03nFpzKwAurYZOr6vslf+OfSeVu9zO8bBrEozZAjsnQHEGTD2iMtH4J45eMG4HbButWjg3JQh0ajCzoJDDvhkQfxqGroE2o+rk9ED1kP7u6ndsubOFAY0HEJkZydRjU1nktYhBzoMqtE8qTOL14NfJKcthje8arPWteffMu7wR/Aaz3Wczo9WM/5zBS5G0iCXhSzh8/zC2+rYs6LQAH3ufKtuHpYXxWehnZEoyEQSBA/cOMNtjNsNdhqMmfnW1Q/+rNLKzxO/bjykvnceF9buR792F0/a13Nv9G8mevrR8cwYu7VuiVAqcjM5gzdl4opLysTDQ4tNBzbE01GZr2EOWHYth5cm7+LWxZlJnR9rZG9eLa0kQBMITctkU+oCcknKGtLVhSFvbarOhtTl2ZFI+W8IecuhGGlK5avbXxkiboe6qzGlTy9qrO/3JrZQCdl5J5EBEKkXlcpzN9fhkYHOGedjSSL/ymU6RSERLGyNa2hixoL8bCdkl2JvqVruYXiRSrT9qY2fMggFuRCUXcPRmGodv/pVJ7tLEDJFIxIU4VdmGu4MxX/m3YnAb6xqXX4jFIjo4mT6WlFNKpRSfO0fhwSCKz51D06UJBr69MOjdC61mzVATi+jsbEZnZzM+HdScmMhY4rbvw2DbaaxyU5EBZ40sKHTvgu2gvrTp2w0NLdV4BKmU4osXKTxyhOKTp1BKJKg1aoTZazNRM6y/L/OiJ5lNPC86dOggXL169aX0/U+2vbuC/NJ2tImaQ0Eza/w2BVfZtkxSSoKHB/F+E/Bb/ilHe6kybwNOVZQ6AxixawGxkuNETr6KuprqoTV7RwTXHuRy8aPH5a5yistpv/gkHw1w4w3vZ9f0/f3wayzPDuNwz59RFIgoGzWTxKm96LdgdZX7FAQdIvX999GwtUUpkeBy7ixizeovupOXLhL7exk6PQqYPn7YM4/7X0FmDPzqq8oSTz0M6lV8hxHb4MCboG+pCopH/gathld/7LhgleucZUtVeYZuNRbaggBBc+D6ZhjwLXi+8fTn9A+UgpKl4UvZFbuLic0n8kHHD8gty2Xe2Xlcz7zOjFYzmO0++1GwFpMbw6zgWSgEBWt6raGNeRsAJDIJn1/8nGMPjtHLoRdfdf0KA82nf5i9SlzPuM5H5z8iQ5LBOLdxXEy9yP2C+/jY+fBhpw+xM/jrBUkik7Dy2kp2xu7EydCJJd2WoCHW4JvL33A98zrNTZuzoNMCPCw9XuIZNVAX3AgO5cGvm3C6eQkNQUG8UytOuflwQMsBOzN9Znk3YUR728eyg3czitga9pB915IpkSpoZWvIBE9HhrS1Qe8l1IaWyxUcikpjY2gCt1MLMdHVwNxAi7sZxWiqi+nTwpJR7e3o7mpe6zKQUqmCoKhUtoQ95GZKAXqaagz3sGNMR3vis4rZH5FCSFw2CqVAC2tDhrnbMqSdDZaGT56NKSmXcyAylR2XE7mZUoCWuphBra0Z28mBjk7PnrSqDYIgcCulkMM30zh2Kw25UsC/nS3DPGxpYv708qaCUknp9esUHAyi8NgxlIWFqDVqhEHPnpTHx1MaEQGCgIaNDfq9e6Hv7Y004QGFhw5RGqky9tJp3x6hZx9iM4pQXAjB/sEdNAQFRVp6pDX3wNrMAKOroSgLChAbGmLQtw9Ggwah27EjIvWXk5MViUTXBEF4oqRSQ2AMbJmzgqKylrgmfoJCS4P+By5V2TYp5j7F/oNImj6Xvh+8wYGJb2F58zKdo65U2r7bpglIlLlcn3700baNFxL48tAdwj/u9diFeio6gxm/X2XX653xdK7FNHkVpKdF0OfEZGabtMP+qgZOuy9hdGQ3Ns6tq9xHKZVyz9sHRV4eZjNnYDF//hP7EQSBt/e8xy3lNY6OOIquxr9cYeJJlBWqguKyfHgj5MmL5c6vgFOLwOdj8PmwZn3EHoPdk6BRU5h8APSqqOs99RWcXw7d50Ovz2p3HtWgUCr4MuxLAuICmNZqGu96vPvogSFTyFgSvoR9cfvwtvPmm+7fEJ0bzZzTc9DX1Gdd73U4Gz9eniMIAlujt/L91e+xM7Bjpc9KXE1c62y89Q2ZUsbaqLWsv7keGz0bvunxDW3N2yJTyNgWvY2fon5CKSiZ0XoG01tNJzonmk8ufEJiUSITm09kjsccdNR1ANV3d+zBMb6/+j0ZkgwGOA1gXod5DXXb/wIyHqRyefUGGp06hHFpIVJzK6wnjsN01EjUTSt/IS4ulxN4PZmtYYnEZhShr6WOv7sNEzwdaW79/LN02cXlbAtLZEvYQ7KLy3G10Gd6t8b4t7NFW0PM7dRC9l5L5kBkCnkSGZaGWgz3sGOEhy0uFtW/ECflStgS9pBdV5IoKJXR1FKfSZ0dGeZhV2FhWHZxOUFRqeyPSCEqueDRwrih7WwY0Mq6Qsb6Tmoh28IfciAyleJyOc0sDRjXyZ5h7nZ1kt2uD5QnJFBw8CCFBw4iS01FpKODQZ/eGA0egl6Xzo8CVnl2NsVnz1J06jQloaEIUpVyhlazZhj6DcJo4EA0bG0fO3ZBdh4RAccpPHUaq+hrqCvkhNu0IqNDD5z698S3lR0OZi83NmgIjGvB5jdXIJE2xaHoO3QyCuh5tnKrY4Co4FA0Z88k5+OldJs8jCOfLqfx3g1YnDqHmW3FBVFtN/pgpu7C6cnrH227npjH8J8usnZie/q3+uvhtfx4LD+fi+fmF33R1aybN6rJm9pTJMh5ZxNI9bToe+TJLkyZc8eRczyCJrt/Q7N1lxr1E5UVxcQjE3mr3VvMajvrGUf9CiMIqrKF2/tVAWvj7jXbLz9JVT5Rm2zEvVOq8gtjB5hyEAz+EQiFr4OjH4DHZBj8Q+2OXQ1ypZzPQj/j0P1DzGo7izfbvlkhiyIIAjtjd7Ls8jJs9W1JL0nHzsCOdX3WVRuwXcu4xvxz8ymRlfBRp4/wd/GvF9PBdUliYSILzi/gZvZNhjYZykeeH6GnofdYm/SSdJZfXc7xB8ex0LUguzQbK10rFndbTEerjpUeVyKTsPHWRjbd3oQIEZNbTmZGqxkNL6r/AgSZjKJTp8jbvgPJ5cuINDQwHDgAk3Hj0G7bttJrRBAErifmsS0skUM30/5QOzJmgqcjg1pbo6NZt2U39zKL2XDhPvuupyCVK/FpZs6Mbo3p5tKo0vGVyxWciclk77VkzsRmoVAKtLEzYri7LYPb2mD2R6mCIAiE3sth08UHnIrJQCwS0b+lFZO6OOLZ2LRG94f4rGIORqZyMCqVhOwSNNRE+DSzYGg7G0qlCrZfTiQiMR9NdTF+bayZ4OmIh0P9KEV5VhT5+RQePUrB/gOURkWBWIxely4Y+Q/FwNcXsZ5etfsrJRIkV66gbm2NdtOmNepTJpVx/UEup+/lcjI6g/isEgBcLfTxbW7BHF/XlzKL0RAY14LfZ/2PMpkTtpobsAiPp9P1O1W2Pb8pgEbffIJ8zUZa9+pC6Nb9mC7+iLIVa3Ef+LgEWkGZhK47O+NuMJItIxY+2l4uV9D68xNM6+bERwOaP9o+YX0Y+RIZh+fUMJiqAduPvcXWW+f4fr2C5NcH0Gfeiifuo/yhM9L4OLT7z4QBy2rc19wzcwlLC+PI8COYalczvf9v5s/SiJ6fgvf7z7+/BxdUNccGlqqa4z9rk2/tg70zVJJvozeDWt3chGRKGQtCFnDi4QnmuM/htTaVL+T8k/C0cN479x6Oho6s8V2DsfaTa6KzJFksOL+Ay+mX8XP249POn1YIHF9VguKDWBy2GDWxGgu7LKS/U/XKIBdTL/K/a/+jZaOWzO8wv0bfQ0pxCquureLog6M00mnE2+3ext/Fv6H++F9CeVwceTt2UnDgAMqSErSaN8dkzGgM/Qajpl/57yNfImXvtWS2X07kflYJBtrq+LezZWwne1ra1M7++u8IgsCl+zmsP5/A6ZhMtNTFDPewY0a3xrhY1HyqP6uonINRqQRcT+Z2aiHqYlXg6u5gTGBECvcyizHT02RcJwcmdHbA2kjnqcd7M6WAA5GpBEWlklmkcr11NtdjgqcjIzxsn0ourb4hyGQUn79AQWAgxWfPIshkaLm6YuTvj6GfHxqWT6Fq9Aw8yC7hdEwmp2IyiM8sIXSB70tRUWkIjGvBptdWIVXYYGdzmMZ7w2kSdQ1NrcqzLMe/WYvDplUYHjyKbVMnEqJiKRvjT/Jr8+jz3uNBQnBcJPMuTmKUw4cs7Dnxsc/814SiqS5m9xuqjKxCKdB20Qn83W1Y7F91qUNtyc6KZt2HI/C/JGAefAALuye88WXcgZ+7gK6ZSt7r3VtVT9P/g/v59xl2cBgTmk/gg44f1MHoXzFy4mFtd7BxV2VwX1Qgkhiu0kXWMVYFx7kJsG0U2HVUScNpPN1D5J/IlXIWnF/A8QfHmd9hPlNaTqnRfhKZBC01rVoFZgqlgl9u/sLaqLU4GDjwnfd3uJm6Pe3QXzoSmYSl4Us5EH8ADwuPFyJRdyPrBt9d+Y7IrEhcTVyZ334+XrZez7XPBl4ciuISCoMOkrdzF+WxsYh1dTH088Nk7Bi0W7SodJ8/F8LtvJzIkVvpSOVKWtsaMbaTPUPa2mCgXbOSAblCyeGbafx6/j63Ugox09NkUhdHJnV2fJTpfVpi0gsJvJ5CYEQKmUXltLEzYkoXJwa1sa5U+/9pUfyhtqAmFtHB8cXWDj8vymJjKQjcT0FQEIqcHNTMzDDy88PIfyhabm714hylciWa6i/HW66mgXGDKgUgKMWIBDma5io92ZzU+1g3rlxuSpqlsoNuZK96qNm3aMIdsRqS+IqWvdfSYgFwt6qocezuYMzOy0nIFUrU1cTEZxVTXC6nnf3TG3tURiPz5vjEikizh5Y2NVjQd2sviMSqLOMmPwhfC76f1qgvZ2NnhjYZys6YnUxsPhEb/WcwonjVkEth73RQ04Dh615cUAzg4Kkq29gyDDYOgPJCVe3xuB11FhQrlAo+C/2s1kEx8FRT+WpiNf6v7f/RwbIDC0IWMOGw6mVrdLPRNb65S2QStsdsx9fBF2ejqiUHnzd38+7y/rn3SShI4I02bzCr7SzUxc//1tvGvA2bB2wm+GEwK6+t5I2Tb9DVtivverxLM9PKddcbeHVQ09fDZNw4jMeOpSwqirxduyk4eJD83bvRbt1alUUeMOCxqXKR6C+FgS8kKsOJnVeS+CTwFosPRTOojTWjO9hXuchMIpWz60oS688nkJJfShNzPb4e3pph7rZ1FrS6WRny0UBDPujvRnphGTZG2s8loPtTbeFVR56XR+GhwxQEBlJ25w5oaGDg44PR8GHod+uGSKN+1Ue/rKC4NtT/Eb4IBDVEghwdS1Ugl5datfyaMiebIi09tHRUi+bUNdTJMrZEnFTRrjc2R2Uv7eVYMdPVzt6YUpmC2Iwi4C9jj2exgq4MWUoKpjlK2pnmw72T1TcWBNUUfGNvlU2w2yC4/IvKLa2GvNnuTUSI+Cnyp2cc+SvG6a8gLRKGrq5cau15Y+sBUw+BQgo6pjBxX82k3GqAUlDyxaUvOHT/EHPc59QqKH5WOlp1ZM+QPXSy7sTi8MW8d+49CsoLnrhfRkkGU45NYdX1VYwOGs3m25tRCsoXMOK/EASBPXf3MP7weArKC/il7y+87f72CwmK/0QkEtHXqS8H/A8wv8N8bmbdZFTQKD658AmpxU82M2qg/iMSidBp1w6br5fieu4slh9/jLJUQtqnnxHXvQdpCz+n9OZN/jk7bKyrydSujTn6TncC3/RiaDsbjt5MY/S6S/h+f46fzt57ZHGcU1zOiuC7eH1zmkVBd7Ax1mb95A4Ev+vNuE4OdZrJ/RM1sQhbY516keV8ESjLyykIOkTizNdIeutt8gMCkeflVdpWUCgoDgkh+Z25xPXwJmPJEgAsP/kE15Bz2P34AwY9e9a7oPhVoSFjDAiCGBFyDK1UZhOF6RWD3D8R5eVSrPv4yl6JhS0GaQ8rtE0ufohIboKZbsWVth5/WD5HJObT0saIiMR8jHQ0aGxWt7WUxefPA2DQRA+ubICm/apunHId8h5Ajz9qY7vNg5hDcPU36DqnRv1Z6Vkxzm0cW6K3MLXlVFxMXJ7xDF4B4k/DxR+g/TRoPvjljcOqNbx9RZXxr6OgWBAEloQtYf+9/cxqO+uJNcXPA1NtU9b0WsPvt3/nh+s/EJUVxdJuS/G09qy0fUxuDG+deotiaTFfd/+a4wnH+e7qd5xKPMXirouxN7R/7mMulhaz6NIijj04RhfrLiztvrRGjoDPC001Taa0nIK/iz8bbm1g251tHE04yji3cbzW+rUa1X7/nZzSHAw1DdFQa3jw1ifUjIwwnTwJk0kTKY2IIH/P3kdZZC03N4xHjcRo8ODHNGRFIhHuDia4O5iwcHALjtxMZ/fVJL49Fsvy47F0cDIlKimfcrmSvi0secPbmfaO/9E1JM+Bsti75O9V/Z+UBQVo2NmpAt9Tp0BNDd327THo3RuDXr4Icjn5AYEU7N+PPCMDNWNjTMePw2j4cLSbNcwC1RUNGWNAENQBBSa2qulWSUbVmRTNwnzKDB5/iAgOTjQqzKa8tOyx7bmyFPTF1pUex85Eh0b6mkQmqYw+IpPyaWdvXCO3nuLzF1AU1SyLWxxyHg0bGzR7ToK4E5BXMYB/xK29oKYJbn5/DLI9NO4Bl9aAvLxG/QHMbD0TXXVdfoj4ocb7vLKUZEPgLDB3g35LX/ZoVJrGdRgUL7uyjN13dzOj1QzebPtmnRz3aRCLxExrNY2tg7aiq67LzBMzWX5lOVKF9LF2IckhTD46GREiNg/YjJ+zHz/4/sDirouJy4tjRNAIdsbsfK7Z47i8OMYeHkvww2De8XiHtX3WvtSg+O8YaRkxr/08Dg8/jJ+zH1ujtzIgYAC/3vgViUzyxP2LpcUsDluMz24f/AL92Hd3HzKl7AWMvIHaIBKJ0PXwUGWRz4dg9cXniMRiMr5aTFz3HqTMf5+SS5cQlI9fB7qa6oxsb8fuN7pwZr4P/+fThLwSKf7tbDk5z5tfJndoCIrrAGVJCfl795IwZgwJQ4eSv3Mn+l274vDbRpqcOI7L6VM47d2L2WszUeTlkrF0Kfd69Sa+X39yfv0VLbdm2K5ahWvIOSw/+qghKK5jGgJjANQQiRSY2apqcMszM6psqVucj9zo8TpgPRdn1AQliTfjHm1TKpWUi9Kx0Knc8lgkEtHO3oSIxDyKy+XEZhQ9souuDll6OkmvvUb26qpNOh6NQSqlJCwMvR7dEXWYppLrurapisYKlVObS5/HA6tu86A4HSK3P7G/PzHWNmZaq2mcSTpDZGbV0nevPIIA+9+E0nwYsQE0/z2yWIIgsOLaCrZFb2NSi0m84/FOvZjSbGnWkt2DdzOm2Rh+v/M74w+P516eypJ9R8wOZp+ejZOhE9sHbX9URysSiRjqMpSAoQG4W7izJHwJrwe//lxKCQ7dP8SEIxMokZWwvu96ZraeiVhU/26zVnpWfNn1S/YN3kcHyw78EPEDAwIGsPXOVsoVlb8EhySH4H/An92xuxnZdCRmOmZ8cekLBgcOJjAusCFArqeoGRhgMnYsjQP24bRvL8YjhlMcEkLitOnE9+5D1uo1yFJSKuzXuJEe7/dzI3ieN8tGtqmVykQDlVMWE0PaokXE9fAm7dPPUJaUYPnRAlxCzmG74nv0unRBJBarymNatcRi7lycg4JocuwoFu/Px2L+e7icOY3DunUY9uuL6AnmWw08HfXvjv0SEFBHJFKgo2tIibYIRU5Ope2USiUGkkIEk8cL9i1aqh7AabdiHm27k5mMSFyOs5FTlf26OxgTn1XC+btZCELN6otLIyIAKDxyFEGhqL7ttWsIEgn6PXqAsT007Q8RW1QLxf7Jw4uqALj1iMe3O/uoVBZCV6mC5xoysflEzLTNWHltZYXatn8Nl3+BuOPQ9yuwqnyx5qvK2htr2XR7E2ObjeX9Du/Xi6D4T3TUdfi086es9l1NVmkWYw6NYfap2SwNX0oPux5s6r8JC92KckRWelas7b2WhV0WcjPrJv4H/NkWvQ1FLX7XVSFVSFkctpiPzn9Ec9Pm7PbbTQerJy5+fum4mLjwY68f2TxgM02Mm7DsyrIKmeDcslw+DPmQt069hYGmAVsHbuXzLp+zbeA21vRag7GWMQsvLmRI4BAC4wKRK+Uv+awaqAqdli2xWrgQ15Bz2CxfjqaTE9lr1nCvdx8eTpumms4vLX3Zw/xXoZRIyN8XoMoO+w+jYF8ABr174bh9G85BQZhOmYK6SfWL7jWdnDCbMQOzmTPRsLR8QSP/79IQGAOCSB1EqodjiYE6opz8StsV5xehrZCi3ujxaVFHd5U0TuHde4+2hSdHA9DKvGr3Lvc/MsSbLj4AqFHG+E87RnlWFpIrlbvtPRpvyHlEGhroef5Ri9lhBpRkQfTBio1v7QUNPWg64PHtIpEqa5yXAHf2P3F8f6KrocustrO4nnmd8ynna7zfK0NOPAR/rsqwd3r9ZY/miZx6eIqfI3+uUVZvZ8xOfgw7f6MAACAASURBVIr8iSFNhvCR50f1Kij+O9723uwbso/ONp05m3yWic0n8j+f/1WrgiESiRjVdBSBQwPxsPDgm8vfMOXYFOLz4596HGnFaUw9NpVdsbuY2nIq6/utx1zX/KmP9zJwt3BnQ98N/Nr3Vyx0LPji0hf47/fn58if8d/vz4mHJ3iz7Zvs9tv9yMpbJBLRw64HOwbtYLXvagw0DVh4cSGDAwez9+5eZIqGDHJ9RaytjZHfIBw2bsDlZDCN3n4LWWISqR98SFy37qR+8gmSK1f+vUmNF0D5vXukL15CnLcPaZ98grKoGMuPFqheSpYtQ9fDo97cW+VKOWeTzrIwdCEbbm7gbt7d//T/vmHxHarAWCRW1VqVGWqjkV9Sabush6qpVy3Lxx96hqZG3NIxQvHgwaNtN7NUQbKnfXOqoo29MSIRhCfk4myuVyNhcUlkJNqtWiG9f5+CQ4fQ69y5yrbF50PQ6dD+L7meJr5g4gRXN0LrkX81lEvhzgFwG1h5OYCbn0r+6/xKaDm8xg5qI1xHsDV6K99e+ZbO1p3RVKvH0z6CAJd/BfuOqgx5dSiVcOAtVT32kLpzlHtehKeFM//cfOSCnIjMCL73+R4DzcqtV48mHGVp+FJ87H1Y5LWoXpYB/J1GOo1Y7bualOIU7AxqrgZio2/Dz71/5tD9Qyy7soxRQaN4vc3rzGg1o1YLyi6lXuKDkA+QKWWs9FlJb8feT3Ma9QKRSERn6854DvTkXPI5foz4kZ+ifqJ1o9Ys8lpUpUW3SCTC296bHnY9OJt0lnU31rHo0iLW3VjHtJbTGO46HG117Rd8NvWXpKIkAuMCaWHWAm97bzTEL3cBo4atLeZvvUWj//s/JFevUrD/AEVHj1GwLwANOzuM/P0xGjoETfvnv2j1VUeQSik6eZK8HTuRXLmCSEMDg379MBk7Bp327etNIPwn9/Pvs//efg7GHySnLAc9DT1KZCX87/r/sNKzorttd7rbdsfT2vM/5aDZEBgDgkgDkVj1diQ3McAgIavSdvnJaegC+tYVpzLyzW3QTkt+9PeDggcISi2am9tWaPsn+lrqNLM0ICa9CPca6Bcry8spuxON2ZTJaDo3puhEMMqFCxFXUmckS01Fei8e4+F/K40Qi1XKCSc/h8xosPgjaL9/FkrzoNWICsd5tF/XuSpHt3snwbXPE8cKoKGmwcedPuaNk2+w6fYmXm9TjzOrMYfg6PugbQwzT0KjqjP9XF4HiZfA/2cwrN9azffz7/PumXdxMnJidLPRfHv5WyYdmcTqXqsrBJKhKaF8fOFjPCw9+K7Hdy9UVuxZEIlEtQqK/77f4CaD8bLx4pvL37Amcg3HHxxnkdeiR1nRqhAEgc13NrPi2gqcjZxZ6bMSp2rKpl4lRCIRPvY+9LDrwYOCBzgaOtbInEUkEtHToSc+9j5cTL3Iuhvr+Pry1/x681emtpzKqKaj/nUPV4lMwuY7m7mSfoVeDr0Y3GRwlS+d2aXZ/HLjF/bc3fOo3KSRTiOGuQxjuOvwp/oN1yUisRi9Tp3Q69QJ5aefUBQcTP7+/WSvWUP26tXoeHhgNGQwhv37o2Zct7KilVF68yYloRfR9eyETrt29S6o/Duy1FTydu0mf+9eFDk5aNjZYf7ePIxHjEDdtH4tViyWFnPswTEC7wVyI+sG6iJ1utt1Z5jLMLrZdSO3NJfQ1FBCkkM4fP8we+7uQUOsQQfLDnS17Up32+40Nmpcr/8fz0qD8x2wduYhdDXjmPzTuxyaMxybs9F43Iiu0O7suh1YrvwSNm6juZfHY58dmDoX22vn8Ii6hlgsxuu3MZQLJVybfqjavhfsu8HOK0l85d+KSZ0dq20ruX6dh+MnYLdmNSINDZJefwO7Nasx6NWrQtu8nbtI/+ILnA8FoeXyN8m0kmxY0RzaT4WB36m2BbwOd4/D/DhQryKrK5fCD+1UGedpR6od5z+Zd3Ye55PPs99/P7b6Vb8ovDSkJbC6kypbLskFLQOYeQr0KhF/z4mHn7uq1DrG76qzbHGxtBh9zbpd3JJTmsOEIxMok5exfdB2bPRtuJx2mbln56Ih1mBVz1W0s2gHQFRWFK+deA0HAwd+6/9blQ/3fzNnk87yVdhXZEmyGN1sNHM85mCoaVihXZm8jEWXFnHo/iH6OPZhcdfF/7qAry4QBIGrGVdZd2Md4WnhGGsZM95tPOPcxtVaHq6+oVAqOBh/kNURq8kszcRO347k4mR01HUY2Hggo5uNpoWZqsSuWFrMptub2HxnM1KFlOGuw3m9zevE5Maw9+5ezqecRxAEvGy8GNl0ZL3IIv8dWWoqBYcOU3DwANJ78Yg0NND38cZwyBD0vb0rTcw8LYJSSXFICLkbNj5WKqhuY41h/wEYDuiPdqtWzzUoK4+LI3fbNmSpqej38Magdy80rCq6VAqCgOTSJXK3b6f49BkA9L29MRk3Fr1u3RCJ689smyAIRGRGEBAXwImHJyiVl+Ji7IK/iz9+zn6Y6VRudCJTyLieeZ2Q5BBCU0KJL1CVnNno2dDNthtdbbvS2brzK3P/a7CErgU/vX4cA63bTPpxHke/fA2n7RdwuBKKnsHjb3pHv1yF0/a1mAWfxsLeutLPTI+exLKxLW02dMdSsyXBk9ZW2/fea8nM3xPF0Xe609y64kP47+Rs2Ejmd9/hGnoBNUND4np4o9elM7YrVlRom/TW25RF38Hl1KmKN5F9r0HsUXgvRqV5u9wVWg2HIT9W2z9hP8OxBTDlEDTuXn3bv5Feks6Q/UPwtPbkR98n9PEyOLkILqyAaUdBrAG/+4F1O5WbnMbfpoCVStg0UGWb/VZYnWWLjz84zgchHzCz9Uzebvd2ndz0y+RlzDgxg7u5d9nYbyOtzf+yGU8oSOCtU2+RUZLBkm5LcDVxZcqxKRhqGrJ5wOZ6Iy32MiiWFrMmcg3bY7ZjomXC+x3fZ2DjgY/+J2nFabxz5h1icmN42/1tXmv92r86c1JXRGZGsuHWBs4mnUVHXYeRTUcyucXk526L/TwITQnl+2vfE5cXRxvzNszvMB93C3duZ99mV+wujiYcpUxRRutGrfG09mTf3X3klefR17Evs91nV5hZSC9JJzAukH1x+8iQZGCmbcaQJkMY5jqMxkaNX85JVoIgCJTduUPhwYMUHD6CIjsbsZERhn37Yujnh27HDk8dDCqlUgqDDpHz20ak9+JRt7bGdPJkDAf0pyQsjKKjxyi+eBFkMjTs7THs3x+D/v3QbtGiTq4/QaGg+FwIuVs2I7kUhkhLC3UrS2QPVZ4G2m3aqLSE+/RG3dycgv0HyNu+Hen9+6gZG2M8ahQmY8egYVu/Ej/ZpdkExQcREBfAg8IH6KrrMqDxAIa7Dqd1o9a1/u5Si1O5kHKB0JRQwtLCkMglqIvVcbdwx8vGi642XWlm2qzeluA1BMY1RKFQsPatcxjrRDJh5TxOr/0M6//tRW//ZhzcOj7W9uCcz3AODsDt5g3U1R+fWgzbfQSjhe9RvOxHnHp1wndfVzoajWej/0fV9i9XKIlKzq+RNmTy7NmUxcTiEnwCgLRFiygI3E/T0AuP2X4KUil3O3fBcPBgrBd9UfFAiWGwsR/4/Q90TGDPFJh8EJy9qx+ArBR+bA8GVqqMai0uqo23NrLy2kpW+67G2/4J/bxIsu7Cz16qmuthf7zE3A6EPVNVpSXD16tKSeCvFwP/n6Hd+DrpPrkomVFBoxAhokhWxMTmE/mg4wfPdLNXCko+CPmAEw9O8L3P9/RxrFj6kleWx9wzc7meeR1DTUM01TTZPGAz9gYNdYQA0TnRfHnpS27l3MLT2pNPPT8lpyyHeWfnUa4o55vu3+Bj7/Oyh/nKcS/vHhtvbeRIwhFEIhF+zn5MazXtpVp215TY3Fi+v/o9l9IuYadvx9z2c+nr2LfCtVpQXkBQfBC77+4moSABT2tP3vV4l5aNWlZ7fLlSTmhKKAFxAZxLPodCUOBh4cEw12H0dexbr7JyglxOyaVLFAQFUXTyFIJEgrqlJYaDBmHkNwit5s1rdA9TFBeTv3Mnub9vRp6VhZabG2bTp2E4YEAF1zZFQQFFJ09SePQYJZcugUKBhoMDhv36YtCvP9otax8kK4qKKAgIIHfrNmRJSahbWmIyfjzGo0ehbmJCeXw8RcEnKTp5krJbt1Q7aWiATKay3Z4wXmW7raVVq36fJ0pByaXUS+y9u5ezSWeRC3LcLdwZ5jKMfk796ux3JFPIiMiMIDQ1lNCUUGLzYgGVIZOXjRdeNl50selSrxItDYFxDSkqyGfzh9cxMYhi/HfvEh64FsOPViH9aRFtfUc/1vbAhDcxv3MNr4jwCsdJjk2gaOhAEqfORjq0Ax9fnsGkxp/xQY/RFdo+DYIgENejB3pdumD77bcASK5d4+GEidh89y1Gg/9yXCsJCydx6tQqyywQBFU5gFisKo1IugzzoqEGdYREbFPVGo/aBC2H1Xj8MoWMkUEjKVeUs3/o/lovxlEq5JSWZqOnX4cZJkGAzUMhNRJmXwX9v0l8XVgJJ79QuQD6fvpcSihkChlTjk3hQcEDdg/ezbbobWyN3spw1+Es7LywRnWdlbHq+irW31zPvPbzmNZqWpXtpAopiy4t4kLKBX7p88sj3d8GVCiUCvbe3cuq66soU5QhCAJ2Bnas8l31SgRy9ZnU4lQ23d5EQFwA5YpyfOx8mNpqKh4WL2alvkKpIDgxGC2xFt3tuldbT59dms3qiNUE3gvEQNOAWW1mMabZmCcu0hQEgZyynKcKDLJLszkYf5CAuAAeFj5ET0OP/k798Xfxp61523o1S6EsLaXo9GkKDx1WOa3K5Wg6O2M4cCCGAwei5Vwx6y3PziZ38xbyduxAWVSEnlcXTGfMQM/Lq0bnJs/Lo+jkSYqOn6AkLAzkcjTs7DDo1xfDvn3RbtOm2uNIExPJ3bKVgn37UEok6Hh4YDp5Ega9elVpoyxLTaXo5CmkyUkY+fmh06b6dQjVEZsbS1B8EI10GuFt742TodMz/08zJZnsv7efgLgAUopTMNYyZkiTIYxwHYGz8fO/X2WXZnMx9SIXUi5wKfUS+eUqda9mJs0eBckelh5oqb28l4iGwLiGZCYlsmfJPRqZ3GDM13OJDjsKU+eRu/A1uo6f91jbQ4PGolWQS58LJyocRyFXcKOtB4lefYka35Y9ictY4bWFPq7t6mSc0uQU4nv3xnLhZ5iOV2UrBaWSe716o9XUFYd16x61zfjuO3I3b6HppUuo6VdhMX1lPRx+T1VK0el1GLCsZgNRKmBtd5BJ4K3LVdckV9Zl+hWmH5/OrLazeKvdWzXeD2DxroEclSSys/ev2Nt3qdW+VXJrH+ydDgOXQ6d/WB0LAhycrdJ9HrIaIrfVeQnFiqsr+O32b3zv/T19nfoiCAJrItew7sY6BjgNYEn3JbWuNQyMC2ThxYWMbDqShZ0X1ixro1Q8dRD+XyC7NJuV11YiVUj5rMtnldYdN/B05JblsjNmJztidpBfnk/rRq2Z0nIKvR16P7ffZGRmJEvDlxKdq1pHYqVnxeimoxnuOvyxWkupQsrW6K38cuMXyuXljHUby6y2szDSMnou46oMQRC4nnmdgLgAgh8GUyovxcnQiaEuQxnsPBhLvfqlaSvPy6Po+HEKDx9BcvUqCAJaLZpjNHAghgMGICgU5GzcSEFAIIJMhkH/fpjNmIlOq+qz6U/qs/j0aQqPH6fk4iWQy1G3ssKgTx8M+vRGt317RGpqCIJA6dWr5Pz+O8WnToOaGoYDB2A6ecoz9X837y7bo7dzMfUibczb4GPvQ3fb7hV+JzKFjBMPT7AzZieRWZGoi9UfLcJ0MHCgh10PvO29aW/RvsbKOAqlgoupF9lzdw8hySEoBAWeVp6MbDoSXwffl6YEpRSUROdGcyn1EhdTLxKRGYFcKUdLTYv2lu1Z4bMCPY0qYpPnSENgXEMSo+8QtCodC4tbjPpyDplJseT08Sf5jUH0eXf5Y22Du/en3MAIvyO7Kj1WcLe+SA2M2TmzFRFFewkdG4aRdt1MWxQEHSL1/fdpHLAP7RYtHm3PXL6cnE2/43o+5JFI+P3BQ1AzM8Nx029VH7C8CL53A2kxzDipkimrKXdPwPZRMOA78Kyd0sSHIR9y8uFJAocG4mBYuSvgP0lLvcbAE1OQi0S0UqqzefwFNLSe8aIqL4LVHVVZ4tfOVJ4tV8hg6whIOKf6uw5LKC6kXOD/Tv4fo5uO5rMunz322Z9lJz72Piz3Xl7jN+zIzEimHZ9GR8uOrOm9pl4t4GmggeoolZdy8N5Bfr/zO0lFSdjq2zKpxSSGuQyrs6nfLEkWK6+tJOh+EJa6lrzX4T00xZrsiN1BeFo46mJ1+jr2ZZzbOLJLs/n+6vckFyfjbefNex3ee+n1viWyEk48OMH+e/u5nnkdsUhMF5su+Dfxx8fep95J4skyMig6doyCI0coi7qh2igWI1JTw2jYMMymT0PTyalO+1QUFFB89iyFJ4IpuXABobwcNVNT9Hv6UB4dQ9mdO6gZGWE8diwm48ejYVnRCKgmyJVyziWdY1vMNq6kX0FbTRtPa09uZd8ipywHNZEa7hbu+Nj74GHhwZmkM+yL20duWS4OBg6MaTaGoS5DkcgkhCSHcDb5LJfTLiNVStHX0KeLTRd62PWgm223Smccskuz2X9vP3vv7iWlOAVTbVP8XfwZ4Tqixs/VF4lEJuFqxlUupV7iXv49funzy0uZ9WgIjGtI7JUrnNxQhLV9NMM/eQuZtIy7bdx5OKIjA5dsfqxtqEcXst3aMXT7z5Ue6+DIGZg8iOXzOc3Ikd0nasaZOhtn+leLyQ8MpNnlcETqf037lUVHkzBsOFZffI7J2LHI0tK419MXi/ffx2zG9OoPGrwQ7p2GWedrVxogCPD7YJXk25wI0K55Bi1LksXg/YNpZ9GOn3v9XKOLY8mugewtTeQ9y24sywxlim4T5o+qudlIpRz/BC6tUUmz2VVznZTmw+YhYNJYVT5SBxdzliSLkUEjMdU2ZcegHZU+0HbG7GRJ+BI8rT35oecPTwwOMiWZjDk0Bh11HXYM2vFCs1oNNFBXKJQKziSd4bfbv3Ej6wYGGgaMaDqCcW7jsNF/upkamULGtuhtrL2xFqlCytSWU5nZeuZj19T9gvvsjt3NgXsHKJYVA+Bi7ML7Hd/Hy8arTs6tLkksTORA/AEOxh8kvSQdfQ19+jn1Y3CTwbhbuNe7xU/S5GSVW6tUivHoUWhYPF1ACqoEwLEHx2hm0oye9j2rVDhRlpRQfP48RSdOUHz2HOpWVphOnozR0CGIdXSequ+C8gL2xe1jV8wuUktSsdazZpzbOIa7DsdIywiloORW9i3OJp3lbPJZ4vLiABAhwtvOm7FuY+li06XS/49EJiEsLYxzyec4n3yerFKVbGwrs1Z0t+tOD7selMhK2B27m9OJp5ELcjytPBnVbBS+9r610l//r9IQGNeQyLNnCd2pxK7JXYa+PwuA8PYtyOrgjN+6v6TWFHIFd1q3IaHXMIasXlzpsYLe+wrnwzuYOtcWLW0LLkzdVmfjTBgxErG+Po6/b3psuyAI3PcbjJqJMU5bt5K3ezfpCz/HOeggWq7VaPGqdn76QC/lOvza868a3Fqw5c4Wvr3ybY0MEbIy79D/yGgGa9nwxbgTLN41kF1lSaxxm04Pz3efbuwZt1XlIO4TVQYdT0KpVH1PdRAUK5QK3gh+g6isKHb67aSJcZMq2x6MP8hnoZ/RwrQFq3utrlJSR6qQMu34NOLy4tg2cFuVRgwNNPAqEZUVxZY7Wzj58CQCAr0cejG5xeRa1diGp4WzJHwJCQUJeNt580HHD6rNqElkEo49OIa6WJ2BjQfWey1vpaDkSvoVDsYffFRqYatvy+AmgxnsPLheZg+fBqWg5HzyeTbe2sj1zOuoidRQCArURGp0sOxAL8de+Nr7VllaIiiVFRQzZEoZpxJPUSorpbtd92prwe8X3GfbnW0cjD9ImaKMTladGO82Hm9772p/I8lFyURkRuBh6VErqVJBEIjJjSEkOYTzKee5kXUDAVWsZqhpiL+LPyObjnzpsxivGjUNjOv3Vf8CkJaUAZqoa/31tlViqIk4r+Cxdnnp2agLSjTMq7549F2bIEbAvCATXdMnfvc1RimRUBYTg9nMmRU+E4lEGPkNImvVD8jS0ig5fx51a2s0/65dXBXPEujZeqhc8C6tUVlNG1o/eZ8/GOc2jgP3DrAkfAkdLDtUq2m6OeQT5MCMbp8D8P7QHUTu6MEndzaw16kXlpa1XAAhCHB4PmgbQe8varZPHepRbri1gfD0cBZ5Lao2KAYY0mQIBhoGfBDyAZOOTmJt77UVHnSCILAkfAk3sm6w0mdlQ1DcwL+GtuZtaevdlrTiNHbE7mDv3b0EPwymlVkrxjcfTz+nflXWUGZJsvju6nccTTiKnb4da3qtoYddjyf2qauhy3DX4XV9Ks8NsUiMp7UnntaefOL5CacSTxEUH8S6qHWsjVpLm0ZtGOg8kP5O/at8sa7PyJQyjiYc5bdbv3Ev/x7WetYs6LSAYS7DSChM4NTDUwQ/DGZp+FKWhi+lrXlbejn0wtfBF0fDv3wB/h4UF0mL2Hd3H1ujt5IhyVB9jojW5q3pad8TX3vfRwHnxdSLbIneQmhKKJpiTfya+DGh+QSamjSt0fjtDOye2nyouVlzmps15422b5BXlkdoaihixPg6+Na7spl/GzXKGItEov7AKkANWC8IwjdVtBsJ7AE6CoJQbTq4vmSMQ/fuJ/KkIS7uSfR7YwoAx/y9UJeU0/vEtUftYi5GIkwfR/rcz+g5q/I60+jzV+G1Saz0F2PS8x2W9asbp7eSy5dJnDwFu7U/Y+DjU+Fz6cOHxPfrj/ncueT8+iuGgwZh/eWiOum7WnLvq4wx2o2vWeb1b8TmxjL28Fj6OPbh2x7fVtomLzeefgeG0kvTnK8n/FWWkvDgLGPOvE1LkTbrJ15ErRYLALkVAHunweBVKpOTF0hkZiRTj02lr2NflvVYVuOsV1RWFLNPzQZgTa81j2kS74rZxeLwxbze5nVmu89+LuNuoIH6gEQm4WD8QbZFb+NB4QNMtU0Z2XQko5uOfpQplCvl7IrdxeqI1ZQrypnZeibTW03/zwUSGSUZHE04yqH7h4jNi0VNpEYXmy74OfvR075njeq2S2QlbI/ezu67u3E0cKRf4370duiNifaTXVqflVJ5KQFxAWy6vYn0knRcTVyZ3mo6/Zz6Vbp2Ij4/npMPT3Iq8dSjRZVNjJrg6+BLL4detDBrQVpJGlujtxIQF0CJrIROVp2Y0nIKlrqWnEk6w5mkM9zJuQOoFsOpidVIKEjATNuMsW5jGd1sNKba9cvFroHaUWelFCKRSA24C/QBkoErwDhBEO78o50BcBjQBN5+VQLj01t2ER1qTnOvTHwnjwXg0LR+mNxJoWv4rUftwvccw/CzdyletpqOQyuRQAMkhcUkdOrInu5iXN5azcR2PetkjNm//ErWihW4Xrr4aIHdP0kYPQZpfDzKkhLsVv+IQe/qSxTqjKMfwuVf4M0wMK+d3NcvN37hx4gfWe69nH5O/Sp8/mPgGH4tuE1g95U0afK4Fu/B0x/zSVIQ/2fYijeH7ahZh/JyWNMJNPRUddUvUIlBIpMwMmgkSkHJ3sF7a+1y97DwIbOCZ5Fdms1y7+V423tzLeMaM4/PxMvWix99f6x3dYUNNPA8UApKwlLD2B6znZDkENREavRy7EVP+55sur2JmNwYvGy8+Njz48eyhv9V4vLiOHz/MIcTDpNeko6Oug4+9j4MbDyQrjZdK9SmSmQSdsbu5Ldbv5Ffno+ntScZJRk8KHyAmkiNztad6d+4P74OvnWu0FIoLWRnzE623tlKXnkeHhYezGw9k2623WqcSEgtTuVM0hlOJ57mWsY1FIICcx1zcstyAejn1I8pLac8cib8O+kl6ZxLOseZpDNI5BJGNh1Jf6f+L03doYG6pS5LKToB9wRBuP/HgXcCQ4E7/2j3FfAtML+WY32pKMqkAGho//XDF5kZo1+ciFKpRPzHFExxegaGgIld1Tq6uob65BjoYptTShf75nU2xtKICDSdnKoMigGMBg0k4+tvQEMD3c51JGdWE3q8r9I2PrkIxm2v1a7TW03nTOIZFoctpr1l+8dqvAoLk9mef5ve6sYVgmKAIb5LCd8extqCm3SIWE8n94plJhW4sh7yHsDEfS80KAZYcW0FSUVJbOy38amsnx0NHdkycAtvn3qbOWfmMNt9NlvubMHOwI6vu3/dEBQ38J9BLBLjZeuFl60XSUVJ7IrZRcC9AI4/OI6FrgXfe6tMbeqT1u/LxNXElbnt5/L/7d15eNzVfe/x93dmNJJGixfkfcErNgRsbIwxWViNDQmFkJsEKPTmEgjpBUIWSJulkAAlKQk0QJNCSUNoS26BhD7ESQEbCEvCVvASMJvM4h1btuVFmhnNeu4fM5JlzYwWW5Zknc/refLE8zs/jY6Y52c+fHXO91w992pWbF3Bf3/w3zyx7gke++AxasO1nHH4GZw1+SyOqTuGX9f/mntX30tjSyMfG/cxrpx9JceMOKZtzevjax9n6dqlXPf8ddz44o18dOxHWTRpEadMOOWAQvL2+Hbuf/N+HnjnAaKpKCeNP4nLjrmMOSPn9Pi9xlaP5aIjL+KiIy9iV8uu3Ga2TX9kTNUY/nLmXzKmuvSyv9FVozl/5vmcP/P8/f5Z5NDXnWA8DtjQ7vVG4IT2N5jZHGCCc+73ZnZIBeNkPhiXR/b+qi1UN4JwBvY0fsjQutyC+ZatDQDUHd75zuiGukrGbW9h8rD933XbnnOO+KpVVBdZQtFezVlnsfUfbiEyd27p3sUHQ1UdfPyrfWdE7QAAIABJREFU8Ie/h7V/gkkf7/aXhgIhbv7EzXz+d5/nhhdv4M5T72z7l9kDz3yH5oDxpfnfLPn13z3nAV57aCHfWnk7D447kREjO+lFGd8Jz/4Ipp4G0/qomp73wuYXePCdB7n4yIs5fnQP2uJ1UFdZx72L7+XaZ6/ljhV3UFVWxR2n3qG+uuKtCTUTuPb4a7ni2CtY1bCK2SNn90t/1ENBwALMGz2PeaPn8Z353+HFD1/k0Q8e5dEPHuXhNQ+3bWg7ccyJXHHsFRw7cm8P/vZrXr8292us3r6ax9c+zrJ1y3h247OEAqFcSD58EadOPLXbfydtiW7hl6t/ycNrHiaZSbJ40mIuPeZSZg6f2Ss/89CKoZw77VzOnXZur7yf+KE7wbjYf3a3rb8wswDwE+D/dPlGZpcDlwNMnDgwdstmErkG2+HI3vYtFSNzVeHtm95tC8aZ7TtIBELUDu+8DdbOSZXMfHYHJBKwny1h2kutX09m504qj+38oJCykSMZdd3fUXFE9zYF9KoFV8Lyf4fffwP++k89OvRjypApXD3nan786o/53fu/45yp5xCLbuM/dqzgpGANR84o/RdapHokt37ih/zVn/6Wr//3X3HvXz5LuLym+M3P3Qotu+GMm3r60x2QPck9XP/89UweMpmvzv3qAb9fpCzCnafdyb2r72XOyDl9cqKRyEAXKYvw0XEDr63aQFUWLOOk8Sdx0viTiKfjPLfxOVY2rOSMw8/guFHHdfq1ZrmNaseMOIZr513L69tfZ9naZSxbt4znNj5H6MUQC8Ys4IzDz+DUCacWXZO8qXkTv3j9Fzzy7iM45zh76tlcevSlTBoy6SD9xCLd151gvBGY0O71eGBzu9c1wNHAM/lq32hgiZmd03GdsXPuHuAeyK0xPoB595pMMheMK6r2bkaoHp37cfdsXgez8xcbd9AUGdK2tKKU9ycZH38a4q+9TtUJ8w94frGVKwG6DMZA24l4fS4cgU/+GP7zfHjhTjipZ780uPioi/nDhj/ww5d/yPzR81n6zPXsChhfmtv1ZrIZ0z/F329ZyTXvP8hND5/HjRcsK2jLw861uXXQx14Eo4/u0dwO1C3/c0vu14Sn3t9rG4BCgRCXz+qdjZ0i4rfKUCWLJy0uus+jK2bGrBGzmDViFtfMu4bV21ezbN0ynlj3BN974XvcYDcwb9Q8Fh6+kNMnnk5LuoWfv/5zfv/e7zEzzpt2Hl885os9amUmcrB1Z2HiK8B0M5tsZmHgAmBJ66Bzbrdzrs45N8k5Nwl4CSgIxQNVJpkBoKLd8oMhY3LV7OYtG9uuBXfvJFbd9aEJK0ZGAYivWN7Fnd0TX7WKQHU15dM6b+3V72acCUeeA8/9ONetogcCFuCmj91ExmX4uz9+m/u2vsAJVHDs0d0L+os+8Xd8ufYjPJLayq+WXlF4w1M3ggXhtO92+j7Lty5nW2xbj+bemafWP8WS95Zw2TGXcXRd3wZyEZG+1FpJvmbeNTz2mcd46OyHuPToS9kW38YPXv4BC3+9kL945C947IPHOH/m+Tz6mUe57sTrFIplwOmyYuycS5vZVcBScu3a7nXOvWFmNwKvOueWdP4OA1smlQWgsmbvhqjDxk1lCxBv+LDtWkXTTmJ1nffqTWaSbA7soXnCYVQtX9Er84uv+jOVs2Zhwb7dLLZfzroF3ns61yf44od71Cd5Qs0Erp13LTe9dBMEjR/N+usefesrzrmfNf/vZG7d+iemLr+bE4/Lf/2m5bD64dwmwdrS68PfbnybSx6/hLHVY7nvzPsYXVV6k2V3NLY0cuOLN3Lk8CP58qwvH9B7iYgcStqvSb567tVt7dTSLs35M87v9DANkf7Wra3szrlHnXNHOOemOuduzl+7vlgods6dcqhUiwGybcF472aBIXXjSQcgvX1v9bA6upvssM57GDbEchv0UkdPJb5qFS6TOaC5ZZqjJOrru7WMYkCoHZs7Be+9p3JhtIc+N+0zLE7CKdly5s2+pEdfGwiG+MF5DzPZBbn2tZ+yfv2fcod5LLsOqkbAx0qv73XOcesrt1ITrmF3YjdfWvYltse393j+7d/vphdvoinZxM0fv1lHdYqI16YOncqXZ3+ZK4+9UqFYBjzvezxlc0uMiVTv3bQVCATYUxPE7dgFQLIlQW0iig3v/IFuPds8NPsYss3NJNasOaC5tbz+GmSzVM45RIIxwPwvwZhj4fFvQ3xXj77U1izj1k3rufP47xSuE+6GqurR3Lnwbgy4+skraF75H7DueTjlW1BqUx7w3MbneHnLy1x57JX888J/ZmtsK5c/cTm7E7tLfk1nHv3gUZ5c/yRXzblKJ9GJiIgcQrwPxi4Nlk0RKtu3qhevLSe4cw8A2zfkjo0Mj+w8GLceLzlkfq6bXWz5ga0zjq9aBUDl7Nld3DmABIK5U+Vi23Nre3vi5bugdjx25Dn7/e0nTDiR22ZfzdpAlm+/dAPZuukw9wsl709lU9z66q1Mqp3E52Z8jjkj53DnaXeybnfuQI3mZHOPvv/Olp3c8j+3MGvELL5wVOnvKyIiIgOP98E4m4FAa9m4neTQCOW74wDs2JhbaxwZ3Xlv4taNW6OmHENo1CjiK1Ye0NxiK1cSnjaVYO0h1qd27LEw/8vw6r2wsZurara+CR88B/Mvg2B3mqWUdsLcy/mb0afwTFWEH0+fjwuUfr9fv/Nr1u5ZyzXzrmk7anTBmAXcdsptvN34Nlc+dSXxdLzb3/u2V2+jKdnE90/8PsE+PkREREREDoz3wdhlDHOFwTg7rJbIntzhH3s2bQGgZmznG7IaYg2EA2GGlA+hcu4cYiv2fwOey2aJ//m1Q2d9cUenfRdqxsDvvgqZVNf3v3w3hCo7re72xIWL/4mLj/g892/5I/e9cV/Re/Yk93DXn+/ihNEncPL4k/cZO2XCKfzwEz9k1bZVfO3pr5HMJLv8ni9/+DK/fe+3XHL0JVpCISIicghSMM4EMFcY3AJ1w6mJZkmnkkS35DbVDe/kOGjIBeORkZGYGZG5x5H+8ENSmzd3+jWlJNeuI7t7N5FDNRiX18AnfwRbV8ML/9T5vbFGeO1BmPV5iHS+wbG7zIxvLvguZ046k39c/o/87r3fFdzz89d+zu7Ebq49/tqix8eeOflMvn/i93lh8wt845lvkMgkSn6/lnQLN754IxNrJqrHsIiIyCHK+2CMCxStGJfVjSTgoHHrWpINuSUSIyZ23q6tNRgDRI6bC0BsP5dTJN55G4CKj3RyzPFAN/NsOOpcePoHsHlV6fuW3wfpFjihZy3auhKwADd//GZOGH0C1z9/Pc9ver5tbMOeDfzqrV/x6Wmf7vT40fOmn8d1C67j2Y3P8pWnvlJyWcU9r93D+qb1XHfidb12kIeIiIj0Le+DscsWD8aV+WOhGze9T2bHdqJlFURqqgrua29bfFtbMC4/4ggCVVX7fdBHS309BIOEpxzCR/6awdm3Q1Ud/NeXIBkrvCeTglf+FSafDKOO6vUphINhbj/1dqYOncrXn/k6b2x/A4CfrPgJoUCIq+Zc1eV7fH7G57nxozfy0ocvccWTVxBNRfcZr99Zzy9X/5Jzpp7DgjELev1nEBERkb6hYOyCGIXBuHpM/ljoD9dhjY00RTo/9c45R0OsgRGREQBYKETl7NnE9vOgj0T9GsKHH06gvHy/vn7AiAyHT98F2+vhiesLx9/+PezZBAv+70GbQnW4mrsW3sXwiuFc8dQVPPLuIzyx7gm+ePQX2/5DpivnTT+Pf/jEP7CyYSWXP3E5e5K5jiVZl+WGF2+gJlzDtfN6dhS2iIiIDCzeB2NcECg8iGPYmMkARLdupmzPTlpqhnb6Ns2pZuLpOKMio9quVR43l0R9PZmmph5PK7FmDeVHHNHjrxuQpp4KC66EV34O9cv2HXvpbhg2CaYvOqhTGBEZwd0L78Y5x3XPX8fIyEi+8JGebfT75JRPctvJt/Hmjje5bOll7GrZxUPvPMRr217jm8d/k2EVww7S7EVERKQveB+MHSHMCivGh42bCkCiYQuVTbtIDuk89LSeejeickTbtchxx4Fzbf2Iuysbi5HasIHy6dN69HUD2unXw8iPwG+vgOb8iYKbV8KGl3Kt3fqgtdmkIZP46ek/ZWRkJH97/N9SGars8Xucfvjp3HHqHby36z0uWXoJt6+4nQVjFnD2lLMPwoxFRESkLykYE8KssGJcPaSOeBgy27dTE9sNww7r9H1aD/do/6v5ylmzIBjs8UEfiffeA+cGT8UYoKwC/tfPoWUPLPlK7rjml+6GcDXMuajPpjFrxCye/OyTLJq0/xXqk8afxM8W/oxNzZtIZ9Ncv+D6ol0tRERE5NByYCcpDAYWAssWHWquCRHYsoNIOkGwrvNg3Ha4R7ulFIFIhIojjyTew3XGifp6ACqmD7JeuKM+Agu/D0u/Dc/+CFY/DPO+CBWdr9/ubb0RYheMWcD9n7yfaCrKhNoJvTArERER6W/eB2NHCAsUD8YttRUMXb8LgPDIzjdptS2liIzY53rkuLnsfPAhXDKJhcPdmlOifg1WUUHZhEEYuE74a1izFJ75Qe71/EO35+8RwwZRRV9ERES0lCJrpYNxalg1Q3fmDnWoGtN1MK4N1xb0sK2cexyupYWWt97q9pwSa+opnzoVCw7CI4UDAfj03VA5HGZ8CuoG0TpqEREROaR5H4xdoAwLuuJjw/f+in/ImFFF72nV/nCP9iJz5wD0qG1bS/0g6khRTO0Y+Mpy+Owv+nsmIiIiIm0UjC1UMhgHh+89nriui1Pv2h/u0V5oxAjKJk4kvrJ7wTjd2Ehm+/bBHYwh19+4rOddIUREREQOFq+DcSaTIRsMl+wUFh6ZqxJngcPGdV4x3hrbuk+rtvYic+cSW74C54oH8PYS9WsAKB9sG+9EREREBjivg3Eiljva10psQYyMGgtAU0WEsvLSG+cy2Qw74jtKnqJWOXcOmcZGkmvXdj2nNflgfISCsYiIiEhf8joYx/In0gXKiv9jqB0zEYCmqs5/5d/Y0kjGZUoG48hxxwEQX7Gyyzkl6usJDhlCaETx6rOIiIiIHBxeB+N4UzMAwRLBeNjYKQBEayqKjrdqiOdatZUKxuEpUwgOHUpsRdcHfSTq6yk/4ggdGCEiIiLSx7wOxi3N+WAcLv6PoW5M7ljoaG1Zp+/TEO08GJsZlXPmdHnQh3OOxJpB3pFCREREZIDyOxjHYgAEwsV334UrI6yeEOKDwztfStF6uEepYAwQOf54kmvXkty4seQ9qU2bycZi2ngnIiIi0g/8DsbRXDAOlRevCGeyjus/PZ0n52Q6fZ+GeAMBC3BYReljo2vOWAhA07InSt6TWJM7CloVYxEREZG+53UwTsZyp9qVlRdvSxFPZcgmxrAztZ5UNlXyfRpiDdRV1BEs1fcNCE+YQMVRR9G0dGnJe/a2atNpcCIiIiJ9zetgnIq3ABCqLC86HkukybSMJUuaD3Z/UPJ9tsWKH+7RUc2iRcT//GdSW7YUHU+sWUNo7BiCNTXdmL2IiIiI9CbPg3GuYhyuKB6Mo8kM2ZbciXfvNL5T8n22xrYyItJ1e7WaxYuA0sspEvX1VEzXMgoRERGR/uB1ME4ncssjwpESwTiRJpusI2ThToNxqeOgOyqfPJny6dPZs6xwOYVLpUh88IEO9hARERHpJ14H41Q+GJeXOMAjlswAQcZGJvP2zreL3tOSbmF3Yne3gjFAzeLFxJevIL1t2z7Xk2vXQiqljXciIiIi/cTrYJxJ5LpNhCORouPRZBqASbXTeafxHZxzBfdsi+cCbneDce3iReAcTU8+uc/1lvp8Rwq1ahMRERHpF34H42QuGFdWVxUdj+WD8/ShR7ArsYutsa0F97T1MK7sXjAOT5tGePJk9ixdts/1xJo1EAwSnjKl2/MXERERkd7jdTDOJrMAVFZXFx1vrRjPHD4TKL4Bb1usZxVjM6Nm8SJir7xCurGx7Xqifg3hSZMIhMPd/wFEREREpNd4HYwz6VwwrqgpHoxjiVww/shhMwB4Z2dhMG6tIo+s6l4wBqhdvBgyGZqeeqrtWu4oaC2jEBEREekvXgfjbCq3ZjhSVVt0PJbKLaUYUT2ECTUTeLuxcANeQ6yBimAFNWXd7z1cPnMmZRMm0JRfTpGNRklt2ECFNt6JiIiI9Buvg7FLg2UzJfsYxxIZAgbloQAzh88suZRiZGQkZtbt72tm1C5eRPSll8js3k3i3XcBbbwTERER6U9eB+NsBsyVPuo5mkxTFQ5hZswYNoP1TeuJpqL73NPdwz06qlm8GNJpmv7wdG7jHahVm4iIiEg/8joYu4wRyJYOxrFEhkh5ENi7Aa9+Z/0+93T3cI+OKo4+mtDYMTQtXUpLfT1WWUnZ+PE9fh8RERER6R1+B+NsAHPpkuOtFWOAGcPzG/DaLadwztEQa+h2q7b2zIzaMxYRff554itXUT5tGhbw+uMQERER6VdeJ7GugnEsubdiPCoyiiHlQ/bZgLcnuYdEJrFfFWOAmsWLcKkULa+/ro4UIiIiIv3M62BMVxXjRJpIvmJsZswctu8GvLbDPfYzGFceeyyhEbn1ydp4JyIiItK/vA7GzgUxOq8YV4WDba9nDJ/Bml1rSGdzX9PTwz06skCAmkWLANSqTURERKSfeR2MIQidBONoMk2kPNT2eubwmSQyCdbtWQe0O9xjP4MxwLALL6Dq5JOomDV7v99DRERERA6c18HYuSBmmZLjscS+FeMjhuWquq3LKbbFcxXj/WnX1qp82jQm/su/EKyu2u/3EBEREZED53cwJgSdBONocu8aY4ApQ6ZQFijj7Z25DXgNsQaGlg+lPFj8gBAREREROXR4HYyxUMmKsXMut8a4fG/FuCxYxrSh09oqxvt7uIeIiIiIDDxeB2NHCAtki44l0lkyWbdPxRhyG/Debnwb51zbcdAiIiIicujzOxhbWclgHEvmKsnt1xgDzBg2g8aWRrbHt+/34R4iIiIiMvB4HYyzgRAWcEXHoolct4piFWOAN3e8yY6WHaoYi4iIiAwSXgdjZ2VYsHgwbq0YR8o7VIzzwfj5zc+TdVkFYxEREZFBwttgnMlkchXjUPHxWDJXMa7qUDGuDdcyrnocf9z4R+DAehiLiIiIyMDhbTBOJeJgAQIlg3G+YtxhjTHk1hlvbN4IHFgPYxEREREZOLwNxrGmJgACZVZ0vHWNcVV5YXJuXU4BMCoy6iDMTkRERET6mr/BeE8uGAfLiv8j6LRinA/GQQsyvGL4QZqhiIiIiPQlb4NxS3MUgEBZYfCF3Kl3ULxiPHP4TADqKusImLf/CEVEREQGFW9TXUs0F4yD5cWDcSxRumI8tmosNWU1WkYhIiIiMoiU2Ho2+CWiMSBEKFz8H0FrxbhjH2MAM+NTUz6lZRQiIiIig4i/wTjeAlRTVhEuOh5LZqgoCxAMFN+c990F3z2IsxMRERGRvubtUopUrAWAYEVZ0fFoIl3Qw1hEREREBi9vg3EyngQgXFledDyWzBSceiciIiIig5e3wTidSAFQViIYq2IsIiIi4hd/g3FLLhiXV1YWHY8lM0U7UoiIiIjI4ORtMM7ku06URyqKjkeT6aI9jEVERERkcPI3GOf7FFdUVxUdjyVUMRYRERHxib/BOJUFoLK6uuh4NKk1xiIiIiI+UTCuqSk6rq4UIiIiIn7xNhhn0w6ASE1t0fFoIl301DsRERERGZy8DcYuDbhM0a4Umawjkc5qjbGIiIiIR7wNxtkMBLLpomOxfMcKrTEWERER8Ye3wdiljUA2VXQslsx1rNAaYxERERF/+BuMs4a54sE4mlDFWERERMQ3HgfjAOZKLaXIV4y1xlhERETEG90KxmZ2ppm9Y2bvmtm3iox/w8zeNLPXzOwpMzu896fay7LBksG4rWKsk+9EREREvNFlMDazIPAz4CzgKOBCMzuqw20rgXnOuVnAb4Af9fZEe5tzAQxVjEVEREQkpzsV4/nAu865951zSeAB4Nz2NzjnnnbOxfIvXwLG9+40D4YQlAjG0aQqxiIiIiK+6U4wHgdsaPd6Y/5aKZcCjx3IpPqCc0HMMkXHYglVjEVERER8052SqBW55oreaHYxMA84ucT45cDlABMnTuzmFA+WIGaJoiNR9TEWERER8U53KsYbgQntXo8HNne8ycwWAt8FznHOFU2czrl7nHPznHPzRowYsT/z7TWOEJSqGKuPsYiIiIh3uhOMXwGmm9lkMwsDFwBL2t9gZnOAfyEXiht6f5q9z1kIs2zRsWgiTShghIPedrMTERER8U6Xyc85lwauApYCbwEPOefeMLMbzeyc/G0/BqqBX5vZKjNbUuLtBgxnISxQPBjHkhki4SBmxVaRiIiIiMhg1K1FtM65R4FHO1y7vt2fF/byvA46Z2VYsOhSaaKJtDpSiIiIiHjG27UC2UDpYNxaMRYRERERf3gcjENYiewbTapiLCIiIuIbL4NxIh4HCxIokX1VMRYRERHxj5fBONa0B4BAqPjmulgyrR7GIiIiIp7xMhjHm5oACISL//ixRIZKVYxFREREvOJnMG5uBiBYVjz8RlUxFhEREfGOl8G4pTkKdF4x1ql3IiIiIn7xMhgnonEAQuVlBWPOOVWMRURERDzkZzCOtwbjwvCbSGfJOlQxFhEREfGMl8E4FUsAxSvG0UQaQBVjEREREc94GYyTLblgHK4MF4zFkhkA9TEWERER8YyXwTjdkgSgLFJRMBZN5ivGOvlORERExCteBuNUSy78llcWCcYJVYxFREREfORlME4nUgCUV0UKxmKqGIuIiIh4yctgnE1mAaioqioYU8VYRERExE9eBuNMKhd+K6oLg3FbxVhdKURERES84mUwbq0YR2prCsairV0p1MdYRERExCt+BuO0AyBSUxiMY+pjLCIiIuIlT4Mx4LKUlVcWjLX2Ma4sU8VYRERExCdeBmOXgUA2RTBYGH5jyTSRcJBAwPphZiIiIiLSXzwNxoZl00XHoskMES2jEBEREfGOn8E4awRcquhYLJGmShvvRERERLzjaTAOYK50xVjri0VERET8o2DcQSyZ1ql3IiIiIh7yMxi7IFB8KUU0kdGpdyIiIiIe8jIY44IYmaJDsWRaPYxFREREPORlMHadBONoIqNT70REREQ85GUwhhBYJ2uMVTEWERER8Y6XwdgRwixbdCyaVMVYRERExEd+BmMLQaBwKUUqkyWZzqpiLCIiIuIhb4OxBQorxrFkLiyrK4WIiIiIfzwOxq7geiyZW3esPsYiIiIi/vEyGGcDZVioMBhHE6oYi4iIiPjKy2DsrIxAkezbVjHWGmMRERER73gXjBPxOC4QxIpk37aKsbpSiIiIiHjHu2Aca24CIBCygrF4ShVjEREREV95F4xbmpoBCIYKf/TWinGVKsYiIiIi3vEuGMdbK8bhwh+9dY1xRBVjEREREe94F4xbmmMABIt0nmirGCsYi4iIiHjHu2CciOaDcZHlEq0V40q1axMRERHxjn/BOB4HoKy8rGAsmsxQFjTCRdYfi4iIiMjg5l0CTMYTAISKBONYIq31xSIiIiKe8jYYl1WWF4xFkxmqtIxCRERExEveBeNMSwqAssqKgrFYMk2kXBVjERERER95F4xTLUkAwpEiFeOEKsYiIiIivvIuGKfznScqqiIFY7Gk1hiLiIiI+Mq7YJzJ9youFoyjiYxOvRMRERHxlHfBOJvKAlBRXV0wpoqxiIiIiL+8C8aZfDCuLBKMo0lVjEVERER85V0wbq0YV9UMKRhTH2MRERERf3kXjF0acFnCkcp9rztHLKWuFCIiIiK+8i4YZzMQyKYJBvcNwC2pLM6hPsYiIiIinvIuGLuMYS5VcD2ab+OmirGIiIiIn7wMxoFsuuB6LN/GTWuMRURERPzkXzDOBjqvGKsrhYiIiIiX/AzGFKkY54OxKsYiIiIifvIuGOMC+dYU+4rml1KoYiwiIiLiJ++CsXNBVYxFREREpICHwTiEWabgelvFWMFYRERExEveBWMIAoXBuLViXKl2bSIiIiJe8i4YO0pUjJNaYywiIiLiM/+CsYUgkC24HkukMYOKkIKxiIiIiI+8DMZmhcE4mswQKQsSCFg/zEpERERE+puHwbgMCxapGCfTRMq18U5ERETEVx4G4xAWdAXXo4kMVdp4JyIiIuIt74JxNlBGoEj+jSXT6mEsIiIi4jGvgnEykcAFQliR/BtNZNSRQkRERMRjXgXjeHMTAIEiwVgVYxERERG/+RWMm/LBuKzwx44lVTEWERER8Zlfwbi5GYBgiWCsirGIiIiIv7oVjM3sTDN7x8zeNbNvFRkvN7MH8+Mvm9mk3p5ob4g3RwEIFuk+EU2m1ZVCRERExGNdBmMzCwI/A84CjgIuNLOjOtx2KbDTOTcN+AlwS29PtDckYzEAgkUqw7FERn2MRURERDzWnYrxfOBd59z7zrkk8ABwbod7zgX+Lf/n3wCnm9mAO0IuEY0DEKrYNwAn01mSmawqxiIiIiIe606JdBywod3rjcAJpe5xzqXNbDdwGLC9NybZWz7c1gRU8uKGPTxw7/+0Xc9kcyfhaY2xiIiIiL+6kwSLVX47Hh3XnXsws8uBywEmTpzYjW/duwKVYcLxdew+rJw98dQ+Y8dPGsaCKYf1+ZxEREREZGDoTjDeCExo93o8sLnEPRvNLAQMARo7vpFz7h7gHoB58+YVnst8kJ1z4Wfgwr7+riIiIiJyKOjOGuNXgOlmNtnMwsAFwJIO9ywBvpD/82eBPzjn+jz4ioiIiIjsry4rxvk1w1cBS4EgcK9z7g0zuxF41Tm3BPgF8B9m9i65SvEFB3PSIiIiIiK9rVu7zZxzjwKPdrh2fbs/twCf692piYiIiIj0Ha9OvhMRERERKUXBWERERESksOo2AAAE00lEQVQEBWMREREREUDBWEREREQEUDAWEREREQEUjEVEREREAAVjERERERFAwVhEREREBFAwFhEREREBFIxFRERERAAFYxERERERQMFYRERERARQMBYRERERARSMRUREREQABWMREREREQDMOdc/39hsG7CuX7451AHb++l7S9/R5+wPfdb+0GftD33W/uiLz/pw59yIrm7qt2Dcn8zsVefcvP6ehxxc+pz9oc/aH/qs/aHP2h8D6bPWUgoRERERERSMRUREREQAf4PxPf09AekT+pz9oc/aH/qs/aHP2h8D5rP2co2xiIiIiEhHvlaMRURERET24VUwNrMzzewdM3vXzL7V3/OR3mNmE8zsaTN7y8zeMLOv5q8PN7MnzGxN/v+H9fdcpXeYWdDMVprZ7/OvJ5vZy/nP+kEzC/f3HOXAmdlQM/uNmb2df75P1HM9OJnZ1/N/f682s/80swo914ODmd1rZg1mtrrdtaLPseXcmc9qr5nZ3L6cqzfB2MyCwM+As4CjgAvN7Kj+nZX0ojRwjXPuSGABcGX+8/0W8JRzbjrwVP61DA5fBd5q9/oW4Cf5z3oncGm/zEp62x3A4865mcBscp+5nutBxszGAVcD85xzRwNB4AL0XA8W9wFndrhW6jk+C5ie/9/lwF19NEfAo2AMzAfedc6975xLAg8A5/bznKSXOOc+dM6tyP+5idy/PMeR+4z/LX/bvwGf7p8ZSm8ys/HAp4B/zb824DTgN/lb9FkPAmZWC5wE/ALAOZd0zu1Cz/VgFQIqzSwERIAP0XM9KDjnngMaO1wu9RyfC/y7y3kJGGpmY/pmpn4F43HAhnavN+avySBjZpOAOcDLwCjn3IeQC8/AyP6bmfSi24G/AbL514cBu5xz6fxrPd+DwxRgG/DL/LKZfzWzKvRcDzrOuU3ArcB6coF4N7AcPdeDWannuF/zmk/B2IpcU0uOQcbMqoGHga855/b093yk95nZ2UCDc255+8tFbtXzfegLAXOBu5xzc4AoWjYxKOXXl54LTAbGAlXkfqXekZ7rwa9f/z73KRhvBCa0ez0e2NxPc5GDwMzKyIXiXznn/it/eWvrr2Dy/9/QX/OTXvMx4BwzW0tuSdRp5CrIQ/O/ggU934PFRmCjc+7l/OvfkAvKeq4Hn4XAB865bc65FPBfwEfRcz2YlXqO+zWv+RSMXwGm53e4hskt6l/Sz3OSXpJfY/oL4C3n3D+2G1oCfCH/5y8Av+3ruUnvcs592zk33jk3idxz/Afn3EXA08Bn87fpsx4EnHNbgA1mNiN/6XTgTfRcD0brgQVmFsn/fd76Weu5HrxKPcdLgP+d706xANjduuSiL3h1wIeZfZJcZSkI3Oucu7mfpyS9xMw+DvwReJ29606/Q26d8UPARHJ/8X7OOddxA4AcoszsFOBa59zZZjaFXAV5OLASuNg5l+jP+cmBM7NjyW2yDAPvA5eQK+rouR5kzOwG4HxyXYZWApeRW1uq5/oQZ2b/CZwC1AFbge8Bj1DkOc7/h9FPyXWxiAGXOOde7bO5+hSMRURERERK8WkphYiIiIhISQrGIiIiIiIoGIuIiIiIAArGIiIiIiKAgrGIiIiICKBgLCIiIiICKBiLiIiIiAAKxiIiIiIiAPx/3nPua3Bv+HMAAAAASUVORK5CYII=
"
>
</div>

</div>

<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Largest probability after 100 flips: 0.5
Smallest probability after 100 flips: 0.42
Median probability after 100 flips: 0.47
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
