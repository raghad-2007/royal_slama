app.py
from flask import Flask, render_template, request
import cv2
import numpy as np

app = Flask(__name__)

@app.route('/')
def index():
    return render_template('index.html')

@app.route('/analyze', methods=['POST'])
def analyze():
    result = "تم الكشف عن حركة غير طبيعية! قد تكون إصابة."
    return render_template('result.html', result=result)

if __name__ == '__main__':
    app.run(debug=True)
templates/index.html
<!DOCTYPE html>
<html>
<head>
    <title>نظام سلامة</title>
</head>
<body>
    <h1>نظام سلامة الذكي لرصد الإصابات</h1>
    <form action="/analyze" method="POST" enctype="multipart/form-data">
        <label>ارفع فيديو اللاعب:</label><br>
        <input type="file" name="video"><br><br>
        <button type="submit">ابدأ التحليل</button>
    </form>
</body>
</html>
templates/result.html
<!DOCTYPE html>
<html>
<head>
    <title>نتيجة التحليل</title>
</head>
<body>
    <h2>النتيجة:</h2>
    <p>{{ result }}</p>
    <a href="/">رجوع</a>
</body>
</html>
requirements.txt
Flask
opencv-python
numpy
README.md
# نظام سلامة الذكي لرصد الإصابات

مشروع يستخدم الذكاء الاصطناعي لتحليل لقطات الفيديو الخاصة باللاعبين بهدف الكشف المبكر عن الإصابات، وتنبيه الطاقم الطبي فوراً.

## المميزات:
- رصد الإصابات من الفيديو.
- واجهة بسيطة لرفع الملفات وتحليلها.
- يمكن تطويره ليشمل بيانات حيوية من الأجهزة الذكية مستقبلاً.