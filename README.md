# K-hall-challl
🌚
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Special Message</title>
<style>
    body {
        margin:0;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        background: radial-gradient(circle at top, #ffdde1, #ee9ca7);
        overflow-x: hidden;
        position: relative;
    }

    /* Glowing shimmer overlay */
    body::before {
        content:"";
        position: fixed;
        top:0; left:0;
        width:100%; height:100%;
        background: linear-gradient(120deg, rgba(255,255,255,0.1), rgba(255,255,255,0.3), rgba(255,255,255,0.1));
        animation: shimmer 8s linear infinite;
        pointer-events:none;
        z-index:0;
    }

    @keyframes shimmer {
        0% {transform: translateX(-100%);}
        100% {transform: translateX(100%);}
    }

    h1 {
        text-align: center;
        margin-top: 40px;
        font-size: 38px;
        background: linear-gradient(90deg, #ff4d6d, #ffb3c1, #ff4d6d);
        background-size: 200% auto;
        color: #fff;
        background-clip: text;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        animation: shine 3s linear infinite;
        position: relative;
        z-index: 1;
    }

    @keyframes shine {
        0% {background-position: 0% center;}
        50% {background-position: 100% center;}
        100% {background-position: 0% center;}
    }

    .message, .password, .nextStep, .paragraph {
        text-align:center;
        margin-top:20px;
        font-size: 20px;
        color:#fff;
        position: relative;
        z-index:1;
    }

    .envelope {
        display:block;
        margin: 40px auto;
        font-size:60px;
        cursor:pointer;
        transition: transform 0.3s;
        position: relative;
        z-index:1;
    }

    .envelope:hover {
        transform: scale(1.2);
    }

    .envelope.clicked {
        text-shadow: 0 0 20px #ff4d6d, 0 0 30px #ffb3c1, 0 0 40px #ff6699;
        animation: glow 1.5s infinite alternate;
    }

    @keyframes glow {
        from {text-shadow: 0 0 10px #ff4d6d, 0 0 15px #ffb3c1;}
        to {text-shadow: 0 0 20px #ff4d6d, 0 0 30px #ffb3c1, 0 0 40px #ff6699;}
    }

    input[type="password"] {
        padding:10px;
        font-size:18px;
        border-radius:5px;
        border:none;
        outline:none;
        text-align:center;
        margin-top:10px;
    }

    button {
        padding:10px 20px;
        font-size:18px;
        margin-left:10px;
        cursor:pointer;
        border-radius:5px;
        border:none;
        background: #ff4d6d;
        color:#fff;
        transition:0.3s;
    }

    button:hover {
        background: #ff6699;
    }

    .paragraph {
        margin:30px auto;
        max-width:90%;
        font-size:18px;
        text-align:left;
        line-height:1.5;
        display:inline-block;
        text-align:left;
        white-space: pre-wrap;
        position: relative;
        z-index:1;
    }

    /* Soft drifting hearts */
    .heart {
        position: fixed;
        font-size: 24px;
        color: #ff4d6d;
        animation: driftUp 12s linear infinite;
        opacity: 0.8;
        z-index:0;
    }

    @keyframes driftUp {
        0% { transform: translateY(100vh) translateX(0) scale(0.6); opacity:0.6;}
        50% { opacity:0.9; }
        100% { transform: translateY(-10vh) translateX(50px) scale(1); opacity:0; }
    }

    /* Soft falling petals */
    .petal {
        position: fixed;
        top: -50px;
        font-size: 20px;
        color: #ffb3c1;
        animation: driftFall 14s linear infinite;
        opacity:0.7;
        z-index:0;
    }

    @keyframes driftFall {
        0% {transform: translateY(-50px) translateX(0) rotate(0deg);}
        50% {opacity:0.9;}
        100% {transform: translateY(110vh) translateX(60px) rotate(360deg); opacity:0;}
    }
</style>
</head>
<body>

<h1>Just some special words for my special one</h1>
<div class="message">Unlock to see 🌚</div>

<div class="envelope" id="envelope" onclick="openStep1()">📩</div>

<div id="step1" style="display:none">
    <div class="message">Enter password to open the secret message:</div>
    <input type="password" id="pass1" placeholder="Password">
    <button onclick="checkPass1()">Unlock</button>
</div>

<div id="step2" style="display:none">
    <div class="message">Sabar kro ruko zaraaaaaa ye bi kolo 👉🏻👈🏻</div>
    <input type="password" id="pass2" placeholder="Password">
    <button onclick="checkPass2()">Unlock</button>
</div>

<div id="step3" style="display:none">
    <div class="message">Enter final password:</div>
    <input type="password" id="pass3" placeholder="Password">
    <button onclick="checkPass3()">Unlock</button>
</div>

<div id="final" class="paragraph" style="display:none"></div>

<script>
    function randomInt(min,max){return Math.floor(Math.random()*(max-min+1)+min);}

    // drifting hearts
    setInterval(()=>{
        let heart=document.createElement('div');
        heart.className='heart';
        heart.style.left=randomInt(0,95)+'vw';
        heart.style.animationDuration = (randomInt(10,16))+'s';
        heart.innerHTML='❤️';
        document.body.appendChild(heart);
        setTimeout(()=>heart.remove(),16000);
    },1000);

    // drifting petals
    setInterval(()=>{
        let petal=document.createElement('div');
        petal.className='petal';
        petal.style.left=randomInt(0,95)+'vw';
        petal.style.animationDuration = (randomInt(12,18))+'s';
        petal.innerHTML='🌹';
        document.body.appendChild(petal);
        setTimeout(()=>petal.remove(),18000);
    },1200);

    function openStep1(){
        document.getElementById("step1").style.display="block";
        document.getElementById("envelope").classList.add("clicked");
    }

    function checkPass1(){
        let p=document.getElementById("pass1").value;
        if(p.toUpperCase()==="ZANOOR"){
            document.getElementById("step2").style.display="block";
            document.getElementById("step1").style.display="none";
        } else alert("Wrong password!");
    }

    function checkPass2(){
        let p=document.getElementById("pass2").value;
        if(p==="28 12 2021"){
            document.getElementById("step3").style.display="block";
            document.getElementById("step2").style.display="none";
        } else alert("Wrong password!");
    }

    function checkPass3(){
        let p=document.getElementById("pass3").value;
        if(p==="2:35"){
            document.getElementById("step3").style.display="none";
            typeParagraph();
        } else alert("Wrong password!");
    }

    function typeParagraph(){
        const text=` Mere ladlyyyyy future begum
Ma jane se pehle ye kahna chahta I promise that
k nikah k bad tm ne Jasa socha hua hm wase life guzre g
Blkay us se b kahin gunah zayda axhe
Ma gurente deta k hmre life same wase h ho g jasa tm chahti jasa hm dono ne mil kr socha hua ❤️
Jasa tm ne muje call pr bataya thaaaaaaa bilkul wasaaa hiiiii
Jasa tm chahti ek ghr ho us ma srf ma or tm<br>
Hm mil kr cooking krein
Ma talwat kru or mere shoulder pr tmra sr<br>
Bilkul asa he ho ga begum
I promise 🤍
Ma talwat pr ke sunao ga tm mere shoulder pr sr rkna 🤍
Dherrr sare batein krein ge hr topic k relatedd
Kabheeee ma bolo gaaa tm sunaaa
Kabhe tm bolna ma suno gaaaa
Sameeeee dressing krein g jaha b jain ge
Tme khd apne hatho se kana kilaua kro ga
Tme khd apne hato se mehndi lagaya kro gaa
Apne hatho se tmre hatho ma churian pehnaya kru ga ❤️
Khd tme rings pehnaya kro ga apne se 🤍
Tmre balo pr brush b ma h kia kru ga 🫠❤️
Hr chzzz hm mil kr krein h
 Bs ma itna kahna chahta jasa tm chahti hm   waseeee h life gusre g mere ladlyyyy begummmmm 🤍
 Tmra hathh kabhii ni chorne wala
 Ekele ma bi nahi or na h sb k smne 🤍
 Begummmm ma tm se behadd pyar krta
 Khd se b zaydaaaaaaaaaaaaaaa
 Maaaa srfff tmraaaaa huuuuuuu
  SRF TMAAAHARAAAA
Begummmm tm bhttt zaydaaaa important ho mereeeee liaaaaaaaa 
Uh know na??
Nahi ptha ta ma bar barrr different wayss se tme btao ga k tm ks qadar imp🫠🤍
 Ma ne srf tmre sth rehnaaaa
 Tmre sth ma ne b itna sb kch sofha hua itna sb kcb 
Or abhe hm dur ho re Allah k raza k lia 
Or tm se dur hona to nihayat h dunyaaaaa ka mushkl tareeeeen kam
Muje aj tak ase mushkllll kse chz ma nahi lageeee jase tm se dur hote hue lagte
Ik kch time k lia dur ho re but uh know na ma tmre bger ek dinnn b nahi reh skta🫠
Itssssss soooo harddd begummmmmmmm to live a day without uh🫠
Tm pleaseeeeeee ase h rehnaaaaaaaaaa 
Tm bhttt zaydaaaa axheeee hooooo bhttttt zayda axheeeee ho tmmmmmmmm
I swear tm bhtttt axheeeeeeeeeeeeeee
Or mere dil ma a kr deko to ksm se mere lia tm dunyaaaa k sb se achiii lrkiiiiiiiiiiiii
Sb se haseeeeeeeeen lrkiiiiii
Sb se alaggggggggggg hoooo
Ahhhhh bs hmesha k lia dur na honaaaa or na muje hne dena 🫠🤍
  Ku k
“ Zindageeee ho mereee tmmmm🥀❤️”
Bhttttt pyar krta tm se begummmm 
Bbttttttttt zaydaaa 
Begummmmmmmmmm muje ne pthaaaaaaaaaaaa ye itneee mhbt kase ai but in realll ye sch haaaaa. Bhtttt muhabt krta hu tm se🥹
Naiii rehna chahta tmre bgerrrrr
Srf tm se nikah krnaaaa
Srf tmre sth rehnaaaa
Srf tm se bateinnn krne
Srf tmre sth hasnaaaaa
Srf tmre srh ronaaaa
Tmre baalon k sth kelnaa 
Hr time tmra hath pakri rkna
Chahe ekele ma ho ya public maaaa and begum
Jab b tm low feel kro to tme deep hug du ga ma or mera shoulder tmre pas he ho gaaaa
Bs mere shoulder pr sr rk kr hr xhzzzz share krna jo kch tmre mind ma chal ra hona hr chz batana or ma tmr better feel krwane k hr A to Z koshish kru ga
Dunyaaaa ka sb seeeeeeeeee qeeemti tohfa ho tm jse ma kona ne chahta js k sth hr chz exp krne
Hr chz srf tmre sth krne🥹
Or ma tmra sth duuu ga
Chahe tmre family tmre dost dunya koi tmra sth na de hr shks tme glt bole but maaaa tmre side pr krw rahu gaaa ye kenne k lia k
Mereeee begummmmm sahiii ha
Tmra hath kabhe ne choro ga
Na ekele ma or na public ma🫠🤍
Begummmmmmm tm please kse chz k tension mat lenaaaaaaaa
Nikah k bad tm jasa chahti wase h life guzre h hm 
Okkk na???????
Ma hmesha tmre sth rahuuuuu ga
Hmesha tmre sth kraaaa rahu gaaa ye
Hmeshaaaaa tme support krta rahu ga 
Nikah k bad agr tmre kse chz ma glti huiiii to sb k smneeee tmra sth h du gaaaaa
Kse ko tmre bare ma glt ne kahne du gaa point out ne krne du ga
Ma tmre sthh kra rahu gaaaa begummmmmm
Kabhe ekala ne choro ga apne begummm ko
Apne seeneee se laga kr rku ga tmeeee
Koi tme kch ne kah skta mere hote hue
Or uh know na agr hmre drmyn nika k bad kabhe koi chori moti lrai hui to hm use private ma sort out kre g kse ko kch ptha ne lage ga
Or tme to ptha na ek to ma drta tm se chup kr kr ma h tmre dant sunta rahu gaaaa tme manao ga even k mere glti na b hui tb b tme manao ga🫠
Ladlyyy tm mereee or hmesha raho g 
Nakhre uthao ga apne ladlyy k maaa
Begummmmmmmmmmm ma tme bht zaydaaa miss kru gaa
Specially un moments ko jab apna sr nechee rk kr tme sun ra hotaaaaaaa or tm muje apne din k bare ma or hr chz share krte ue chz ma bhtt zaydaaa misss kru gaaaa begummm
Bhtt zaydaaaaaaa
Hr chzzz miss kru ga
Hmre lraiyan pr une hm kase sort out krte
Pr kabbe tm muje sunte ghnto tkkk
Kabbe maa
Ye chze ma bhtt miss kru ga begumm🥹🤍
Mera bht dil krta k roz tmre sth bat ho or tme ghntooo tk pure pure rt sunta raho rozzz
Begummmmmmmmm ma bht kch kahna chahta ab b tm seeeeeeee ab muje ne ptha kah pao ga ya nahii
Control rk ra ma khd pr bssssssssssss
 Nikah k bad tme smne bitha kr hr chz btao ga hr chzzzzz
 Controlll zain controllllllll
 Last ma ye kahu ga begumm
 Ma tmraaaa hi hu tm abhe b haq rko muj pr tmra haqq ha srf muj prrrrrrr prhle b ta ab bi ha or ageyy b tmra h haq rahe ga muj prrrrrrr 🤍
 I am all yoursssssss
Or begummmmm ma tmeee bht zaydaaaaa miss kru gaaaaa bhttt zaydaaaa i swear🥹🤍 
Ek reminder re raa
Idk abhe ye sahi ha bolna ya nahii but ma ye sache dil se kahna chata tme k..
  “Za ta sira mina kummmmmmm🫠🤍”
  “Zama tol jahana🌍❤️”
  “Zama zargiyaaaaaaaa🤍”
  “Zama janana❤️”
  “Ta zama akri mena ay❤️”
  “Saranghaeeeeee🥀”
  “Seni soviyorummmm🤍”
  “Love uhhh endlessly begummmmmm🫠🤍”
   And thankyewwwww muje choooose krne k liaaaaa
Muje is qabilll smjneeee k liaaaaaa
Mera sth dene k lia
Muje asa banane k lia🤍
Hr chz k liaaa thankyewwwwww so muchhhhhh
Specially muj pr trust krne k lia
Ye trust ma ne toro ga❤️
And mere hr us chz k lia sorryyyyyyy
Js chz se tm hurt hui🫠
Kabbe tmr hurt ne krna chahta maaaaaa
Khush dekna chahta tme begum🫠
 Ye sare bate smjeeee?????`;

        let i=0;
        const finalDiv=document.getElementById('final');
        finalDiv.style.display="block";
        function typeWriter(){
            if(i<text.length){
                finalDiv.innerHTML+=text.charAt(i);
                i++;
                setTimeout(typeWriter,15);
            }
        }
        typeWriter();
    }
</script>

</body>
</html>
