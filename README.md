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