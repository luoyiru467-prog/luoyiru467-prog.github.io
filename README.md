
<html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <style>
            header h1 a{
                color:black !important;
            }
            header ul {
                display: none !important;
            }
            body{
                background-color:#995459;
            }
            p{
                font-size:20px;
                letter-spacing:1px;
                color:#bfc993;
                font-family:DFKai-SB;
                display:flex;
            }
            button{
                display:flex;
            }
            .button1{
                background-color:#FFDAC8;
                font-size:20px;
                width:25%;
                border:solid;
                border-radius:8px;
                color:black;
                font-family:DFKai-SB;
                justify-content:center;
                margin-top:10px;
                margin-left: auto;
                margin-right: auto;
            }
            h1{
                color:black;
                font-family:DFKai-SB;
            }
            h2{ 
                color:black;
                font-family:DFKai-SB;
                display:flex;
            }
            .aaa{
                font-size:26px;
                display:block;
                margin:20px auto;
                width:100%;
                height:auto;
                text-align:center;
            }
            .bbb{
                font-size:22px;
                justify-content:center;
                margin-top:10px;
            }
            .s1{
                justify-content:center;
                margin-top:10px;
                /*right:65%;
                bottom:60%;*/
            }
            .s2{
                justify-content:center;
                margin-top:10px;
                /*right:48%;
                bottom:50%;*/
            }
            .s3{
                justify-content:center;
                margin-top:10px;
                /*right:48%;
                bottom:40%;*/
            }
            .s4{
                justify-content:center;
                margin-top:10px;
                /*right:48%;
                bottom:30%;*/
            }
            .s5{
                justify-content:center;
                margin-top:10px;
                /*right:48%;
                bottom:20%;*/
            }
            /*.iii{
                display: block;
                width: 40%;
                height: auto;
                margin: 20px auto;
                padding: 0;
                border: 0px solid #935555;
                border-radius: 3px;
            }
            .jjj{
                display: block;
                width: 40%;
                height: auto;
                margin: 20px auto;
                padding: 0;
                border: 0px solid #935555;
                border-radius: 3px;
            }*/
            img{
                width:100%;
                padding: 0;
                border: 0px solid #935555;
            }
            .parent{
                display:flex;
            }
            #myform{
                background-color:#E6DE9C;
                border:3px solid black;
            }
            textarea {
                min-width: 45%;
                height: 150px;
                margin-bottom: 10px;
                border: 1px solid #ccc;
                border-radius: 4px;
                padding: 10px;
            }
        </style>
        <h1 class="aaa">和大觀園眾人一起詠白海棠!</h1>
        <h2 class="bbb">試試你能抽到哪個紅樓夢角色的詩!</h2>
        <form id="myform" method="POST" action="https://formsubmit.co/luoyiru467@gmail.com" enctype="multipart/form-data">
        <label for="class">班級:</label>label<input type="text" id="class" name="class"><label for="number">座號:</label><input type="text" id="number" name="number">ps:用於紀錄你一共找到了幾個牌子，最多的人會有小禮物喔~(如果確定不想要禮物可以不填)<br>
        敘寫你的故事吧!<textarea id="story" name="story" placeholder="Write somthing.."></textarea>
        請上傳圖片:<input type="file" id="profile_pic" name="profile_pic" accept=".jpg, .jpeg, .png" required><br>
        <input type="submit">
        </form>
        <button class="button1" onclick="printArandomPoam()">按下抽取</button>
        <script>
            function getRandomInt(max) {
                return Math.floor(Math.random() * max);
            }
            function printArandomPoam(){
                var name=["詠白海棠-探春","詠白海棠-寶釵","詠白海棠-寶玉","詠白海棠-黛玉","詠白海棠-湘雲(1)","詠白海棠-湘雲(2)"]
                var poam1=["斜陽寒草帶重門,苔翠盈鋪雨後盆。","珍重芳姿晝掩門,自攜手甕灌苔盆。","秋容淺淡映重門,七節攢成雪滿盆。","半卷湘簾半掩門,碾冰為土玉為盆。","神仙昨日降都門,種得藍田玉一盆。","蘅芷階通蘿薜門,也宜牆角也宜盆。"]
                var poam2=["玉是精神難比潔,雪為肌骨易銷魂。","胭脂洗出秋階影,冰雪招來露砌魂。","出浴太真冰作影,捧心西子玉為魂。","偷來梨蕊三分白,借得梅花一縷魂。","自是霜娥偏愛冷,非關倩女亦離魂。","花因喜潔難尋偶,人為悲秋易斷魂。"]
                var poam3=["芳心一點嬌無力,倩影三更月有痕。","淡極始知花更艷,愁多焉得玉無痕。","曉風不散愁千點,宿雨還添淚一痕。","月窟仙人縫縞袂,秋閨怨女拭啼痕。","秋陰捧出何方雪,雨漬添來隔宿痕。","玉燭滴幹風裡淚,晶簾隔破月中痕。"]
                var poam4=["莫謂縞仙能羽化,多情伴我詠黃昏。","欲償白帝憑清潔,不語婷婷日又昏。","獨倚畫欄如有意,清砧怨笛送黃昏。","嬌羞默默同誰訴,倦倚西風夜已昏。","卻喜詩人吟不倦,豈令寂寞度朝昏。","幽情慾向嫦娥訴,無奈虛廊夜色昏。"]
                var ans=getRandomInt(6)
                console.log(ans)
                document.getElementById("1s").textContent=name[ans]
                document.getElementById("2s").textContent=poam1[ans]
                document.getElementById("3s").textContent=poam2[ans]
                document.getElementById("4s").textContent=poam3[ans]
                document.getElementById("5s").textContent=poam4[ans]
            }
        </script>
        <p class="s1"><span id="1s"></span></p>
        <p class="s2"><span id="2s"></span></p>
        <p class="s3"><span id="3s"></span></p>
        <p class="s4"><span id="4s"></span></p>
        <p class="s5"><span id="5s"></span></p>
        <div class="parent">
        <div>
        <img src="S__185057304.png">
        </div>
        <div>
        <img src="S__185057303.png">
        </div>
        </div>
    </body>
</html>
