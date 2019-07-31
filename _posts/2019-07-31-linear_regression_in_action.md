---
layout: post
comments: true
title: "Linear Regression in Action"
date: 2019-05-03
---


<!DOCTYPE html>
<html>
<head><meta charset="utf-8" />
<title>Linear_regression</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
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

<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#data source</span>
<span class="c1">#Objective</span>
<span class="c1">#libraries</span>
<span class="c1">#directory</span>
<span class="c1">#load data</span>
<span class="c1">#describe data</span>
<span class="c1">#exploratory analysis</span>
<span class="c1">#split into train and test</span>
<span class="c1">#model</span>
<span class="c1">#assumptions</span>
<span class="c1">#improve model</span>
<span class="c1">#Hide Directory while publishing</span>
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
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Source of Dataset - https://archive.ics.uci.edu/ml/datasets/Airfoil+Self-Noise#</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Objective</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Load Modules</span>
<span class="kn">import</span> <span class="nn">os</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="o">%</span><span class="k">matplotlib</span> inline
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Set Directory</span>
<span class="n">os</span><span class="o">.</span><span class="n">chdir</span><span class="p">(</span><span class="s2">&quot;C:/Users/abhishek2.s/Documents/Data Science/My Blog/Linear Regression&quot;</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Load data</span>
<span class="n">data</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;Data.csv&quot;</span><span class="p">)</span>
<span class="n">data</span><span class="o">.</span><span class="n">head</span><span class="p">()</span> <span class="c1">#view snapshot of data</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[6]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Frequency</th>
      <th>Angle_of_Attack</th>
      <th>Chord_Length</th>
      <th>Free_Stream_Velocity</th>
      <th>Suction_Side_Displacement</th>
      <th>Scaled_Sound_Pressure_Level</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>800</td>
      <td>0.0</td>
      <td>0.3048</td>
      <td>71.3</td>
      <td>0.002663</td>
      <td>126.201</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1000</td>
      <td>0.0</td>
      <td>0.3048</td>
      <td>71.3</td>
      <td>0.002663</td>
      <td>125.201</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1250</td>
      <td>0.0</td>
      <td>0.3048</td>
      <td>71.3</td>
      <td>0.002663</td>
      <td>125.951</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1600</td>
      <td>0.0</td>
      <td>0.3048</td>
      <td>71.3</td>
      <td>0.002663</td>
      <td>127.591</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2000</td>
      <td>0.0</td>
      <td>0.3048</td>
      <td>71.3</td>
      <td>0.002663</td>
      <td>127.461</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[7]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Basic information about data</span>
<span class="n">data</span><span class="o">.</span><span class="n">info</span><span class="p">()</span>
<span class="c1"># no missing values present in the data</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>&lt;class &#39;pandas.core.frame.DataFrame&#39;&gt;
RangeIndex: 1503 entries, 0 to 1502
Data columns (total 6 columns):
Frequency                      1503 non-null int64
Angle_of_Attack                1503 non-null float64
Chord_Length                   1503 non-null float64
Free_Stream_Velocity           1503 non-null float64
Suction_Side_Displacement      1503 non-null float64
Scaled_Sound_Pressure_Level    1503 non-null float64
dtypes: float64(5), int64(1)
memory usage: 70.5 KB
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Exploratory Analysis</span>
<span class="c1">##Univariate Analysis</span>

<span class="c1">#get data summary</span>
<span class="n">data</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[8]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Frequency</th>
      <th>Angle_of_Attack</th>
      <th>Chord_Length</th>
      <th>Free_Stream_Velocity</th>
      <th>Suction_Side_Displacement</th>
      <th>Scaled_Sound_Pressure_Level</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1503.000000</td>
      <td>1503.000000</td>
      <td>1503.000000</td>
      <td>1503.000000</td>
      <td>1503.000000</td>
      <td>1503.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2886.380572</td>
      <td>6.782302</td>
      <td>0.136548</td>
      <td>50.860745</td>
      <td>0.011140</td>
      <td>124.835943</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3152.573137</td>
      <td>5.918128</td>
      <td>0.093541</td>
      <td>15.572784</td>
      <td>0.013150</td>
      <td>6.898657</td>
    </tr>
    <tr>
      <th>min</th>
      <td>200.000000</td>
      <td>0.000000</td>
      <td>0.025400</td>
      <td>31.700000</td>
      <td>0.000401</td>
      <td>103.380000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>800.000000</td>
      <td>2.000000</td>
      <td>0.050800</td>
      <td>39.600000</td>
      <td>0.002535</td>
      <td>120.191000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1600.000000</td>
      <td>5.400000</td>
      <td>0.101600</td>
      <td>39.600000</td>
      <td>0.004957</td>
      <td>125.721000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>4000.000000</td>
      <td>9.900000</td>
      <td>0.228600</td>
      <td>71.300000</td>
      <td>0.015576</td>
      <td>129.995500</td>
    </tr>
    <tr>
      <th>max</th>
      <td>20000.000000</td>
      <td>22.200000</td>
      <td>0.304800</td>
      <td>71.300000</td>
      <td>0.058411</td>
      <td>140.987000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[9]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Histogram</span>
<span class="n">data</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">16</span><span class="p">,</span> <span class="mi">20</span><span class="p">),</span> <span class="n">bins</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span> <span class="n">xlabelsize</span><span class="o">=</span><span class="mi">8</span><span class="p">,</span> <span class="n">ylabelsize</span><span class="o">=</span><span class="mi">8</span><span class="p">);</span>

<span class="c1">#most of the variables seem right skewed but scaled_sound_pressure_level has left skewed normal distribution</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Bivariate Analysis</span>
<span class="n">corr_matrix</span> <span class="o">=</span> <span class="n">data</span><span class="o">.</span><span class="n">corr</span><span class="p">()</span>
<span class="n">corr_matrix</span>

<span class="c1">#As suspected from the distribution, we have negative correlation for most of the variables with the dependent variable</span>
<span class="c1"># also, there is good correlation between Angle_of_Attack and Suction_Side_Displacement</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[10]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Frequency</th>
      <th>Angle_of_Attack</th>
      <th>Chord_Length</th>
      <th>Free_Stream_Velocity</th>
      <th>Suction_Side_Displacement</th>
      <th>Scaled_Sound_Pressure_Level</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Frequency</th>
      <td>1.000000</td>
      <td>-0.272765</td>
      <td>-0.003661</td>
      <td>0.133664</td>
      <td>-0.230107</td>
      <td>-0.390711</td>
    </tr>
    <tr>
      <th>Angle_of_Attack</th>
      <td>-0.272765</td>
      <td>1.000000</td>
      <td>-0.504868</td>
      <td>0.058760</td>
      <td>0.753394</td>
      <td>-0.156108</td>
    </tr>
    <tr>
      <th>Chord_Length</th>
      <td>-0.003661</td>
      <td>-0.504868</td>
      <td>1.000000</td>
      <td>0.003787</td>
      <td>-0.220842</td>
      <td>-0.236162</td>
    </tr>
    <tr>
      <th>Free_Stream_Velocity</th>
      <td>0.133664</td>
      <td>0.058760</td>
      <td>0.003787</td>
      <td>1.000000</td>
      <td>-0.003974</td>
      <td>0.125103</td>
    </tr>
    <tr>
      <th>Suction_Side_Displacement</th>
      <td>-0.230107</td>
      <td>0.753394</td>
      <td>-0.220842</td>
      <td>-0.003974</td>
      <td>1.000000</td>
      <td>-0.312670</td>
    </tr>
    <tr>
      <th>Scaled_Sound_Pressure_Level</th>
      <td>-0.390711</td>
      <td>-0.156108</td>
      <td>-0.236162</td>
      <td>0.125103</td>
      <td>-0.312670</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[16]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Scatter Plots</span>

<span class="c1"># for i in range(5):</span>
<span class="c1">#     x = data.iloc[:,i]</span>
<span class="c1">#     y = data[&quot;Scaled_Sound_Pressure_Level&quot;]</span>
<span class="c1">#     plt.scatter(x, y)</span>
<span class="c1">#     plt.title(&#39;Scatter plot pythonspot.com&#39;)</span>
<span class="c1">#     plt.xlabel(&#39;x&#39;)</span>
<span class="c1">#     plt.ylabel(&#39;y&#39;)</span>
<span class="c1">#     plt.show()</span>
    

<span class="n">fig</span><span class="p">,</span> <span class="n">axes</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">subplots</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">12</span><span class="p">,</span><span class="mi">3</span><span class="p">))</span>

<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">4</span><span class="p">):</span>
    <span class="n">axes</span><span class="p">[</span><span class="n">i</span><span class="p">]</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">data</span><span class="o">.</span><span class="n">iloc</span><span class="p">[:,</span><span class="n">i</span><span class="p">],</span> <span class="n">data</span><span class="p">[</span><span class="s2">&quot;Scaled_Sound_Pressure_Level&quot;</span><span class="p">])</span>
    <span class="n">axes</span><span class="p">[</span><span class="n">i</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="n">data</span><span class="o">.</span><span class="n">columns</span><span class="p">[</span><span class="n">i</span><span class="p">])</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[17]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#split data into dependent and independent variables</span>
<span class="n">X</span> <span class="o">=</span> <span class="n">data</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;Scaled_Sound_Pressure_Level&#39;</span><span class="p">],</span><span class="n">axis</span><span class="o">=</span>  <span class="mi">1</span><span class="p">)</span>
<span class="n">Y</span> <span class="o">=</span> <span class="n">data</span><span class="o">.</span><span class="n">loc</span><span class="p">[:,</span> <span class="s2">&quot;Scaled_Sound_Pressure_Level&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
<span class="nb">print</span><span class="p">(</span><span class="n">X</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">Y</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>      Frequency  Angle_of_Attack  Chord_Length  Free_Stream_Velocity  \
0           800              0.0        0.3048                  71.3   
1          1000              0.0        0.3048                  71.3   
2          1250              0.0        0.3048                  71.3   
3          1600              0.0        0.3048                  71.3   
4          2000              0.0        0.3048                  71.3   
5          2500              0.0        0.3048                  71.3   
6          3150              0.0        0.3048                  71.3   
7          4000              0.0        0.3048                  71.3   
8          5000              0.0        0.3048                  71.3   
9          6300              0.0        0.3048                  71.3   
10         8000              0.0        0.3048                  71.3   
11        10000              0.0        0.3048                  71.3   
12        12500              0.0        0.3048                  71.3   
13        16000              0.0        0.3048                  71.3   
14          500              0.0        0.3048                  55.5   
15          630              0.0        0.3048                  55.5   
16          800              0.0        0.3048                  55.5   
17         1000              0.0        0.3048                  55.5   
18         1250              0.0        0.3048                  55.5   
19         1600              0.0        0.3048                  55.5   
20         2000              0.0        0.3048                  55.5   
21         2500              0.0        0.3048                  55.5   
22         3150              0.0        0.3048                  55.5   
23         4000              0.0        0.3048                  55.5   
24         5000              0.0        0.3048                  55.5   
25         6300              0.0        0.3048                  55.5   
26         8000              0.0        0.3048                  55.5   
27        10000              0.0        0.3048                  55.5   
28        12500              0.0        0.3048                  55.5   
29          200              0.0        0.3048                  39.6   
...         ...              ...           ...                   ...   
1473        200             15.6        0.1016                  71.3   
1474        250             15.6        0.1016                  71.3   
1475        315             15.6        0.1016                  71.3   
1476        400             15.6        0.1016                  71.3   
1477        500             15.6        0.1016                  71.3   
1478        630             15.6        0.1016                  71.3   
1479        800             15.6        0.1016                  71.3   
1480       1000             15.6        0.1016                  71.3   
1481       1250             15.6        0.1016                  71.3   
1482       1600             15.6        0.1016                  71.3   
1483       2000             15.6        0.1016                  71.3   
1484       2500             15.6        0.1016                  71.3   
1485       3150             15.6        0.1016                  71.3   
1486       4000             15.6        0.1016                  71.3   
1487        200             15.6        0.1016                  39.6   
1488        250             15.6        0.1016                  39.6   
1489        315             15.6        0.1016                  39.6   
1490        400             15.6        0.1016                  39.6   
1491        500             15.6        0.1016                  39.6   
1492        630             15.6        0.1016                  39.6   
1493        800             15.6        0.1016                  39.6   
1494       1000             15.6        0.1016                  39.6   
1495       1250             15.6        0.1016                  39.6   
1496       1600             15.6        0.1016                  39.6   
1497       2000             15.6        0.1016                  39.6   
1498       2500             15.6        0.1016                  39.6   
1499       3150             15.6        0.1016                  39.6   
1500       4000             15.6        0.1016                  39.6   
1501       5000             15.6        0.1016                  39.6   
1502       6300             15.6        0.1016                  39.6   

      Suction_Side_Displacement  
0                      0.002663  
1                      0.002663  
2                      0.002663  
3                      0.002663  
4                      0.002663  
5                      0.002663  
6                      0.002663  
7                      0.002663  
8                      0.002663  
9                      0.002663  
10                     0.002663  
11                     0.002663  
12                     0.002663  
13                     0.002663  
14                     0.002831  
15                     0.002831  
16                     0.002831  
17                     0.002831  
18                     0.002831  
19                     0.002831  
20                     0.002831  
21                     0.002831  
22                     0.002831  
23                     0.002831  
24                     0.002831  
25                     0.002831  
26                     0.002831  
27                     0.002831  
28                     0.002831  
29                     0.003101  
...                         ...  
1473                   0.043726  
1474                   0.043726  
1475                   0.043726  
1476                   0.043726  
1477                   0.043726  
1478                   0.043726  
1479                   0.043726  
1480                   0.043726  
1481                   0.043726  
1482                   0.043726  
1483                   0.043726  
1484                   0.043726  
1485                   0.043726  
1486                   0.043726  
1487                   0.052849  
1488                   0.052849  
1489                   0.052849  
1490                   0.052849  
1491                   0.052849  
1492                   0.052849  
1493                   0.052849  
1494                   0.052849  
1495                   0.052849  
1496                   0.052849  
1497                   0.052849  
1498                   0.052849  
1499                   0.052849  
1500                   0.052849  
1501                   0.052849  
1502                   0.052849  

[1503 rows x 5 columns]
[126.201 125.201 125.951 ... 106.604 106.224 104.204]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[19]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#split data into train and test</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">train_test_split</span>
<span class="n">X_train</span><span class="p">,</span> <span class="n">X_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="p">,</span> <span class="n">test_size</span> <span class="o">=</span> <span class="mf">0.2</span><span class="p">,</span> <span class="n">random_state</span> <span class="o">=</span> <span class="mi">0</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[20]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Fitting Multiple Linear Regression to the Training set</span>
<span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="k">import</span> <span class="n">LinearRegression</span>
<span class="n">regressor</span> <span class="o">=</span> <span class="n">LinearRegression</span><span class="p">()</span>
<span class="n">regressor</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[20]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>LinearRegression(copy_X=True, fit_intercept=True, n_jobs=1, normalize=False)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[27]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Predicting the Test set results</span>
<span class="n">y_pred</span> <span class="o">=</span> <span class="n">regressor</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>

<span class="n">y_fitted</span> <span class="o">=</span> <span class="n">regressor</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_train</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[29]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># model evaluation train</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">mean_squared_error</span><span class="p">,</span> <span class="n">r2_score</span>

<span class="n">rmse_train</span> <span class="o">=</span> <span class="n">mean_squared_error</span><span class="p">(</span><span class="n">y_train</span><span class="p">,</span> <span class="n">y_fitted</span><span class="p">)</span>
<span class="n">r2_train</span> <span class="o">=</span> <span class="n">r2_score</span><span class="p">(</span><span class="n">y_train</span><span class="p">,</span> <span class="n">y_fitted</span><span class="p">)</span>
<span class="c1">#get adjusted r square as well</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Slope:&#39;</span> <span class="p">,</span><span class="n">regressor</span><span class="o">.</span><span class="n">coef_</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Intercept:&#39;</span><span class="p">,</span> <span class="n">regressor</span><span class="o">.</span><span class="n">intercept_</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Root mean squared error: &#39;</span><span class="p">,</span> <span class="n">rmse_train</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;R2 score: &#39;</span><span class="p">,</span> <span class="n">r2_train</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Slope: [-1.28041334e-03 -4.10769342e-01 -3.60326340e+01  9.81537999e-02
 -1.44109711e+02]
Intercept: 132.8456572124818
Root mean squared error:  23.618448776410744
R2 score:  0.5047490146008985
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[26]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># model evaluation test</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">mean_squared_error</span><span class="p">,</span> <span class="n">r2_score</span>

<span class="n">rmse_test</span> <span class="o">=</span> <span class="n">mean_squared_error</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span> <span class="n">y_pred</span><span class="p">)</span>
<span class="n">r2</span> <span class="o">=</span> <span class="n">r2_score</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span> <span class="n">y_pred</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Root mean squared error: &#39;</span><span class="p">,</span> <span class="n">rmse_test</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;R2 score: &#39;</span><span class="p">,</span> <span class="n">r2</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Slope: [-1.28041334e-03 -4.10769342e-01 -3.60326340e+01  9.81537999e-02
 -1.44109711e+02]
Intercept: 132.8456572124818
Root mean squared error:  20.765101495623412
R2 score:  0.558555727310101
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[46]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#assumptions testing</span>

<span class="c1">#first already tested, no linearity</span>
<span class="c1">#second, normality of residuals</span>

<span class="n">residuals</span> <span class="o">=</span> <span class="n">y_train</span> <span class="o">-</span> <span class="n">y_fitted</span>

<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">residuals</span><span class="p">,</span><span class="n">bins</span> <span class="o">=</span> <span class="mi">10</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
<span class="c1">#assumption passed</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[47]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#third homoscedasticity</span>

<span class="n">plt</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">y_fitted</span><span class="p">,</span><span class="n">residuals</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
<span class="c1">#check</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[48]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#fourth autocorrelation</span>
<span class="n">plt</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="n">residuals</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">]),</span><span class="n">residuals</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
<span class="c1">#passed</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[50]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">nbconvert</span>
<span class="n">jupyter</span> <span class="n">nbconvert</span> <span class="o">--</span><span class="n">to</span> <span class="n">html</span> <span class="n">notebook</span><span class="o">.</span><span class="n">ipynb</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_text output_error">
<pre>
<span class="ansi-cyan-intense-fg ansi-bold">  File </span><span class="ansi-green-intense-fg ansi-bold">&#34;&lt;ipython-input-50-0e32a0cdda7f&gt;&#34;</span><span class="ansi-cyan-intense-fg ansi-bold">, line </span><span class="ansi-green-intense-fg ansi-bold">2</span>
<span class="ansi-yellow-intense-fg ansi-bold">    jupyter nbconvert --to html notebook.ipynb</span>
<span class="ansi-white-intense-fg ansi-bold">                    ^</span>
<span class="ansi-red-intense-fg ansi-bold">SyntaxError</span><span class="ansi-red-intense-fg ansi-bold">:</span> invalid syntax
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
