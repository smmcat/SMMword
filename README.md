<!DOCTYPE html>
<html lang="zh-CN">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>日历</title>
    <style media="screen and (min-width: 640px)">
        * {
            list-style: none;
            margin: 0;
            padding: 0;
            user-select: none;
        }

        .monthBox {
            margin: 100px auto;
            box-sizing: border-box;
            width: 640px;
            padding: 20px 10px;
            overflow: hidden;
            background-color: #cfedfc;
            border-radius: 10px;
            box-shadow: 2px 2px 10px #4e4e4e;
        }

        .monthBox select {
            border: 1px solid #66cc;
            height: 30px;
            width: 100px;
            text-align: center;
            color: brown;
        }

        .monthBox ul {
            display: flex;
            overflow: hidden;
            flex-wrap: wrap;
            justify-content: left;
            text-align: center;
            color: #fff;
            font-size: 18px;
            background-color: #fff;
            box-shadow: 0px 0px 2px #4e4e4e;
            padding: 5px 0px;
        }

        .monthBox ul li {
            position: relative;
            height: 70px;
            width: 13%;
            background-color: #042536;
            flex-shrink: 0;
            margin: 2.95px;
            line-height: 70px;
            font-size: 27px;
            border: 1px solid #66cc;
            transition: all 0.4s;
        }

        .monthBox ul li:hover p {
            height: 100%;
            border: 0;
        }

        .monthBox ul li:hover {
            background-color: #09374e;
            transform: scale(1.04);
            z-index: 9999;
        }

        .monthBox .weekBox {
            margin-top: 20px;
            margin-bottom: 5px;
        }

        .monthBox .weekBox li {
            font-size: 12px;
            height: 30px;
            line-height: 30px;
        }

        .monthBox .weekBox li:hover {
            background-color: #042536;
            transform: scale(1);
        }

        .airBox {
            width: 13%;
            background-color: transparent !important;
            flex-shrink: 0;
            margin: 2.95px;
            line-height: 70px;
            font-size: 27px;
            border: 1px solid transparent !important;
        }

        /* 事项lun提醒栏 */
        .monthBox ul li p {
            position: absolute;
            display: block;
            top: 0;
            left: 0;
            text-align: center;
            width: 100%;
            height: 0px;
            border-bottom: 5px solid orange;
            overflow: hidden;
            line-height: 27px;
            font-size: 12px;
            transition: all 0.5s;

        }

        .monthBox ul li p span {
            margin-top: 2px;
            display: block;
            font-size: 12px;
            line-height: 12px;

        }

        .monthBox ul li p:hover {
            z-index: 999;
        }

        /* 事项提醒栏 */
        .monthBox ul li p::before {
            content: '提醒事项';
        }

        /* 今日事件 */
        .nowHelpBox {
            display: none;
            position: fixed;
            width: 460px;
            padding: 0px 20px;
            height: 309px;
            border: 2px solid #66cc;
            top: 50%;
            left: 50%;
            background-color: #fff;
            border-radius: 20px;
            transform: translate(-50%, -50%);
            z-index: 99999;
            overflow: hidden;
            text-align: center;
        }

        .nowHelpBox .title {
            position: absolute;
            top: 0; 
            left: 0;
            height: 50px;
            width: 100%;
            background-color: #66ccff;

        }

        .nowHelpBox h3 {
            margin: 70px 0 20px 0;
            color: green;
            font-size: 25px;
        }

        .nowHelpBox p {
            font-size: 20px;
            margin-bottom: 50px;
        }

        .nowHelpBox button {
            border: 0;
            width: 140px;
            height: 40px;
            background: #66cc;
            color: #fff;
        }
    </style>
    <style media="screen and (max-width: 640px)">
        * {
            list-style: none;
            margin: 0;
            padding: 0;
            user-select: none;
        }

        .monthBox {
            margin: 50px auto;
            box-sizing: border-box;
            width: 90%;
            padding: 10px 5px;
            overflow: hidden;
            background-color: #cfedfc;
            border-radius: 10px;
            box-shadow: 2px 2px 10px #4e4e4e;
        }

        .monthBox select {
            border: 1px solid #66cc;
            height: 30px;
            width: 23%;
            text-align: center;
            color: brown;
        }

        .monthBox ul {
            display: flex;
            overflow: hidden;
            flex-wrap: wrap;
            justify-content: left;
            text-align: center;
            color: #fff;
            font-size: 18px;
            background-color: #fff;
            box-shadow: 0px 0px 2px #4e4e4e;
            padding: 5px 0px;
        }

        .monthBox ul li {
            position: relative;
            height: 40px;
            width: 13%;
            background-color: #042536;
            flex-shrink: 0;
            margin: 1px;
            line-height: 40px;
            font-size: 27px;
            border: 1px solid #66cc;
        }

        .monthBox ul li:hover {
            background-color: #09374e;
        }

        .monthBox .weekBox {
            margin-top: 20px;
            margin-bottom: 5px;
        }

        .monthBox .weekBox li {
            position: relative;
            font-size: 12px;
            height: 30px;
            line-height: 30px;
        }

        .monthBox .weekBox li:hover p {
            background-color: #042536;
        }

        .airBox {
            width: 13%;
            background-color: transparent !important;
            flex-shrink: 0;
            margin: 1px;
            line-height: 40px;
            font-size: 27px;
            border: 1px solid transparent !important;
        }

        /* 事项提醒栏 */
        .monthBox ul li p {
            position: absolute;
            display: block;
            top: 0;
            left: 0;
            text-align: center;
            width: 100%;
            height: 0px;
            border-bottom: 5px solid orange;
            background-color: orange;
            overflow: hidden;
            line-height: 12px;
            font-size: 12px;
            transition: all 0.5s;

        }

        .monthBox ul li p span {
            margin-top: 2px;
            display: block;
            font-size: 12px;
            margin-top: 8px;
            line-height: 12px;

        }

        .monthBox ul li p:hover {
            z-index: 999;
        }

        /* 事项提醒栏 */
        .monthBox ul li p::before {
            content: '💡';
        }

        .monthBox ul li p::-webkit-scrollbar {
            display: none;
        }

        .monthBox ul li:hover p {
            height: 100%;
            overflow: scroll;
            border-bottom: 1px solid orange;
        }

        /* 今日事件Lun */
        .nowHelpBox {
            display: none;
            position: fixed;
            width: 70%;
            height: 160px;
            border: 2px solid #66cc;
            top: 80%;
            left: 50%;
            background-color: #fff;
            border-radius: 10px;
            transform: translate(-50%, -50%);
            z-index: 99999;
            overflow: hidden;
            text-align: center;
        }

        .nowHelpBox .title {
            position: absolute;
            top: 0;
            left: 0;
            height: 20px;
            width: 100%;
            background-color: #66ccff;

        }

        .nowHelpBox h3 {
            margin: 26px 0 20px 0;
            color: green;
            font-size: 18px;
        }

        .nowHelpBox p {
            font-size: 16px;
            margin-bottom: 10px;
        }

        .nowHelpBox button {
            border: 0;
            width: 110px;
            height: 40px;
            background: #66cc;
            color: #fff;
        }
    </style>
</head>

<body>
    <div class="nowHelpBox">
        <div class="title"></div>
        <h3>今日存在事件</h3>
        <p class="nowHelpContent">-</p>
        <button>好的我明白了</button>
    </div>
    <div class="monthBox">
        <select class="yearType">
            <option value="2000">2000年</option>
            <option value="2001">2001年</option>
            <option value="2002">2002年</option>
            <option value="2003">2003年</option>
            <option value="2004">2004年</option>
            <option value="2005">2005年</option>
            <option value="2006">2006年</option>
            <option value="2007">2007年</option>
            <option value="2008">2008年</option>
            <option value="2009">2009年</option>
            <option value="2010">2010年</option>
            <option value="2011">2011年</option>
            <option value="2012">2012年</option>
            <option value="2013">2013年</option>
            <option value="2014">2014年</option>
            <option value="2015">2015年</option>
            <option value="2016">2016年</option>
            <option value="2017">2017年</option>
            <option value="2018">2018年</option>
            <option value="2019">2019年</option>
            <option value="2020">2020年</option>
            <option value="2021">2021年</option>
            <option value="2022">2022年</option>
            <option value="2023">2023年</option>
            <option value="2024">2024年</option>
            <option value="2025">2025年</option>
            <option value="2026">2026年</option>
            <option value="2027">2027年</option>
            <option value="2028">2028年</option>
            <option value="2029">2029年</option>
            <option value="2030">2030年</option>
            <option value="2031">2031年</option>
            <option value="2032">2032年</option>
            <option value="2033">2033年</option>
            <option value="2034">2034年</option>
            <option value="2035">2035年</option>
            <option value="2036">2036年</option>
            <option value="2037">2037年</option>
            <option value="2038">2038年</option>
            <option value="2039">2039年</option>
            <option value="2040">2040年</option>
            <option value="2041">2041年</option>
            <option value="2042">2042年</option>
            <option value="2043">2043年</option>
            <option value="2044">2044年</option>
            <option value="2045">2045年</option>
            <option value="2046">2046年</option>
            <option value="2047">2047年</option>
            <option value="2048">2048年</option>
            <option value="2049">2049年</option>
        </select>
        <select class="monthType">
            <option value="1">1月份</option>
            <option value="2">2月份</option>
            <option value="3">3月份</option>
            <option value="4">4月份</option>
            <option value="5">5月份</option>
            <option value="6">6月份</option>
            <option value="7">7月份</option>
            <option value="8">8月份</option>
            <option value="9">9月份</option>
            <option value="10">10月份</option>
            <option value="11">11月份</option>
            <option value="12">12月份</option>
        </select>
        <ul class="weekBox">
            <li>星期日</li>
            <li>星期一</li>
            <li>星期二</li>
            <li>星期三</li>
            <li>星期四</li>
            <li>星期五</li>
            <li>星期六</li>
        </ul>
        <ul id="monthliBox">
        </ul>
        <script>
            //提醒事项 示例数据
            let matterData = [
                { year: 2022, month: 1, day: 7, matter: '滑雪' },
                { year: 2022, month: 1, day: 8, matter: '上机考试'},
                { year: 2022, month: 1, day: 9, matter: '上机考试'},
                { year: 2022, month: 1, day: 10, matter: '上机考试'},
                { year: 2022, month: 1, day: 11, matter: '上机考试'},
                { year: 2022, month: 1, day: 12, matter: '上机考试'},
                { year: 2022, month: 1, day: 13, matter: '上机考试'},
                { year: 2022, month: 1, day: 14, matter: '上机交作业'},
                { year: 2022, month: 2, day: 17, matter: '返校' },
            ]

            //绑定元素
            let monthbox = document.querySelector('.monthBox');
            let monthliBox = monthbox.querySelector('#monthliBox');
            let monthType = monthbox.querySelector('.monthType');
            let yearType = monthbox.querySelector('.yearType');
            let nowHelp = document.querySelector('.nowHelpBox');
            let nowHelpContent = document.querySelector('.nowHelpContent');
            let offNowHelp = nowHelp.querySelector('button');

            //初始化选中
            let nowMonth = new Date().getMonth() + 1;
            let nowYear = new Date().getFullYear();
            let nowDay = new Date().getDate();
            yearType.value = nowYear;
            monthType.value = nowMonth;

            

            //检测今日是否有事件 若有 显示今日事件提示框
            for (let i = 0; i < matterData.length; i++) {
                if (matterData[i].year == nowYear && matterData[i].month == nowMonth && matterData[i].day == nowDay) {
                    nowHelp.style.display = 'block';
                    nowHelpContent.innerHTML = matterData[i].matter;
                }
            }
            //关闭 今日事件提示框
            offNowHelp.addEventListener('click', function () {
                nowHelp.style.display = 'none';
            })

            //预执行
            buildmonthLi(yearType.value, monthType.value);

            //判断润年
            function leapYear(year) {
                if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
                    return true;
                } else {
                    return false;
                }
            }


            //判断 传过来的 年份 月份 返回月份天数
            function checkSolarmonth(year, month) {
                const maxmonthbox = [1, 3, 5, 7, 8, 10, 12];
                let day = 30;
                if (leapYear(year)) {
                    if (month == 2) {
                        return 29;
                    } else {
                        for (let i = 0; i < maxmonthbox.length; i++) {
                            if (month == maxmonthbox[i]) {
                                day = 31;
                            }
                        }
                    }
                } else {
                    if (month == 2) {
                        return 28;
                    } else {
                        for (let i = 0; i < maxmonthbox.length; i++) {
                            if (month == maxmonthbox[i]) {
                                day = 31;
                            }
                        }
                    }
                }
                return day;
            }

            //建造月份 li 盒子
            function buildmonthLi(year, month) {
                //---------------------------------
                //检测是否存在事项提醒
                let DataType = checkForMatter();
                //获取当年当月事件下 的下标
                let Type = DataType.splice(0, 1)[0];
                //---------------------------------
                //循环 建造 空格子 用于格式化
                let airBoxLen = oneDay(year, month, 1);
                if (airBoxLen) {
                    for (let i = 0; i < airBoxLen; i++) {
                        let airBox = document.createElement('li');
                        airBox.className = 'airBox';
                        monthliBox.appendChild(airBox);
                    }
                }
                //循环 建造 日盒子
                for (let i = 1; i <= checkSolarmonth(year, month); i++) {
                    let monthli = document.createElement('li');
                    monthli.innerHTML = i;
                    monthli.index = i;
                    if (Type) {
                        for (let k = 0; k < DataType.length; k++) {
                            if (i == matterData[DataType[k]].day) {
                                builCatBox(monthli, DataType[k]);
                            }
                        }
                    }
                    monthliBox.appendChild(monthli);
                }
            }

            //日期下拉框改变内容事件
            yearType.addEventListener('change', function () {
                monthliBox.innerHTML = '';
                buildmonthLi(yearType.value, monthType.value);

                console.log('改变了年的属性');
            });
            monthType.addEventListener('change', function () {
                monthliBox.innerHTML = '';
                buildmonthLi(yearType.value, monthType.value);
                console.log('改变了月的属性');
            });


            //判断某一天伦是星期几
            function oneDay(y, m, d) {
                let myDate = new Date();
                myDate.setFullYear(+y, +(m - 1), +d);
                let week = myDate.getDay();
                return week;
            }

            //随机数
            function getRandom(max) {
                return Math.floor(Math.random() * max);
            }
            //随机颜色
            function getRandomColor() {
                let color = ['1', '2', '3', '4', '5', '6', '7', '8', '9', 'A', 'B', 'C', 'D', 'E', 'F'];
                let colorAdd = '#';
                while (colorAdd.length <= 6) {
                    colorAdd += color[getRandom(12)];
                }
                return colorAdd;
            }

            let catBox = document.querySelectorAll('#monthliBox li');


            //当检测到该月存在事件，将返回true false 并该月存在事件的下标 对象集合
            function checkForMatter() {
                let year = yearType.value;
                let month = monthType.value;
                let type = false;
                let monthDataIndex = [];
                for (let i = 0; i < matterData.length; i++) {
                    if (year == matterData[i].year && month == matterData[i].month) {
                        type = true;
                        monthDataIndex.push(i);
                    }
                }
                monthDataIndex.unshift(type);
                return monthDataIndex;
            }

            //memo布局
            function builCatBox(element, index) {
                //渲染 catBox 布局
                if (element) {
                    let memoP = document.createElement('p');
                    memoP.innerHTML = '<span>' + matterData[index].matter + '</span>';
                    memoP.style.backgroundColor = getRandomColor();
                    element.appendChild(memoP);
                }
            }

            //加载伦完成 执行选中
            window.addEventListener('load',function(){
                let airBoxLen = oneDay(yearType.value, monthType.value, 1);
                console.log(airBoxLen);
                catBox[airBoxLen+nowDay-1].style.outline='3px solid red';
            })
        </script>
    </div>
</body>

</html>
