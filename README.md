# 🏠 Tehran House Price Prediction
پروژهٔ پیش‌بینی قیمت خانه‌های تهران با استفاده از یادگیری ماشین  
مدل نهایی: Linear Regression + StandardScaler

---

## 📌 خلاصه پروژه
هدف این پروژه پیش‌بینی قیمت خانه‌های تهران براساس ویژگی‌هایی مانند:

- متراژ
- سن بنا
- تعداد اتاق خواب
- منطقه
- … و سایر ویژگی‌های موجود در دیتاست

این پروژه از صفر تا صد شامل:
1. پاک‌سازی داده‌ها  
2. نرمال‌سازی داده با StandardScaler  
3. آموزش مدل  
4. ارزیابی عملکرد  
5. ذخیره مدل و اسکلر برای استفاده‌ی آینده  
6. تولید فایل خروجی prediction  

---

## 📂 ساختار فایل‌ها
---

## 🧹 1. پاک‌سازی و آماده‌سازی داده
در این بخش:
- حذف مقادیر گمشده  
- تبدیل ستون‌های متنی به عددی  
- تبدیل ستون‌هایی با کاراکترهای اضافی (مثل کاما)  
- تبدیل واحدها در صورت نیاز  

---

## 📊 2. نرمال‌سازی داده‌ها
برای اینکه مدل نسبت به اختلاف مقیاس ویژگی‌ها حساس نشود:

`python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled  = scaler.transform(X_test)

from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(X_train_scaled, y_train)
y_pred = model.predict(X_test_scaled)

R2: 0.99+
MAE: ~60

import joblib

joblib.dump(scaler, "scaler.pkl")
joblib.dump(model, "house_price_model_scaled.pkl")

loaded_scaler = joblib.load("scaler.pkl")
loaded_model  = joblib.load("house_price_model_scaled.pkl")

sample_scaled = loaded_scaler.transform(sample)
pred = loaded_model.predict(sample_scaled)

predictions_output_scaled.csv.
