
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
                border-radius:4px;
            }
            #status{
                color:black;
            }
            input{
                width:10%;
            }
            label{
                vertical-align:top;
            }
            textarea {
                vertical-align:top;
                min-width: 45%;
                height: 150px;
                margin-bottom: 10px;
                border: 1px solid #ccc;
                border-radius: 4px;
                padding: 10px;
            }
            #profile_pic{
            }
            #submit{
                border:1px solid black;
                border-radius:2px;
                background-color:#FFDAC8;
                color:black;
            }
        </style>
        <h1 class="aaa">留下你改寫他們命運的痕跡吧！</h1>
        <h2 class="bbb">試試你能抽到哪個紅樓夢角色的詩!</h2>
        <!--https://formsubmit.co/luoyiru467@gmail.com-->
        <!--備用:https://formsubmit.app/f/7954fm7gtu-->
        <form id="myform" method="POST" action="https://formsubmit.app/f/xqwntvew6f" enctype="multipart/form-data">
        <label for="class">班級:</label><input type="text" id="class" name="class"><label for="number">座號:</label><input type="text" id="number" name="number"><br>ps:用於紀錄你一共找到了幾個牌子，集滿的人會有小禮物喔~(如果確定不想要禮物可以不填)<br>
        <label for="story">敘寫你的故事吧!（非必填）</label><textarea id="story" name="story" placeholder="Write somthing.."></textarea><br>
        <label for="profile_pic">請上傳圖片:（必填）</label><input type="file" id="profile_pic" name="profile_pic" accept=".jpg, .jpeg, .png" required><br>
        <input type="submit" id="submit">
        <p id="status" role="status">要先上傳圖片才能抽籤喔~</p>
        </form>
        <button class="button1" onclick="printArandomPoam()">按下抽取</button>
        <script>
            const form = document.getElementById("myform");
            const statusText = document.getElementById("status");
            const submitBtn = form.querySelector('input[type="submit"]');
            const drawBtn = document.querySelector(".button1");
            let everSubmit = false;
            drawBtn.disabled = true;
            form.addEventListener("submit", async function(event) {
                event.preventDefault();
                if (submitBtn.disabled) return;
                submitBtn.disabled = true;
                //statusText.textContent = "投稿傳送中，請稍候……";
                try {
                    const formData = new FormData(form);
                    const response = await fetch(form.action, {
                        method: "POST",
                        headers: {
                            "Accept": "application/json"
                        },
                        body: formData
                    });
                    const data = await response.json();
                    if (!response.ok || data.ok !== true) {
                        throw new Error(
                            data.error?.message || data.message || "提交失敗"
                        );
                    }
                    everSubmit = true;
                    drawBtn.disabled = false;
                    statusText.textContent="上傳成功！可以抽啦！";
                    form.reset();
                } catch (error) {
                    console.error("錯誤：", error);
                    statusText.textContent="上傳沒有成功，請檢查表單設定或網路後重試";
                } finally {
                    submitBtn.disabled = false;
                }
            });
            /*const Class=document.getElementById("class");
            const number=document.getElementById("number");
            const story=document.getElementById("story");
            const profile_pic=document.getElementById("profile_pic");
            let everSubmit=false;
            const res = await fetch("https://formsubmit.app/f/xqwntvew6f", {
                method: "POST",
                headers: { "Content-Type": "application/json", Accept: "application/json" },
                body: JSON.stringify({ name: "Ada", email: "ada@example.com", message: "Hi!" }),
            });
            const data = await res.json(); // { ok: true, id: "…" } or { ok: false, error: { code, message } }
            form.addEventListener("submit", async function(event) {
                event.preventDefault();
                const formData = new FormData(form);
                try {
                    const response = await fetch(form.action, {
                        method: "POST",
                        body: formData,
                        headers: {
                            "Accept": "application/json"
                        }
                    });
                    if (response.ok) {
                        everSubmit=true;
                        alert("提交成功！");
                        form.reset();
                    } else {
                        alert("提交失敗，請再試一次。");
                    }
                } catch (error) {
                    alert("傳送失敗，請檢查網路或服務設定。");
                    console.error(error);
                }
            });
            fetch("https://formsubmit.co/ajax/luoyiru467@gmail.com", {
                everSubmit=true;
                method: "POST",
                headers: { 
                    'Content-Type': 'application/x-www-form-urlencoded',
                    'Accept': 'application/x-www-form-urlencoded'
                },
                body: JSON.stringify({
                    class: Class,
                    number:number,
                    story:story,
                    picture:profile_pic
                })
            })
            .then(response => response.json())
            .then(data => console.log(data))
            .catch(error => console.log(error));*/
            function getRandomInt(max) {
                return Math.floor(Math.random() * max);
            }
            function printArandomPoam(){
                var name=["詠白海棠-探春","詠白海棠-寶釵","詠白海棠-寶玉","詠白海棠-黛玉","詠白海棠-湘雲(1)","詠白海棠-湘雲(2)","黛玉、寶釵判詞","賈元春判詞"]
                var poam1=["斜陽寒草帶重門，苔翠盈鋪雨後盆。","珍重芳姿晝掩門，自攜手甕灌苔盆。","秋容淺淡映重門，七節攢成雪滿盆。","半卷湘簾半掩門，碾冰為土玉為盆。","神仙昨日降都門，種得藍田玉一盆。","蘅芷階通蘿薜門，也宜牆角也宜盆。","可嘆停機德，","二十年來辨是非，"]
                var poam2=["玉是精神難比潔，雪為肌骨易銷魂。","胭脂洗出秋階影，冰雪招來露砌魂。","出浴太真冰作影，捧心西子玉為魂。","偷來梨蕊三分白，借得梅花一縷魂。","自是霜娥偏愛冷，非關倩女亦離魂。","花因喜潔難尋偶，人為悲秋易斷魂。","堪憐詠絮才。","榴花開處照宮闈。"]
                var poam3=["芳心一點嬌無力，倩影三更月有痕。","淡極始知花更艷，愁多焉得玉無痕。","曉風不散愁千點，宿雨還添淚一痕。","月窟仙人縫縞袂，秋閨怨女拭啼痕。","秋陰捧出何方雪，雨漬添來隔宿痕。","玉燭滴幹風裡淚，晶簾隔破月中痕。","玉帶林中掛，","三春爭及初春景，"]
                var poam4=["莫謂縞仙能羽化，多情伴我詠黃昏。","欲償白帝憑清潔，不語婷婷日又昏。","獨倚畫欄如有意，清砧怨笛送黃昏。","嬌羞默默同誰訴，倦倚西風夜已昏。","卻喜詩人吟不倦，豈令寂寞度朝昏。","幽情慾向嫦娥訴，無奈虛廊夜色昏。","金簪雪裡埋。","虎兕相逢大夢歸。"]
                var ans=getRandomInt(8)
                console.log(ans)
                if(everSubmit){
                document.getElementById("1s").textContent=name[ans]
                document.getElementById("2s").textContent=poam1[ans]
                document.getElementById("3s").textContent=poam2[ans]
                document.getElementById("4s").textContent=poam3[ans]
                document.getElementById("5s").textContent=poam4[ans]
                }
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
