
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
            .s6{
                display:none;
                justify-content:center;
                margin-top:10px;
            }
            .s7{
                display:none;
                justify-content:center;
                margin-top:10px;
            }
            .s8{
                display:none;
                justify-content:center;
                margin-top:10px;
            }
            .s9{
                display:none;
                justify-content:center;
                margin-top:10px;
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
                var name=["詠白海棠-探春","詠白海棠-寶釵","詠白海棠-寶玉","詠白海棠-黛玉","詠白海棠-湘雲(1)","詠白海棠-湘雲(2)","黛玉、寶釵判詞","賈元春判詞","賈探春判詞","史湘雲判詞","妙玉判詞","賈迎春判詞","賈惜春判詞","王熙鳳判詞","賈巧姐判詞","李紈判詞","秦可卿判詞","第一回石頭偈語"]
                var poam1=["斜陽寒草帶重門，苔翠盈鋪雨後盆。","珍重芳姿晝掩門，自攜手甕灌苔盆。","秋容淺淡映重門，七節攢成雪滿盆。","半卷湘簾半掩門，碾冰為土玉為盆。","神仙昨日降都門，種得藍田玉一盆。","蘅芷階通蘿薜門，也宜牆角也宜盆。","可嘆停機德，","二十年來辨是非，","才自精明志自高，","富貴又何為？","欲潔何曾潔？","子系中山狼，","勘破三春景不長，","凡鳥偏從末世來，","勢敗休云貴，","桃李春風結子完，","情天情海幻情身，","無才可去補蒼天，"]
                var poam2=["玉是精神難比潔，雪為肌骨易銷魂。","胭脂洗出秋階影，冰雪招來露砌魂。","出浴太真冰作影，捧心西子玉為魂。","偷來梨蕊三分白，借得梅花一縷魂。","自是霜娥偏愛冷，非關倩女亦離魂。","花因喜潔難尋偶，人為悲秋易斷魂。","堪憐詠絮才。","榴花開處照宮闈。","生於末世運偏消。","襁褓之間父母違。","雲空未必空。","得志便猖狂。","緇衣頓改昔年妝。","都知愛慕此生才。","家亡莫論親。","到頭誰似一盆蘭？","情既相逢必主淫。","枉入紅塵若許年。"]
                var poam3=["芳心一點嬌無力，倩影三更月有痕。","淡極始知花更艷，愁多焉得玉無痕。","曉風不散愁千點，宿雨還添淚一痕。","月窟仙人縫縞袂，秋閨怨女拭啼痕。","秋陰捧出何方雪，雨漬添來隔宿痕。","玉燭滴幹風裡淚，晶簾隔破月中痕。","玉帶林中掛，","三春爭及初春景，","清明涕送江邊望，","展眼弔斜暉，","可憐金玉質，","金閨花柳質，","可憐秀戶侯門女，","一從二令三人木，","偶因濟村婦，","如冰水好空相妒，","漫言不肖皆榮出，","此係身前身後事，"]
                var poam4=["莫謂縞仙能羽化，多情伴我詠黃昏。","欲償白帝憑清潔，不語婷婷日又昏。","獨倚畫欄如有意，清砧怨笛送黃昏。","嬌羞默默同誰訴，倦倚西風夜已昏。","卻喜詩人吟不倦，豈令寂寞度朝昏。","幽情慾向嫦娥訴，無奈虛廊夜色昏。","金簪雪裡埋。","虎兕相逢大夢歸。","千里東風一夢遙。","湘江水逝楚雲飛。","終陷淖泥中！","一載赴黃粱。","獨臥青燈古佛旁。","哭向金陵事更哀。","巧得遇恩人。","枉與他人作笑談。","造釁開端實在寧。","倩誰記去作奇傳？"]
                var poam19=["好了歌","世人都曉神仙好，唯有功名忘不了；","古今將相在何方？荒塚一堆草沒了。","世人都曉神仙好，只有金銀忘不了；","終朝只恨聚無多，及到多時眼閉了。","世人都曉神仙好，只有嬌妻忘不了；","君生日日說恩情，君死又隨人去了。","世人都曉神仙好，只有兒孫忘不了；","癡心父母古來多，孝順兒孫誰見了！"]
                var poam20=["飛鳥各投林","為官的，家業凋零；富貴的，金銀散盡；","有恩的，死裡逃生；無情的，分明報應；","欠命的，命己還；欠淚的，淚已盡；","冤冤相報自非輕，分離聚合皆前定。","欲知命短問前生，老來富貴也真僥倖。","看破的，遁入空門；癡迷的，枉送了性命。","好一似食盡鳥投林，","落了片白茫茫大地真乾淨！"]
                var ans=getRandomInt(20)
                console.log(ans)
                if(ans<19){
                    if(everSubmit){
                    document.getElementById("1s").textContent=name[ans]
                    document.getElementById("2s").textContent=poam1[ans]
                    document.getElementById("3s").textContent=poam2[ans]
                    document.getElementById("4s").textContent=poam3[ans]
                    document.getElementById("5s").textContent=poam4[ans]
                    }
                }else if(ans==19){
                    document.getElementById("6s").style.display="flex"
                    document.getElementById("7s").style.display="flex"
                    document.getElementById("8s").style.display="flex"
                    document.getElementById("9s").style.display="flex"
                    document.getElementById("1s").textContent=poam19[0]
                    document.getElementById("2s").textContent=poam19[1]
                    document.getElementById("3s").textContent=poam19[2]
                    document.getElementById("4s").textContent=poam19[3]
                    document.getElementById("5s").textContent=poam19[4]
                    document.getElementById("6s").textContent=poam19[5]
                    document.getElementById("7s").textContent=poam19[6]
                    document.getElementById("8s").textContent=poam19[7]
                    document.getElementById("9s").textContent=poam19[8]
                }else if(ans==20){
                    document.getElementById("6s").style.display="flex"
                    document.getElementById("7s").style.display="flex"
                    document.getElementById("8s").style.display="flex"
                    document.getElementById("1s").textContent=poam20[0]
                    document.getElementById("2s").textContent=poam20[1]
                    document.getElementById("3s").textContent=poam20[2]
                    document.getElementById("4s").textContent=poam20[3]
                    document.getElementById("5s").textContent=poam20[4]
                    document.getElementById("6s").textContent=poam20[5]
                    document.getElementById("7s").textContent=poam20[6]
                    document.getElementById("8s").textContent=poam20[7]
                }
            }
        </script>
        <p class="s1"><span id="1s"></span></p>
        <p class="s2"><span id="2s"></span></p>
        <p class="s3"><span id="3s"></span></p>
        <p class="s4"><span id="4s"></span></p>
        <p class="s5"><span id="5s"></span></p>
        <p class="s6"><span id="6s"></span></p>
        <p class="s7"><span id="7s"></span></p>
        <p class="s8"><span id="8s"></span></p>
        <p class="s9"><span id="9s"></span></p>
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
