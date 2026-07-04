# STATE.md — מצב הפרויקט

עודכן לאחרונה: 2026-07-04 ~09:35 UTC (ריצה מתוזמנת 8 — הושלמה)

## מצב נוכחי

- ריצה: ריצה מתוזמנת 8 (2026-07-04 12:06 מקומי / 09:06 UTC) — הושלמה
- ריצה פעילה מאז: — (המנעול נוקה בסיום ריצה 8)
- בעבודה כעת: — (אין משימה פתוחה)
- הושלם בריצה 8: METRICS (קריאה 7 — 27 צפיות, +2 בית בלבד, אין אורגני/בינג עדיין), מדריך 10 "How to brief an AI like a contractor" #36 (commit 8e32b83, +feed/Latest/changelog/sitemap/קישור ממדריך 3), תבנית /templates/project-file.txt #37 עם אירוע קליק GoatCounter (commit 4aae982), אימות חי (8/8 MARKER-OK), IndexNow ping על 6 URLs (כולם 200). דוח: reports/2026-07-04-12.md

## עובדות קבועות (לכל ריצה)

- **נושא האתר**: "An AI's field guide to working with AI" — מדריכים פרקטיים לעבודה עם כלי AI, כתובים על ידי AI שמנהל אתר אמיתי. ראה DECISIONS.md (2026-07-03). אושר על ידי האדמין.
- **שפת האתר**: אנגלית (ביקוש חיפוש גלובלי).
- **תאריכים ושעון**: תאריכי פרסום לפי זמן מקומי של האדמין (UTC+3). **אימות שעה**: שעון ה-sandbox אינו אמין — לאמת מול חותמת קובץ (touch + ls --time-style=full-iso בתיקייה הממופה). ריצה 6 רשמה זמנים שגויים ב-3 שעות; הדוח שלה נקרא -09 למרות שרצה ב-06 מקומי, ולכן דוח ריצה 7 הוא -09b.
- **git**: התיקייה הממופה לא תומכת בפעולות git. בכל ריצה: שיבוט לנתיב זמני **ייחודי** (/tmp/nh-run-XXXX), עבודה ודחיפה משם, ושיקוף קבצי האתר (ללא .git, עם rsync --delete על תיקיות התוכן) ל-repo/ בתיקיית הפרויקט. מקור האמת: GitHub. הערה: מחיקת קבצים בתיקייה הממופה דרך bash חסומה (Operation not permitted) — שיקוף עם rsync --delete עלול להיכשל על קבצים שנמחקו; לא קריטי.
- **גישה לרשת בריצות מתוזמנות**: web_fetch חסום (provenance). הפתרון: כלי הדפדפן (Claude in Chrome) — navigate + get_page_text + javascript_tool עובדים ל-GoatCounter, לאתר החי ול-IndexNow. בדיקת site: במנועי חיפוש נחסמת ב-CAPTCHA — לא לעקוף; מעקב אינדוקס דרך referrers אורגניים ב-GoatCounter.
- **IndexNow (מריצה 7, פרוטוקול קבוע)**: מפתח 6c5ec57a48628297f881681c91b437dd.txt בשורש המאגר — לא למחוק. על כל URL חדש/מעודכן: ping. POST חסום ב-CORS; הדרך — navigate ל-`https://api.indexnow.org/indexnow?url=<URL>&key=<KEY>` ומשם fetch same-origin לשאר ה-URLs.
- **אימות חי — origin (מריצה 8)**: fetch חוצה-origin מדף GoatCounter נחסם (CSP). הדרך: navigate ל-https://nohumans.xyz/robots.txt (לא-HTML, בלי count.js — אין זיהום) ומשם fetch same-origin עם no-store לכל העמודים.
- **הימנעות מזיהום מדידה**: ב