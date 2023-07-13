---
title: "Challenge"
date: 2023-07-07T15:08:05+02:00
draft: false
---

<script type="text/javascript" src="./jquery.min.js"></script>
<script type="text/javascript" src="./qrcode.js"></script>

<h1 id="title">Titel</h1>
<p id="description">Beschreibung</p>
<p id="playerCount">Personen: </p>
<p id="duration">Dauer: </p>
<p id="level">Level: </p>
<div id="qrcode" style="width:300px; height:300px; margin-top:15px;"></div>


<script type="text/javascript">

var foundChallenge = true;
var id = window.location.href.split('#')[1];
var obj;

if (id == undefined) foundChallenge = false;

if (foundChallenge) {
$.getJSON("challenges.json", function(json) {
    
    // if id's are in order use selector, otherwise search for .id

    if (id >= json.length && id >= 0) {
        foundChallenge = false;
    } else {
        obj = json[id - 1];

        console.log(obj);
        document.getElementById("title").innerHTML = obj["Name der Chellange"];
        document.getElementById("description").innerHTML = obj["Beschreibung"];
        document.getElementById("playerCount").innerHTML = "Personen: " + obj["Anzahl der Mitspieler"];
        document.getElementById("duration").innerHTML = "Dauer: " + obj["Dauer (Minuten)"] + " Minuten";
        document.getElementById("level").innerHTML = "Level: " + obj["Level"];
    }
});
}



    new QRCode(document.getElementById("qrcode"), window.location.href, {
	width : 300,
	height : 300
});
</script>


