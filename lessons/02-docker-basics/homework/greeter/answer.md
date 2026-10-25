איזו פקודה תבנה מה-Dockerfile שלכן image בשם greeter עם התגית v1? (מהתיקייה הראשית של הריפו.)
docker build -t greeter:v1 .
איזו פקודה תריץ אותו ברקע, בשם greeter, כך שבדפדפן נגיע אליו דרך http://localhost:9000?
docker run -d --name greeter -p 9000:8000 greeter:v1
מה צריך להוסיף לפקודה משאלה 2 כדי שהברכה תהיה Shalom במקום Hello?
docker run -d --name greeter -p 9000:8000 -e GREETING=Shalom greeter:v1
מה תחזיר הכתובת http://localhost:9000/hello/Rivka אחרי השינוי משאלה 3?
{"message": "Shalom, Rivka!"}
שיניתן שורה ב-app.py ובניתן שוב. אילו שלבים ב-build יסומנו CACHED, ואילו ירוצו מחדש? למה?
שלבי התמונת-בסיס והתקנת הספריות (requirements.txt) נשארים ב-Cache (CACHED) – מכיוון שקובץ התלויות לא השתנה, ודוקר חוסך את ההורדה וההתקנה מחדש.
השלבים מתחילת העתקת הקוד (COPY . .) והלאה ירוצו מחדש – מכיוון שדוקר מזהה שינוי בקובצי הפרויקט, וכל שלב שמגיע לאחר שינוי חייב להתבצע מחדש.
