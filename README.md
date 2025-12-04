<!doctype html>
<html lang="ky">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title data-key="title">ОшМУ студенттик кеңеш</title>

  <style>
    /*================================================
    ОҢДОО: DARK MODE ҮЧҮН НЕГИЗГИ ӨЗГӨРМӨЛӨР
    ================================================*/
    :root {
      /* Theme colors (Blue) */
      --blue: #0a3d62;
      --blue-light: #134e7c;
      --blue-darker: #05263d; /* NEW: for dark button */

      /* Light Theme Variables */
      --bg-color: #f4f7fb;
      --card-background: #ffffff;
      --text-color: #062135;
      --muted: #5e6b7a;
      --border: rgba(10,61,98,0.15);
      --header-bg: rgba(255,255,255,0.85);
      --card-shadow: 0 10px 20px rgba(0,0,0,0.12), 0 4px 6px rgba(0,0,0,0.08);
      --link-hover-bg: rgba(10,61,98,0.08);
      --hr-color: rgba(10,61,98,0.15);
      --focus-color: #3498db; 
    }

    /* Dark Mode Active Styles */
    body.dark-mode {
      --bg-color: #1a202c; 
      --card-background: #2d3748; 
      --text-color: #e2e8f0; 
      --muted: #a0aec0; 
      --border: rgba(255, 255, 255, 0.1);
      --header-bg: rgba(45, 55, 72, 0.95);
      --card-shadow: 0 8px 15px rgba(0,0,0,0.5); 
      --link-hover-bg: rgba(255,255,255,0.15);
      --hr-color: rgba(255,255,255,0.1);
      --focus-color: #4a90e2; 
    }
    /*================================================*/

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body{
      font-family: "Inter", system-ui, sans-serif;
      background: var(--bg-color);
      color: var(--text-color);
      line-height: 1.5;
      transition: background 0.3s, color 0.3s; 
    }

    header{
      position: sticky;
      top: 0;
      z-index: 50;
      background: var(--header-bg);
      backdrop-filter: blur(10px);
      border-bottom: 1px solid var(--border);
      box-shadow: 0 2px 10px rgba(0,0,0,0.05);
    }

    .container{
      max-width: 1100px;
      margin: 0 auto;
      padding: 16px 18px;
    }


    .nav{
      display: flex;
      align-items: center;
      gap: 20px;
      flex-wrap: nowrap; 
    }

    /* ОҢДОО: ЛОГОТИПТЕРДИ ЖАНА ТЕКСТТИ БИРИКТИРҮҮ */
    .brand{ 
        display:flex; 
        align-items:center; 
        gap:10px; 
    }

    .logo{
      width: 55px; 
      height: 55px;
      border-radius: 6px;
      overflow: hidden;
      border: 1px solid var(--border);
      background: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    
    .logo.council-logo {
        background: var(--card-background); 
        border: 1px solid var(--border);
    }

    .logo img{ 
        width: 100%; 
        height: 100%; 
        object-fit: contain; 
        padding: 4px; 
    }

    .brand-text{ font-weight:700; font-size:17px; white-space: nowrap; } 

    nav{
        display: flex;
        gap: 6px; 
        flex-wrap: nowrap; 
        overflow-x: auto; 
        -webkit-overflow-scrolling: touch; 
    }
    
    nav a{
      text-decoration: none;
      color: var(--text-color);
      padding: 6px 8px; 
      border-radius: 8px;
      transition: 0.2s;
      font-weight: 500;
      font-size: 14px; 
      white-space: nowrap; 
    }

    nav a:hover{ background: var(--link-hover-bg); }

    .spacer{ flex: 1; }

    .btn{
      padding: 8px 14px;
      background: var(--blue);
      color: #fff;
      border-radius: 8px;
      border: none;
      cursor: pointer;
      font-weight: 600;
      transition: 0.3s;
      text-decoration: none; 
      display: inline-block; 
    }
    .btn:hover{ background: var(--blue-light); }
    .btn:disabled {
        background: var(--muted);
        cursor: not-allowed;
    }

    .lang-toggle, .mode-toggle{
      padding: 6px 10px;
      border-radius: 6px;
      border: 1px solid var(--border);
      background: var(--card-background);
      color: var(--text-color);
      cursor: pointer;
      font-weight: 600;
      font-size: 14px;
      transition: 0.3s;
    }
    .lang-toggle:hover, .mode-toggle:hover{ 
        background: var(--link-hover-bg); 
    }

    .hero{
      display: grid;
      grid-template-columns: 1fr 370px;
      gap: 28px;
      align-items: center;
      padding: 48px 0;
    }

    .hero-card{
      background: var(--card-background);
      padding: 28px;
      border-radius: 14px;
      border: 1px solid var(--border);
      backdrop-filter: blur(8px);
      box-shadow: 0 4px 20px rgba(0,0,0,0.06);
    }

    .hero h1{
      font-size: 30px;
      margin-bottom: 10px;
      font-weight: 800;
      color: var(--blue);
    }

    .hero p{ color:var(--muted); font-size:15px; margin-bottom:17px; }

    .actions{ display:flex; gap:12px; }

    /* CARD STYLES START - "ВАУ" АНИМАЦИЯ КҮЧӨТҮЛДҮ */
    
    @keyframes bouncingFloat {
        0%, 100% { 
            transform: translateY(0px) rotateZ(0deg); 
            box-shadow: var(--card-shadow);
        }
        50% { 
            transform: translateY(-8px) rotateZ(0.5deg); 
            box-shadow: 0 15px 30px rgba(0,0,0,0.25); 
        }
    }
    
    .card, .member-card {
        background: var(--card-background); 
        border: 1px solid var(--border);
        border-radius: 16px;
        padding: 18px;
        box-shadow: var(--card-shadow); 
        transition: transform 0.35s ease, box-shadow 0.35s ease, filter 0.35s ease, background 0.3s;
        
        animation: bouncingFloat 4s ease-in-out infinite; 
        backdrop-filter: blur(4px);
    }

    .card:hover, .member-card:hover {
        transform: translateY(-12px) scale(1.02); 
        box-shadow: 0 20px 40px rgba(0,0,0,0.25);
        filter: brightness(1.1);
        animation-play-state: paused; 
    }
    
    /* Бул карталарга анимацияны өчүрүү */
    .news-item, .resource-item, .carousel-card, .hero-card, .contact-card-v2, .event-card, .event-reg-details, .contact-info-v2 { 
        animation: none;
        transform: none;
        transition: all 0.3s ease; 
    }
    .news-item:hover, .resource-item:hover, .event-card:hover, .event-reg-details:hover {
        transform: none;
        filter: none;
    }
    
    /* NEWS SECTION STYLES */
    #news .card h4 {
        font-size: 18px;
        margin-bottom: 5px;
        color: var(--text-color);
    }

    section{ padding: 40px 0; }

    h2{
      font-size: 24px;
      margin-bottom: 14px;
      color: var(--blue);
      font-weight: 800;
    }

    /* ==================================
       КЕҢЕШТИН КУРАМЫ (MEMBER SECTION)
       ================================== */
    .members-section {
        padding: 40px 20px;
        text-align: center;
    }

    .members-section h2 {
        font-size: 32px;
        margin-bottom: 30px;
        font-weight: 700;
    }

    .members-grid {
        display: grid;
        gap: 25px;
        grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    }

    .member-card {
        padding: 22px; 
        border-radius: 16px; 
    }

    .member-card img {
        width: 100% !important; 
        height: 390px !important;
        object-fit: cover;
        border-radius: 12px;
        margin-bottom: 20px; 
    }

    .member-name {
        font-size: 20px;
        margin-bottom: 8px; 
        font-weight: 600;
        color: var(--text-color);
    }
    
    .role {
        font-size: 15px;
        color: var(--muted);
        margin-bottom: 12px;
    }
    .contact p { margin: 4px 0; font-size: 14px; color: var(--muted); }
    
    
    
    /* ============================
       ГАЛЕРЕЯ (КАРУСЕЛЬ) ОҢДОО
       ============================ */
    .carousel-section {
        text-align: center;
        padding: 50px 20px;
    }

    .carousel {
        position: relative;
        width: 100%;
        max-width: 900px;
        margin: auto;
        overflow: hidden;
    }

    .carousel-track {
        display: flex;
        gap: 15px;
        transition: transform 0.4s ease;
    }

    .card.carousel-card { 
        min-width: 260px;
        height: 180px;
        border-radius: 20px;
        overflow: hidden;
        flex-shrink: 0;
        box-shadow: 0px 4px 12px rgba(0,0,0,0.15);
        transition: transform 0.3s ease;
        padding: 0; 
        cursor: pointer; 
        animation: none; 
        transform: none;
    }
    
    .card.carousel-card img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .card.carousel-card:hover {
        transform: scale(1.05) translateY(-6px) rotateZ(0.3deg); 
        box-shadow: 0 8px 15px rgba(0,0,0,0.3);
    }

    .prev, .next {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        background: var(--card-background);
        color: var(--text-color);
        border: 1px solid var(--border);
        font-size: 24px;
        padding: 10px 15px;
        border-radius: 12px;
        cursor: pointer;
        box-shadow: 0 2px 8px rgba(0,0,0,0.2);
        transition: 0.3s;
        z-index: 10;
    }

    .prev:hover, .next:hover {
        background: var(--link-hover-bg);
    }


    .prev { left: -10px; }
    .next { right: -10px; }


    /* ============================
       ИШ-ЧАРАЛАР (EVENTS) СТИЛДЕРИ
       ============================ */
    #events .event-card {
        padding: 25px;
        margin-bottom: 20px;
        border-radius: 16px;
    }
    #events .event-card h3 {
        font-size: 22px;
        margin-bottom: 8px;
        color: var(--text-color);
    }
    #events .event-card p {
        font-size: 15px;
        color: var(--muted);
        margin-bottom: 15px;
    }
    
    /* ЖАҢЫ: EVENT DETAILS ЖАШЫРУУ */
    .event-details {
        max-height: 0;
        overflow: hidden;
        transition: max-height 0.4s ease-out;
    }
    .event-details.expanded {
        max-height: 1000px; /* Жетиштүү чоң маани */
    }

    .event-card .more-info-btn {
        margin-top: 10px;
        padding: 8px 15px;
        border: 1px solid var(--border);
        background: var(--link-hover-bg);
        color: var(--blue);
        cursor: pointer;
        border-radius: 8px;
        font-weight: 600;
        transition: background 0.2s;
        /* Жаңы стил */
        display: inline-block; 
        width: auto;
    }
    .event-card .more-info-btn:hover {
        background: var(--border);
    }
    
    /* ЖАҢЫ ДИЗАЙН: ИШ-ЧАРАГА КАТТАЛУУ БӨЛҮГҮ */
    .event-reg-details {
        padding: 20px;
        border-radius: 14px;
        margin-top: 15px;
        /* background: var(--link-hover-bg); */ /* Фон түсүн алып салдык */
    }
    .event-reg-details h4 {
        font-size: 18px;
        margin-top: 15px;
        margin-bottom: 10px;
        color: var(--text-color);
        /* border-bottom: 1px solid var(--border); */ /* Чекти алып салдык */
        padding-bottom: 5px;
    }
    .event-reg-details .venue-info {
        font-size: 15px;
        color: var(--muted);
        margin-bottom: 15px;
        padding-bottom: 10px;
        border-bottom: 1px dashed var(--border);
    }


    /* ФОРМАГА ОҢДООЛОР */
    #event1Form {
      display: flex;
      gap: 12px;
      margin-top: 15px; 
    }
    
    /* ЖАҢЫ: БАРДЫК INPUT СТИЛДЕРИ */
    #event1Form input, 
    #event1Form select, 
    #event1Form textarea,
    #event1Form button,
    .contact-form input,
    .contact-form select,
    .contact-form textarea {
      padding: 12px;
      border-radius: 8px;
      border: 1px solid var(--border);
      font-size: 14px;
      width: 100%; 
      background: var(--card-background); 
      color: var(--text-color);
      transition: border-color 0.3s, box-shadow 0.3s;
    }
    
    #event1Form input:focus, 
    .contact-form input:focus,
    .contact-form textarea:focus {
        border-color: var(--focus-color);
        box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.2);
        outline: none;
    }
    
    #event1Form select, .contact-form select {
        color: var(--muted);
    }
    body.dark-mode #event1Form select, body.dark-mode .contact-form select {
        color: var(--text-color);
    }
    #event1Form select option, .contact-form select option {
        color: var(--text-color);
        background-color: var(--card-background);
    }

    #event1Form .btn {
        width: 150px;
        flex-shrink: 0;
    }

    /* ============================
       БАЙЛАНЫШ (CONTACT SECTION) - ЖАҢЫ ДИЗАЙН
       ============================ */
    .contact-section {
        padding: 60px 20px;
        text-align: center;
    }

    .contact-section h2 {
        font-size: 32px;
        margin-bottom: 30px;
    }

    /* ЖАҢЫ КОНТАКТ КАРТАСЫ */
    .contact-card-v2 {
        display: grid;
        grid-template-columns: 1fr 2fr; /* Инфо 1/3, Форма 2/3 */
        gap: 30px;
        background: var(--card-background); 
        padding: 40px;
        border-radius: 16px;
        max-width: 900px;
        margin: auto;
        box-shadow: var(--card-shadow);
        border: 1px solid var(--border);
    }

    .contact-info-v2 {
        text-align: left;
        padding: 20px;
        border-right: 1px solid var(--border); /* Визуалдык бөлүү */
    }
    body.dark-mode .contact-info-v2 {
        border-right: 1px solid var(--border);
    }

    .contact-info-v2 h3 {
        font-size: 24px;
        margin-bottom: 25px;
        color: var(--blue);
        font-weight: 700;
    }
    
    .contact-details {
        display: flex;
        flex-direction: column;
        gap: 15px;
    }

    .contact-details div {
        display: flex;
        align-items: center;
        gap: 10px;
        font-size: 15px;
        color: var(--muted);
    }
    .contact-details div span.icon {
        color: var(--blue);
        font-size: 18px;
    }
    
    .contact-info-v2 p {
        margin-top: 20px;
        font-style: italic;
        font-size: 14px;
        color: var(--muted);
    }


    .contact-form {
        display: flex;
        flex-direction: column;
        gap: 12px;
        padding-left: 10px;
    }
    
    .contact-form .btn-send {
        background: var(--blue-darker); /* Түсү өзгөртүлдү */
        color: #fff;
        padding: 12px;
        border-radius: 10px;
        border: none;
        font-size: 16px;
        cursor: pointer;
        transition: background 0.3s;
        font-weight: 600;
        margin-top: 8px;
    }
    .contact-form .btn-send:hover {
        background: var(--blue-light);
    }

    /* ФОРМА ЭЛЕМЕНТТЕРИН КЕҢЕЙТҮҮ */
    .contact-form input,
    .contact-form select,
    .contact-form textarea {
        width: 100%;
    }


    footer{
      padding:24px 0;
      font-size:14px;
      color:var(--muted);
      border-top:1px solid var(--border);
      background: var(--card-background);
      margin-top:40px;
    }
    
    /* HORIZONTAL RULE STYLE */
    hr {
        border-color: var(--hr-color);
    }
    
    /* LIGHTBOX FIXED */
    .lightbox{
      position:fixed;
      inset:0;
      background:rgba(0,0,0,0.8); 
      display:flex;
      align-items:center;
      justify-content:center;
      padding:20px;
      visibility:hidden;
      opacity:0;
      transition: .2s;
      z-index:100;
    }

    .lightbox.show{
      visibility:visible;
      opacity:1;
    }

    .lightbox img{
      max-width:95%;
      max-height:90%;
      border-radius:6px;
    }


    /* Responsive */
    @media(max-width: 900px){
      .hero{ grid-template-columns:1fr; }
      .brand-text { display: none; } 
      
      nav {
          display: flex;
          overflow-x: auto;
          padding-bottom: 5px; 
          -webkit-overflow-scrolling: touch;
      }
      
      /* КОНТАКТ ДИЗАЙН МОБИЛДИК ҮЧҮН */
      .contact-card-v2 {
          grid-template-columns: 1fr;
          padding: 30px;
          gap: 20px;
      }
      .contact-info-v2 {
          border-right: none;
          border-bottom: 1px solid var(--border); /* Вертикалдуу чек горизонталдуу чекке өзгөрөт */
          padding: 0 0 20px 0;
      }
      .contact-form {
          padding-left: 0;
      }
    }
    
    @media(max-width: 750px){
        /* Мобилдик версияда форманы бир колонкага которуу */
        #event1Form {
          flex-direction: column;
        }
        #event1Form .btn {
            width: 100%;
        }
    }

    @media(max-width:600px){
      .nav { gap: 10px; }
    }
  </style>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>

<body>

  <header>
    <div class="container nav">
      <div class="brand">
        <div class="logo">
          <img src="oshsu.png" alt="ОшМУ логотиби">
        </div>
        
        <div class="logo council-logo">
          <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTFkQq1RVYNBjZoPS1y4WI02xkVHA11MTSleQ&s" alt="Студенттик кеңеш логотиби" style="padding: 2px;">
        </div>
        
        <div class="brand-text" data-key="brandTitle">ОшМУ студенттик кеңеш</div>
      </div>

      <nav>
        <a href="#about" data-key="navAbout">Биз тууралуу</a>
        <a href="#news" data-key="navNews">Жаңылыктар</a>
        <a href="#resources" data-key="navResources">Ресурстар</a>
        <a href="#members-section" data-key="navMembers">Кеңештин курамы</a>
        <a href="#events" data-key="navEvents">Иш-чаралар</a> 
        <a href="#gallery" data-key="navGallery">Галерея</a>
        <a href="#contact-card-v2" data-key="navContact">Байланыш</a>
      </nav>

      <div class="spacer"></div>

      <button class="mode-toggle" id="darkModeToggle">☀️</button>
      <button class="lang-toggle" id="langBtn">KY</button>
      <button class="btn" onclick="location.href='#contact-card-v2'" data-key="btnContact">Байланыш</button>
    </div>
  </header>

  <main class="container">
    <section class="hero">
        <div class="hero-card">
            <h1 data-key="heroTitle">ОшМУ студенттик кеңеш — Сиздин үнүңүз</h1>

            <p id="shortText" data-key="heroShortText">
              Студенттик кеңеш — бул жогорку окуу жайдагы студенттердин өз алдынча уюштурулган органы. 
              Негизги максаты — студенттердин кызыкчылыгын коргоо, иш-чараларды уюштуруу жана администрация менен студенттерди байланыштыруучу көпүрө болуу.
            </p>

            <div id="fullText" style="max-height:0; overflow:hidden; transition:max-height 0.5s ease;">
              
              <h3 data-key="heroFunctionsTitle">Негизги функциялары:</h3>
              <ul style="color:var(--muted)">
                <li data-key="func1">Окуу жайдагы маселелерди жетекчиликке жеткирүү</li>
                <li data-key="func2">Маданий, спорттук, социалдык иш-чараларды уюштуруу</li>
                <li data-key="func3">Жаңы студенттерге жардам берүү (адаптация, багыт берүү)</li>
                <li data-key="func4">Стипендия, жатакана маселелеринде колдоо көрсөтүү)</li>
                <li data-key="func5">Коомдук иштерге студенттерди тартуу</li>
              </ul>
            </div>

            <div class="actions">
              <button class="btn" id="moreBtn" data-key="moreBtn">Көбүрөөк</button>
            </div>
        </div>

      <div style="display:flex;flex-direction:column;gap:14px">
        <div class="card">
          <h3 data-key="fastLinks">Тез шилтемелер</h3>
          <ul style="margin-top:8px;color:var(--muted);padding-left:18px">
            <li><a href="#news" style="color:var(--muted);text-decoration:none;" data-key="fastNews">Жаңылыктар</a></li>
            <li><a href="#resources" style="color:var(--muted);text-decoration:none;" data-key="fastResources">Ресурстар</a></li>
            <li><a href="#gallery" style="color:var(--muted);text-decoration:none;" data-key="fastGallery">Галерея</a></li>
          </ul>
        </div>

        <div class="card">
          <h3 data-key="contactTitle">Контакт</h3>
          <div style="font-size:14px;color:var(--muted)" data-key="address">Адрес: Ош шаары, Алымбек Датка 331, ОшМУ башкы корпусу</div>
          <div style="margin-top:6px;font-weight:700;color:var(--text-color)">studentcouncil@oshmu.kg</div>
        </div>
      </div>
    </section>

    <section id="about">
        <h2 data-key="aboutTitle">Биз тууралуу</h2>
        <div class="hero-card">
          <p id="shortText_about" data-key="aboutShortText">
            Биздин өлкөдө жаштар уюмдарынын башаты советтик мезгилге туура келет. Азыркы жаштар комитети студенттер менен жетекчилерди тыгыз байланыштырган миссияны аркалап, студенттердин кадыр-барктуу уюму катары иш алып барууда.
          </p>

          <div id="fullText_about" style="max-height:0; overflow:hidden; transition:max-height 0.5s ease;">
            <p data-key="aboutP1" style="color:var(--muted)">
              Октябрь революциясы жеңгенден кийин 1918-жылы август айында Большевиктер партиясынын жаштар канаты – Комсомол уюштурулат. 
              1918-жылы бул уюмга В.И.Лениндин аты берилип ВЛКСМ (Буткул Союздук Ленинчил Жаштар Союму) 1991-жылга чейин жашап келди.
            </p>
            <p data-key="aboutP2" style="color:var(--muted)">
              Ал эми биздин окуу жайдагы комсомол комитети 1951-жылы Ош пединституту түзүлгөндөн тартып өз ишмердүүлугүн жүргүзө баштаган.
              1992-жылы комсомол комитетинин ордуна студенттик сенат түзүлүп иштей баштады. Ош мамлекеттик университети болуп кайра уюшулганда студенттик сенат сакталды.
              2000-жылдын 10-декабрындагы КР Президентинин жаштар иштери боюнча указына ылайык, студенттик сенат жаштар комитети болуп кайрадан түзүлүп, өз ишмердүүлүгүн жүргүзө баштаган.
            </p>
            <p data-key="aboutP3" style="color:var(--muted)">
              Азыркы учурда жаштар комитети студенттер менен жетекчилерди тыгыз байланыштырган миссияны аркалап, студенттердин кадыр-барктуу уюму катары иш алып барууда.
            </p>
          </div>

          <div class="actions">
            <button class="btn" id="moreBtn_about" data-key="moreBtn">Көбүрөөк</button> 
          </div>
        </div>
    </section>
    <section id="news" class="container" style="padding: 40px 18px;">
        <h2 data-key="newsTitle">Акыркы жаңылыктар</h2>
        <div class="news-grid" style="display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px;">

            <div class="card news-item">
                <div style="color: #e67e22; font-weight: 700; margin-bottom: 8px;" data-key="newsTagNew">📣 ЖАҢЫ!</div>
                <h4 data-key="news1Title">Студенттер үчүн жатаканага арыз берүү</h4>
                <p style="font-size: 14px; color: var(--muted); margin-top: 5px;" data-key="news1Text">2025-2026 окуу жылына жатаканадан орун алуу үчүн арыздарды кабыл алуу 1-июндан башталат.</p>
                <div style="font-size: 12px; color: var(--blue); margin-top: 10px;">18-ноябрь, 2025</div>
                </div>
            
            <div class="card news-item">
                <div style="color: var(--blue); font-weight: 700; margin-bottom: 8px;" data-key="newsTagEvent">🎉 Иш-чара</div>
                <h4 data-key="news2Title">Ректор менен жолугушуу: Суроо-жооп</h4>
                <p style="font-size: 14px; color: var(--muted); margin-top: 5px;" data-key="news2Text">Ректор менен студенттердин салттуу жолугушуусу 25-ноябрда саат 14:00дө Чоң залда өтөт.</p>
                <div style="font-size: 12px; color: var(--blue); margin-top: 10px;">10-ноябрь, 2025</div>
                </div>

            <div class="card news-item">
                <div style="color: #c0392b; font-weight: 700; margin-bottom: 8px;" data-key="newsTagImportant">❗️ МААНИЛҮҮ</div>
                <h4 data-key="news3Title">Акыркы сессияга даярдык графиги</h4>
                <p style="font-size: 14px; color: var(--muted); margin-top: 5px;" data-key="news3Text">Сессияга даярдык графиги факультеттерге жөнөтүлдү. Өзгөртүүлөр болсо, деканатка кайрылыңыз.</p>
                <div style="font-size: 12px; color: var(--blue); margin-top: 10px;">01-ноябрь, 2025</div>
                </div>

        </div>
    </section>
    <section id="resources">
        <h2 data-key="resourcesTitle">Ресурстар Борбору</h2>
        <div class="resources-grid" style="display: flex; flex-direction: column; gap: 15px;">

            <div class="card resource-item">
                <div>
                    <h4 data-key="res1Title">Жатаканага арыз берүү формасы (PDF)</h4>
                    <p style="font-size: 14px; color: var(--muted);" data-key="res1Desc">Жатаканадан орун алуу үчүн милдеттүү түрдө толтурулуучу форма.</p>
                </div>
                <a href="#" class="btn" data-key="btnDownload" download>Жүктөө</a>
            </div>

            <div class="card resource-item">
                <div>
                    <h4 data-key="res2Title">Стипендия алуу үчүн документтердин тизмеси</h4>
                    <p style="font-size: 14px; color: var(--muted);" data-key="res2Desc">Социалдык жана Президенттик стипендияга талап кылынган документтердин тизмеси.</p>
                </div>
                <a href="#" class="btn" data-key="btnDownload" download>Жүктөө</a>
            </div>

            <div class="card resource-item">
                <div>
                    <h4 data-key="res3Title">ОшМУ Студенттик Кеңешинин Жобосу (Устав)</h4>
                    <p style="font-size: 14px; color: var(--muted);" data-key="res3Desc">Кеңештин ишин жөнгө салуучу расмий документ.</p>
                </div>
                <a href="#" class="btn" data-key="btnDownload" download>Жүктөө</a>
            </div>

        </div>
    </section>
    <section class="members-section" id="members-section">
      <h2 data-key="memberSectionTitle">Студенттик кеңешинин курамы</h2>

      <div class="members-grid">
        <div class="member-card">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR-7_3qprW9BdB0SKe9tZ0Gsn4q9UdGH4NKuQVPCCrLkeCTa-W-Z7NntcmZ0sLCVtYwaYo&usqp=CAU" alt="Кенжеев Токторбай сүрөтү">
            <h3>Кенжеев Токторбай</h3>
            <p class="role" data-key="roleChairman">Төрага</p>
            <div class="contact">
                <p>Тел: +996 558 053 405</p>
                <p>Email: toktorbajkenzeev252@gmail.com</p>
            </div>
        </div>
      <div class="member-card">
            <img src="/almas.jpeg" alt="Алмасбек уулу Адилет сүрөтү">
            <h3>Алмасбек уулу Адилет</h3>
            <p class="role" data-key="roleViceChairman">Төраганын биринчи орун басары</p>
            <div class="contact">
                <p>Тел: +996 775 452 004</p>
                <p>Тел: +996 501 452 004</p>
                <p>Email: adilet1011@icloud.com</p>
            </div>
        </div>

        <div class="member-card">
            <img src="marlen.jpg" alt="Таалайбеков Марлен сүрөтү">
            <h3>Таалайбеков Марлен</h3>
            <p class="role" data-key="roleAdvisor">Төраганын кеңешчиси</p>
            <div class="contact">
                <p>Тел: +996 779 802 504</p>
                <p>Email: marlen200416@icloud.com</p>
            </div>
        </div>

        <div class="member-card">
            <img src="/ ayana.jpeg" alt="Ысмайылова Аяна сүрөтү">
            <h3>Ысмайылова Аяна</h3>
            <p class="role" data-key="roleSecretary">Төраганын катчысы / Медиа секторунун башчысы</p>
            <div class="contact">
                <p>Тел: +996 703 885 013</p>
                <p>Email: ayana20244@icloud.com</p>
            </div>
        </div>

        <div class="member-card">
            <img src="/anjelika.jpeg" alt="Осмонали кызы Анжелика сүрөтү">
            <h3>Осмонали кызы Анжелика</h3>
            <p class="role" data-key="roleScienceHead">Илим-билим секторунун башчысы</p>
            <div class="contact">
                <p>Тел: +996 507 290 887</p>
                <p>Email: anje1ikkaocmonalieva@gmail.com </p>
            </div>
        </div>

        <div class="member-card">
            <img src="/meerim.jpeg" alt="Турдухунова Мээрим сүрөтү">
            <h3>Турдухунова Мээрим</h3>
            <p class="role" data-key="roleCultureHead">Маданий иштер секторунун башчысы</p>
            <div class="contact">
                <p>Тел: +996 704 696 366</p>
                <p>Email: turduahunovameerim176@gmail.com</p>
            </div>
        </div>
        
        <div class="member-card">
            <img src="muha.jpeg" alt="Жоробаев Мухамедарин сүрөтү">
            <h3>Жоробаев Мухамедарын</h3>
            <p class="role" data-key="roleCollegeVice">Колледждер боюнча орун басары</p>
            <div class="contact">
                <p>Тел: +996 997 333 911</p>
                <p>Email: muhajoro@gmail.com</p>
            </div>
        </div>

        <div class="member-card">
            <img src="/bekzat.jpeg" alt="Иброхимов Бекзат сүрөтү">
            <h3>Иброхимов Бекзат</h3>
            <p class="role" data-key="roleSportHead">Спорт секторунун башчысы</p>
            <div class="contact">
                <p>Тел: +996 500 553 760</p>
                <p>Email: ibroximovbekzod2007@gmail.com</p>
            </div>
        </div>

        <div class="member-card">
            <img src="/nurgul.jpeg" alt="Пайзиллаева Нүргүл сүрөтү">
            <h3>Пайзиллаева Нүргүл</h3>
            <p class="role" data-key="roleMindHead">Акыл таймаш секторунун башчысы</p>
            <div class="contact">
                <p>Тел: +996 777 338 821</p>
                <p>Email: pajzillaevanurgul70@gmail.com</p>
            </div>
        </div>

        <div class="member-card">
            <img src="/dali.jpeg" alt="Салиев Далиер сүрөтү">
            <h3>Салиев Далиер</h3>
            <p class="role" data-key="roleSocialHead">Социалдык иштер секторунун башчысы</p>
            <div class="contact">
                <p>Тел: +996 222 270 642</p>
                <p>Email: dalier757@gmail.com</p>
            </div>
        </div>
        
        <div class="member-card">
            <img src="abdulla.png" alt="Калилов Абдулла Медетбекович сүрөтү">
            <h3>Калилов Абдулла</h3>
            <p class="role" data-key="roleITHead">IT-секторунун башчысы</p>
            <div class="contact">
                <p>Тел: +996 705 597 373</p>
                <p>Email: kalilovabdulla26@gmail.com</p>
            </div>
        </div>
      </div>
    </section>

    <section id="events" class="container" style="padding: 40px 18px;">
      <h2 data-key="eventsTitle">Иш-чаралар</h2>
      <div class="events-grid" style="display: grid; grid-template-columns: 1fr; gap: 20px;">
          
          <div class="card event-card">
              <h3 data-key="event1Title">Студенттер форуму 2025</h3>
              <p data-key="event1Date">🗓️ 10-апрель, 2025 | 🏢 ОшМУ</p>
              
              <div class="event-details" id="event1Details">
                  <div class="event-reg-details">
                      <h4 data-key="event1VenueTitle">Өтүү жайы</h4>
                      <p class="venue-info" data-key="event1Venue">ОшМУ башкы корпусу, 2-кабат, Чоң жыйын залы</p>
                      
                      <h4 data-key="event1RegTitle">Катышуу үчүн катталуу</h4>
                      <form id="event1Form">
                          <input type="text" name="name" placeholder="Аты-жөнүңүз" required>
                          <input type="text" name="faculty" placeholder="Факультетиңиз" required>
                          <button type="submit" class="btn" data-key="btnRegister">Катталуу</button>
                      </form>
                  </div>
              </div>
              
              <button class="more-info-btn" data-target="event1Details" data-key="moreBtn">Көбүрөөк</button>

          </div>
          
          <div class="card event-card">
              <h3 data-key="event2Title">Жазгы кайрымдуулук фестивалы</h3>
              <p data-key="event2Date">🗓️ 25-март, 2025 | 🏢 ОшМУ Спорт аянтчасы</p>
              
              <div class="event-details" id="event2Details">
                  <div class="event-reg-details">
                      <h4 data-key="event2VenueTitle">Өтүү жайы</h4>
                      <p class="venue-info" data-key="event2Venue">ОшМУнун спорт аянтчасы</p>
                      
                      <h4 data-key="event1RegTitle">Катышуу үчүн катталуу</h4>
                      <p style="color: red; font-weight: 700; margin-bottom: 15px;" data-key="event2RegClosed">Катталуу аяктады.</p>
                      <form id="event2Form" style="display: flex; gap: 10px;">
                          <input type="text" name="name" placeholder="Аты-жөнүңүз" disabled>
                          <input type="text" name="faculty" placeholder="Факультетиңиз" disabled>
                          <button type="button" class="btn" disabled data-key="btnRegister">Катталуу</button>
                      </form>
                  </div>
              </div>
              
              <button class="more-info-btn" data-target="event2Details" data-key="moreBtn">Көбүрөөк</button>

          </div>

      </div>
    </section>
    <section class="carousel-section" id="gallery">
        <h2 data-key="galleryTitle">Галерея</h2>
        <div class="carousel-container">
            <div class="carousel">
                <div class="carousel-track" id="carouselTrack">
                    </div>
                <div class="prev" id="prevBtn">❮</div>
                <div class="next" id="nextBtn">❯</div>
            </div>
        </div>
    </section>
    <section class="contact-section">
      <div class="contact-card-v2" id="contact-card-v2">
        
        <div class="contact-info-v2">
            <h3 data-key="contactTitle">Студенттик кеңеш менен байланыш</h3>

            <div class="contact-details">
                <div>
                    <span class="icon"><i class="fas fa-map-marker-alt"></i></span>
                    <span data-key="contactAddress">ОшМУ, Башкы корпус, 0-кабат, 001-кабинет</span>
                </div>
                <div>
                    <span class="icon"><i class="fas fa-phone-alt"></i></span>
                    <span data-key="contactPhone">+996 000 000 000</span>
                </div>
                <div>
                    <span class="icon"><i class="fas fa-envelope"></i></span>
                    <span data-key="contactEmail">studentcouncil@oshmu.kg</span>
                </div>
            </div>

            <p data-key="contactNote">
                Жаңылыктар, иш-чаралар жана башка сунуштар боюнча кайрылсаңыз болот.
            </p>
        </div>
        
        <form class="contact-form" id="contactForm">
          <input type="text" name="name" placeholder="Аты-жөнүңүз" required>
          <input type="email" name="email" placeholder="Электрондук почта" required>
          
          <select name="subject" required>
            <option value="" disabled selected>Тема танда</option>
            <option value="news" data-key="topicNews">Жаңылык жөнөтүү</option>
            <option value="event" data-key="topicEvent">Иш-чара сунуштоо</option>
            <option value="suggestion" data-key="topicSuggestion">Сунуш/Пикир</option>
            <option value="other" data-key="topicOther">Башка</option>
          </select>
          
          <input type="tel" name="phone" placeholder="Телефон (милдеттүү эмес)">
          <textarea name="message" rows="5" placeholder="Билдирүү" required></textarea>
          <button type="submit" class="btn-send" data-key="btnSend">Жөнөт</button>
        </form>

      </div>
    </section>
    </main>

  <footer>
    <div class="container" style="text-align:center;">
        © 2025 ОшМУ Студенттик кеңеши | 
        <span data-key="developer">К.А.М тарабынан иштелип чыккан</span>
    </div>
  </footer>
  
  <div class="lightbox" id="lightbox">
      <img src="" alt="" id="lightboxImage">
  </div>


  <script>
    // ===================================
    // 1. КОБОРООК БАСКЫЧТАРЫ (HERO & ABOUT)
    // ===================================
    document.getElementById('moreBtn').addEventListener('click', function() {
        const fullText = document.getElementById('fullText');
        const shortText = document.getElementById('shortText');
        
        if (fullText.style.maxHeight === '0px' || fullText.style.maxHeight === '') {
            fullText.style.maxHeight = fullText.scrollHeight + 'px';
            shortText.style.display = 'none';
            this.textContent = currentLang === 'ky' ? 'Жашыруу' : (currentLang === 'ru' ? 'Скрыть' : 'Hide');
        } else {
            fullText.style.maxHeight = '0px';
            shortText.style.display = 'block';
            this.textContent = translations[currentLang].moreBtn;
        }
    });

    document.getElementById('moreBtn_about').addEventListener('click', function() {
        const fullText = document.getElementById('fullText_about');
        const shortText = document.getElementById('shortText_about');
        
        if (fullText.style.maxHeight === '0px' || fullText.style.maxHeight === '') {
            fullText.style.maxHeight = fullText.scrollHeight + 'px';
            shortText.style.display = 'none';
            this.textContent = currentLang === 'ky' ? 'Жашыруу' : (currentLang === 'ru' ? 'Скрыть' : 'Hide');
        } else {
            fullText.style.maxHeight = '0px';
            shortText.style.display = 'block';
            this.textContent = translations[currentLang].moreBtn;
        }
    });

    // ===================================
    // ИШ-ЧАРАЛАРДЫ АЧУУ/ЖАБУУ
    // ===================================
    document.querySelectorAll('.more-info-btn').forEach(button => {
        button.addEventListener('click', function() {
            const targetId = this.getAttribute('data-target');
            const targetElement = document.getElementById(targetId);
            
            if (targetElement.style.maxHeight === '0px' || targetElement.style.maxHeight === '') {
                // Маалыматты көрсөтүү
                targetElement.style.maxHeight = targetElement.scrollHeight + 'px';
                targetElement.classList.add('expanded');
                this.textContent = currentLang === 'ky' ? 'Жашыруу' : (currentLang === 'ru' ? 'Скрыть' : 'Hide');
                this.classList.add('active');
                
                // Эгер форма мобилдик режимде болсо, scroll кылуу
                if (window.innerWidth <= 750) {
                     targetElement.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }

            } else {
                // Маалыматты жашыруу
                targetElement.style.maxHeight = '0px';
                targetElement.classList.remove('expanded');
                this.textContent = translations[currentLang].moreBtn;
                this.classList.remove('active');
            }
        });

        // Иш-чаралар башында жашыруун болсун
        const targetId = button.getAttribute('data-target');
        const targetElement = document.getElementById(targetId);
        targetElement.style.maxHeight = '0px';
    });


    // ===================================
    // 2. ТИЛ АЛМАШТЫРУУ (KY/RU/EN)
    // ===================================
    const translations = {
        ky: {
            title: "ОшМУ студенттик кеңеш",
            brandTitle: "ОшМУ студенттик кеңеш",
            navAbout: "Биз тууралуу",
            navNews: "Жаңылыктар",
            navResources: "Ресурстар",
            navMembers: "Кеңештин курамы",
            navEvents: "Иш-чаралар",
            navGallery: "Галерея",
            navContact: "Байланыш",
            btnContact: "Байланыш",
            heroTitle: "ОшМУ студенттик кеңеш — Сиздин үнүңүз",
            heroShortText: "Студенттик кеңеш — бул жогорку окуу жайдагы студенттердин өз алдынча уюштурулган органы. Негизги максаты — студенттердин кызыкчылыгын коргоо, иш-чараларды уюштуруу жана администрация менен студенттерди байланыштыруучу көпүрө болуу.",
            heroFunctionsTitle: "Негизги функциялары:",
            func1: "Окуу жайдагы маселелерди жетекчиликке жеткирүү",
            func2: "Маданий, спорттук, социалдык иш-чараларды уюштуруу",
            func3: "Жаңы студенттерге жардам берүү (адаптация, багыт берүү)",
            func4: "Стипендия, жатакана маселелеринде колдоо көрсөтүү",
            func5: "Коомдук иштерге студенттерди тартуу",
            moreBtn: "Көбүрөөк",
            fastLinks: "Тез шилтемелер",
            fastNews: "Жаңылыктар",
            fastResources: "Ресурстар",
            fastGallery: "Галерея",
            contactTitle: "Контакт",
            address: "Адрес: Ош шаары, Алымбек Датка 331, ОшМУ башкы корпусу",
            aboutTitle: "Биз тууралуу",
            aboutShortText: "Биздин өлкөдө жаштар уюмдарынын башаты советтик мезгилге туура келет. Азыркы жаштар комитети студенттер менен жетекчилерди тыгыз байланыштырган миссияны аркалап, студенттердин кадыр-барктуу уюму катары иш алып барууда.",
            aboutP1: "Октябрь революциясы жеңгенден кийин 1918-жылы август айында Большевиктер партиясынын жаштар канаты – Комсомол уюштурулат. 1918-жылы бул уюмга В.И.Лениндин аты берилип ВЛКСМ (Буткул Союздук Ленинчил Жаштар Союму) 1991-жылга чейин жашап келди.",
            aboutP2: "Ал эми биздин окуу жайдагы комсомол комитети 1951-жылы Ош пединституту түзүлгөндөн тартып өз ишмердүүлугүн жүргүзө баштаган. 1992-жылы комсомол комитетинин ордуна студенттик сенат түзүлүп иштей баштады. Ош мамлекеттик университети болуп кайра уюшулганда студенттик сенат сакталды. 2000-жылдын 10-декабрындагы КР Президентинин жаштар иштери боюнча указына ылайык, студенттик сенат жаштар комитети болуп кайрадан түзүлүп, өз ишмердүүлүгүн жүргүзө баштаган.",
            aboutP3: "Азыркы учурда жаштар комитети студенттер менен жетекчилерди тыгыз байланыштырган миссияны аркалап, студенттердин кадыр-барктуу уюму катары иш алып барууда.",
            newsTitle: "Акыркы жаңылыктар",
            newsTagNew: "📣 ЖАҢЫ!",
            news1Title: "Студенттер үчүн жатаканага арыз берүү",
            news1Text: "2025-2026 окуу жылына жатаканадан орун алуу үчүн арыздарды кабыл алуу 1-июндан башталат.",
            newsTagEvent: "🎉 Иш-чара",
            news2Title: "Ректор менен жолугушуу: Суроо-жооп",
            news2Text: "Ректор менен студенттердин салттуу жолугушуусу 25-ноябрда саат 14:00дө Чоң залда өтөт.",
            newsTagImportant: "❗️ МААНИЛҮҮ",
            news3Title: "Акыркы сессияга даярдык графиги",
            news3Text: "Сессияга даярдык графиги факультеттерге жөнөтүлдү. Өзгөртүүлөр болсо, деканатка кайрылыңыз.",
            btnMore: "Көбүрөөк", // Баскыч эми Жашыруу/Көбүрөөк үчүн гана колдонулат
            resourcesTitle: "Ресурстар борбору",
            res1Title: "Жатаканага арыз берүү формасы (PDF)",
            res1Desc: "Жатаканадан орун алуу үчүн милдеттүү түрдө толтурулуучу форма.",
            res2Title: "Стипендия алуу үчүн документтердин тизмеси",
            res2Desc: "Социалдык жана Президенттик стипендияга талап кылынган документтердин тизмеси.",
            res3Title: "ОшМУ Студенттик Кеңешинин Жобосу (Устав)",
            res3Desc: "Кеңештин ишин жөнгө салуучу расмий документ.",
            btnDownload: "Жүктөө",
            memberSectionTitle: "Студенттик кеңешинин курамы",
            roleChairman: "Төрага",
            roleViceChairman: "Төраганын биринчи орун басары",
            roleAdvisor: "Төраганын кеңешчиси",
            roleSecretary: "Төраганын катчысы / Медиа секторунун башчысы",
            roleScienceHead: "Илим-билим секторунун башчысы",
            roleCultureHead: "Маданий иштер секторунун башчысы",
            roleCollegeVice: "Колледждер боюнча орун басары",
            roleSportHead: "Спорт секторунун башчысы",
            roleMindHead: "Акыл таймаш секторунун башчысы",
            roleSocialHead: "Социалдык иштер секторунун башчысы",
            roleITHead: "IT-секторунун башчысы", 
            eventsTitle: "Иш-чаралар",
            event1Title: "Студенттер форуму 2025",
            event1Date: "🗓️ 10-апрель, 2025 | 🏢 ОшМУ",
            event1VenueTitle: "Өтүү жайы",
            event1Venue: "ОшМУ башкы корпусу, 2-кабат, Чоң жыйын залы",
            event1RegTitle: "Катышуу үчүн катталуу",
            btnRegister: "Катталуу",
            event2Title: "Жазгы кайрымдуулук фестивалы",
            event2Date: "🗓️ 25-март, 2025 | 🏢 ОшМУ Спорт аянтчасы",
            event2VenueTitle: "Өтүү жайы",
            event2Venue: "ОшМУнун спорт аянтчасы",
            event2RegClosed: "Катталуу аяктады.",
            galleryTitle: "Галерея",
            contactTitle: "Студенттик кеңеш менен байланыш", 
            contactAddress: "ОшМУ, Башкы корпус, 0-кабат, 001-кабинет",
            contactPhone: "+996 000 000 000",
            contactEmail: "studentcouncil@oshmu.kg",
            contactNote: "Жаңылыктар, иш-чаралар жана башка сунуштар боюнча кайрылсаңыз болот.",
            btnSend: "Жөнөт",
            topicNews: "Жаңылык жөнөтүү",
            topicEvent: "Иш-чара сунуштоо",
            topicSuggestion: "Сунуш/Пикир",
            topicOther: "Башка",
            developer: "К.А.М тарабынан иштелип чыккан"
            
        },
        ru: {
            title: "Студенческий совет ОшГУ",
            brandTitle: "Студенческий совет ОшГУ",
            navAbout: "О нас",
            navNews: "Новости",
            navResources: "Ресурсы",
            navMembers: "Состав Совета",
            navEvents: "Мероприятия",
            navGallery: "Галерея",
            navContact: "Контакты",
            btnContact: "Связаться",
            heroTitle: "Студенческий совет ОшГУ — Ваш голос",
            heroShortText: "Студенческий совет — это орган студенческого самоуправления в вузе. Основная цель — защита интересов студентов, организация мероприятий и служение мостом между администрацией и студентами.",
            heroFunctionsTitle: "Основные функции:",
            func1: "Донесение проблем вуза до руководства",
            func2: "Организация культурных, спортивных, социальных мероприятий",
            func3: "Помощь новым студентам (адаптация, наставничество)",
            func4: "Поддержка в вопросах стипендий и общежитий",
            func5: "Привлечение студентов к общественной работе",
            moreBtn: "Подробнее",
            fastLinks: "Быстрые ссылки",
            fastNews: "Новости",
            fastResources: "Ресурсы",
            fastGallery: "Галерея",
            contactTitle: "Контакт",
            address: "Адрес: Город Ош, Алымбек Датка 331, главный корпус ОшГУ",
            aboutTitle: "О нас",
            aboutShortText: "История молодежных организаций в нашей стране восходит к советскому периоду. Нынешний молодежный комитет выполняет миссию по тесной связи студентов и руководителей, действуя как авторитетная студенческая организация.",
            aboutP1: "После победы Октябрьской революции, в августе 1918 года был организован Комсомол — молодежное крыло партии большевиков. В 1918 году этой организации было присвоено имя В.И. Ленина, и ВЛКСМ (Всесоюзный Ленинский Коммунистический Союз Молодежи) просуществовал до 1991 года.",
            aboutP2: "Комсомольский комитет в нашем учебном заведении начал свою деятельность с момента основания Ошского педагогического института в 1951 году. В 1992 году вместо комсомольского комитета начал работать студенческий сенат. Студенческий сенат был сохранен, когда вуз был реорганизован в Ошский государственный университет. В соответствии с указом Президента КР по делам молодежи от 10 декабря 2000 года, студенческий сенат был реорганизован в Молодежный комитет и начал свою деятельность.",
            aboutP3: "В настоящее время молодежный комитет выполняет миссию по тесной связи студентов и руководителей, действуя как авторитетная студенческая организация.",
            newsTitle: "Последние новости",
            newsTagNew: "📣 НОВОЕ!",
            news1Title: "Подача заявок на общежитие для студентов",
            news1Text: "Прием заявлений на получение места в общежитии на 2025-2026 учебный год начинается с 1 июня.",
            newsTagEvent: "🎉 Мероприятие",
            news2Title: "Встреча с ректором: Вопросы и ответы",
            news2Text: "Традиционная встреча ректора со студентами пройдет 25 ноября в 14:00 в Большом зале.",
            newsTagImportant: "❗️ ВАЖНО",
            news3Title: "График подготовки к итоговой сессии",
            news3Text: "График подготовки к сессии направлен на факультеты. В случае изменений, обращайтесь в деканат.",
            btnMore: "Подробнее", // Баскыч эми Скрыть/Подробнее үчүн гана колдонулат
            resourcesTitle: "Ресурсный центр",
            res1Title: "Форма заявления на общежитие (PDF)",
            res1Desc: "Обязательная форма для заполнения для получения места в общежитии.",
            res2Title: "Список документов для получения стипендии",
            res2Desc: "Список документов, необходимых для социальной и Президентской стипендии.",
            res3Title: "Положение о Студенческом Совете ОшГУ (Устав)",
            res3Desc: "Официальный документ, регулирующий работу Совета.",
            btnDownload: "Скачать",
            memberSectionTitle: "Состав Студенческого совета",
            roleChairman: "Председатель",
            roleViceChairman: "Первый заместитель председателя",
            roleAdvisor: "Советник председателя",
            roleSecretary: "Секретарь / Глава Медиа сектора",
            roleScienceHead: "Глава сектора науки и образования",
            roleCultureHead: "Глава сектора культурной работы",
            roleCollegeVice: "Заместитель по колледжам",
            roleSportHead: "Глава спортивного сектора",
            roleMindHead: "Глава сектора интеллектуальных игр",
            roleSocialHead: "Глава сектора социальной работы",
            roleITHead: "Глава IT-сектора", 
            eventsTitle: "Мероприятия",
            event1Title: "Студенческий форум 2025",
            event1Date: "🗓️ 10 апреля, 2025 | 🏢 ОшГУ",
            event1VenueTitle: "Место проведения",
            event1Venue: "Главный корпус ОшГУ, 2-й этаж, Большой актовый зал",
            event1RegTitle: "Регистрация для участия",
            btnRegister: "Регистрация",
            event2Title: "Весенний благотворительный фестиваль",
            event2Date: "🗓️ 25 марта, 2025 | 🏢 Спортивная площадка ОшГУ",
            event2VenueTitle: "Место проведения",
            event2Venue: "Спортивная площадка ОшГУ",
            event2RegClosed: "Регистрация завершена.",
            galleryTitle: "Галерея",
            contactTitle: "Связаться состуденческим советом", 
            contactAddress: "ОшГУ, Главный корпус, 0-кабат, 001-кабинет",
            contactPhone: "+996 000 000 000)",
            contactEmail: "studentcouncil@oshmu.kg",
            contactNote: "Вы можете обратиться по вопросам новостей, мероприятий и другим предложениям.",
            btnSend: "Отправить",
            topicNews: "Отправить новость",
            topicEvent: "Предложить мероприятие",
            topicSuggestion: "Предложение/Отзыв",
            topicOther: "Другое",
            developer: "Разработано К.А.М."
        },
        en: {
            title: "OshSU Student Council",
            brandTitle: "OshSU Student Council",
            navAbout: "About Us",
            navNews: "News",
            navResources: "Resources",
            navMembers: "Council Members",
            navEvents: "Events",
            navGallery: "Gallery",
            navContact: "Contact",
            btnContact: "Contact Us",
            heroTitle: "OshSU Student Council — Your Voice",
            heroShortText: "The Student Council is a self-governing body for students at the university. Its main goal is to protect student interests, organize events, and serve as a bridge between the administration and students.",
            heroFunctionsTitle: "Key Functions:",
            func1: "Addressing university issues with the leadership",
            func2: "Organizing cultural, sports, and social events",
            func3: "Helping new students (adaptation, mentorship)",
            func4: "Providing support on scholarships and dormitory issues",
            func5: "Involving students in public activities",
            moreBtn: "Read More",
            fastLinks: "Quick Links",
            fastNews: "News",
            fastResources: "Resources",
            fastGallery: "Gallery",
            contactTitle: "Contact",
            address: "Address: Osh city, Alymbek Datka 331, OshSU main building",
            aboutTitle: "About Us",
            aboutShortText: "The origins of youth organizations in our country date back to the Soviet period. The current Youth Committee fulfills the mission of closely connecting students and leaders, operating as an authoritative student organization.",
            aboutP1: "After the victory of the October Revolution, the Komsomol, the youth wing of the Bolshevik party, was organized in August 1918. The organization was named after V.I. Lenin in 1918, and the VLKSM (All-Union Leninist Communist Youth League) existed until 1991.",
            aboutP2: "The Komsomol Committee at our educational institution began its activities from the moment the Osh Pedagogical Institute was founded in 1951. In 1992, the Student Senate began operating in place of the Komsomol Committee. The Student Senate was retained when the university was reorganized into Osh State University. In accordance with the Decree of the President of the Kyrgyz Republic on Youth Affairs dated December 10, 2000, the Student Senate was reorganized into the Youth Committee and began its work.",
            aboutP3: "Currently, the Youth Committee fulfills the mission of closely connecting students and leaders, operating as an authoritative student organization.",
            newsTitle: "Latest News",
            newsTagNew: "📣 NEW!",
            news1Title: "Application for Student Dormitories",
            news1Text: "Acceptance of applications for dormitory placement for the 2025-2026 academic year begins on June 1st.",
            newsTagEvent: "🎉 Event",
            news2Title: "Meeting with the Rector: Q&A Session",
            news2Text: "The traditional meeting between the Rector and students will be held on November 25th at 14:00 in the Grand Hall.",
            newsTagImportant: "❗️ IMPORTANT",
            news3Title: "Final Session Preparation Schedule",
            news3Text: "The session preparation schedule has been sent to the faculties. If there are changes, please contact the Dean's office.",
            btnMore: "Read More", 
            resourcesTitle: "Resource Center",
            res1Title: "Dormitory Application Form (PDF)",
            res1Desc: "Mandatory form to fill out to obtain a place in the dormitory.",
            res2Title: "List of documents for scholarship application",
            res2Desc: "List of documents required for social and Presidential scholarships.",
            res3Title: "OshSU Student Council Charter (Statute)",
            res3Desc: "Official document governing the work of the Council.",
            btnDownload: "Download",
            memberSectionTitle: "Council Members",
            roleChairman: "Chairman",
            roleViceChairman: "First Vice-Chairman",
            roleAdvisor: "Advisor to the Chairman",
            roleSecretary: "Secretary / Head of Media Sector",
            roleScienceHead: "Head of Science & Education Sector",
            roleCultureHead: "Head of Cultural Affairs Sector",
            roleCollegeVice: "Vice-Chairman for Colleges",
            roleSportHead: "Head of Sports Sector",
            roleMindHead: "Head of Intellectual Games Sector",
            roleSocialHead: "Head of Social Work Sector",
            roleITHead: "Head of IT Sector", 
            eventsTitle: "Events",
            event1Title: "Student Forum 2025",
            event1Date: "🗓️ April 10, 2025 | 🏢 OshSU",
            event1VenueTitle: "Venue",
            event1Venue: "OshSU Main Building, 2nd floor, Grand Assembly Hall",
            event1RegTitle: "Registration for Participation",
            btnRegister: "Register",
            event2Title: "Spring Charity Festival",
            event2Date: "🗓️ March 25, 2025 | 🏢 OshSU Sports Field",
            event2VenueTitle: "Venue",
            event2Venue: "OshSU Sports Field",
            event2RegClosed: "Registration is closed.",
            galleryTitle: "Gallery",
            contactTitle: "Contact the Student Council", 
            contactAddress: "OshSU, Main Building, 0th floor, Office 001",
            contactPhone: "+996 000 000 000",
            contactEmail: "studentcouncil@oshmu.kg",
            contactNote: "You can contact us regarding news, events, and other suggestions.",
            btnSend: "Send",
            topicNews: "Submit News",
            topicEvent: "Propose Event",
            topicSuggestion: "Suggestion/Feedback",
            topicOther: "Other",
            developer: "Developed by K.A.M."
        }
    };

    let currentLang = 'ky'; 

    function setLanguage(lang) {
        currentLang = lang;
        document.querySelectorAll('[data-key]').forEach(element => {
            const key = element.getAttribute('data-key');
            if (translations[lang][key]) {
                element.textContent = translations[lang][key];
            }
        });
        document.getElementById('langBtn').textContent = lang.toUpperCase();
        
        // Update hero and about button texts manually if they are in "Hide" state
        const hideText = lang === 'ky' ? 'Жашыруу' : (lang === 'ru' ? 'Скрыть' : 'Hide');

        document.getElementById('moreBtn').textContent = document.getElementById('fullText').style.maxHeight === '0px' || document.getElementById('fullText').style.maxHeight === '' ? translations[lang].moreBtn : hideText;
        document.getElementById('moreBtn_about').textContent = document.getElementById('fullText_about').style.maxHeight === '0px' || document.getElementById('fullText_about').style.maxHeight === '' ? translations[lang].moreBtn : hideText;

        // Update event buttons manually
        document.querySelectorAll('.more-info-btn').forEach(btn => {
            if (btn.classList.contains('active')) {
                btn.textContent = hideText;
            } else {
                btn.textContent = translations[lang].moreBtn;
            }
        });


        // Update dropdown placeholder color
        const selectElement = document.querySelector('.contact-form select');
        if (selectElement) {
            selectElement.style.color = lang === 'ky' ? 'var(--muted)' : 'var(--muted)';
        }
    }

    document.getElementById('langBtn').addEventListener('click', function() {
        // Switch through ky -> ru -> en -> ky
        let newLang;
        if (currentLang === 'ky') {
            newLang = 'ru';
        } else if (currentLang === 'ru') {
            newLang = 'en';
        } else {
            newLang = 'ky';
        }
        setLanguage(newLang);
    });

    // Set initial language
    setLanguage('ky');


    // ===================================
    // 3. DARK/LIGHT MODE
    // ===================================
    const darkModeToggle = document.getElementById('darkModeToggle');
    const body = document.body;

    function toggleDarkMode() {
        body.classList.toggle('dark-mode');
        // Save user preference
        const isDarkMode = body.classList.contains('dark-mode');
        localStorage.setItem('darkMode', isDarkMode);
        darkModeToggle.textContent = isDarkMode ? '🌙' : '☀️';
    }

    // Load preference from local storage
    if (localStorage.getItem('darkMode') === 'true') {
        body.classList.add('dark-mode');
        darkModeToggle.textContent = '🌙';
    } else {
        darkModeToggle.textContent = '☀️';
    }

    darkModeToggle.addEventListener('click', toggleDarkMode);


    // ===================================
    // 4. ГАЛЕРЕЯ (КАРУСЕЛЬ) ЖАНА LIGHTBOX
    // ===================================
    const imageList = [
        "1.jpeg",
        "2.jpeg",
        "3.jpeg",
        "4.jpeg",
        "5.jpeg",
        "6.jpeg",
    ];

    const carouselTrack = document.getElementById('carouselTrack');
    const prevBtn = document.getElementById('prevBtn');
    const nextBtn = document.getElementById('nextBtn');
    const lightbox = document.getElementById('lightbox');
    const lightboxImage = document.getElementById('lightboxImage');
    let currentIndex = 0;

    // Load images into carousel
    imageList.forEach((src, index) => {
        const card = document.createElement('div');
        card.className = 'card carousel-card';
        
        const img = document.createElement('img');
        img.src = src;
        img.alt = `Gallery Image ${index + 1}`;
        
        card.appendChild(img);
        carouselTrack.appendChild(card);
        
        card.addEventListener('click', () => {
            showLightbox(src);
        });
    });

    function updateCarousel() {
        // Calculate the translation necessary to show the current image/set
        const cardWidth = 275; // Card width (260) + gap (15)
        const offset = -currentIndex * cardWidth;
        carouselTrack.style.transform = `translateX(${offset}px)`;
    }

    nextBtn.addEventListener('click', () => {
        const totalItems = imageList.length;
        const visibleItems = Math.floor(carouselTrack.parentElement.clientWidth / 275);
        
        if (currentIndex < totalItems - visibleItems) {
            currentIndex++;
        } else {
            currentIndex = 0; // Loop back to start
        }
        updateCarousel();
    });

    prevBtn.addEventListener('click', () => {
        const totalItems = imageList.length;
        const visibleItems = Math.floor(carouselTrack.parentElement.clientWidth / 275);

        if (currentIndex > 0) {
            currentIndex--;
        } else {
            // Loop back to the end
            currentIndex = Math.max(0, totalItems - visibleItems); 
        }
        updateCarousel();
    });

    // Initial update and handle window resize
    window.addEventListener('resize', () => {
        updateCarousel();
    });
    updateCarousel();


    // Lightbox functions
    function showLightbox(src) {
        lightboxImage.src = src;
        lightbox.classList.add('show');
    }

    lightbox.addEventListener('click', () => {
        lightbox.classList.remove('show');
    });

    // ===================================
    // 5. ФОРМАЛАРДЫН ИШТЕШИ
    // ===================================
    document.getElementById('contactForm').addEventListener('submit', function(e) {
        e.preventDefault();
        alert(translations[currentLang].btnSend + ' ' + (currentLang === 'ky' ? 'ийгиликтүү жөнөтүлдү!' : (currentLang === 'ru' ? 'успешно отправлено!' : 'sent successfully!')));
        this.reset();
    });

    document.getElementById('event1Form').addEventListener('submit', function(e) {
        e.preventDefault();
        alert(translations[currentLang].event1Title + ' ' + (currentLang === 'ky' ? 'иш-чарасына ийгиликтүү катталдыңыз!' : (currentLang === 'ru' ? 'на мероприятие успешно зарегистрированы!' : 'event registration successful!')));
        this.reset();
    });


  </script>
</body>
</html>
