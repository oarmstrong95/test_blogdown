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

### Round 1 2020

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
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#vlxbdgsake .gt_subtitle {
  color: #333333;
  font-size: 10px;
  font-weight: initial;
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
  border-bottom-width: 3px;
  border-bottom-color: black;
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

#vlxbdgsake .gt_column_spanner_outer {
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

#vlxbdgsake .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#vlxbdgsake .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#vlxbdgsake .gt_column_spanner {
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
  font-size: 12px;
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
      <th colspan="3" class="gt_heading gt_title gt_font_normal" style>Richmond vs. Carlton</th>
    </tr>
    <tr>
      <th colspan="3" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Thu 19 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1">Player Name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Predicted Votes</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/35/Richmond_Tigers_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Dion Prestia</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/Carlton_FC_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Patrick Cripps</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/35/Richmond_Tigers_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Dustin Martin</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
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
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#zyspnprboy .gt_subtitle {
  color: #333333;
  font-size: 10px;
  font-weight: initial;
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
  border-bottom-width: 3px;
  border-bottom-color: black;
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

#zyspnprboy .gt_column_spanner_outer {
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

#zyspnprboy .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#zyspnprboy .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#zyspnprboy .gt_column_spanner {
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
  font-size: 12px;
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
      <th colspan="3" class="gt_heading gt_title gt_font_normal" style>Western Bulldogs vs. Collingwood</th>
    </tr>
    <tr>
      <th colspan="3" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Fri 20 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1">Player Name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Predicted Votes</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Brodie Grundy</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Scott Pendlebury</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/a6/Collingwood_Football_Club_Logo_%282017%E2%80%93present%29.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Taylor Adams</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
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
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#vjlwhygxbn .gt_subtitle {
  color: #333333;
  font-size: 10px;
  font-weight: initial;
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
  border-bottom-width: 3px;
  border-bottom-color: black;
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

#vjlwhygxbn .gt_column_spanner_outer {
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

#vjlwhygxbn .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#vjlwhygxbn .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#vjlwhygxbn .gt_column_spanner {
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
  font-size: 12px;
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
      <th colspan="3" class="gt_heading gt_title gt_font_normal" style>Essendon vs. Fremantle</th>
    </tr>
    <tr>
      <th colspan="3" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 21 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1">Player Name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Predicted Votes</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/8/8b/Essendon_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Dylan Shiel</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/ca/Fremantle_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Rory Lobb</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/8/8b/Essendon_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Adam Saad</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
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
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#smzbyqcuuq .gt_subtitle {
  color: #333333;
  font-size: 10px;
  font-weight: initial;
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
  border-bottom-width: 3px;
  border-bottom-color: black;
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

#smzbyqcuuq .gt_column_spanner_outer {
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

#smzbyqcuuq .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#smzbyqcuuq .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#smzbyqcuuq .gt_column_spanner {
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
  font-size: 12px;
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
      <th colspan="3" class="gt_heading gt_title gt_font_normal" style>Adelaide vs. Sydney</th>
    </tr>
    <tr>
      <th colspan="3" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 21 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1">Player Name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Predicted Votes</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/af/Sydney_Swans_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Isaac Heeney</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/af/Sydney_Swans_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Luke Parker</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/a/af/Sydney_Swans_Logo_2020.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Josh P. Kennedy</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
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
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#gzehxlxrot .gt_subtitle {
  color: #333333;
  font-size: 10px;
  font-weight: initial;
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
  border-bottom-width: 3px;
  border-bottom-color: black;
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

#gzehxlxrot .gt_column_spanner_outer {
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

#gzehxlxrot .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#gzehxlxrot .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#gzehxlxrot .gt_column_spanner {
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
  font-size: 12px;
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
      <th colspan="3" class="gt_heading gt_title gt_font_normal" style>Greater Western Sydney vs. Geelong</th>
    </tr>
    <tr>
      <th colspan="3" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 21 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1">Player Name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Predicted Votes</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/07/GWS_Giants_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Harry Perryman</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/5f/Geelong_Cats_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Mitch Duncan</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/0/07/GWS_Giants_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Toby Greene</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
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
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#cmlivqizip .gt_subtitle {
  color: #333333;
  font-size: 10px;
  font-weight: initial;
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
  border-bottom-width: 3px;
  border-bottom-color: black;
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

#cmlivqizip .gt_column_spanner_outer {
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

#cmlivqizip .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#cmlivqizip .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#cmlivqizip .gt_column_spanner {
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
  font-size: 12px;
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
      <th colspan="3" class="gt_heading gt_title gt_font_normal" style>Gold Coast vs. Port Adelaide</th>
    </tr>
    <tr>
      <th colspan="3" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sat 21 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1">Player Name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Predicted Votes</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Travis Boak</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Tom Rockliff</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/3/36/Port_Adelaide_Football_Club_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Connor Rozee</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
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
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#exqxxzalta .gt_subtitle {
  color: #333333;
  font-size: 10px;
  font-weight: initial;
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
  border-bottom-width: 3px;
  border-bottom-color: black;
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

#exqxxzalta .gt_column_spanner_outer {
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

#exqxxzalta .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#exqxxzalta .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#exqxxzalta .gt_column_spanner {
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
  font-size: 12px;
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
      <th colspan="3" class="gt_heading gt_title gt_font_normal" style>North Melbourne vs. St Kilda</th>
    </tr>
    <tr>
      <th colspan="3" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 22 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1">Player Name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Predicted Votes</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/f/fc/North_Melbourne_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Ben Cunnington</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/f/fc/North_Melbourne_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jared Polec</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/5/58/St_Kilda_FC_logo.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Zak Jones</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
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
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#qphyfsidli .gt_subtitle {
  color: #333333;
  font-size: 10px;
  font-weight: initial;
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
  border-bottom-width: 3px;
  border-bottom-color: black;
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

#qphyfsidli .gt_column_spanner_outer {
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

#qphyfsidli .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#qphyfsidli .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#qphyfsidli .gt_column_spanner {
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
  font-size: 12px;
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
      <th colspan="3" class="gt_heading gt_title gt_font_normal" style>Hawthorn vs. Brisbane Lions</th>
    </tr>
    <tr>
      <th colspan="3" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 22 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1">Player Name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Predicted Votes</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/6/62/Hawthorn-football-club-brand.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Chad Wingard</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/c/c7/Brisbane_Lions_logo_2010.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Lachie Neale</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/6/62/Hawthorn-football-club-brand.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Shaun Burgoyne</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
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
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#ahzguehngf .gt_subtitle {
  color: #333333;
  font-size: 10px;
  font-weight: initial;
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
  border-bottom-width: 3px;
  border-bottom-color: black;
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

#ahzguehngf .gt_column_spanner_outer {
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

#ahzguehngf .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#ahzguehngf .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#ahzguehngf .gt_column_spanner {
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
  font-size: 12px;
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
      <th colspan="3" class="gt_heading gt_title gt_font_normal" style>West Coast vs. Melbourne</th>
    </tr>
    <tr>
      <th colspan="3" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Sun 22 Mar 2020</th>
    </tr>
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1"></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1">Player Name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">Predicted Votes</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/4/4e/Melbournefc.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Jack Viney</td>
      <td class="gt_row gt_right" style="background-color: #80DF7C; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">3</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/b/b5/West_Coast_Eagles_logo_2017.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Andrew Gaff</td>
      <td class="gt_row gt_right" style="background-color: #C3F0BD; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">2</td>
    </tr>
    <tr>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;"><img src="https://upload.wikimedia.org/wikipedia/en/b/b5/West_Coast_Eagles_logo_2017.svg" style="height:25px;"></td>
      <td class="gt_row gt_left" style="border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">Liam Ryan</td>
      <td class="gt_row gt_right" style="background-color: #FFFFFF; color: #000000; border-bottom-width: 2px; border-bottom-style: solid; border-bottom-color: transparent;">1</td>
    </tr>
  </tbody>
  
  
</table></div>

</div>

</div>

</p>

</div>

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
