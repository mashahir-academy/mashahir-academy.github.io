<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>سامانه استعلام مدارک آکادمی مشاهیر</title>
  <style>
    :root {
      --navy: #0d1b2a;
      --navy-light: #1b263b;
      --gold: #d4af37;
      --gold-gradient: linear-gradient(135deg, #f39c12, #d4af37, #f1c40f);
      --bg: #09111e;
      --card-bg: rgba(27, 38, 59, 0.7);
      --text: #e0e1dd;
      --success: #2ecc71;
    }
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif; }
    body { background: var(--bg); color: var(--text); min-height: 100vh; display: flex; flex-direction: column; align-items: center; padding: 20px 15px; }
    .header { text-align: center; margin-bottom: 25px; }
    .header h1 { color: var(--gold); font-size: 1.5rem; margin-bottom: 6px; letter-spacing: 0.5px; }
    .header p { color: #a0aec0; font-size: 0.9rem; }
    .card { background: var(--card-bg); border: 1px solid rgba(212, 175, 55, 0.3); border-radius: 16px; padding: 24px; max-width: 520px; width: 100%; box-shadow: 0 10px 30px rgba(0,0,0,0.5); backdrop-filter: blur(10px); }
    .badge-valid { display: flex; align-items: center; justify-content: center; gap: 8px; background: rgba(46, 204, 113, 0.15); border: 1px solid var(--success); color: var(--success); padding: 10px; border-radius: 30px; font-weight: bold; font-size: 0.95rem; margin-bottom: 20px; }
    .info-row { display: flex; justify-content: space-between; padding: 10px 0; border-bottom: 1px solid rgba(255,255,255,0.08); font-size: 0.92rem; }
    .info-label { color: #a0aec0; }
    .info-val { color: #fff; font-weight: 600; text-align: left; direction: ltr; }
    .cert-image-container { margin-top: 20px; text-align: center; }
    .cert-image { width: 100%; border-radius: 10px; border: 2px solid var(--gold); box-shadow: 0 8px 20px rgba(0,0,0,0.4); }
    .footer-note { text-align: center; margin-top: 25px; color: #718096; font-size: 0.8rem; line-height: 1.6; }
    .not-found { text-align: center; color: #e74c3c; padding: 30px 10px; }
  </style>
</head>
<body>

  <div class="header">
    <h1>آکادمی و سالن زیبایی مشاهیر</h1>
    <p>Mashahir Beauty & Training Academy</p>
  </div>

  <div class="card" id="content-box">
    <!-- محتوا با اسکن بارکد بارگذاری می‌شود -->
  </div>

  <div class="footer-note">
    این سامانه صرفاً جهت تأیید پایان‌دوره تخصصی آکادمی مشاهیر به مدیریت پریسا بم‌سیوند طراحی گردیده است.
  </div>

  <script>
    // دیتابیس ساده و سبک مدارک
    const certificates = {
      "MSH-1403-0001": {
        name: "الینا محمودوند (Elina Mahmoudvand)",
        course: "کاشت مژه تخصصی (Eyelash Extensions)",
        hours: "150 Hours",
        date: "2024 / 1403",
        instructor: "پریسا بم‌سیوند (Parisa Bamsivand)",
        image: "https://gapgpt.app/api/v1/files/image_gen_fc626df5-a467-4daf-95b6-82b0d4eb2400_0.webp"
      },
      "MSH-1403-0002": {
        name: "سیده زهرا حسینی شجاعی (Seyedeh Zahra Hosseini)",
        course: "کاشت مژه تخصصی (Eyelash Extensions)",
        hours: "150 Hours",
        date: "2024 / 1403",
        instructor: "پریسا بم‌سیوند (Parisa Bamsivand)",
        image: "https://gapgpt.app/api/v1/files/image_gen_a2240d3d-70e5-408f-81d6-0b9639a43138_0.webp"
      }
    };

    const urlParams = new URLSearchParams(window.location.search);
    const certId = urlParams.get('id') || "MSH-1403-0001";
    const box = document.getElementById('content-box');

    if (certificates[certId]) {
      const data = certificates[certId];
      box.innerHTML = `
        <div class="badge-valid">
          <span>✓</span> مدرک معتبر و تأییدشده
        </div>
        <div class="info-row"><span class="info-label">شماره مدرک:</span><span class="info-val">${certId}</span></div>
        <div class="info-row"><span class="info-label">هنرجو:</span><span class="info-val" style="direction:rtl">${data.name}</span></div>
        <div class="info-row"><span class="info-label">دوره تخصصی:</span><span class="info-val" style="direction:rtl">${data.course}</span></div>
        <div class="info-row"><span class="info-label">مدت دوره:</span><span class="info-val">${data.hours}</span></div>
        <div class="info-row"><span class="info-label">مدرس و مدیریت:</span><span class="info-val" style="direction:rtl">${data.instructor}</span></div>
        <div class="cert-image-container">
          <p style="color: #d4af37; margin-bottom: 8px; font-size: 0.85rem;">تصویر رسمی مدرک ثبت‌شده:</p>
          <img src="${data.image}" alt="Certificate" class="cert-image">
        </div>
      `;
    } else {
      box.innerHTML = `
        <div class="not-found">
          <h2>مدرکی با این شماره یافت نشد</h2>
          <p style="margin-top: 10px; color: #a0aec0;">لطفاً صحت شماره مدرک را بررسی کنید.</p>
        </div>
      `;
    }
  </script>
</body>
</html>
