<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>فائدة</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" integrity="sha512-..." crossorigin="anonymous" referrerpolicy="no-referrer" />
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            text-align: center;
            background: linear-gradient(135deg, #ffe5d9, #d0f4f7);
            animation: bgMove 20s infinite alternate;
        }
        @keyframes bgMove {
            0% {background-position: 0% 0%;}
            100% {background-position: 100% 100%;}
        }
        header {
            background-color: #ff6b6b;
            color: white;
            padding: 25px 0;
            font-size: 2.5em;
            font-weight: bold;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        main {
            padding: 50px 20px;
        }
        .tip-box {
            padding: 35px 25px;
            border-radius: 20px;
            box-shadow: 0 6px 15px rgba(0,0,0,0.1);
            margin: 20px auto;
            max-width: 650px;
            font-size: 1.3em;
            display: flex;
            align-items: center;
            justify-content: flex-start;
            gap: 20px;
            transition: transform 0.3s, background-color 0.3s;
        }
        .tip-box:hover {
            transform: scale(1.02);
        }
        .tip-box i {
            font-size: 2em;
            animation: iconBounce 2s infinite;
        }
        @keyframes iconBounce {
            0%, 100% { transform: translateY(0);}
            50% { transform: translateY(-10px);}
        }
        button.share-btn {
            background: linear-gradient(45deg, #f58529, #dd2a7b, #8134af);
            border: none;
            padding: 15px 40px;
            font-size: 1.1em;
            cursor: pointer;
            border-radius: 30px;
            color: white;
            transition: transform 0.2s, box-shadow 0.3s;
            box-shadow: 0 4px 12px rgba(0,0,0,0.2);
            margin-top: 25px;
        }
        button.share-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 6px 18px rgba(0,0,0,0.3);
        }
        footer {
            margin-top: 50px;
            background-color: #ff6b6b;
            color: white;
            padding: 20px 0;
            font-size: 1em;
        }
    </style>
</head>
<body>
    <header>
        فائدة
    </header>
    <main>
        <div class="tip-box" id="dailyTip">
            <i class="fas fa-lightbulb"></i>
            تحميل الفائدة اليومية...
        </div>
        <button class="share-btn" onclick="shareSite()">مشاركة الموقع</button>
    </main>
    <footer>
        © 2025 فائدة - جميع الحقوق محفوظة
    </footer>

    <script>
        // مصفوفة الفوائد مع أيقونة ونوع كل فائدة
        const tips = [
            {icon: 'fa-lightbulb', text: "قال الإمام علي (ع): 'العقل زينة، والعمل له جمال'.", type: 'ديني'},
            {icon: 'fa-book', text: "في عام 1920، تأسست عصبة الأمم لتشجيع السلام بين الدول.", type: 'تاريخي'},
            {icon: 'fa-heart', text: "كل صباح هو فرصة جديدة لتحقيق أهدافك وأحلامك.", type: 'تحفيزي'},
            {icon: 'fa-star', text: "اطلب العلم من المهد إلى اللحد.", type: 'ديني'},
            {icon: 'fa-feather-alt', text: "الصدق طريق القلوب الطيبة والنجاح الحقيقي.", type: 'تحفيزي'}
        ];

        function showDailyTip() {
            const tipBox = document.getElementById('dailyTip');
            const randomIndex = Math.floor(Math.random() * tips.length);
            const tip = tips[randomIndex];

            // اختيار لون حسب نوع الفائدة
            let bgColor = '#ffffffdd';
            switch(tip.type) {
                case 'تحفيزي': bgColor = '#d1ffd6dd'; break;
                case 'تاريخي': bgColor = '#fff4d1dd'; break;
                case 'ديني': bgColor = '#d1e0ffff'; break;
            }

            tipBox.style.backgroundColor = bgColor;
            tipBox.innerHTML = `<i class="fas ${tip.icon}"></i> ${tip.text}`;
        }

        // تغيير الفائدة كل 10 ثواني
        setInterval(showDailyTip, 10000);
        showDailyTip();

        // زر المشاركة
        function shareSite() {
            if (navigator.share) {
                navigator.share({
                    title: 'فائدة',
                    text: 'تعالوا شوفوا موقع فائدة!',
                    url: window.location.href
                }).then(() => {
                    alert('تمت المشاركة بنجاح!');
                }).catch((error) => {
                    alert('فشل المشاركة: ' + error);
                });
            } else {
                alert('المشاركة غير مدعومة في متصفحك، انسخ الرابط يدوياً.');
            }
        }
    </script>
</body>
</html>
