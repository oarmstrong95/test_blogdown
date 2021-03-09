---
title: Predicting Charlie.
author: ''
date: '2021-03-07'
slug: predicting-charlie
categories: []
tags: 
  - Sport
subtitle: ''
summary: 'A projection system that creates a probabilistic forecast of what each AFL player might poll in the Brownlow Medal.'
authors: []
lastmod: '2021-03-07T18:51:47+11:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: true
projects: []
---

<style type="text/css">
  body{
  font-size: 9pt;
}
</style>

At its core, our brownlow medal model makes a probabilistic forecast of how many brownlow votes each player in each game of the season may get. Player attributes and in game statistics are passed to the model, which is a based on a [random forest](https://en.wikipedia.org/wiki/Random_forest) algorithm, and computes probabilities of 3 votes, 2 votes, 1 vote and no votes for each player. To account for the fact that certain players do not poll well (despite having good statistical games), the model applies a MERRET factor. This is defined as a weight that is applied to each players chance of getting a vote. Named after Zach Merrett, who churns out good statistical games but is not rewarded with votes, the model will punish those players who rack up possessions but who do not have a material impact on the outcome of the game (in the eyes of the umpires).

<body>

<style>
/* Create an active/current tablink class */
.tab button.active {
  background-color: #ccc;
}
</style>

<div class="tab">

<button class="tablinks" onclick="openCity(event, 'Top 20 Player Totals')" id="defaultOpen">Top 20 Player Totals</button>
<button class="tablinks" onclick="openCity(event, 'Game By Game Predictions')">Game By Game Predictions</button>

</div>

<div id="Top 20 Player Totals" class="tabcontent">

<p>

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#hxkzmjokeq .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#hxkzmjokeq .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#hxkzmjokeq .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#hxkzmjokeq .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#hxkzmjokeq .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#hxkzmjokeq .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: black;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#hxkzmjokeq .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#hxkzmjokeq .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#hxkzmjokeq .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#hxkzmjokeq .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#hxkzmjokeq .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: black;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#hxkzmjokeq .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#hxkzmjokeq .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#hxkzmjokeq .gt_from_md > :first-child {
  margin-top: 0;
}

#hxkzmjokeq .gt_from_md > :last-child {
  margin-bottom: 0;
}

#hxkzmjokeq .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#hxkzmjokeq .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#hxkzmjokeq .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#hxkzmjokeq .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#hxkzmjokeq .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#hxkzmjokeq .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#hxkzmjokeq .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#hxkzmjokeq .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#hxkzmjokeq .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#hxkzmjokeq .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#hxkzmjokeq .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#hxkzmjokeq .gt_sourcenote {
  font-size: 12px;
  padding: 4px;
}

#hxkzmjokeq .gt_left {
  text-align: left;
}

#hxkzmjokeq .gt_center {
  text-align: center;
}

#hxkzmjokeq .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#hxkzmjokeq .gt_font_normal {
  font-weight: normal;
}

#hxkzmjokeq .gt_font_bold {
  font-weight: bold;
}

#hxkzmjokeq .gt_font_italic {
  font-style: italic;
}

#hxkzmjokeq .gt_super {
  font-size: 65%;
}

#hxkzmjokeq .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="hxkzmjokeq" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="6" class="gt_heading gt_title gt_font_normal" style>Top 20 Brownlow Medal Pollers 2020</th>
    </tr>
    <tr>
      <th colspan="6" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Predicted votes are added up for each player for each game to give a total across the season</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_center gt_columns_bottom_border" rowspan="2" colspan="1">Player Name</th>
      <th class="gt_col_heading gt_center gt_columns_bottom_border" rowspan="2" colspan="1"></th>
      <th class="gt_col_heading gt_center gt_columns_bottom_border" rowspan="2" colspan="1">Team</th>
      <th class="gt_center gt_columns_top_border gt_column_spanner_outer" rowspan="1" colspan="2">
        <span class="gt_column_spanner">Season Averages</span>
      </th>
      <th class="gt_col_heading gt_center gt_columns_bottom_border" rowspan="2" colspan="1">Total Predicted Votes</th>
    </tr>
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1">Average Disposals<sup class="gt_footnote_marks">1</sup></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1">Average Supercoach<sup class="gt_footnote_marks">1</sup></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left">Lachie Neale</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Brisbane Lions</td>
      <td class="gt_row gt_right">51&percnt;</td>
      <td class="gt_row gt_right">62&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #3FC1C9; color: #000000;">28</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Travis Boak</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Port Adelaide</td>
      <td class="gt_row gt_right">43&percnt;</td>
      <td class="gt_row gt_right">51&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #8DD6DB; color: #000000;">22</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Christian Petracca</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/4/4e/Melbournefc.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Melbourne</td>
      <td class="gt_row gt_right">44&percnt;</td>
      <td class="gt_row gt_right">54&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #ACE0E4; color: #000000;">19</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Jack Macrae</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/0/09/Western_Bulldogs_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Western Bulldogs</td>
      <td class="gt_row gt_right">50&percnt;</td>
      <td class="gt_row gt_right">56&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #BFE7EA; color: #000000;">17</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Zach Merrett</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/8/8b/Essendon_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Essendon</td>
      <td class="gt_row gt_right">49&percnt;</td>
      <td class="gt_row gt_right">54&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #BFE7EA; color: #000000;">17</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Marcus Bontempelli</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/0/09/Western_Bulldogs_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Western Bulldogs</td>
      <td class="gt_row gt_right">39&percnt;</td>
      <td class="gt_row gt_right">54&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #C8EBED; color: #000000;">16</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Jack Steele</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/St_Kilda_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">St Kilda</td>
      <td class="gt_row gt_right">41&percnt;</td>
      <td class="gt_row gt_right">57&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #C8EBED; color: #000000;">16</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Patrick Dangerfield</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Geelong</td>
      <td class="gt_row gt_right">40&percnt;</td>
      <td class="gt_row gt_right">53&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #D2EEF0; color: #000000;">15</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Dustin Martin</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/3/35/Richmond_Tigers_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Richmond</td>
      <td class="gt_row gt_right">38&percnt;</td>
      <td class="gt_row gt_right">47&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #DBF1F3; color: #000000;">14</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Luke Parker</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/a/af/Sydney_Swans_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Sydney</td>
      <td class="gt_row gt_right">41&percnt;</td>
      <td class="gt_row gt_right">49&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #DBF1F3; color: #000000;">14</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Taylor Adams</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Collingwood</td>
      <td class="gt_row gt_right">42&percnt;</td>
      <td class="gt_row gt_right">51&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #DBF1F3; color: #000000;">14</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Lachie Whitfield</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/0/07/GWS_Giants_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Greater Western Sydney</td>
      <td class="gt_row gt_right">42&percnt;</td>
      <td class="gt_row gt_right">49&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #DBF1F3; color: #000000;">14</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Cameron Guthrie</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Geelong</td>
      <td class="gt_row gt_right">41&percnt;</td>
      <td class="gt_row gt_right">48&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #E4F5F6; color: #000000;">13</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Josh Kelly</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/0/07/GWS_Giants_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Greater Western Sydney</td>
      <td class="gt_row gt_right">41&percnt;</td>
      <td class="gt_row gt_right">53&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #EDF8F9; color: #000000;">12</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Zak Jones</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/St_Kilda_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">St Kilda</td>
      <td class="gt_row gt_right">36&percnt;</td>
      <td class="gt_row gt_right">43&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #EDF8F9; color: #000000;">12</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Scott Pendlebury</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Collingwood</td>
      <td class="gt_row gt_right">46&percnt;</td>
      <td class="gt_row gt_right">51&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #F6FCFC; color: #000000;">11</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Nic Naitanui</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/b/b5/West_Coast_Eagles_logo_2017.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">West Coast</td>
      <td class="gt_row gt_right">20&percnt;</td>
      <td class="gt_row gt_right">51&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #F6FCFC; color: #000000;">11</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Ollie Wines</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Port Adelaide</td>
      <td class="gt_row gt_right">40&percnt;</td>
      <td class="gt_row gt_right">49&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #F6FCFC; color: #000000;">11</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">David Mundy</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/c/ca/Fremantle_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Fremantle</td>
      <td class="gt_row gt_right">34&percnt;</td>
      <td class="gt_row gt_right">44&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000;">10</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Tom Hawkins</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Geelong</td>
      <td class="gt_row gt_right">23&percnt;</td>
      <td class="gt_row gt_right">49&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000;">10</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Tom Rockliff</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Port Adelaide</td>
      <td class="gt_row gt_right">43&percnt;</td>
      <td class="gt_row gt_right">50&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000;">10</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Mitch Duncan</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Geelong</td>
      <td class="gt_row gt_right">36&percnt;</td>
      <td class="gt_row gt_right">48&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000;">10</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Nat Fyfe</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/c/ca/Fremantle_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Fremantle</td>
      <td class="gt_row gt_right">40&percnt;</td>
      <td class="gt_row gt_right">53&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000;">10</td>
    </tr>
    <tr>
      <td class="gt_row gt_left">Clayton Oliver</td>
      <td class="gt_row gt_left"><img src="https://upload.wikimedia.org/wikipedia/en/4/4e/Melbournefc.svg" style="height:25px;"></td>
      <td class="gt_row gt_left">Melbourne</td>
      <td class="gt_row gt_right">46&percnt;</td>
      <td class="gt_row gt_right">57&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000;">10</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Andrew Brayshaw</td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/ca/Fremantle_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Fremantle</td>
      <td class="gt_row gt_right" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">37&percnt;</td>
      <td class="gt_row gt_right" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">47&percnt;</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">10</td>
    </tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="6"><strong>Data</strong>: fitzroy | <strong>Table:</strong> @oarmstrong95</td>
    </tr>
  </tfoot>
  <tfoot>
    <tr class="gt_footnotes">
      <td colspan="6">
        <p class="gt_footnote">
          <sup class="gt_footnote_marks">
            <em>1</em>
          </sup>
           
          Note: percentile average per game.
          <br />
        </p>
      </td>
    </tr>
  </tfoot>
</table></div>

</p>

</div>

<div id="Game By Game Predictions" class="tabcontent">

<p>

## Round 1 2020

-----

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#vlxbdgsake .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#vlxbdgsake .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#vlxbdgsake .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#vlxbdgsake .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#vlxbdgsake .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#vlxbdgsake .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#vlxbdgsake .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#vlxbdgsake .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#vlxbdgsake .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#vlxbdgsake .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#vlxbdgsake .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#vlxbdgsake .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#vlxbdgsake .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#vlxbdgsake .gt_from_md > :first-child {
  margin-top: 0;
}

#vlxbdgsake .gt_from_md > :last-child {
  margin-bottom: 0;
}

#vlxbdgsake .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#vlxbdgsake .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#vlxbdgsake .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#vlxbdgsake .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#vlxbdgsake .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#vlxbdgsake .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#vlxbdgsake .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#vlxbdgsake .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#vlxbdgsake .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#vlxbdgsake .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#vlxbdgsake .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#vlxbdgsake .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#vlxbdgsake .gt_left {
  text-align: left;
}

#vlxbdgsake .gt_center {
  text-align: center;
}

#vlxbdgsake .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#vlxbdgsake .gt_font_normal {
  font-weight: normal;
}

#vlxbdgsake .gt_font_bold {
  font-weight: bold;
}

#vlxbdgsake .gt_font_italic {
  font-style: italic;
}

#vlxbdgsake .gt_super {
  font-size: 65%;
}

#vlxbdgsake .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="vlxbdgsake" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Richmond vs. Carlton</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Thu 19 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/35/Richmond_Tigers_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Dion Prestia</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">50&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/Carlton_FC_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Patrick Cripps</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">50&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/35/Richmond_Tigers_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Dustin Martin</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">28&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#zyspnprboy .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#zyspnprboy .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#zyspnprboy .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#zyspnprboy .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#zyspnprboy .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#zyspnprboy .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#zyspnprboy .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#zyspnprboy .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#zyspnprboy .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#zyspnprboy .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#zyspnprboy .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#zyspnprboy .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#zyspnprboy .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#zyspnprboy .gt_from_md > :first-child {
  margin-top: 0;
}

#zyspnprboy .gt_from_md > :last-child {
  margin-bottom: 0;
}

#zyspnprboy .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#zyspnprboy .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#zyspnprboy .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#zyspnprboy .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#zyspnprboy .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#zyspnprboy .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#zyspnprboy .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#zyspnprboy .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#zyspnprboy .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#zyspnprboy .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#zyspnprboy .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#zyspnprboy .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#zyspnprboy .gt_left {
  text-align: left;
}

#zyspnprboy .gt_center {
  text-align: center;
}

#zyspnprboy .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#zyspnprboy .gt_font_normal {
  font-weight: normal;
}

#zyspnprboy .gt_font_bold {
  font-weight: bold;
}

#zyspnprboy .gt_font_italic {
  font-style: italic;
}

#zyspnprboy .gt_super {
  font-size: 65%;
}

#zyspnprboy .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="zyspnprboy" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Western Bulldogs vs. Collingwood</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Fri 20 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Brodie Grundy</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">44&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Scott Pendlebury</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">38&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Taylor Adams</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">43&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#vjlwhygxbn .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#vjlwhygxbn .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#vjlwhygxbn .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#vjlwhygxbn .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#vjlwhygxbn .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#vjlwhygxbn .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#vjlwhygxbn .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#vjlwhygxbn .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#vjlwhygxbn .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#vjlwhygxbn .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#vjlwhygxbn .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#vjlwhygxbn .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#vjlwhygxbn .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#vjlwhygxbn .gt_from_md > :first-child {
  margin-top: 0;
}

#vjlwhygxbn .gt_from_md > :last-child {
  margin-bottom: 0;
}

#vjlwhygxbn .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#vjlwhygxbn .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#vjlwhygxbn .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#vjlwhygxbn .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#vjlwhygxbn .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#vjlwhygxbn .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#vjlwhygxbn .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#vjlwhygxbn .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#vjlwhygxbn .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#vjlwhygxbn .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#vjlwhygxbn .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#vjlwhygxbn .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#vjlwhygxbn .gt_left {
  text-align: left;
}

#vjlwhygxbn .gt_center {
  text-align: center;
}

#vjlwhygxbn .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#vjlwhygxbn .gt_font_normal {
  font-weight: normal;
}

#vjlwhygxbn .gt_font_bold {
  font-weight: bold;
}

#vjlwhygxbn .gt_font_italic {
  font-style: italic;
}

#vjlwhygxbn .gt_super {
  font-size: 65%;
}

#vjlwhygxbn .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="vjlwhygxbn" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Essendon vs. Fremantle</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 21 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/8/8b/Essendon_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Dylan Shiel</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">81&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/ca/Fremantle_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Rory Lobb</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">49&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/8/8b/Essendon_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Adam Saad</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">38&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#smzbyqcuuq .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#smzbyqcuuq .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#smzbyqcuuq .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#smzbyqcuuq .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#smzbyqcuuq .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#smzbyqcuuq .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#smzbyqcuuq .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#smzbyqcuuq .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#smzbyqcuuq .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#smzbyqcuuq .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#smzbyqcuuq .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#smzbyqcuuq .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#smzbyqcuuq .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#smzbyqcuuq .gt_from_md > :first-child {
  margin-top: 0;
}

#smzbyqcuuq .gt_from_md > :last-child {
  margin-bottom: 0;
}

#smzbyqcuuq .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#smzbyqcuuq .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#smzbyqcuuq .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#smzbyqcuuq .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#smzbyqcuuq .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#smzbyqcuuq .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#smzbyqcuuq .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#smzbyqcuuq .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#smzbyqcuuq .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#smzbyqcuuq .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#smzbyqcuuq .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#smzbyqcuuq .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#smzbyqcuuq .gt_left {
  text-align: left;
}

#smzbyqcuuq .gt_center {
  text-align: center;
}

#smzbyqcuuq .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#smzbyqcuuq .gt_font_normal {
  font-weight: normal;
}

#smzbyqcuuq .gt_font_bold {
  font-weight: bold;
}

#smzbyqcuuq .gt_font_italic {
  font-style: italic;
}

#smzbyqcuuq .gt_super {
  font-size: 65%;
}

#smzbyqcuuq .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="smzbyqcuuq" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Adelaide vs. Sydney</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 21 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/af/Sydney_Swans_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Isaac Heeney</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">55&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/af/Sydney_Swans_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Luke Parker</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">40&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/af/Sydney_Swans_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Josh P. Kennedy</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">27&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#gzehxlxrot .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#gzehxlxrot .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gzehxlxrot .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#gzehxlxrot .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#gzehxlxrot .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gzehxlxrot .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gzehxlxrot .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#gzehxlxrot .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#gzehxlxrot .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#gzehxlxrot .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#gzehxlxrot .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#gzehxlxrot .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#gzehxlxrot .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#gzehxlxrot .gt_from_md > :first-child {
  margin-top: 0;
}

#gzehxlxrot .gt_from_md > :last-child {
  margin-bottom: 0;
}

#gzehxlxrot .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#gzehxlxrot .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#gzehxlxrot .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gzehxlxrot .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#gzehxlxrot .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gzehxlxrot .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#gzehxlxrot .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#gzehxlxrot .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gzehxlxrot .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gzehxlxrot .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#gzehxlxrot .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gzehxlxrot .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#gzehxlxrot .gt_left {
  text-align: left;
}

#gzehxlxrot .gt_center {
  text-align: center;
}

#gzehxlxrot .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#gzehxlxrot .gt_font_normal {
  font-weight: normal;
}

#gzehxlxrot .gt_font_bold {
  font-weight: bold;
}

#gzehxlxrot .gt_font_italic {
  font-style: italic;
}

#gzehxlxrot .gt_super {
  font-size: 65%;
}

#gzehxlxrot .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="gzehxlxrot" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>GWS vs. Geelong</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 21 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/07/GWS_Giants_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Harry Perryman</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">51&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Mitch Duncan</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">38&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/07/GWS_Giants_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Toby Greene</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">37&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#cmlivqizip .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#cmlivqizip .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#cmlivqizip .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#cmlivqizip .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#cmlivqizip .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#cmlivqizip .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#cmlivqizip .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#cmlivqizip .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#cmlivqizip .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#cmlivqizip .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#cmlivqizip .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#cmlivqizip .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#cmlivqizip .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#cmlivqizip .gt_from_md > :first-child {
  margin-top: 0;
}

#cmlivqizip .gt_from_md > :last-child {
  margin-bottom: 0;
}

#cmlivqizip .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#cmlivqizip .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#cmlivqizip .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#cmlivqizip .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#cmlivqizip .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#cmlivqizip .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#cmlivqizip .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#cmlivqizip .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#cmlivqizip .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#cmlivqizip .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#cmlivqizip .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#cmlivqizip .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#cmlivqizip .gt_left {
  text-align: left;
}

#cmlivqizip .gt_center {
  text-align: center;
}

#cmlivqizip .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#cmlivqizip .gt_font_normal {
  font-weight: normal;
}

#cmlivqizip .gt_font_bold {
  font-weight: bold;
}

#cmlivqizip .gt_font_italic {
  font-style: italic;
}

#cmlivqizip .gt_super {
  font-size: 65%;
}

#cmlivqizip .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="cmlivqizip" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Gold Coast vs. Port Adelaide</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 21 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Travis Boak</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">43&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Tom Rockliff</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">43&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Connor Rozee</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">54&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#exqxxzalta .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#exqxxzalta .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#exqxxzalta .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#exqxxzalta .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#exqxxzalta .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#exqxxzalta .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#exqxxzalta .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#exqxxzalta .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#exqxxzalta .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#exqxxzalta .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#exqxxzalta .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#exqxxzalta .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#exqxxzalta .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#exqxxzalta .gt_from_md > :first-child {
  margin-top: 0;
}

#exqxxzalta .gt_from_md > :last-child {
  margin-bottom: 0;
}

#exqxxzalta .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#exqxxzalta .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#exqxxzalta .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#exqxxzalta .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#exqxxzalta .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#exqxxzalta .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#exqxxzalta .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#exqxxzalta .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#exqxxzalta .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#exqxxzalta .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#exqxxzalta .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#exqxxzalta .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#exqxxzalta .gt_left {
  text-align: left;
}

#exqxxzalta .gt_center {
  text-align: center;
}

#exqxxzalta .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#exqxxzalta .gt_font_normal {
  font-weight: normal;
}

#exqxxzalta .gt_font_bold {
  font-weight: bold;
}

#exqxxzalta .gt_font_italic {
  font-style: italic;
}

#exqxxzalta .gt_super {
  font-size: 65%;
}

#exqxxzalta .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="exqxxzalta" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>North Melbourne vs. St Kilda</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 22 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/f/fc/North_Melbourne_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Ben Cunnington</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">65&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/f/fc/North_Melbourne_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jared Polec</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">31&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/St_Kilda_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Zak Jones</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">47&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#qphyfsidli .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#qphyfsidli .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#qphyfsidli .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#qphyfsidli .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#qphyfsidli .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#qphyfsidli .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#qphyfsidli .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#qphyfsidli .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#qphyfsidli .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#qphyfsidli .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#qphyfsidli .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#qphyfsidli .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#qphyfsidli .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#qphyfsidli .gt_from_md > :first-child {
  margin-top: 0;
}

#qphyfsidli .gt_from_md > :last-child {
  margin-bottom: 0;
}

#qphyfsidli .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#qphyfsidli .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#qphyfsidli .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#qphyfsidli .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#qphyfsidli .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#qphyfsidli .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#qphyfsidli .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#qphyfsidli .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#qphyfsidli .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#qphyfsidli .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#qphyfsidli .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#qphyfsidli .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#qphyfsidli .gt_left {
  text-align: left;
}

#qphyfsidli .gt_center {
  text-align: center;
}

#qphyfsidli .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#qphyfsidli .gt_font_normal {
  font-weight: normal;
}

#qphyfsidli .gt_font_bold {
  font-weight: bold;
}

#qphyfsidli .gt_font_italic {
  font-style: italic;
}

#qphyfsidli .gt_super {
  font-size: 65%;
}

#qphyfsidli .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="qphyfsidli" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Hawthorn vs. Brisbane Lions</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 22 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/6/62/Hawthorn-football-club-brand.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Chad Wingard</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">51&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Lachie Neale</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">44&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/6/62/Hawthorn-football-club-brand.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Shaun Burgoyne</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">29&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#ahzguehngf .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#ahzguehngf .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ahzguehngf .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#ahzguehngf .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#ahzguehngf .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ahzguehngf .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ahzguehngf .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#ahzguehngf .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#ahzguehngf .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#ahzguehngf .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#ahzguehngf .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#ahzguehngf .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#ahzguehngf .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#ahzguehngf .gt_from_md > :first-child {
  margin-top: 0;
}

#ahzguehngf .gt_from_md > :last-child {
  margin-bottom: 0;
}

#ahzguehngf .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#ahzguehngf .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#ahzguehngf .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ahzguehngf .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#ahzguehngf .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ahzguehngf .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#ahzguehngf .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#ahzguehngf .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ahzguehngf .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ahzguehngf .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#ahzguehngf .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ahzguehngf .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#ahzguehngf .gt_left {
  text-align: left;
}

#ahzguehngf .gt_center {
  text-align: center;
}

#ahzguehngf .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#ahzguehngf .gt_font_normal {
  font-weight: normal;
}

#ahzguehngf .gt_font_bold {
  font-weight: bold;
}

#ahzguehngf .gt_font_italic {
  font-style: italic;
}

#ahzguehngf .gt_super {
  font-size: 65%;
}

#ahzguehngf .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="ahzguehngf" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>West Coast vs. Melbourne</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 22 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/4/4e/Melbournefc.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jack Viney</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">28&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/b/b5/West_Coast_Eagles_logo_2017.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Andrew Gaff</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">45&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/b/b5/West_Coast_Eagles_logo_2017.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Liam Ryan</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">43&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

## Round 2 2020

-----

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#cvjquihofk .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#cvjquihofk .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#cvjquihofk .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#cvjquihofk .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#cvjquihofk .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#cvjquihofk .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#cvjquihofk .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#cvjquihofk .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#cvjquihofk .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#cvjquihofk .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#cvjquihofk .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#cvjquihofk .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#cvjquihofk .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#cvjquihofk .gt_from_md > :first-child {
  margin-top: 0;
}

#cvjquihofk .gt_from_md > :last-child {
  margin-bottom: 0;
}

#cvjquihofk .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#cvjquihofk .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#cvjquihofk .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#cvjquihofk .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#cvjquihofk .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#cvjquihofk .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#cvjquihofk .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#cvjquihofk .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#cvjquihofk .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#cvjquihofk .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#cvjquihofk .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#cvjquihofk .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#cvjquihofk .gt_left {
  text-align: left;
}

#cvjquihofk .gt_center {
  text-align: center;
}

#cvjquihofk .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#cvjquihofk .gt_font_normal {
  font-weight: normal;
}

#cvjquihofk .gt_font_bold {
  font-weight: bold;
}

#cvjquihofk .gt_font_italic {
  font-style: italic;
}

#cvjquihofk .gt_super {
  font-size: 65%;
}

#cvjquihofk .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="cvjquihofk" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Collingwood vs. Richmond</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Thu 11 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Scott Pendlebury</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">39&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/35/Richmond_Tigers_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Bachar Houli</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">32&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Taylor Adams</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">23&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#loegtjiuqd .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#loegtjiuqd .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#loegtjiuqd .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#loegtjiuqd .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#loegtjiuqd .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#loegtjiuqd .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#loegtjiuqd .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#loegtjiuqd .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#loegtjiuqd .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#loegtjiuqd .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#loegtjiuqd .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#loegtjiuqd .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#loegtjiuqd .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#loegtjiuqd .gt_from_md > :first-child {
  margin-top: 0;
}

#loegtjiuqd .gt_from_md > :last-child {
  margin-bottom: 0;
}

#loegtjiuqd .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#loegtjiuqd .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#loegtjiuqd .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#loegtjiuqd .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#loegtjiuqd .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#loegtjiuqd .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#loegtjiuqd .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#loegtjiuqd .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#loegtjiuqd .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#loegtjiuqd .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#loegtjiuqd .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#loegtjiuqd .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#loegtjiuqd .gt_left {
  text-align: left;
}

#loegtjiuqd .gt_center {
  text-align: center;
}

#loegtjiuqd .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#loegtjiuqd .gt_font_normal {
  font-weight: normal;
}

#loegtjiuqd .gt_font_bold {
  font-weight: bold;
}

#loegtjiuqd .gt_font_italic {
  font-style: italic;
}

#loegtjiuqd .gt_super {
  font-size: 65%;
}

#loegtjiuqd .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="loegtjiuqd" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Geelong vs. Hawthorn</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Fri 12 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Joel Selwood</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">58&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Rhys Stanley</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">40&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Brandan Parfitt</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">45&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#thxjeyksxm .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#thxjeyksxm .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#thxjeyksxm .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#thxjeyksxm .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#thxjeyksxm .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#thxjeyksxm .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#thxjeyksxm .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#thxjeyksxm .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#thxjeyksxm .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#thxjeyksxm .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#thxjeyksxm .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#thxjeyksxm .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#thxjeyksxm .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#thxjeyksxm .gt_from_md > :first-child {
  margin-top: 0;
}

#thxjeyksxm .gt_from_md > :last-child {
  margin-bottom: 0;
}

#thxjeyksxm .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#thxjeyksxm .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#thxjeyksxm .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#thxjeyksxm .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#thxjeyksxm .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#thxjeyksxm .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#thxjeyksxm .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#thxjeyksxm .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#thxjeyksxm .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#thxjeyksxm .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#thxjeyksxm .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#thxjeyksxm .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#thxjeyksxm .gt_left {
  text-align: left;
}

#thxjeyksxm .gt_center {
  text-align: center;
}

#thxjeyksxm .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#thxjeyksxm .gt_font_normal {
  font-weight: normal;
}

#thxjeyksxm .gt_font_bold {
  font-weight: bold;
}

#thxjeyksxm .gt_font_italic {
  font-style: italic;
}

#thxjeyksxm .gt_super {
  font-size: 65%;
}

#thxjeyksxm .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="thxjeyksxm" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Brisbane Lions vs. Fremantle</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 13 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Lachie Neale</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">76&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Charlie Cameron</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">39&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/ca/Fremantle_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Nat Fyfe</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">34&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#atrjievfgq .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#atrjievfgq .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#atrjievfgq .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#atrjievfgq .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#atrjievfgq .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#atrjievfgq .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#atrjievfgq .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#atrjievfgq .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#atrjievfgq .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#atrjievfgq .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#atrjievfgq .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#atrjievfgq .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#atrjievfgq .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#atrjievfgq .gt_from_md > :first-child {
  margin-top: 0;
}

#atrjievfgq .gt_from_md > :last-child {
  margin-bottom: 0;
}

#atrjievfgq .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#atrjievfgq .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#atrjievfgq .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#atrjievfgq .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#atrjievfgq .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#atrjievfgq .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#atrjievfgq .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#atrjievfgq .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#atrjievfgq .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#atrjievfgq .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#atrjievfgq .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#atrjievfgq .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#atrjievfgq .gt_left {
  text-align: left;
}

#atrjievfgq .gt_center {
  text-align: center;
}

#atrjievfgq .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#atrjievfgq .gt_font_normal {
  font-weight: normal;
}

#atrjievfgq .gt_font_bold {
  font-weight: bold;
}

#atrjievfgq .gt_font_italic {
  font-style: italic;
}

#atrjievfgq .gt_super {
  font-size: 65%;
}

#atrjievfgq .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="atrjievfgq" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Carlton vs. Melbourne</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 13 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/4/4e/Melbournefc.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Christian Petracca</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">59&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/4/4e/Melbournefc.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Max Gawn</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">36&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/4/4e/Melbournefc.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Clayton Oliver</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">36&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#jysjqqjoyx .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#jysjqqjoyx .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#jysjqqjoyx .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#jysjqqjoyx .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#jysjqqjoyx .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#jysjqqjoyx .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#jysjqqjoyx .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#jysjqqjoyx .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#jysjqqjoyx .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#jysjqqjoyx .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#jysjqqjoyx .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#jysjqqjoyx .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#jysjqqjoyx .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#jysjqqjoyx .gt_from_md > :first-child {
  margin-top: 0;
}

#jysjqqjoyx .gt_from_md > :last-child {
  margin-bottom: 0;
}

#jysjqqjoyx .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#jysjqqjoyx .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#jysjqqjoyx .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#jysjqqjoyx .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#jysjqqjoyx .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#jysjqqjoyx .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#jysjqqjoyx .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#jysjqqjoyx .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#jysjqqjoyx .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#jysjqqjoyx .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#jysjqqjoyx .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#jysjqqjoyx .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#jysjqqjoyx .gt_left {
  text-align: left;
}

#jysjqqjoyx .gt_center {
  text-align: center;
}

#jysjqqjoyx .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#jysjqqjoyx .gt_font_normal {
  font-weight: normal;
}

#jysjqqjoyx .gt_font_bold {
  font-weight: bold;
}

#jysjqqjoyx .gt_font_italic {
  font-style: italic;
}

#jysjqqjoyx .gt_super {
  font-size: 65%;
}

#jysjqqjoyx .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="jysjqqjoyx" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Gold Coast vs. West Coast</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 13 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/7/7d/Gold_Coast_Suns_AFL_Logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Matthew Rowell</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">57&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/b/b5/West_Coast_Eagles_logo_2017.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Luke Shuey</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">50&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/7/7d/Gold_Coast_Suns_AFL_Logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Lachie Weller</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">38&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#uibxrcnwcq .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#uibxrcnwcq .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#uibxrcnwcq .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#uibxrcnwcq .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#uibxrcnwcq .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#uibxrcnwcq .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#uibxrcnwcq .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#uibxrcnwcq .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#uibxrcnwcq .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#uibxrcnwcq .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#uibxrcnwcq .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#uibxrcnwcq .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#uibxrcnwcq .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#uibxrcnwcq .gt_from_md > :first-child {
  margin-top: 0;
}

#uibxrcnwcq .gt_from_md > :last-child {
  margin-bottom: 0;
}

#uibxrcnwcq .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#uibxrcnwcq .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#uibxrcnwcq .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#uibxrcnwcq .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#uibxrcnwcq .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#uibxrcnwcq .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#uibxrcnwcq .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#uibxrcnwcq .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#uibxrcnwcq .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#uibxrcnwcq .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#uibxrcnwcq .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#uibxrcnwcq .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#uibxrcnwcq .gt_left {
  text-align: left;
}

#uibxrcnwcq .gt_center {
  text-align: center;
}

#uibxrcnwcq .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#uibxrcnwcq .gt_font_normal {
  font-weight: normal;
}

#uibxrcnwcq .gt_font_bold {
  font-weight: bold;
}

#uibxrcnwcq .gt_font_italic {
  font-style: italic;
}

#uibxrcnwcq .gt_super {
  font-size: 65%;
}

#uibxrcnwcq .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="uibxrcnwcq" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Port Adelaide vs. Adelaide</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 13 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Travis Boak</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">26&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Steven Motlop</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">31&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Darcy Byrne-Jones</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">48&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#zuyzxmvuzz .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#zuyzxmvuzz .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#zuyzxmvuzz .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#zuyzxmvuzz .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#zuyzxmvuzz .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#zuyzxmvuzz .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#zuyzxmvuzz .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#zuyzxmvuzz .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#zuyzxmvuzz .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#zuyzxmvuzz .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#zuyzxmvuzz .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#zuyzxmvuzz .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#zuyzxmvuzz .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#zuyzxmvuzz .gt_from_md > :first-child {
  margin-top: 0;
}

#zuyzxmvuzz .gt_from_md > :last-child {
  margin-bottom: 0;
}

#zuyzxmvuzz .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#zuyzxmvuzz .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#zuyzxmvuzz .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#zuyzxmvuzz .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#zuyzxmvuzz .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#zuyzxmvuzz .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#zuyzxmvuzz .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#zuyzxmvuzz .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#zuyzxmvuzz .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#zuyzxmvuzz .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#zuyzxmvuzz .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#zuyzxmvuzz .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#zuyzxmvuzz .gt_left {
  text-align: left;
}

#zuyzxmvuzz .gt_center {
  text-align: center;
}

#zuyzxmvuzz .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#zuyzxmvuzz .gt_font_normal {
  font-weight: normal;
}

#zuyzxmvuzz .gt_font_bold {
  font-weight: bold;
}

#zuyzxmvuzz .gt_font_italic {
  font-style: italic;
}

#zuyzxmvuzz .gt_super {
  font-size: 65%;
}

#zuyzxmvuzz .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="zuyzxmvuzz" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>GWS vs. North Melbourne</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 14 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/f/fc/North_Melbourne_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Todd Goldstein</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">57&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/f/fc/North_Melbourne_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Shaun Higgins</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">51&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/f/fc/North_Melbourne_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jared Polec</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">46&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#nidljttuns .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#nidljttuns .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#nidljttuns .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#nidljttuns .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#nidljttuns .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#nidljttuns .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#nidljttuns .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#nidljttuns .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#nidljttuns .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#nidljttuns .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#nidljttuns .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#nidljttuns .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#nidljttuns .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#nidljttuns .gt_from_md > :first-child {
  margin-top: 0;
}

#nidljttuns .gt_from_md > :last-child {
  margin-bottom: 0;
}

#nidljttuns .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#nidljttuns .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#nidljttuns .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#nidljttuns .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#nidljttuns .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#nidljttuns .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#nidljttuns .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#nidljttuns .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#nidljttuns .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#nidljttuns .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#nidljttuns .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#nidljttuns .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#nidljttuns .gt_left {
  text-align: left;
}

#nidljttuns .gt_center {
  text-align: center;
}

#nidljttuns .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#nidljttuns .gt_font_normal {
  font-weight: normal;
}

#nidljttuns .gt_font_bold {
  font-weight: bold;
}

#nidljttuns .gt_font_italic {
  font-style: italic;
}

#nidljttuns .gt_super {
  font-size: 65%;
}

#nidljttuns .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="nidljttuns" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Sydney vs. Essendon</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 14 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/8/8b/Essendon_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Zach Merrett</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">77&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/8/8b/Essendon_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Adam Saad</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">26&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/af/Sydney_Swans_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Oliver Florent</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">43&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#tiwbnqwxvt .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#tiwbnqwxvt .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#tiwbnqwxvt .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#tiwbnqwxvt .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#tiwbnqwxvt .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#tiwbnqwxvt .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#tiwbnqwxvt .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#tiwbnqwxvt .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#tiwbnqwxvt .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#tiwbnqwxvt .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#tiwbnqwxvt .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#tiwbnqwxvt .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#tiwbnqwxvt .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#tiwbnqwxvt .gt_from_md > :first-child {
  margin-top: 0;
}

#tiwbnqwxvt .gt_from_md > :last-child {
  margin-bottom: 0;
}

#tiwbnqwxvt .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#tiwbnqwxvt .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#tiwbnqwxvt .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#tiwbnqwxvt .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#tiwbnqwxvt .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#tiwbnqwxvt .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#tiwbnqwxvt .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#tiwbnqwxvt .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#tiwbnqwxvt .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#tiwbnqwxvt .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#tiwbnqwxvt .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#tiwbnqwxvt .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#tiwbnqwxvt .gt_left {
  text-align: left;
}

#tiwbnqwxvt .gt_center {
  text-align: center;
}

#tiwbnqwxvt .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#tiwbnqwxvt .gt_font_normal {
  font-weight: normal;
}

#tiwbnqwxvt .gt_font_bold {
  font-weight: bold;
}

#tiwbnqwxvt .gt_font_italic {
  font-style: italic;
}

#tiwbnqwxvt .gt_super {
  font-size: 65%;
}

#tiwbnqwxvt .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="tiwbnqwxvt" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>St Kilda vs. Western Bulldogs</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 14 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/St_Kilda_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jack Billings</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">72&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/St_Kilda_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Zak Jones</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">41&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/09/Western_Bulldogs_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Josh Dunkley</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">45&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

## Round 3 2020

-----

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#qoszbacmii .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#qoszbacmii .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#qoszbacmii .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#qoszbacmii .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#qoszbacmii .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#qoszbacmii .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#qoszbacmii .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#qoszbacmii .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#qoszbacmii .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#qoszbacmii .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#qoszbacmii .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#qoszbacmii .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#qoszbacmii .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#qoszbacmii .gt_from_md > :first-child {
  margin-top: 0;
}

#qoszbacmii .gt_from_md > :last-child {
  margin-bottom: 0;
}

#qoszbacmii .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#qoszbacmii .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#qoszbacmii .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#qoszbacmii .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#qoszbacmii .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#qoszbacmii .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#qoszbacmii .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#qoszbacmii .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#qoszbacmii .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#qoszbacmii .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#qoszbacmii .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#qoszbacmii .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#qoszbacmii .gt_left {
  text-align: left;
}

#qoszbacmii .gt_center {
  text-align: center;
}

#qoszbacmii .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#qoszbacmii .gt_font_normal {
  font-weight: normal;
}

#qoszbacmii .gt_font_bold {
  font-weight: bold;
}

#qoszbacmii .gt_font_italic {
  font-style: italic;
}

#qoszbacmii .gt_super {
  font-size: 65%;
}

#qoszbacmii .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="qoszbacmii" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Richmond vs. Hawthorn</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Thu 18 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/6/62/Hawthorn-football-club-brand.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jaeger O'Meara</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">54&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/6/62/Hawthorn-football-club-brand.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Isaac Smith</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">43&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/6/62/Hawthorn-football-club-brand.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jonathon Ceglar</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">44&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#drdwlkivll .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#drdwlkivll .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#drdwlkivll .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#drdwlkivll .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#drdwlkivll .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#drdwlkivll .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#drdwlkivll .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#drdwlkivll .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#drdwlkivll .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#drdwlkivll .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#drdwlkivll .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#drdwlkivll .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#drdwlkivll .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#drdwlkivll .gt_from_md > :first-child {
  margin-top: 0;
}

#drdwlkivll .gt_from_md > :last-child {
  margin-bottom: 0;
}

#drdwlkivll .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#drdwlkivll .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#drdwlkivll .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#drdwlkivll .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#drdwlkivll .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#drdwlkivll .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#drdwlkivll .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#drdwlkivll .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#drdwlkivll .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#drdwlkivll .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#drdwlkivll .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#drdwlkivll .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#drdwlkivll .gt_left {
  text-align: left;
}

#drdwlkivll .gt_center {
  text-align: center;
}

#drdwlkivll .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#drdwlkivll .gt_font_normal {
  font-weight: normal;
}

#drdwlkivll .gt_font_bold {
  font-weight: bold;
}

#drdwlkivll .gt_font_italic {
  font-style: italic;
}

#drdwlkivll .gt_super {
  font-size: 65%;
}

#drdwlkivll .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="drdwlkivll" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Western Bulldogs vs. GWS</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Fri 19 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/09/Western_Bulldogs_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jack Macrae</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">20&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/09/Western_Bulldogs_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Caleb Daniel</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">32&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/09/Western_Bulldogs_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Bailey Smith</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">45&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#oomjwoinlx .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#oomjwoinlx .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#oomjwoinlx .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#oomjwoinlx .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#oomjwoinlx .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#oomjwoinlx .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#oomjwoinlx .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#oomjwoinlx .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#oomjwoinlx .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#oomjwoinlx .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#oomjwoinlx .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#oomjwoinlx .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#oomjwoinlx .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#oomjwoinlx .gt_from_md > :first-child {
  margin-top: 0;
}

#oomjwoinlx .gt_from_md > :last-child {
  margin-bottom: 0;
}

#oomjwoinlx .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#oomjwoinlx .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#oomjwoinlx .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#oomjwoinlx .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#oomjwoinlx .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#oomjwoinlx .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#oomjwoinlx .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#oomjwoinlx .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#oomjwoinlx .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#oomjwoinlx .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#oomjwoinlx .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#oomjwoinlx .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#oomjwoinlx .gt_left {
  text-align: left;
}

#oomjwoinlx .gt_center {
  text-align: center;
}

#oomjwoinlx .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#oomjwoinlx .gt_font_normal {
  font-weight: normal;
}

#oomjwoinlx .gt_font_bold {
  font-weight: bold;
}

#oomjwoinlx .gt_font_italic {
  font-style: italic;
}

#oomjwoinlx .gt_super {
  font-size: 65%;
}

#oomjwoinlx .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="oomjwoinlx" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>North Melbourne vs. Sydney</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 20 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/f/fc/North_Melbourne_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jy Simpkin</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">51&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/af/Sydney_Swans_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Isaac Heeney</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">40&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/af/Sydney_Swans_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Luke Parker</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">37&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#gsnctglxme .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#gsnctglxme .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gsnctglxme .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#gsnctglxme .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#gsnctglxme .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gsnctglxme .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gsnctglxme .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#gsnctglxme .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#gsnctglxme .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#gsnctglxme .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#gsnctglxme .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#gsnctglxme .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#gsnctglxme .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#gsnctglxme .gt_from_md > :first-child {
  margin-top: 0;
}

#gsnctglxme .gt_from_md > :last-child {
  margin-bottom: 0;
}

#gsnctglxme .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#gsnctglxme .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#gsnctglxme .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gsnctglxme .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#gsnctglxme .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gsnctglxme .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#gsnctglxme .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#gsnctglxme .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gsnctglxme .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gsnctglxme .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#gsnctglxme .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gsnctglxme .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#gsnctglxme .gt_left {
  text-align: left;
}

#gsnctglxme .gt_center {
  text-align: center;
}

#gsnctglxme .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#gsnctglxme .gt_font_normal {
  font-weight: normal;
}

#gsnctglxme .gt_font_bold {
  font-weight: bold;
}

#gsnctglxme .gt_font_italic {
  font-style: italic;
}

#gsnctglxme .gt_super {
  font-size: 65%;
}

#gsnctglxme .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="gsnctglxme" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Collingwood vs. St Kilda</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 20 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Steele Sidebottom</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">25&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Taylor Adams</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">47&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Brodie Grundy</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">42&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#ksjtcwtvdc .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#ksjtcwtvdc .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ksjtcwtvdc .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#ksjtcwtvdc .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#ksjtcwtvdc .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ksjtcwtvdc .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ksjtcwtvdc .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#ksjtcwtvdc .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#ksjtcwtvdc .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#ksjtcwtvdc .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#ksjtcwtvdc .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#ksjtcwtvdc .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#ksjtcwtvdc .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#ksjtcwtvdc .gt_from_md > :first-child {
  margin-top: 0;
}

#ksjtcwtvdc .gt_from_md > :last-child {
  margin-bottom: 0;
}

#ksjtcwtvdc .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#ksjtcwtvdc .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#ksjtcwtvdc .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ksjtcwtvdc .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#ksjtcwtvdc .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ksjtcwtvdc .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#ksjtcwtvdc .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#ksjtcwtvdc .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ksjtcwtvdc .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ksjtcwtvdc .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#ksjtcwtvdc .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ksjtcwtvdc .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#ksjtcwtvdc .gt_left {
  text-align: left;
}

#ksjtcwtvdc .gt_center {
  text-align: center;
}

#ksjtcwtvdc .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#ksjtcwtvdc .gt_font_normal {
  font-weight: normal;
}

#ksjtcwtvdc .gt_font_bold {
  font-weight: bold;
}

#ksjtcwtvdc .gt_font_italic {
  font-style: italic;
}

#ksjtcwtvdc .gt_super {
  font-size: 65%;
}

#ksjtcwtvdc .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="ksjtcwtvdc" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Brisbane Lions vs. West Coast</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 20 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Lachie Neale</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">88&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Hugh McCluggage</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">52&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jarrod Berry</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">40&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#ftlpsjjxpb .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#ftlpsjjxpb .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ftlpsjjxpb .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#ftlpsjjxpb .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#ftlpsjjxpb .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ftlpsjjxpb .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ftlpsjjxpb .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#ftlpsjjxpb .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#ftlpsjjxpb .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#ftlpsjjxpb .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#ftlpsjjxpb .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#ftlpsjjxpb .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#ftlpsjjxpb .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#ftlpsjjxpb .gt_from_md > :first-child {
  margin-top: 0;
}

#ftlpsjjxpb .gt_from_md > :last-child {
  margin-bottom: 0;
}

#ftlpsjjxpb .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#ftlpsjjxpb .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#ftlpsjjxpb .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ftlpsjjxpb .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#ftlpsjjxpb .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ftlpsjjxpb .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#ftlpsjjxpb .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#ftlpsjjxpb .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ftlpsjjxpb .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ftlpsjjxpb .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#ftlpsjjxpb .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ftlpsjjxpb .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#ftlpsjjxpb .gt_left {
  text-align: left;
}

#ftlpsjjxpb .gt_center {
  text-align: center;
}

#ftlpsjjxpb .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#ftlpsjjxpb .gt_font_normal {
  font-weight: normal;
}

#ftlpsjjxpb .gt_font_bold {
  font-weight: bold;
}

#ftlpsjjxpb .gt_font_italic {
  font-style: italic;
}

#ftlpsjjxpb .gt_super {
  font-size: 65%;
}

#ftlpsjjxpb .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="ftlpsjjxpb" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Geelong vs. Carlton</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 20 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/Carlton_FC_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Patrick Cripps</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">24&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/Carlton_FC_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Levi Casboult</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">34&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/Carlton_FC_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Marc Pittonet</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">34&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#gjdohjhcqb .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#gjdohjhcqb .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gjdohjhcqb .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#gjdohjhcqb .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#gjdohjhcqb .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gjdohjhcqb .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gjdohjhcqb .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#gjdohjhcqb .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#gjdohjhcqb .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#gjdohjhcqb .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#gjdohjhcqb .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#gjdohjhcqb .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#gjdohjhcqb .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#gjdohjhcqb .gt_from_md > :first-child {
  margin-top: 0;
}

#gjdohjhcqb .gt_from_md > :last-child {
  margin-bottom: 0;
}

#gjdohjhcqb .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#gjdohjhcqb .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#gjdohjhcqb .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gjdohjhcqb .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#gjdohjhcqb .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gjdohjhcqb .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#gjdohjhcqb .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#gjdohjhcqb .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gjdohjhcqb .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gjdohjhcqb .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#gjdohjhcqb .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gjdohjhcqb .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#gjdohjhcqb .gt_left {
  text-align: left;
}

#gjdohjhcqb .gt_center {
  text-align: center;
}

#gjdohjhcqb .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#gjdohjhcqb .gt_font_normal {
  font-weight: normal;
}

#gjdohjhcqb .gt_font_bold {
  font-weight: bold;
}

#gjdohjhcqb .gt_font_italic {
  font-style: italic;
}

#gjdohjhcqb .gt_super {
  font-size: 65%;
}

#gjdohjhcqb .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="gjdohjhcqb" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Gold Coast vs. Adelaide</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 21 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/7/7d/Gold_Coast_Suns_AFL_Logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Matthew Rowell</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">52&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/7/7d/Gold_Coast_Suns_AFL_Logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jarrod Witts</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">40&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/7/7d/Gold_Coast_Suns_AFL_Logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Touk Miller</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">52&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#lnnxhqeqsm .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#lnnxhqeqsm .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#lnnxhqeqsm .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#lnnxhqeqsm .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#lnnxhqeqsm .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#lnnxhqeqsm .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#lnnxhqeqsm .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#lnnxhqeqsm .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#lnnxhqeqsm .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#lnnxhqeqsm .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#lnnxhqeqsm .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#lnnxhqeqsm .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#lnnxhqeqsm .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#lnnxhqeqsm .gt_from_md > :first-child {
  margin-top: 0;
}

#lnnxhqeqsm .gt_from_md > :last-child {
  margin-bottom: 0;
}

#lnnxhqeqsm .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#lnnxhqeqsm .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#lnnxhqeqsm .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#lnnxhqeqsm .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#lnnxhqeqsm .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#lnnxhqeqsm .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#lnnxhqeqsm .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#lnnxhqeqsm .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#lnnxhqeqsm .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#lnnxhqeqsm .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#lnnxhqeqsm .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#lnnxhqeqsm .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#lnnxhqeqsm .gt_left {
  text-align: left;
}

#lnnxhqeqsm .gt_center {
  text-align: center;
}

#lnnxhqeqsm .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#lnnxhqeqsm .gt_font_normal {
  font-weight: normal;
}

#lnnxhqeqsm .gt_font_bold {
  font-weight: bold;
}

#lnnxhqeqsm .gt_font_italic {
  font-style: italic;
}

#lnnxhqeqsm .gt_super {
  font-size: 65%;
}

#lnnxhqeqsm .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="lnnxhqeqsm" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Fremantle vs. Port Adelaide</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 21 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Travis Boak</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">68&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Ollie Wines</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">45&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/ca/Fremantle_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Nat Fyfe</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">26&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#xlkrbodstm .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#xlkrbodstm .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#xlkrbodstm .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#xlkrbodstm .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#xlkrbodstm .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#xlkrbodstm .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#xlkrbodstm .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#xlkrbodstm .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#xlkrbodstm .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#xlkrbodstm .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#xlkrbodstm .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#xlkrbodstm .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#xlkrbodstm .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#xlkrbodstm .gt_from_md > :first-child {
  margin-top: 0;
}

#xlkrbodstm .gt_from_md > :last-child {
  margin-bottom: 0;
}

#xlkrbodstm .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#xlkrbodstm .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#xlkrbodstm .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#xlkrbodstm .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#xlkrbodstm .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#xlkrbodstm .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#xlkrbodstm .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#xlkrbodstm .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#xlkrbodstm .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#xlkrbodstm .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#xlkrbodstm .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#xlkrbodstm .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#xlkrbodstm .gt_left {
  text-align: left;
}

#xlkrbodstm .gt_center {
  text-align: center;
}

#xlkrbodstm .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#xlkrbodstm .gt_font_normal {
  font-weight: normal;
}

#xlkrbodstm .gt_font_bold {
  font-weight: bold;
}

#xlkrbodstm .gt_font_italic {
  font-style: italic;
}

#xlkrbodstm .gt_super {
  font-size: 65%;
}

#xlkrbodstm .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="xlkrbodstm" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Sydney vs. Western Bulldogs</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Thu 25 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/09/Western_Bulldogs_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Marcus Bontempelli</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">58&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/09/Western_Bulldogs_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Tim English</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">35&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/af/Sydney_Swans_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Tom Papley</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">44&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

## Round 4 2020

-----

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#jncjaqvehv .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#jncjaqvehv .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#jncjaqvehv .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#jncjaqvehv .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#jncjaqvehv .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#jncjaqvehv .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#jncjaqvehv .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#jncjaqvehv .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#jncjaqvehv .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#jncjaqvehv .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#jncjaqvehv .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#jncjaqvehv .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#jncjaqvehv .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#jncjaqvehv .gt_from_md > :first-child {
  margin-top: 0;
}

#jncjaqvehv .gt_from_md > :last-child {
  margin-bottom: 0;
}

#jncjaqvehv .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#jncjaqvehv .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#jncjaqvehv .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#jncjaqvehv .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#jncjaqvehv .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#jncjaqvehv .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#jncjaqvehv .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#jncjaqvehv .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#jncjaqvehv .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#jncjaqvehv .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#jncjaqvehv .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#jncjaqvehv .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#jncjaqvehv .gt_left {
  text-align: left;
}

#jncjaqvehv .gt_center {
  text-align: center;
}

#jncjaqvehv .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#jncjaqvehv .gt_font_normal {
  font-weight: normal;
}

#jncjaqvehv .gt_font_bold {
  font-weight: bold;
}

#jncjaqvehv .gt_font_italic {
  font-style: italic;
}

#jncjaqvehv .gt_super {
  font-size: 65%;
}

#jncjaqvehv .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="jncjaqvehv" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>GWS vs. Collingwood</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Fri 26 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/07/GWS_Giants_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Toby Greene</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">44&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Scott Pendlebury</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">42&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Brodie Grundy</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">41&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#hfqnfrlkwo .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#hfqnfrlkwo .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#hfqnfrlkwo .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#hfqnfrlkwo .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#hfqnfrlkwo .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#hfqnfrlkwo .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#hfqnfrlkwo .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#hfqnfrlkwo .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#hfqnfrlkwo .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#hfqnfrlkwo .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#hfqnfrlkwo .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#hfqnfrlkwo .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#hfqnfrlkwo .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#hfqnfrlkwo .gt_from_md > :first-child {
  margin-top: 0;
}

#hfqnfrlkwo .gt_from_md > :last-child {
  margin-bottom: 0;
}

#hfqnfrlkwo .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#hfqnfrlkwo .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#hfqnfrlkwo .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#hfqnfrlkwo .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#hfqnfrlkwo .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#hfqnfrlkwo .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#hfqnfrlkwo .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#hfqnfrlkwo .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#hfqnfrlkwo .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#hfqnfrlkwo .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#hfqnfrlkwo .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#hfqnfrlkwo .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#hfqnfrlkwo .gt_left {
  text-align: left;
}

#hfqnfrlkwo .gt_center {
  text-align: center;
}

#hfqnfrlkwo .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#hfqnfrlkwo .gt_font_normal {
  font-weight: normal;
}

#hfqnfrlkwo .gt_font_bold {
  font-weight: bold;
}

#hfqnfrlkwo .gt_font_italic {
  font-style: italic;
}

#hfqnfrlkwo .gt_super {
  font-size: 65%;
}

#hfqnfrlkwo .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="hfqnfrlkwo" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Port Adelaide vs. West Coast</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 27 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Charlie Dixon</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">46&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Hamish Hartlett</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">25&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Brad Ebert</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">50&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#mbckjgxnsd .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#mbckjgxnsd .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#mbckjgxnsd .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#mbckjgxnsd .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#mbckjgxnsd .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#mbckjgxnsd .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#mbckjgxnsd .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#mbckjgxnsd .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#mbckjgxnsd .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#mbckjgxnsd .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#mbckjgxnsd .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#mbckjgxnsd .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#mbckjgxnsd .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#mbckjgxnsd .gt_from_md > :first-child {
  margin-top: 0;
}

#mbckjgxnsd .gt_from_md > :last-child {
  margin-bottom: 0;
}

#mbckjgxnsd .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#mbckjgxnsd .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#mbckjgxnsd .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#mbckjgxnsd .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#mbckjgxnsd .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#mbckjgxnsd .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#mbckjgxnsd .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#mbckjgxnsd .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#mbckjgxnsd .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#mbckjgxnsd .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#mbckjgxnsd .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#mbckjgxnsd .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#mbckjgxnsd .gt_left {
  text-align: left;
}

#mbckjgxnsd .gt_center {
  text-align: center;
}

#mbckjgxnsd .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#mbckjgxnsd .gt_font_normal {
  font-weight: normal;
}

#mbckjgxnsd .gt_font_bold {
  font-weight: bold;
}

#mbckjgxnsd .gt_font_italic {
  font-style: italic;
}

#mbckjgxnsd .gt_super {
  font-size: 65%;
}

#mbckjgxnsd .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="mbckjgxnsd" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>St Kilda vs. Richmond</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 27 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/St_Kilda_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Dan Butler</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">37&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/St_Kilda_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Tim Membrey</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">44&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/35/Richmond_Tigers_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Toby Nankervis</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">37&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#jtzrdkizco .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#jtzrdkizco .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#jtzrdkizco .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#jtzrdkizco .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#jtzrdkizco .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#jtzrdkizco .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#jtzrdkizco .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#jtzrdkizco .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#jtzrdkizco .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#jtzrdkizco .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#jtzrdkizco .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#jtzrdkizco .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#jtzrdkizco .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#jtzrdkizco .gt_from_md > :first-child {
  margin-top: 0;
}

#jtzrdkizco .gt_from_md > :last-child {
  margin-bottom: 0;
}

#jtzrdkizco .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#jtzrdkizco .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#jtzrdkizco .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#jtzrdkizco .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#jtzrdkizco .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#jtzrdkizco .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#jtzrdkizco .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#jtzrdkizco .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#jtzrdkizco .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#jtzrdkizco .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#jtzrdkizco .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#jtzrdkizco .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#jtzrdkizco .gt_left {
  text-align: left;
}

#jtzrdkizco .gt_center {
  text-align: center;
}

#jtzrdkizco .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#jtzrdkizco .gt_font_normal {
  font-weight: normal;
}

#jtzrdkizco .gt_font_bold {
  font-weight: bold;
}

#jtzrdkizco .gt_font_italic {
  font-style: italic;
}

#jtzrdkizco .gt_super {
  font-size: 65%;
}

#jtzrdkizco .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="jtzrdkizco" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Essendon vs. Carlton</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 27 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/Carlton_FC_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Sam Docherty</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">24&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/Carlton_FC_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">David Cuningham</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">35&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/Carlton_FC_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Levi Casboult</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">42&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#zobbniycws .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#zobbniycws .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#zobbniycws .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#zobbniycws .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#zobbniycws .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#zobbniycws .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#zobbniycws .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#zobbniycws .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#zobbniycws .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#zobbniycws .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#zobbniycws .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#zobbniycws .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#zobbniycws .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#zobbniycws .gt_from_md > :first-child {
  margin-top: 0;
}

#zobbniycws .gt_from_md > :last-child {
  margin-bottom: 0;
}

#zobbniycws .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#zobbniycws .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#zobbniycws .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#zobbniycws .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#zobbniycws .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#zobbniycws .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#zobbniycws .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#zobbniycws .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#zobbniycws .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#zobbniycws .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#zobbniycws .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#zobbniycws .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#zobbniycws .gt_left {
  text-align: left;
}

#zobbniycws .gt_center {
  text-align: center;
}

#zobbniycws .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#zobbniycws .gt_font_normal {
  font-weight: normal;
}

#zobbniycws .gt_font_bold {
  font-weight: bold;
}

#zobbniycws .gt_font_italic {
  font-style: italic;
}

#zobbniycws .gt_super {
  font-size: 65%;
}

#zobbniycws .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="zobbniycws" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Gold Coast vs. Fremantle</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 27 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/7/7d/Gold_Coast_Suns_AFL_Logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Matthew Rowell</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">45&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/7/7d/Gold_Coast_Suns_AFL_Logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jarrod Witts</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">49&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/7/7d/Gold_Coast_Suns_AFL_Logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Touk Miller</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">33&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#leliorwkfc .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#leliorwkfc .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#leliorwkfc .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#leliorwkfc .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#leliorwkfc .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#leliorwkfc .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#leliorwkfc .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#leliorwkfc .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#leliorwkfc .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#leliorwkfc .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#leliorwkfc .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#leliorwkfc .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#leliorwkfc .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#leliorwkfc .gt_from_md > :first-child {
  margin-top: 0;
}

#leliorwkfc .gt_from_md > :last-child {
  margin-bottom: 0;
}

#leliorwkfc .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#leliorwkfc .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#leliorwkfc .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#leliorwkfc .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#leliorwkfc .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#leliorwkfc .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#leliorwkfc .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#leliorwkfc .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#leliorwkfc .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#leliorwkfc .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#leliorwkfc .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#leliorwkfc .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#leliorwkfc .gt_left {
  text-align: left;
}

#leliorwkfc .gt_center {
  text-align: center;
}

#leliorwkfc .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#leliorwkfc .gt_font_normal {
  font-weight: normal;
}

#leliorwkfc .gt_font_bold {
  font-weight: bold;
}

#leliorwkfc .gt_font_italic {
  font-style: italic;
}

#leliorwkfc .gt_super {
  font-size: 65%;
}

#leliorwkfc .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="leliorwkfc" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Brisbane Lions vs. Adelaide</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 28 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Hugh McCluggage</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">62&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Lachie Neale</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">45&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jarrod Berry</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">39&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#sfvdxxydqt .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#sfvdxxydqt .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#sfvdxxydqt .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#sfvdxxydqt .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#sfvdxxydqt .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#sfvdxxydqt .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#sfvdxxydqt .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#sfvdxxydqt .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#sfvdxxydqt .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#sfvdxxydqt .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#sfvdxxydqt .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#sfvdxxydqt .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#sfvdxxydqt .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#sfvdxxydqt .gt_from_md > :first-child {
  margin-top: 0;
}

#sfvdxxydqt .gt_from_md > :last-child {
  margin-bottom: 0;
}

#sfvdxxydqt .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#sfvdxxydqt .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#sfvdxxydqt .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#sfvdxxydqt .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#sfvdxxydqt .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#sfvdxxydqt .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#sfvdxxydqt .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#sfvdxxydqt .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#sfvdxxydqt .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#sfvdxxydqt .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#sfvdxxydqt .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#sfvdxxydqt .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#sfvdxxydqt .gt_left {
  text-align: left;
}

#sfvdxxydqt .gt_center {
  text-align: center;
}

#sfvdxxydqt .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#sfvdxxydqt .gt_font_normal {
  font-weight: normal;
}

#sfvdxxydqt .gt_font_bold {
  font-weight: bold;
}

#sfvdxxydqt .gt_font_italic {
  font-style: italic;
}

#sfvdxxydqt .gt_super {
  font-size: 65%;
}

#sfvdxxydqt .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="sfvdxxydqt" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Melbourne vs. Geelong</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 28 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Cameron Guthrie</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">64&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Patrick Dangerfield</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">39&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/4/4e/Melbournefc.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Angus Brayshaw</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">36&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#ouoqwhuvhe .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#ouoqwhuvhe .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ouoqwhuvhe .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#ouoqwhuvhe .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#ouoqwhuvhe .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ouoqwhuvhe .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ouoqwhuvhe .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#ouoqwhuvhe .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#ouoqwhuvhe .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#ouoqwhuvhe .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#ouoqwhuvhe .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#ouoqwhuvhe .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#ouoqwhuvhe .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#ouoqwhuvhe .gt_from_md > :first-child {
  margin-top: 0;
}

#ouoqwhuvhe .gt_from_md > :last-child {
  margin-bottom: 0;
}

#ouoqwhuvhe .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#ouoqwhuvhe .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#ouoqwhuvhe .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ouoqwhuvhe .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#ouoqwhuvhe .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ouoqwhuvhe .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#ouoqwhuvhe .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#ouoqwhuvhe .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ouoqwhuvhe .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ouoqwhuvhe .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#ouoqwhuvhe .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ouoqwhuvhe .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#ouoqwhuvhe .gt_left {
  text-align: left;
}

#ouoqwhuvhe .gt_center {
  text-align: center;
}

#ouoqwhuvhe .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#ouoqwhuvhe .gt_font_normal {
  font-weight: normal;
}

#ouoqwhuvhe .gt_font_bold {
  font-weight: bold;
}

#ouoqwhuvhe .gt_font_italic {
  font-style: italic;
}

#ouoqwhuvhe .gt_super {
  font-size: 65%;
}

#ouoqwhuvhe .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="ouoqwhuvhe" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Hawthorn vs. North Melbourne</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 28 Jun 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/6/62/Hawthorn-football-club-brand.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Chad Wingard</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">42&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/6/62/Hawthorn-football-club-brand.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Tom Mitchell</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">39&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/f/fc/North_Melbourne_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Todd Goldstein</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">43&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#sotuwhrsga .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#sotuwhrsga .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#sotuwhrsga .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#sotuwhrsga .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#sotuwhrsga .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#sotuwhrsga .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#sotuwhrsga .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#sotuwhrsga .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#sotuwhrsga .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#sotuwhrsga .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#sotuwhrsga .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#sotuwhrsga .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#sotuwhrsga .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#sotuwhrsga .gt_from_md > :first-child {
  margin-top: 0;
}

#sotuwhrsga .gt_from_md > :last-child {
  margin-bottom: 0;
}

#sotuwhrsga .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#sotuwhrsga .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#sotuwhrsga .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#sotuwhrsga .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#sotuwhrsga .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#sotuwhrsga .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#sotuwhrsga .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#sotuwhrsga .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#sotuwhrsga .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#sotuwhrsga .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#sotuwhrsga .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#sotuwhrsga .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#sotuwhrsga .gt_left {
  text-align: left;
}

#sotuwhrsga .gt_center {
  text-align: center;
}

#sotuwhrsga .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#sotuwhrsga .gt_font_normal {
  font-weight: normal;
}

#sotuwhrsga .gt_font_bold {
  font-weight: bold;
}

#sotuwhrsga .gt_font_italic {
  font-style: italic;
}

#sotuwhrsga .gt_super {
  font-size: 65%;
}

#sotuwhrsga .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="sotuwhrsga" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Carlton vs. St Kilda</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Thu 2 Jul 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/St_Kilda_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jack Steele</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">44&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/St_Kilda_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Rowan Marshall</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">39&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/St_Kilda_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jack Billings</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">31&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

## Round 5 2020

-----

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#efhmthcqhl .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#efhmthcqhl .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#efhmthcqhl .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#efhmthcqhl .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#efhmthcqhl .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#efhmthcqhl .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#efhmthcqhl .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#efhmthcqhl .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#efhmthcqhl .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#efhmthcqhl .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#efhmthcqhl .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#efhmthcqhl .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#efhmthcqhl .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#efhmthcqhl .gt_from_md > :first-child {
  margin-top: 0;
}

#efhmthcqhl .gt_from_md > :last-child {
  margin-bottom: 0;
}

#efhmthcqhl .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#efhmthcqhl .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#efhmthcqhl .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#efhmthcqhl .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#efhmthcqhl .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#efhmthcqhl .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#efhmthcqhl .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#efhmthcqhl .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#efhmthcqhl .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#efhmthcqhl .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#efhmthcqhl .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#efhmthcqhl .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#efhmthcqhl .gt_left {
  text-align: left;
}

#efhmthcqhl .gt_center {
  text-align: center;
}

#efhmthcqhl .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#efhmthcqhl .gt_font_normal {
  font-weight: normal;
}

#efhmthcqhl .gt_font_bold {
  font-weight: bold;
}

#efhmthcqhl .gt_font_italic {
  font-style: italic;
}

#efhmthcqhl .gt_super {
  font-size: 65%;
}

#efhmthcqhl .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="efhmthcqhl" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Collingwood vs. Essendon</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Fri 3 Jul 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/8/8b/Essendon_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Dylan Shiel</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">80&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Brodie Grundy</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">35&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/8/8b/Essendon_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jordan Ridley</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">50&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#ywldjpjucm .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#ywldjpjucm .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ywldjpjucm .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#ywldjpjucm .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#ywldjpjucm .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ywldjpjucm .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ywldjpjucm .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#ywldjpjucm .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#ywldjpjucm .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#ywldjpjucm .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#ywldjpjucm .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#ywldjpjucm .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#ywldjpjucm .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#ywldjpjucm .gt_from_md > :first-child {
  margin-top: 0;
}

#ywldjpjucm .gt_from_md > :last-child {
  margin-bottom: 0;
}

#ywldjpjucm .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#ywldjpjucm .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#ywldjpjucm .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ywldjpjucm .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#ywldjpjucm .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ywldjpjucm .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#ywldjpjucm .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#ywldjpjucm .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ywldjpjucm .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ywldjpjucm .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#ywldjpjucm .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ywldjpjucm .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#ywldjpjucm .gt_left {
  text-align: left;
}

#ywldjpjucm .gt_center {
  text-align: center;
}

#ywldjpjucm .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#ywldjpjucm .gt_font_normal {
  font-weight: normal;
}

#ywldjpjucm .gt_font_bold {
  font-weight: bold;
}

#ywldjpjucm .gt_font_italic {
  font-style: italic;
}

#ywldjpjucm .gt_super {
  font-size: 65%;
}

#ywldjpjucm .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="ywldjpjucm" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>West Coast vs. Sydney</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 4 Jul 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/b/b5/West_Coast_Eagles_logo_2017.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Nic Naitanui</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">34&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/b/b5/West_Coast_Eagles_logo_2017.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Elliot Yeo</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">46&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/b/b5/West_Coast_Eagles_logo_2017.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Dom Sheed</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">39&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#dusgolgdep .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#dusgolgdep .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#dusgolgdep .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#dusgolgdep .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#dusgolgdep .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#dusgolgdep .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#dusgolgdep .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#dusgolgdep .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#dusgolgdep .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#dusgolgdep .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#dusgolgdep .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#dusgolgdep .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#dusgolgdep .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#dusgolgdep .gt_from_md > :first-child {
  margin-top: 0;
}

#dusgolgdep .gt_from_md > :last-child {
  margin-bottom: 0;
}

#dusgolgdep .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#dusgolgdep .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#dusgolgdep .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#dusgolgdep .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#dusgolgdep .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#dusgolgdep .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#dusgolgdep .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#dusgolgdep .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#dusgolgdep .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#dusgolgdep .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#dusgolgdep .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#dusgolgdep .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#dusgolgdep .gt_left {
  text-align: left;
}

#dusgolgdep .gt_center {
  text-align: center;
}

#dusgolgdep .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#dusgolgdep .gt_font_normal {
  font-weight: normal;
}

#dusgolgdep .gt_font_bold {
  font-weight: bold;
}

#dusgolgdep .gt_font_italic {
  font-style: italic;
}

#dusgolgdep .gt_super {
  font-size: 65%;
}

#dusgolgdep .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="dusgolgdep" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Geelong vs. Gold Coast</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 4 Jul 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Tom Hawkins</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">41&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Mitch Duncan</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">40&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Joel Selwood</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">29&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#nmsuudgvul .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#nmsuudgvul .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#nmsuudgvul .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#nmsuudgvul .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#nmsuudgvul .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#nmsuudgvul .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#nmsuudgvul .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#nmsuudgvul .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#nmsuudgvul .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#nmsuudgvul .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#nmsuudgvul .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#nmsuudgvul .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#nmsuudgvul .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#nmsuudgvul .gt_from_md > :first-child {
  margin-top: 0;
}

#nmsuudgvul .gt_from_md > :last-child {
  margin-bottom: 0;
}

#nmsuudgvul .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#nmsuudgvul .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#nmsuudgvul .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#nmsuudgvul .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#nmsuudgvul .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#nmsuudgvul .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#nmsuudgvul .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#nmsuudgvul .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#nmsuudgvul .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#nmsuudgvul .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#nmsuudgvul .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#nmsuudgvul .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#nmsuudgvul .gt_left {
  text-align: left;
}

#nmsuudgvul .gt_center {
  text-align: center;
}

#nmsuudgvul .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#nmsuudgvul .gt_font_normal {
  font-weight: normal;
}

#nmsuudgvul .gt_font_bold {
  font-weight: bold;
}

#nmsuudgvul .gt_font_italic {
  font-style: italic;
}

#nmsuudgvul .gt_super {
  font-size: 65%;
}

#nmsuudgvul .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="nmsuudgvul" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Western Bulldogs vs. North Melbourne</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 4 Jul 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/09/Western_Bulldogs_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Josh Bruce</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">42&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/09/Western_Bulldogs_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Caleb Daniel</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">23&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/09/Western_Bulldogs_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jason Johannisen</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">46&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#lqhspwdglm .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#lqhspwdglm .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#lqhspwdglm .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#lqhspwdglm .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#lqhspwdglm .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#lqhspwdglm .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#lqhspwdglm .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#lqhspwdglm .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#lqhspwdglm .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#lqhspwdglm .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#lqhspwdglm .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#lqhspwdglm .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#lqhspwdglm .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#lqhspwdglm .gt_from_md > :first-child {
  margin-top: 0;
}

#lqhspwdglm .gt_from_md > :last-child {
  margin-bottom: 0;
}

#lqhspwdglm .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#lqhspwdglm .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#lqhspwdglm .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#lqhspwdglm .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#lqhspwdglm .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#lqhspwdglm .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#lqhspwdglm .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#lqhspwdglm .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#lqhspwdglm .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#lqhspwdglm .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#lqhspwdglm .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#lqhspwdglm .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#lqhspwdglm .gt_left {
  text-align: left;
}

#lqhspwdglm .gt_center {
  text-align: center;
}

#lqhspwdglm .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#lqhspwdglm .gt_font_normal {
  font-weight: normal;
}

#lqhspwdglm .gt_font_bold {
  font-weight: bold;
}

#lqhspwdglm .gt_font_italic {
  font-style: italic;
}

#lqhspwdglm .gt_super {
  font-size: 65%;
}

#lqhspwdglm .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="lqhspwdglm" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Brisbane Lions vs. Port Adelaide</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 4 Jul 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Lachie Neale</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">72&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jarryd Lyons</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">49&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Hugh McCluggage</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">43&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#ulomcbqxas .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#ulomcbqxas .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ulomcbqxas .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#ulomcbqxas .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#ulomcbqxas .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ulomcbqxas .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ulomcbqxas .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#ulomcbqxas .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#ulomcbqxas .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#ulomcbqxas .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#ulomcbqxas .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#ulomcbqxas .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#ulomcbqxas .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#ulomcbqxas .gt_from_md > :first-child {
  margin-top: 0;
}

#ulomcbqxas .gt_from_md > :last-child {
  margin-bottom: 0;
}

#ulomcbqxas .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#ulomcbqxas .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#ulomcbqxas .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ulomcbqxas .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#ulomcbqxas .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ulomcbqxas .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#ulomcbqxas .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#ulomcbqxas .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ulomcbqxas .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ulomcbqxas .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#ulomcbqxas .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ulomcbqxas .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#ulomcbqxas .gt_left {
  text-align: left;
}

#ulomcbqxas .gt_center {
  text-align: center;
}

#ulomcbqxas .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#ulomcbqxas .gt_font_normal {
  font-weight: normal;
}

#ulomcbqxas .gt_font_bold {
  font-weight: bold;
}

#ulomcbqxas .gt_font_italic {
  font-style: italic;
}

#ulomcbqxas .gt_super {
  font-size: 65%;
}

#ulomcbqxas .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="ulomcbqxas" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Adelaide vs. Fremantle</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 5 Jul 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/ca/Fremantle_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Andrew Brayshaw</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">51&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/ca/Fremantle_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">David Mundy</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">33&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/ca/Fremantle_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Brad Crouch</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">45&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

<div class="row">

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#afubmyvgoh .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#afubmyvgoh .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#afubmyvgoh .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#afubmyvgoh .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#afubmyvgoh .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#afubmyvgoh .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#afubmyvgoh .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#afubmyvgoh .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#afubmyvgoh .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#afubmyvgoh .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#afubmyvgoh .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#afubmyvgoh .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#afubmyvgoh .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#afubmyvgoh .gt_from_md > :first-child {
  margin-top: 0;
}

#afubmyvgoh .gt_from_md > :last-child {
  margin-bottom: 0;
}

#afubmyvgoh .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#afubmyvgoh .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#afubmyvgoh .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#afubmyvgoh .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#afubmyvgoh .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#afubmyvgoh .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#afubmyvgoh .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#afubmyvgoh .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#afubmyvgoh .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#afubmyvgoh .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#afubmyvgoh .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#afubmyvgoh .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#afubmyvgoh .gt_left {
  text-align: left;
}

#afubmyvgoh .gt_center {
  text-align: center;
}

#afubmyvgoh .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#afubmyvgoh .gt_font_normal {
  font-weight: normal;
}

#afubmyvgoh .gt_font_bold {
  font-weight: bold;
}

#afubmyvgoh .gt_font_italic {
  font-style: italic;
}

#afubmyvgoh .gt_super {
  font-size: 65%;
}

#afubmyvgoh .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="afubmyvgoh" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Melbourne vs. Richmond</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 5 Jul 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/35/Richmond_Tigers_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Kane Lambert</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">75&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/35/Richmond_Tigers_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jack Higgins</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">30&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/4/4e/Melbournefc.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Max Gawn</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">43&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#cismkexfmi .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#cismkexfmi .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#cismkexfmi .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#cismkexfmi .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#cismkexfmi .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#cismkexfmi .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#cismkexfmi .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#cismkexfmi .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#cismkexfmi .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#cismkexfmi .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#cismkexfmi .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#cismkexfmi .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#cismkexfmi .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#cismkexfmi .gt_from_md > :first-child {
  margin-top: 0;
}

#cismkexfmi .gt_from_md > :last-child {
  margin-bottom: 0;
}

#cismkexfmi .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#cismkexfmi .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#cismkexfmi .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#cismkexfmi .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#cismkexfmi .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#cismkexfmi .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#cismkexfmi .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#cismkexfmi .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#cismkexfmi .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#cismkexfmi .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#cismkexfmi .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#cismkexfmi .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#cismkexfmi .gt_left {
  text-align: left;
}

#cismkexfmi .gt_center {
  text-align: center;
}

#cismkexfmi .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#cismkexfmi .gt_font_normal {
  font-weight: normal;
}

#cismkexfmi .gt_font_bold {
  font-weight: bold;
}

#cismkexfmi .gt_font_italic {
  font-style: italic;
}

#cismkexfmi .gt_super {
  font-size: 65%;
}

#cismkexfmi .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="cismkexfmi" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>GWS vs. Hawthorn</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 5 Jul 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/07/GWS_Giants_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Nick Haynes</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">47&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/07/GWS_Giants_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Josh Kelly</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">49&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/07/GWS_Giants_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Harry Perryman</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">43&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

<div class="col-md-4">

<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Chivo, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#pvgljadjyk .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#pvgljadjyk .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#pvgljadjyk .gt_title {
  color: #333333;
  font-size: 12px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#pvgljadjyk .gt_subtitle {
  color: #333333;
  font-size: 8px;
  font-weight: lighter;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#pvgljadjyk .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#pvgljadjyk .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: transparent;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#pvgljadjyk .gt_col_heading {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#pvgljadjyk .gt_column_spanner_outer {
  color: #333333;
  background-color: white;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#pvgljadjyk .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#pvgljadjyk .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#pvgljadjyk .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: transparent;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#pvgljadjyk .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#pvgljadjyk .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#pvgljadjyk .gt_from_md > :first-child {
  margin-top: 0;
}

#pvgljadjyk .gt_from_md > :last-child {
  margin-bottom: 0;
}

#pvgljadjyk .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#pvgljadjyk .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#pvgljadjyk .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#pvgljadjyk .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#pvgljadjyk .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#pvgljadjyk .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#pvgljadjyk .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#pvgljadjyk .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#pvgljadjyk .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#pvgljadjyk .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#pvgljadjyk .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#pvgljadjyk .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#pvgljadjyk .gt_left {
  text-align: left;
}

#pvgljadjyk .gt_center {
  text-align: center;
}

#pvgljadjyk .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#pvgljadjyk .gt_font_normal {
  font-weight: normal;
}

#pvgljadjyk .gt_font_bold {
  font-weight: bold;
}

#pvgljadjyk .gt_font_italic {
  font-style: italic;
}

#pvgljadjyk .gt_super {
  font-size: 65%;
}

#pvgljadjyk .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="pvgljadjyk" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  <thead class="gt_header">
    <tr>
      <th colspan="4" class="gt_heading gt_title gt_font_normal" style>Geelong vs. Brisbane Lions</th>
    </tr>
    <tr>
      <th colspan="4" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Thu 9 Jul 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Votes</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Prob</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Patrick Dangerfield</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">59&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Joel Selwood</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">35&percnt;</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Tom Hawkins</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
      <td class="gt_row gt_right" style="background-color: #F0F0F0; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">35&percnt;</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

</p>

<script>
function openCity(evt, cityName) {
  var i, tabcontent, tablinks;
  tabcontent = document.getElementsByClassName("tabcontent");
  for (i = 0; i < tabcontent.length; i++) {
    tabcontent[i].style.display = "none";
  }
  tablinks = document.getElementsByClassName("tablinks");
  for (i = 0; i < tablinks.length; i++) {
    tablinks[i].className = tablinks[i].className.replace(" active", "");
  }
  document.getElementById(cityName).style.display = "block";
  evt.currentTarget.className += " active";
}

// Get the element with id="defaultOpen" and click on it
document.getElementById("defaultOpen").click();
</script>

</body>
