# הקמת המאגר הציבורי של Burg Backup ב-GitHub

מסמך זה מיועד למאגר הפצה ציבורי **ללא קוד המקור של Burg Backup**.

## 1. יצירת Repository

צור Repository חדש בשם `BurgBackup` והגדר אותו כ-**Public**. מומלץ לא לסמן יצירה אוטומטית של README, License או `.gitignore`, משום שכל הקבצים הדרושים כבר נמצאים בחבילה הזו.

תיאור מומלץ:

`Free Windows backup and restore frontend powered by restic — SFTP, SMB/NAS, scheduling, retention and restore. Freeware, closed source.`

## 2. העלאת הקבצים הציבוריים

העלה את תוכן החבילה הזו לשורש המאגר, אך אל תעלה את קובץ ה-ZIP של קוד המקור, פרויקט Visual Studio, קובצי C#, WiX או סקריפטי Build פנימיים.

## 3. GitHub Issues ו-Discussions

Issue templates נמצאים תחת `.github/ISSUE_TEMPLATE`. ניתן להפעיל Discussions דרך `Settings` של המאגר כדי להפריד שאלות שימוש מבאגים.

## 4. דיווח אבטחה פרטי

במאגר ציבורי מומלץ להפעיל **Private vulnerability reporting** דרך הגדרות האבטחה של ה-Repository. לאחר ההפעלה, חוקרים יכולים לדווח דרך `Report a vulnerability` בלי לפרסם את הפרטים כ-Issue ציבורי.

## 5. יצירת Release ראשון

צור Draft Release עם tag `v2.1.0` וכותרת `Burg Backup 2.1.0`. צרף את ה-MSI הסופי, את המדריך הציבורי ואת `SHA256SUMS.txt`. השתמש ב-`RELEASE-NOTES-v2.1.0.md` כתיאור הגרסה.

GitHub ייצור אוטומטית גם קישורי “Source code”. הם יכילו רק את תוכן המאגר הציבורי הזה ולא את מקור האפליקציה.

## 6. לפני Publish

עבור על `RELEASE-CHECKLIST.md`. מומלץ לפרסם רק אחרי בדיקת התקנה, גיבוי ושחזור על מחשב/VM ניסוי ואימות ה-SHA-256 של קובץ ה-MSI הסופי.
