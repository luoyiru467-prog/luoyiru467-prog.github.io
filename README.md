# 木石前盟
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>木石前盟</title>
    </head>
    <body>
        <h1>試試你能抽到哪個紅樓夢角色的詩!</h1>
        <button onclick="printArandomPoam()">按下抽取</button>
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
                document.write(name[ans])
                document.write("<br>")
                document.write(poam1[ans])
                document.write("<br>")
                document.write(poam2[ans])
                document.write("<br>")
                document.write(poam3[ans])
                document.write("<br>")
                document.write(poam4[ans])
            }
            
        </script>
        
    </body>
</html>
