<!DOCTYPE html>
<html lang="kg">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeutschLernen · Кыргызча немис тили</title>
    <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Manrope:wght@400;500;600;700;800&family=Playfair+Display:wght@700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <style>
        *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

        :root {
            --kg-red: #c8102e;
            --de-gold: #ffce00;
            --de-black: #0d0d0d;
            --ru-blue: #0033a0;
            --light: #f5f0e8;
            --paper: #fffaf2;
            --white: #ffffff;
            --text: #151515;
            --muted: #666;
            --surface: #ffffff;
            --surface-2: #f8f1e6;
            --surface-dark: #141821;
            --surface-dark-2: #212837;
            --border: rgba(0, 0, 0, 0.08);
            --shadow: 0 24px 50px rgba(13, 13, 13, 0.08);
            --font-display: 'Bebas Neue', sans-serif;
            --font-body: 'Manrope', sans-serif;
            --font-serif: 'Playfair Display', serif;
            --r-sm: 10px;
            --r-md: 18px;
            --r-lg: 28px;
            --r-xl: 40px;
            --r-full: 999px;
        }

        body {
            font-family: var(--font-body);
            background: var(--light);
            color: var(--text);
            overflow-x: hidden;
        }

        body.theme-dark {
            --light: #0f1117;
            --paper: #111621;
            --text: #f5f0e8;
            --muted: rgba(255, 255, 255, 0.72);
            --surface: #171c28;
            --surface-2: #222939;
            --border: rgba(255, 255, 255, 0.08);
            --shadow: 0 24px 50px rgba(0, 0, 0, 0.28);
        }

        html { scroll-behavior: smooth; }
        a { color: inherit; text-decoration: none; }
        button, input, textarea, select { font: inherit; }
        button { cursor: pointer; }

        .hidden { display: none !important; }

        #progress-bar {
            position: fixed;
            top: 0;
            left: 0;
            width: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--kg-red), var(--de-gold), var(--ru-blue));
            z-index: 3000;
        }

        .top-strip {
            background: var(--de-black);
            color: rgba(255, 255, 255, 0.88);
            border-bottom: 2px solid var(--de-gold);
            position: relative;
            z-index: 1200;
        }

        .top-inner,
        .nav-inner,
        .section-wrap,
        .footer-inner {
            width: min(1380px, calc(100% - 40px));
            margin: 0 auto;
        }

        .top-inner {
            padding: 12px 0;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 18px;
            flex-wrap: wrap;
        }

        .lang-pills,
        .top-actions,
        .streak-chip {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .lang-pills {
            background: rgba(255, 255, 255, 0.08);
            border-radius: var(--r-full);
            padding: 6px;
        }

        .lang-pill {
            border: none;
            padding: 10px 18px;
            border-radius: var(--r-full);
            background: transparent;
            color: rgba(255, 255, 255, 0.62);
            font-weight: 800;
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .lang-pill.active {
            background: var(--de-gold);
            color: var(--de-black);
        }

        .streak-chip,
        .theme-btn,
        .ghost-btn,
        .solid-btn,
        .tool-btn,
        .quiz-btn,
        .share-btn,
        .small-btn {
            border-radius: var(--r-full);
            border: 2px solid transparent;
            transition: transform 0.2s ease, background 0.2s ease, border-color 0.2s ease, color 0.2s ease;
        }

        .streak-chip {
            padding: 9px 14px;
            background: rgba(255, 255, 255, 0.08);
            font-weight: 700;
        }

        .theme-btn,
        .ghost-btn,
        .solid-btn {
            padding: 10px 18px;
            font-weight: 800;
            border: none;
        }

        .theme-btn,
        .ghost-btn {
            background: rgba(255, 255, 255, 0.1);
            color: white;
        }

        .solid-btn {
            background: var(--de-gold);
            color: var(--de-black);
        }

        .theme-btn:hover,
        .ghost-btn:hover,
        .solid-btn:hover,
        .tool-btn:hover,
        .quiz-btn:hover,
        .share-btn:hover,
        .small-btn:hover {
            transform: translateY(-2px);
        }

        .navbar {
            position: sticky;
            top: 0;
            z-index: 1100;
            backdrop-filter: blur(18px);
            background: color-mix(in srgb, var(--paper) 92%, transparent);
            border-bottom: 1px solid var(--border);
        }

        .nav-inner {
            height: 76px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 18px;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-family: var(--font-display);
            letter-spacing: 2px;
            font-size: 1.9rem;
        }

        .logo-badge {
            width: 44px;
            height: 44px;
            border-radius: 14px;
            display: grid;
            place-items: center;
            background: var(--de-black);
            color: var(--de-gold);
        }

        .nav-links,
        .nav-actions {
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .nav-link {
            padding: 10px 16px;
            border-radius: var(--r-full);
            color: var(--muted);
            font-weight: 700;
        }

        .nav-link.active,
        .nav-link:hover {
            background: rgba(200, 16, 46, 0.08);
            color: var(--kg-red);
        }

        .hamburger {
            display: none;
            width: 44px;
            height: 44px;
            border-radius: 14px;
            border: 1px solid var(--border);
            background: var(--surface);
            align-items: center;
            justify-content: center;
            flex-direction: column;
            gap: 4px;
        }

        .hamburger span {
            width: 22px;
            height: 2px;
            background: var(--text);
            border-radius: 2px;
        }

        .mobile-nav {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(13, 13, 13, 0.96);
            z-index: 2000;
            padding: 120px 24px 40px;
        }

        .mobile-nav.open { display: block; }

        .mobile-links {
            display: grid;
            gap: 14px;
        }

        .mobile-link {
            padding: 18px 20px;
            border-radius: 20px;
            background: rgba(255, 255, 255, 0.06);
            color: white;
            font-family: var(--font-display);
            letter-spacing: 2px;
            font-size: 2rem;
        }

        .hero-bg {
            position: relative;
            overflow: hidden;
        }

        .hero-bg::before {
            content: '';
            position: absolute;
            inset: 0;
            background:
                radial-gradient(circle at 15% 20%, rgba(200, 16, 46, 0.14), transparent 30%),
                radial-gradient(circle at 85% 15%, rgba(255, 206, 0, 0.16), transparent 28%),
                linear-gradient(180deg, transparent, rgba(13, 13, 13, 0.02));
            pointer-events: none;
        }

        .hero {
            position: relative;
            min-height: 90vh;
            display: grid;
            grid-template-columns: 1.05fr 0.95fr;
            align-items: center;
            gap: 48px;
            padding: 72px 0 90px;
        }

        .hero-tag,
        .section-tag,
        .badge,
        .mini-pill {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            font-size: 0.82rem;
            font-weight: 800;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            border-radius: var(--r-full);
        }

        .hero-tag {
            margin-bottom: 20px;
            padding: 10px 18px;
            background: var(--de-black);
            color: var(--de-gold);
        }

        .hero-title,
        .section-title,
        .card-title,
        .feature-title {
            font-family: var(--font-display);
            letter-spacing: 2px;
            line-height: 0.95;
        }

        .hero-title {
            font-size: clamp(3.6rem, 8vw, 7rem);
            margin-bottom: 22px;
        }

        .hero-title span:last-child { color: var(--kg-red); }

        .hero-copy {
            max-width: 560px;
            color: var(--muted);
            font-size: 1.08rem;
            line-height: 1.8;
            margin-bottom: 34px;
        }

        .hero-actions {
            display: flex;
            gap: 14px;
            flex-wrap: wrap;
            margin-bottom: 38px;
        }

        .hero-stats,
        .mini-stats,
        .course-grid,
        .feature-grid,
        .teacher-grid,
        .testimonial-grid,
        .dialogue-grid,
        .faq-grid,
        .footer-grid {
            display: grid;
            gap: 24px;
        }

        .hero-stats {
            grid-template-columns: repeat(3, 1fr);
        }

        .hero-stat,
        .mini-stat {
            padding: 20px;
            border-radius: 24px;
            background: var(--surface);
            box-shadow: var(--shadow);
            border: 1px solid var(--border);
        }

        .hero-stat-num,
        .mini-number {
            font-family: var(--font-display);
            font-size: 2rem;
            color: var(--kg-red);
            letter-spacing: 1px;
        }

        .hero-stat-label,
        .mini-label {
            margin-top: 6px;
            color: var(--muted);
            font-size: 0.84rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .hero-card {
            background: linear-gradient(145deg, #111726, #1f2737);
            color: white;
            border-radius: var(--r-xl);
            padding: 30px;
            box-shadow: 0 28px 60px rgba(13, 13, 13, 0.2);
            border: 2px solid rgba(255, 206, 0, 0.24);
            position: relative;
            overflow: hidden;
        }

        .hero-card::before {
            content: '';
            position: absolute;
            inset: auto -40px -60px auto;
            width: 190px;
            height: 190px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(255, 206, 0, 0.22), transparent 70%);
        }

        .rotator-card,
        .hero-floating {
            border-radius: 24px;
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .rotator-card {
            padding: 28px;
            margin-top: 18px;
        }

        .rotator-word {
            font-family: var(--font-display);
            color: var(--de-gold);
            font-size: 4rem;
            letter-spacing: 3px;
            margin-bottom: 14px;
        }

        .rotator-translations {
            display: grid;
            gap: 10px;
            color: rgba(255, 255, 255, 0.84);
        }

        .hero-floating {
            display: flex;
            justify-content: space-between;
            gap: 16px;
            padding: 16px 18px;
            margin-bottom: 14px;
        }

        .floating-label {
            color: rgba(255, 255, 255, 0.64);
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 700;
        }

        .floating-value {
            font-weight: 800;
            font-size: 1.1rem;
        }

        .section-wrap {
            padding: 92px 0;
        }

        .dark-section {
            background: linear-gradient(160deg, #141821, #202637);
            color: white;
        }

        .section-head {
            margin-bottom: 38px;
        }

        .section-tag {
            padding: 8px 16px;
            background: rgba(200, 16, 46, 0.08);
            color: var(--kg-red);
            margin-bottom: 16px;
        }

        .dark-section .section-tag {
            background: rgba(255, 206, 0, 0.12);
            color: var(--de-gold);
        }

        .section-title {
            font-size: clamp(2.6rem, 6vw, 4.6rem);
            margin-bottom: 14px;
        }

        .section-copy {
            max-width: 740px;
            color: var(--muted);
            line-height: 1.8;
        }

        .dark-section .section-copy { color: rgba(255, 255, 255, 0.72); }

        .course-grid {
            grid-template-columns: repeat(3, 1fr);
        }

        .course-card,
        .feature-card,
        .teacher-card,
        .testimonial-card,
        .dialogue-card,
        .faq-card,
        .newsletter,
        .quiz-card,
        .flashcard-panel,
        .placement-card {
            border-radius: var(--r-lg);
            background: var(--surface);
            border: 1px solid var(--border);
            box-shadow: var(--shadow);
        }

        .course-card {
            overflow: hidden;
        }

        .course-top {
            padding: 28px;
            color: white;
            position: relative;
            min-height: 180px;
        }

        .course-top.a1 { background: linear-gradient(135deg, #1d2030, #2b2f47); }
        .course-top.a2 { background: linear-gradient(135deg, #00365e, #1b5a87); }
        .course-top.b1 { background: linear-gradient(135deg, #571400, #7d2200); }

        .course-level {
            position: absolute;
            right: 24px;
            top: 18px;
            font-family: var(--font-display);
            font-size: 4.6rem;
            color: rgba(255, 255, 255, 0.12);
        }

        .card-title {
            font-size: 2rem;
        }

        .course-body,
        .feature-card,
        .teacher-card,
        .testimonial-card,
        .dialogue-card,
        .faq-card,
        .quiz-card,
        .placement-card {
            padding: 28px;
        }

        .course-copy,
        .card-copy,
        .teacher-bio,
        .testimonial-text,
        .dialogue-copy {
            color: var(--muted);
            line-height: 1.7;
        }

        .course-list,
        .teacher-meta,
        .vocab-list,
        .badge-list,
        .leaderboard-list,
        .faq-list {
            display: grid;
            gap: 12px;
        }

        .course-item,
        .teacher-meta-row,
        .vocab-item,
        .badge-item,
        .leaderboard-item,
        .faq-item {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .course-item i,
        .teacher-meta-row i {
            color: #21c49c;
        }

        .practice-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 28px;
        }

        .flashcard-panel,
        .quiz-card {
            background: rgba(255, 255, 255, 0.06);
            border-color: rgba(255, 255, 255, 0.1);
            box-shadow: none;
            color: white;
        }

        .flashcard-scene {
            perspective: 1000px;
            height: 340px;
            margin-bottom: 18px;
        }

        .flashcard {
            position: relative;
            width: 100%;
            height: 100%;
            transform-style: preserve-3d;
            transition: transform 0.7s ease;
        }

        .flashcard.flipped { transform: rotateY(180deg); }

        .flash-face {
            position: absolute;
            inset: 0;
            border-radius: var(--r-lg);
            padding: 28px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            backface-visibility: hidden;
        }

        .flash-front {
            background: linear-gradient(135deg, #0d1117, #273142);
            border: 2px solid rgba(255, 206, 0, 0.35);
        }

        .flash-back {
            background: linear-gradient(135deg, #8c1327, #bf2038);
            transform: rotateY(180deg);
        }

        .flash-hint {
            position: absolute;
            top: 18px;
            font-size: 0.78rem;
            color: rgba(255, 255, 255, 0.66);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1.3px;
        }

        .flash-word {
            font-family: var(--font-display);
            font-size: 3.3rem;
            letter-spacing: 2px;
            color: var(--de-gold);
            line-height: 1;
        }

        .flash-back .flash-word {
            color: white;
            font-size: 2.7rem;
        }

        .flash-example {
            margin-top: 14px;
            color: rgba(255, 255, 255, 0.76);
            max-width: 430px;
            line-height: 1.7;
        }

        .panel-actions,
        .quiz-actions,
        .placement-options,
        .small-actions {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .tool-btn,
        .share-btn,
        .small-btn {
            border: none;
            padding: 12px 16px;
            font-weight: 800;
        }

        .tool-btn {
            background: rgba(255, 255, 255, 0.1);
            color: white;
        }

        .tool-btn.primary { background: var(--de-gold); color: var(--de-black); }

        .progress-row {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-top: 16px;
        }

        .progress-bar {
            flex: 1;
            height: 8px;
            border-radius: var(--r-full);
            background: rgba(255, 255, 255, 0.1);
            overflow: hidden;
        }

        .progress-fill {
            width: 0;
            height: 100%;
            background: var(--de-gold);
            border-radius: inherit;
        }

        .panel-status {
            margin-top: 14px;
            padding: 14px 16px;
            border-radius: 18px;
            background: rgba(255, 255, 255, 0.08);
            color: rgba(255, 255, 255, 0.86);
            line-height: 1.6;
        }

        .quiz-head {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 12px;
            margin-bottom: 16px;
        }

        .quiz-title,
        .feature-title {
            font-family: var(--font-display);
            letter-spacing: 2px;
            font-size: 2rem;
        }

        .quiz-score {
            padding: 8px 14px;
            background: rgba(255, 255, 255, 0.08);
            border-radius: var(--r-full);
            color: var(--de-gold);
            font-weight: 800;
        }

        .quiz-question {
            font-size: 1.1rem;
            color: rgba(255, 255, 255, 0.8);
            margin-bottom: 14px;
        }

        .quiz-word {
            font-family: var(--font-display);
            color: var(--de-gold);
            font-size: 2.7rem;
            letter-spacing: 2px;
            margin-bottom: 18px;
        }

        .quiz-options {
            display: grid;
            gap: 10px;
        }

        .quiz-option,
        .placement-option {
            width: 100%;
            border: 2px solid rgba(255, 255, 255, 0.12);
            background: rgba(255, 255, 255, 0.06);
            color: white;
            padding: 14px 18px;
            border-radius: 18px;
            text-align: left;
            font-weight: 700;
        }

        .quiz-option.correct,
        .placement-option.correct {
            background: rgba(0, 184, 148, 0.2);
            border-color: #00b894;
        }

        .quiz-option.wrong,
        .placement-option.wrong {
            background: rgba(231, 76, 60, 0.2);
            border-color: #e74c3c;
        }

        .quiz-feedback {
            margin-top: 14px;
            min-height: 28px;
            color: rgba(255, 255, 255, 0.84);
            font-weight: 700;
        }

        .share-btn {
            background: var(--de-gold);
            color: var(--de-black);
        }

        .feature-grid {
            grid-template-columns: repeat(2, 1fr);
            margin-top: 32px;
        }

        .mini-pill {
            padding: 7px 12px;
            background: rgba(255, 206, 0, 0.14);
            color: var(--text);
        }

        .feature-head {
            display: flex;
            align-items: flex-start;
            justify-content: space-between;
            gap: 16px;
            margin-bottom: 16px;
        }

        .feature-kicker {
            font-size: 0.8rem;
            font-weight: 800;
            letter-spacing: 1.4px;
            text-transform: uppercase;
            color: var(--kg-red);
            margin-bottom: 8px;
        }

        .feature-copy {
            color: var(--muted);
            line-height: 1.75;
            margin-bottom: 16px;
        }

        .mini-stats {
            grid-template-columns: repeat(3, 1fr);
        }

        .dashboard-bars {
            display: grid;
            gap: 14px;
            margin-top: 18px;
        }

        .dash-row {
            display: grid;
            grid-template-columns: 140px 1fr 56px;
            gap: 12px;
            align-items: center;
        }

        .dash-track {
            height: 10px;
            background: var(--surface-2);
            border-radius: var(--r-full);
            overflow: hidden;
        }

        .dash-fill {
            height: 100%;
            width: 0;
            background: linear-gradient(90deg, var(--kg-red), var(--de-gold));
        }

        .vocab-item,
        .badge-item,
        .leaderboard-item {
            justify-content: space-between;
            padding: 14px 16px;
            border-radius: 18px;
            background: var(--surface-2);
        }

        .vocab-word {
            font-weight: 800;
            color: var(--text);
        }

        .small-btn {
            background: var(--surface);
            border: 1px solid var(--border);
            color: var(--text);
            padding: 10px 14px;
        }

        .grammar-tabs {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 16px;
        }

        .grammar-tab {
            border: 1px solid var(--border);
            background: var(--surface-2);
            padding: 10px 15px;
            border-radius: var(--r-full);
            font-weight: 800;
        }

        .grammar-tab.active {
            background: var(--de-black);
            color: white;
        }

        .grammar-panel {
            display: none;
        }

        .grammar-panel.active { display: block; }

        .grammar-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 12px;
            overflow: hidden;
            border-radius: 18px;
        }

        .grammar-table th,
        .grammar-table td {
            padding: 12px 14px;
            border-bottom: 1px solid var(--border);
            text-align: left;
        }

        .grammar-table th {
            background: var(--surface-2);
        }

        .placement-card {
            background: linear-gradient(135deg, #fff9ef, #fff1d8);
        }

        body.theme-dark .placement-card {
            background: linear-gradient(135deg, #1a2130, #232b3d);
        }

        .placement-option {
            color: var(--text);
            background: var(--surface);
            border-color: var(--border);
        }

        .placement-status {
            margin-top: 16px;
            padding: 14px 16px;
            border-radius: 16px;
            background: rgba(255, 206, 0, 0.15);
            font-weight: 700;
            line-height: 1.6;
        }

        .dialogue-grid {
            grid-template-columns: repeat(3, 1fr);
        }

        .dialogue-card {
            background: linear-gradient(160deg, #151a27, #1f2637);
            color: white;
            border-color: rgba(255, 255, 255, 0.1);
        }

        .dialogue-title {
            font-family: var(--font-display);
            font-size: 1.8rem;
            letter-spacing: 1.5px;
            margin-bottom: 10px;
        }

        .dialogue-lines {
            display: grid;
            gap: 12px;
            margin-top: 14px;
        }

        .dialogue-line {
            padding: 12px 0;
            border-bottom: 1px dashed rgba(255, 255, 255, 0.12);
        }

        .dialogue-line:last-child { border-bottom: none; }

        .speaker {
            color: var(--de-gold);
            font-weight: 800;
        }

        .transcript-tabs {
            display: flex;
            gap: 8px;
            margin-top: 16px;
            flex-wrap: wrap;
        }

        .transcript-tab {
            border: 1px solid rgba(255, 255, 255, 0.16);
            background: rgba(255, 255, 255, 0.08);
            color: white;
            padding: 8px 12px;
            border-radius: var(--r-full);
            font-weight: 700;
        }

        .transcript-tab.active {
            background: var(--de-gold);
            color: var(--de-black);
        }

        .teacher-grid,
        .testimonial-grid,
        .footer-grid {
            grid-template-columns: repeat(3, 1fr);
        }

        .teacher-card,
        .testimonial-card {
            text-align: center;
        }

        .avatar {
            width: 96px;
            height: 96px;
            border-radius: 50%;
            margin: 0 auto 16px;
            display: grid;
            place-items: center;
            font-family: var(--font-display);
            font-size: 2rem;
            color: white;
            background: linear-gradient(135deg, var(--kg-red), var(--ru-blue));
        }

        .teacher-name,
        .testimonial-name {
            font-family: var(--font-display);
            font-size: 1.8rem;
            letter-spacing: 1.2px;
        }

        .teacher-role,
        .testimonial-city {
            color: var(--kg-red);
            font-weight: 800;
            margin: 6px 0 10px;
        }

        .teacher-meta {
            margin-top: 14px;
        }

        .testimonial-stars {
            margin-top: 14px;
            color: var(--de-gold);
        }

        .faq-grid {
            grid-template-columns: 1fr;
        }

        .faq-card {
            padding: 0;
            overflow: hidden;
        }

        .faq-item {
            flex-direction: column;
            align-items: stretch;
            gap: 0;
            border-bottom: 1px solid var(--border);
        }

        .faq-item:last-child { border-bottom: none; }

        .faq-question {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 14px;
            padding: 22px 24px;
            background: transparent;
            border: none;
            width: 100%;
            text-align: left;
            font-weight: 800;
            color: var(--text);
        }

        .faq-answer {
            display: none;
            padding: 0 24px 22px;
            color: var(--muted);
            line-height: 1.75;
        }

        .faq-item.open .faq-answer { display: block; }

        .newsletter {
            padding: 36px;
            background: linear-gradient(135deg, var(--kg-red), var(--de-black));
            color: white;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 26px;
            align-items: center;
        }

        .newsletter-title {
            font-family: var(--font-display);
            font-size: 3rem;
            letter-spacing: 2px;
            line-height: 0.95;
            margin-bottom: 12px;
        }

        .newsletter-copy {
            color: rgba(255, 255, 255, 0.8);
            line-height: 1.7;
        }

        .newsletter-form {
            display: grid;
            gap: 12px;
        }

        .newsletter-input {
            width: 100%;
            border: 2px solid rgba(255, 255, 255, 0.16);
            background: rgba(255, 255, 255, 0.08);
            color: white;
            padding: 15px 18px;
            border-radius: var(--r-full);
            outline: none;
        }

        .newsletter-input::placeholder {
            color: rgba(255, 255, 255, 0.6);
        }

        .footer {
            background: var(--de-black);
            color: rgba(255, 255, 255, 0.84);
        }

        .footer-inner {
            padding: 70px 0 38px;
        }

        .footer-grid {
            gap: 30px;
            margin-bottom: 30px;
        }

        .footer-title {
            font-family: var(--font-display);
            letter-spacing: 1.6px;
            font-size: 1.4rem;
            margin-bottom: 14px;
            color: white;
        }

        .footer-copy {
            color: rgba(255, 255, 255, 0.72);
            line-height: 1.7;
        }

        .footer-links {
            display: grid;
            gap: 10px;
        }

        .footer-links button {
            text-align: left;
            border: none;
            background: transparent;
            color: rgba(255, 255, 255, 0.72);
        }

        .footer-bottom {
            padding-top: 18px;
            border-top: 1px solid rgba(255, 255, 255, 0.08);
            display: flex;
            justify-content: space-between;
            gap: 14px;
            flex-wrap: wrap;
            color: rgba(255, 255, 255, 0.6);
        }

        #back-to-top {
            position: fixed;
            right: 24px;
            bottom: 24px;
            width: 52px;
            height: 52px;
            border-radius: 50%;
            border: none;
            background: var(--de-black);
            color: var(--de-gold);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 1600;
            box-shadow: var(--shadow);
        }

        #back-to-top.visible { display: inline-flex; }

        /* Social links */
        .footer-socials { display:flex; gap:10px; margin-top:18px; flex-wrap:wrap; }
        .social-btn { width:40px;height:40px;border-radius:50%;background:rgba(255,255,255,0.1);color:rgba(255,255,255,0.8);display:inline-flex;align-items:center;justify-content:center;font-size:1.1rem;transition:background 0.2s,transform 0.2s,color 0.2s;text-decoration:none; }
        .social-btn:hover { background:var(--de-gold);color:var(--de-black);transform:translateY(-3px); }

        /* Toast */
        #toast-container { position:fixed;bottom:90px;right:24px;z-index:4000;display:flex;flex-direction:column;gap:10px;pointer-events:none; }
        .toast { background:var(--de-black);color:white;padding:14px 20px;border-radius:14px;border-left:4px solid var(--de-gold);font-weight:700;font-size:0.9rem;box-shadow:0 8px 28px rgba(0,0,0,0.25);animation:toastIn 0.3s ease,toastOut 0.3s ease 2.7s forwards;pointer-events:auto;max-width:320px; }
        .toast.success { border-color:#21c49c; }
        .toast.error { border-color:#e74c3c; }
        @keyframes toastIn { from{opacity:0;transform:translateY(16px)}to{opacity:1;transform:translateY(0)} }
        @keyframes toastOut { from{opacity:1}to{opacity:0;transform:translateY(-8px)} }

        /* Modal */
        .modal-overlay { display:none;position:fixed;inset:0;background:rgba(13,13,13,0.72);backdrop-filter:blur(6px);z-index:3000;align-items:center;justify-content:center;padding:24px; }
        .modal-overlay.open { display:flex; }
        .modal-box { background:var(--paper);border-radius:var(--r-xl);padding:40px;width:100%;max-width:480px;position:relative;box-shadow:0 32px 80px rgba(0,0,0,0.3);border:1px solid var(--border);animation:modalIn 0.3s cubic-bezier(.34,1.56,.64,1); }
        body.theme-dark .modal-box { background:var(--surface); }
        .modal-box.wide { max-width:620px; }
        @keyframes modalIn { from{opacity:0;transform:scale(0.92) translateY(20px)}to{opacity:1;transform:scale(1) translateY(0)} }
        .modal-close { position:absolute;top:16px;right:16px;width:36px;height:36px;border-radius:50%;border:none;background:var(--surface-2);color:var(--text);font-size:1rem;display:grid;place-items:center;cursor:pointer;transition:background 0.2s; }
        .modal-close:hover { background:var(--kg-red);color:white; }
        .modal-title { font-family:var(--font-display);font-size:2.4rem;letter-spacing:2px;margin-bottom:6px;color:var(--text); }
        .modal-sub { color:var(--muted);margin-bottom:28px;line-height:1.6; }
        .modal-field { margin-bottom:16px; }
        .modal-label { display:block;font-weight:800;font-size:0.85rem;text-transform:uppercase;letter-spacing:1px;margin-bottom:8px;color:var(--muted); }
        .modal-input { width:100%;border:2px solid var(--border);background:var(--surface-2);color:var(--text);padding:14px 18px;border-radius:var(--r-md);font:inherit;font-size:1rem;outline:none;transition:border-color 0.2s; }
        .modal-input:focus { border-color:var(--kg-red); }
        .modal-actions { display:flex;gap:12px;margin-top:24px; }
        .modal-actions .solid-btn,.modal-actions .ghost-btn-modal { flex:1;padding:14px;font-size:1rem;border:none;border-radius:var(--r-full);cursor:pointer;font:inherit;font-weight:800; }
        .modal-actions .ghost-btn-modal { background:var(--surface-2);color:var(--text); }
        .modal-switch { text-align:center;margin-top:18px;color:var(--muted);font-size:0.9rem; }
        .modal-switch button { border:none;background:transparent;color:var(--kg-red);font-weight:800;cursor:pointer;font:inherit; }
        .modal-divider { display:flex;align-items:center;gap:14px;margin:20px 0;color:var(--muted);font-size:0.85rem; }
        .modal-divider::before,.modal-divider::after { content:'';flex:1;height:1px;background:var(--border); }
        .teacher-modal-header { display:flex;gap:24px;align-items:flex-start;margin-bottom:24px; }
        .teacher-modal-avatar { width:80px;height:80px;border-radius:50%;flex-shrink:0;display:grid;place-items:center;font-family:var(--font-display);font-size:2rem;color:white;background:linear-gradient(135deg,var(--kg-red),var(--ru-blue)); }
        .course-modal-header { padding:32px 32px 24px;border-radius:20px;color:white;position:relative;overflow:hidden;margin-bottom:24px; }
        .course-modal-header.a1 { background:linear-gradient(135deg,#1d2030,#2b2f47); }
        .course-modal-header.a2 { background:linear-gradient(135deg,#00365e,#1b5a87); }
        .course-modal-header.b1 { background:linear-gradient(135deg,#571400,#7d2200); }
        .course-modal-level { font-family:var(--font-display);font-size:5rem;color:rgba(255,255,255,0.15);position:absolute;right:30px;top:10px; }
        .course-feats-grid { display:grid;grid-template-columns:1fr 1fr;gap:10px;margin:16px 0; }
        .course-feat-item { display:flex;align-items:center;gap:8px;padding:10px 12px;background:var(--surface-2);border-radius:12px;font-size:0.9rem;font-weight:700; }
        .course-feat-item i { color:#21c49c; }

        @media (max-width: 1180px) {
            .hero,
            .newsletter,
            .practice-grid,
            .feature-grid,
            .teacher-grid,
            .testimonial-grid,
            .dialogue-grid,
            .course-grid {
                grid-template-columns: 1fr;
            }

            .hero {
                min-height: auto;
                padding-top: 48px;
            }

            .mini-stats {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 900px) {
            .nav-links,
            .nav-actions {
                display: none;
            }

            .hamburger {
                display: inline-flex;
            }

            .hero-stats,
            .footer-grid {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 640px) {
            .top-inner,
            .section-wrap,
            .footer-inner,
            .nav-inner {
                width: min(100% - 28px, 1380px);
            }

            .top-inner {
                align-items: stretch;
            }

            .lang-pills {
                width: 100%;
                justify-content: center;
            }

            .lang-pill {
                flex: 1;
                padding-inline: 12px;
                font-size: 0.76rem;
            }

            .hero-title {
                font-size: 3.2rem;
            }

            .hero-actions,
            .panel-actions,
            .quiz-actions {
                flex-direction: column;
            }

            .dash-row {
                grid-template-columns: 1fr;
            }

            .newsletter {
                padding: 28px;
            }

            .newsletter-title {
                font-size: 2.4rem;
            }
        }

        /* ═══════ STUDENT DASHBOARD ═══════ */
        #student-dashboard {
            display: none;
            min-height: 100vh;
            background: var(--light);
        }
        #student-dashboard.active { display: block; }
        .main-site { transition: opacity 0.3s; }
        .main-site.hidden-site { display: none; }

        .db-wrap {
            width: min(1380px, calc(100% - 40px));
            margin: 0 auto;
            padding: 40px 0 80px;
        }

        /* Profile hero */
        .db-profile-hero {
            background: linear-gradient(135deg, var(--de-black) 60%, #1a1000);
            border-radius: var(--r-xl);
            padding: 36px 40px;
            display: flex;
            align-items: center;
            gap: 32px;
            margin-bottom: 32px;
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(255,206,0,0.18);
        }
        .db-profile-hero::before {
            content:'';
            position:absolute;
            inset: auto -60px -80px auto;
            width:260px; height:260px;
            border-radius:50%;
            background: radial-gradient(circle, rgba(255,206,0,0.14), transparent 70%);
            pointer-events:none;
        }
        .db-avatar-wrap { position:relative; flex-shrink:0; }
        .db-avatar {
            width:96px; height:96px; border-radius:50%;
            background: linear-gradient(135deg, var(--kg-red), var(--ru-blue));
            display:grid; place-items:center;
            font-family:var(--font-display); font-size:2.6rem; color:white;
            border:3px solid var(--de-gold);
        }
        .db-online-dot {
            position:absolute; bottom:4px; right:4px;
            width:16px; height:16px; border-radius:50%;
            background:#21c49c; border:3px solid var(--de-black);
        }
        .db-profile-info { flex:1; }
        .db-name {
            font-family:var(--font-display); font-size:2.6rem;
            letter-spacing:2px; color:white; margin-bottom:4px;
        }
        .db-major { color:rgba(255,255,255,0.6); font-size:0.9rem; font-weight:700; text-transform:uppercase; letter-spacing:1.2px; margin-bottom:12px; }
        .db-level-badge {
            display:inline-flex; align-items:center; gap:8px;
            padding:8px 16px; border-radius:var(--r-full);
            background:rgba(255,206,0,0.15); border:1px solid rgba(255,206,0,0.3);
            color:var(--de-gold); font-weight:800; font-size:0.9rem;
        }
        .db-profile-actions { display:flex; gap:12px; flex-wrap:wrap; align-items:center; }
        .db-btn-primary {
            padding:12px 24px; border-radius:var(--r-full); border:none;
            background:var(--de-gold); color:var(--de-black);
            font-weight:800; font-size:0.9rem; cursor:pointer;
            transition:transform 0.2s, opacity 0.2s;
        }
        .db-btn-primary:hover { transform:translateY(-2px); opacity:0.9; }
        .db-btn-ghost {
            padding:12px 24px; border-radius:var(--r-full);
            border:2px solid rgba(255,255,255,0.2);
            background:transparent; color:rgba(255,255,255,0.8);
            font-weight:800; font-size:0.9rem; cursor:pointer;
            transition:transform 0.2s, border-color 0.2s;
        }
        .db-btn-ghost:hover { transform:translateY(-2px); border-color:var(--de-gold); color:var(--de-gold); }

        /* XP bar */
        .db-xp-row {
            margin-top:16px; display:flex; align-items:center; gap:14px;
        }
        .db-xp-track {
            flex:1; height:10px; border-radius:var(--r-full);
            background:rgba(255,255,255,0.1); overflow:hidden;
        }
        .db-xp-fill {
            height:100%;
            background:linear-gradient(90deg,var(--kg-red),var(--de-gold));
            border-radius:inherit; transition:width 1s cubic-bezier(.4,0,.2,1);
        }
        .db-xp-label { color:rgba(255,255,255,0.7); font-size:0.82rem; font-weight:700; white-space:nowrap; }

        /* Stats grid */
        .db-stats-grid {
            display:grid;
            grid-template-columns:repeat(4,1fr);
            gap:16px;
            margin-bottom:28px;
        }
        .db-stat-card {
            background:var(--surface); border:1px solid var(--border);
            border-radius:var(--r-lg); padding:24px 20px;
            box-shadow:var(--shadow);
            display:flex; align-items:center; gap:16px;
            transition:transform 0.2s;
        }
        .db-stat-card:hover { transform:translateY(-3px); }
        .db-stat-icon {
            width:52px; height:52px; border-radius:16px;
            display:grid; place-items:center; font-size:1.3rem; flex-shrink:0;
        }
        .db-stat-icon.fire { background:rgba(255,143,50,0.12); color:#ff8f32; }
        .db-stat-icon.star { background:rgba(255,206,0,0.12); color:var(--de-gold); }
        .db-stat-icon.book { background:rgba(0,51,160,0.1); color:var(--ru-blue); }
        .db-stat-icon.check { background:rgba(33,196,156,0.12); color:#21c49c; }
        .db-stat-num { font-family:var(--font-display); font-size:2.2rem; color:var(--text); letter-spacing:1px; line-height:1; }
        .db-stat-lbl { color:var(--muted); font-size:0.8rem; font-weight:700; text-transform:uppercase; letter-spacing:1px; margin-top:4px; }

        /* Main 2-col layout */
        .db-main-grid {
            display:grid;
            grid-template-columns:1fr 360px;
            gap:24px;
            align-items:start;
        }
        .db-left { display:grid; gap:24px; }
        .db-right { display:grid; gap:24px; }

        /* Card base */
        .db-card {
            background:var(--surface); border:1px solid var(--border);
            border-radius:var(--r-lg); padding:28px;
            box-shadow:var(--shadow);
        }
        .db-card-title {
            font-family:var(--font-display); font-size:1.6rem;
            letter-spacing:1.5px; color:var(--text); margin-bottom:6px;
        }
        .db-card-sub { color:var(--muted); font-size:0.85rem; margin-bottom:20px; font-weight:600; }

        /* Progress bars */
        .db-prog-item { margin-bottom:18px; }
        .db-prog-item:last-child { margin-bottom:0; }
        .db-prog-header { display:flex; justify-content:space-between; align-items:center; margin-bottom:8px; }
        .db-prog-name { font-weight:800; font-size:0.9rem; color:var(--text); }
        .db-prog-pct { font-weight:800; font-size:0.9rem; color:var(--kg-red); }
        .db-prog-track { height:10px; border-radius:var(--r-full); background:var(--surface-2); overflow:hidden; }
        .db-prog-fill { height:100%; border-radius:inherit; transition:width 1s cubic-bezier(.4,0,.2,1); }
        .db-prog-fill.red { background:linear-gradient(90deg,var(--kg-red),#ff6b6b); }
        .db-prog-fill.gold { background:linear-gradient(90deg,#e6b800,var(--de-gold)); }
        .db-prog-fill.blue { background:linear-gradient(90deg,var(--ru-blue),#4d7ee0); }
        .db-prog-fill.green { background:linear-gradient(90deg,#00956b,#21c49c); }

        /* Lessons list */
        .db-lesson-item {
            display:flex; align-items:center; gap:16px;
            padding:16px 0; border-bottom:1px solid var(--border);
        }
        .db-lesson-item:last-child { border-bottom:none; padding-bottom:0; }
        .db-lesson-icon {
            width:44px; height:44px; border-radius:14px; flex-shrink:0;
            display:grid; place-items:center; font-size:1.1rem;
        }
        .db-lesson-icon.done { background:rgba(33,196,156,0.12); color:#21c49c; }
        .db-lesson-icon.active { background:rgba(200,16,46,0.1); color:var(--kg-red); }
        .db-lesson-icon.locked { background:var(--surface-2); color:var(--muted); }
        .db-lesson-info { flex:1; }
        .db-lesson-name { font-weight:800; color:var(--text); margin-bottom:3px; }
        .db-lesson-meta { font-size:0.82rem; color:var(--muted); font-weight:600; }
        .db-lesson-btn {
            padding:8px 16px; border-radius:var(--r-full); border:none; cursor:pointer;
            font-weight:800; font-size:0.82rem; transition:transform 0.2s, opacity 0.2s;
        }
        .db-lesson-btn.go { background:var(--kg-red); color:white; }
        .db-lesson-btn.review { background:var(--surface-2); color:var(--text); }
        .db-lesson-btn.lock { background:var(--surface-2); color:var(--muted); cursor:not-allowed; }
        .db-lesson-btn.go:hover, .db-lesson-btn.review:hover { transform:translateY(-2px); opacity:0.9; }

        /* Badges */
        .db-badges-grid { display:grid; grid-template-columns:repeat(3,1fr); gap:12px; }
        .db-badge-item {
            display:flex; flex-direction:column; align-items:center; gap:8px;
            padding:16px 12px; border-radius:var(--r-md);
            background:var(--surface-2); border:1px solid var(--border);
            text-align:center; transition:transform 0.2s;
        }
        .db-badge-item:hover { transform:translateY(-3px); }
        .db-badge-item.locked { opacity:0.45; }
        .db-badge-icon {
            width:48px; height:48px; border-radius:50%;
            display:grid; place-items:center; font-size:1.3rem;
        }
        .db-badge-icon.gold { background:rgba(255,206,0,0.18); color:var(--de-gold); }
        .db-badge-icon.red { background:rgba(200,16,46,0.12); color:var(--kg-red); }
        .db-badge-icon.green { background:rgba(33,196,156,0.14); color:#21c49c; }
        .db-badge-icon.blue { background:rgba(0,51,160,0.1); color:var(--ru-blue); }
        .db-badge-icon.orange { background:rgba(255,143,50,0.14); color:#ff8f32; }
        .db-badge-name { font-weight:800; font-size:0.8rem; color:var(--text); line-height:1.3; }
        .db-badge-note { font-size:0.73rem; color:var(--muted); }

        /* Calendar */
        .db-calendar-grid { display:grid; grid-template-columns:repeat(7,1fr); gap:6px; margin-top:4px; }
        .db-cal-day {
            aspect-ratio:1; border-radius:10px;
            display:grid; place-items:center;
            font-size:0.75rem; font-weight:800;
            background:var(--surface-2); color:var(--muted);
        }
        .db-cal-day.studied { background:rgba(200,16,46,0.15); color:var(--kg-red); }
        .db-cal-day.today { background:var(--kg-red); color:white; }
        .db-cal-day.future { background:transparent; color:rgba(0,0,0,0.12); }
        body.theme-dark .db-cal-day.future { color:rgba(255,255,255,0.08); }
        .db-cal-headers { display:grid; grid-template-columns:repeat(7,1fr); gap:6px; margin-bottom:8px; }
        .db-cal-hdr { text-align:center; font-size:0.72rem; font-weight:800; text-transform:uppercase; letter-spacing:0.8px; color:var(--muted); }

        /* Chat */
        .db-chat-msg { display:flex; gap:10px; margin-bottom:14px; }
        .db-chat-msg.mine { flex-direction:row-reverse; }
        .db-chat-bubble {
            max-width:76%; padding:12px 16px; border-radius:18px;
            font-size:0.88rem; line-height:1.55; font-weight:600;
        }
        .db-chat-bubble.theirs { background:var(--surface-2); color:var(--text); border-bottom-left-radius:4px; }
        .db-chat-bubble.mine-b { background:var(--kg-red); color:white; border-bottom-right-radius:4px; }
        .db-chat-time { font-size:0.72rem; color:var(--muted); margin-top:4px; text-align:right; }
        .db-chat-mini-avatar {
            width:32px; height:32px; border-radius:50%; flex-shrink:0;
            background:linear-gradient(135deg,var(--kg-red),var(--ru-blue));
            display:grid; place-items:center; font-size:0.85rem; color:white; font-weight:800;
        }
        .db-chat-input-row { display:flex; gap:10px; margin-top:16px; }
        .db-chat-input {
            flex:1; border:2px solid var(--border); background:var(--surface-2);
            color:var(--text); padding:12px 16px; border-radius:var(--r-full);
            font:inherit; outline:none; transition:border-color 0.2s;
        }
        .db-chat-input:focus { border-color:var(--kg-red); }
        .db-chat-send {
            width:44px; height:44px; border-radius:50%; border:none;
            background:var(--kg-red); color:white; cursor:pointer;
            display:grid; place-items:center; font-size:1rem;
            transition:transform 0.2s, opacity 0.2s;
        }
        .db-chat-send:hover { transform:scale(1.1); }

        /* Vocab */
        .db-vocab-item {
            display:flex; align-items:center; justify-content:space-between;
            gap:12px; padding:12px 0; border-bottom:1px solid var(--border);
        }
        .db-vocab-item:last-child { border-bottom:none; }
        .db-vocab-de { font-weight:800; color:var(--text); }
        .db-vocab-tr { font-size:0.84rem; color:var(--muted); margin-top:2px; }
        .db-vocab-tag {
            padding:4px 10px; border-radius:var(--r-full);
            font-size:0.75rem; font-weight:800;
            background:rgba(255,206,0,0.14); color:#9a7b00;
        }
        body.theme-dark .db-vocab-tag { color:var(--de-gold); }

        /* Cert */
        .db-cert-card {
            background:linear-gradient(135deg,#1d2030,#2b2f47);
            border-radius:var(--r-lg); padding:28px;
            color:white; text-align:center;
            border:1px solid rgba(255,206,0,0.25); position:relative; overflow:hidden;
        }
        .db-cert-card::before {
            content:''; position:absolute; inset:0;
            background:radial-gradient(circle at 80% 20%,rgba(255,206,0,0.12),transparent 60%);
            pointer-events:none;
        }
        .db-cert-icon { font-size:3rem; margin-bottom:12px; }
        .db-cert-title { font-family:var(--font-display); font-size:1.8rem; letter-spacing:2px; margin-bottom:8px; color:var(--de-gold); }
        .db-cert-sub { color:rgba(255,255,255,0.6); font-size:0.85rem; line-height:1.6; margin-bottom:20px; }
        .db-cert-btn {
            display:inline-flex; align-items:center; gap:8px;
            padding:12px 24px; border-radius:var(--r-full); border:none;
            background:var(--de-gold); color:var(--de-black);
            font-weight:800; cursor:pointer; font:inherit;
            transition:transform 0.2s, opacity 0.2s;
        }
        .db-cert-btn:hover { transform:translateY(-2px); opacity:0.9; }
        .db-cert-btn:disabled { opacity:0.4; cursor:not-allowed; transform:none; }

        /* Leaderboard inside dashboard */
        .db-lb-item {
            display:flex; align-items:center; gap:14px;
            padding:12px 0; border-bottom:1px solid var(--border);
        }
        .db-lb-item:last-child { border-bottom:none; }
        .db-lb-rank { font-family:var(--font-display); font-size:1.4rem; width:32px; text-align:center; color:var(--muted); }
        .db-lb-rank.top1 { color:#FFD700; }
        .db-lb-rank.top2 { color:#C0C0C0; }
        .db-lb-rank.top3 { color:#CD7F32; }
        .db-lb-name { flex:1; font-weight:800; color:var(--text); }
        .db-lb-score { font-family:var(--font-display); font-size:1.4rem; color:var(--kg-red); letter-spacing:1px; }
        .db-lb-you { font-size:0.75rem; font-weight:800; padding:3px 8px; border-radius:var(--r-full); background:rgba(200,16,46,0.1); color:var(--kg-red); margin-left:6px; }

        /* Dark overrides */
        body.theme-dark .db-profile-hero { background:linear-gradient(135deg,#0a0a14 60%,#120d00); }
        body.theme-dark .db-cert-card { background:linear-gradient(135deg,#111726,#1a1f30); }

        /* Responsive */
        @media(max-width:1100px) {
            .db-main-grid { grid-template-columns:1fr; }
            .db-stats-grid { grid-template-columns:repeat(2,1fr); }
        }
        @media(max-width:640px) {
            .db-profile-hero { flex-direction:column; text-align:center; padding:28px 20px; }
            .db-profile-actions { justify-content:center; }
            .db-stats-grid { grid-template-columns:1fr 1fr; }
            .db-badges-grid { grid-template-columns:repeat(2,1fr); }
            .db-wrap { padding:24px 0 60px; }
        }
    </style>
</head>
<body>
    <div id="progress-bar"></div>

    <div class="top-strip">
        <div class="top-inner">
            <div class="lang-pills" aria-label="Language switcher">
                <button class="lang-pill active" data-lang="kg">🇰🇬 Кыргызча</button>
                <button class="lang-pill" data-lang="ru">🇷🇺 Русский</button>
                <button class="lang-pill" data-lang="de">🇩🇪 Deutsch</button>
            </div>
            <div class="top-actions">
                <div class="streak-chip"><i class="fas fa-fire" style="color:#ff8f32"></i> <span id="streak-top">0</span></div>
                <button class="theme-btn" id="theme-toggle"><i class="fas fa-circle-half-stroke"></i> <span data-i18n="themeToggle">Тема</span></button>
            </div>
        </div>
    </div>

    <nav class="navbar">
        <div class="nav-inner">
            <a href="#hero" class="logo">
                <span class="logo-badge"><i class="fas fa-language"></i></span>
                <span>DEUTSCHLERNEN</span>
            </a>

            <div class="nav-links">
                <a class="nav-link active" href="#hero" data-i18n="navHome">Башкы</a>
                <a class="nav-link" href="#courses" data-i18n="navCourses">Курстар</a>
                <a class="nav-link" href="#practice" data-i18n="navPractice">Практика</a>
                <a class="nav-link" href="#hub" data-i18n="navHub">Прогресс</a>
                <a class="nav-link" href="#teachers" data-i18n="navTeachers">Мугалимдер</a>
                <a class="nav-link" href="#faq" data-i18n="navFaq">Суроолор</a>
            </div>

            <div class="nav-actions">
                <button class="ghost-btn" id="login-btn" onclick="authMode='login';updateAuthModal();openModal('auth-modal')" data-i18n="login">Кирүү</button>
                <button class="solid-btn" id="register-btn" onclick="authMode='register';updateAuthModal();openModal('auth-modal')" data-i18n="register">Катталуу</button>
            </div>

            <button class="hamburger" id="hamburger" aria-label="Open menu">
                <span></span>
                <span></span>
                <span></span>
            </button>
        </div>
    </nav>

    <div class="mobile-nav" id="mobile-nav">
        <div class="mobile-links">
            <a class="mobile-link" href="#hero" data-i18n="navHome">Башкы</a>
            <a class="mobile-link" href="#courses" data-i18n="navCourses">Курстар</a>
            <a class="mobile-link" href="#practice" data-i18n="navPractice">Практика</a>
            <a class="mobile-link" href="#hub" data-i18n="navHub">Прогресс</a>
            <a class="mobile-link" href="#teachers" data-i18n="navTeachers">Мугалимдер</a>
            <a class="mobile-link" href="#faq" data-i18n="navFaq">Суроолор</a>
        </div>
    </div>


    <!-- ═══════ STUDENT DASHBOARD ═══════ -->
    <div id="student-dashboard">
        <div class="db-wrap">

            <!-- Profile hero -->
            <div class="db-profile-hero">
                <div class="db-avatar-wrap">
                    <div class="db-avatar" id="db-avatar-letter">А</div>
                    <div class="db-online-dot"></div>
                </div>
                <div class="db-profile-info">
                    <div class="db-name" id="db-user-name">Окуучу</div>
                    <div class="db-major" id="db-user-email">student@mail.com</div>
                    <div class="db-level-badge"><i class="fas fa-graduation-cap"></i> <span id="db-level-text">A1 — Башталгыч</span></div>
                    <div class="db-xp-row">
                        <div class="db-xp-track"><div class="db-xp-fill" id="db-xp-fill" style="width:0%"></div></div>
                        <div class="db-xp-label" id="db-xp-label">0 / 500 XP</div>
                    </div>
                </div>
                <div class="db-profile-actions">
                    <button class="db-btn-primary" onclick="openCourseModal(0)"><i class="fas fa-play"></i> <span id="db-btn-continue">Окууну улантуу</span></button>
                    <button class="db-btn-ghost" onclick="logoutUser()"><i class="fas fa-sign-out-alt"></i> <span id="db-btn-logout">Чыгуу</span></button>
                </div>
            </div>

            <!-- Stats -->
            <div class="db-stats-grid">
                <div class="db-stat-card">
                    <div class="db-stat-icon fire"><i class="fas fa-fire"></i></div>
                    <div><div class="db-stat-num" id="db-stat-streak">0</div><div class="db-stat-lbl" id="db-lbl-streak">Катар күн</div></div>
                </div>
                <div class="db-stat-card">
                    <div class="db-stat-icon star"><i class="fas fa-star"></i></div>
                    <div><div class="db-stat-num" id="db-stat-xp">0</div><div class="db-stat-lbl" id="db-lbl-xp">Упай (XP)</div></div>
                </div>
                <div class="db-stat-card">
                    <div class="db-stat-icon book"><i class="fas fa-book-open"></i></div>
                    <div><div class="db-stat-num" id="db-stat-lessons">0</div><div class="db-stat-lbl" id="db-lbl-lessons">Бүткөн сабак</div></div>
                </div>
                <div class="db-stat-card">
                    <div class="db-stat-icon check"><i class="fas fa-bullseye"></i></div>
                    <div><div class="db-stat-num" id="db-stat-acc">0%</div><div class="db-stat-lbl" id="db-lbl-acc">Тактык</div></div>
                </div>
            </div>

            <!-- Main grid -->
            <div class="db-main-grid">
                <!-- LEFT -->
                <div class="db-left">

                    <!-- Course progress -->
                    <div class="db-card">
                        <div class="db-card-title" id="db-title-progress">Курс прогресси</div>
                        <div class="db-card-sub" id="db-sub-progress">Немис тили A1–B1 боюнча жалпы илгерилөө</div>
                        <div class="db-prog-item">
                            <div class="db-prog-header"><span class="db-prog-name">A1 — Башталгыч</span><span class="db-prog-pct" id="dp-a1-pct">0%</span></div>
                            <div class="db-prog-track"><div class="db-prog-fill red" id="dp-a1" style="width:0%"></div></div>
                        </div>
                        <div class="db-prog-item">
                            <div class="db-prog-header"><span class="db-prog-name">A2 — Орто башталгыч</span><span class="db-prog-pct" id="dp-a2-pct" style="color:var(--de-gold)">0%</span></div>
                            <div class="db-prog-track"><div class="db-prog-fill gold" id="dp-a2" style="width:0%"></div></div>
                        </div>
                        <div class="db-prog-item">
                            <div class="db-prog-header"><span class="db-prog-name">B1 — Орто</span><span class="db-prog-pct" id="dp-b1-pct" style="color:var(--ru-blue)">0%</span></div>
                            <div class="db-prog-track"><div class="db-prog-fill blue" id="dp-b1" style="width:0%"></div></div>
                        </div>
                        <div class="db-prog-item">
                            <div class="db-prog-header"><span class="db-prog-name" id="dp-vocab-lbl">Сөздүк</span><span class="db-prog-pct" id="dp-vocab-pct" style="color:#21c49c">0%</span></div>
                            <div class="db-prog-track"><div class="db-prog-fill green" id="dp-vocab" style="width:0%"></div></div>
                        </div>
                    </div>

                    <!-- Lessons list -->
                    <div class="db-card">
                        <div class="db-card-title" id="db-title-lessons">Акыркы сабактар</div>
                        <div class="db-card-sub" id="db-sub-lessons">Уланта же кайрадан карагыла</div>
                        <div id="db-lessons-list"></div>
                    </div>

                    <!-- Badges -->
                    <div class="db-card">
                        <div class="db-card-title" id="db-title-badges">Жетишкендиктер</div>
                        <div class="db-card-sub" id="db-sub-badges">Топтолгон медалдар жана сыйлыктар</div>
                        <div class="db-badges-grid" id="db-badges-grid"></div>
                    </div>

                    <!-- My Vocabulary -->
                    <div class="db-card">
                        <div style="display:flex;align-items:center;justify-content:space-between;gap:16px;margin-bottom:6px">
                            <div class="db-card-title" id="db-title-vocab">Менин сөздүгүм</div>
                            <button class="db-btn-primary" style="padding:8px 16px;font-size:0.82rem" onclick="exportVocabulary()"><i class="fas fa-file-export"></i> <span id="db-btn-export">Экспорт</span></button>
                        </div>
                        <div class="db-card-sub" id="db-sub-vocab">Флэш-картадан сакталган сөздөр</div>
                        <div id="db-vocab-list"></div>
                    </div>

                </div>

                <!-- RIGHT -->
                <div class="db-right">

                    <!-- Calendar -->
                    <div class="db-card">
                        <div class="db-card-title" id="db-title-calendar">Окуу графиги</div>
                        <div class="db-card-sub" id="db-sub-calendar">Бул айдагы машыккан күндөр</div>
                        <div class="db-cal-headers" id="db-cal-headers"></div>
                        <div class="db-calendar-grid" id="db-calendar"></div>
                    </div>

                    <!-- Leaderboard -->
                    <div class="db-card">
                        <div class="db-card-title" id="db-title-lb">Рейтинг</div>
                        <div class="db-card-sub" id="db-sub-lb">Башка студенттер арасында орнуңуз</div>
                        <div id="db-leaderboard"></div>
                    </div>

                    <!-- Cert -->
                    <div class="db-cert-card">
                        <div class="db-cert-icon">🎓</div>
                        <div class="db-cert-title" id="db-cert-title">СЕРТИФИКАТ</div>
                        <div class="db-cert-sub" id="db-cert-sub">A1 курсун 100% бүткөндө сертификат жүктөп алса болот.</div>
                        <button class="db-cert-btn" id="db-cert-btn" onclick="downloadCert()" disabled>
                            <i class="fas fa-download"></i> <span id="db-cert-btn-lbl">Жүктөп алуу</span>
                        </button>
                    </div>

                    <!-- Teacher chat -->
                    <div class="db-card">
                        <div class="db-card-title" id="db-title-chat">Мугалим менен байланыш</div>
                        <div class="db-card-sub" id="db-sub-chat">Айсулуу мугалим онлайн</div>
                        <div id="db-chat-messages"></div>
                        <div class="db-chat-input-row">
                            <input class="db-chat-input" type="text" id="db-chat-input" placeholder="Суроо жазыңыз…">
                            <button class="db-chat-send" onclick="sendChatMsg()"><i class="fas fa-paper-plane"></i></button>
                        </div>
                    </div>

                </div>
            </div>
        </div>
    </div>
    <!-- ═══════ END DASHBOARD ═══════ -->

    <div class="main-site">
    <main>
        <section id="hero" class="hero-bg">
            <div class="section-wrap">
                <div class="hero">
                    <div data-aos="fade-right">
                        <div class="hero-tag"><i class="fas fa-flag"></i> <span data-i18n="heroTag">Кыргызча негизги интерфейс</span></div>
                        <h1 class="hero-title" id="hero-title"></h1>
                        <p class="hero-copy" id="hero-copy"></p>
                        <div class="hero-actions">
                            <button class="solid-btn" data-action="start" data-i18n="heroPrimary">Акысыз баштоо</button>
                            <button class="ghost-btn" onclick="document.getElementById('courses').scrollIntoView({behavior:'smooth'})" data-i18n="heroSecondary">Курстарды көрүү</button>
                        </div>
                        <div class="hero-stats">
                            <div class="hero-stat">
                                <div class="hero-stat-num">50K+</div>
                                <div class="hero-stat-label" data-i18n="heroStatStudents">Окуучу</div>
                            </div>
                            <div class="hero-stat">
                                <div class="hero-stat-num">4.9 ★</div>
                                <div class="hero-stat-label" data-i18n="heroStatRating">Баа</div>
                            </div>
                            <div class="hero-stat">
                                <div class="hero-stat-num">A1-B1</div>
                                <div class="hero-stat-label" data-i18n="heroStatLevels">Деңгээлдер</div>
                            </div>
                        </div>
                    </div>

                    <div data-aos="fade-left">
                        <div class="hero-card">
                            <div class="hero-floating">
                                <div>
                                    <div class="floating-label" data-i18n="heroFloat1Label">Бүгүнкү сөз</div>
                                    <div class="floating-value" id="hero-floating-word">Hallo</div>
                                </div>
                                <div class="mini-pill"><i class="fas fa-wave-square"></i> <span data-i18n="heroFloat1Badge">Жандуу ротатор</span></div>
                            </div>
                            <div class="hero-floating">
                                <div>
                                    <div class="floating-label" data-i18n="heroFloat2Label">Күнүмдүк максат</div>
                                    <div class="floating-value" id="hero-goal-label"></div>
                                </div>
                                <div class="mini-pill"><i class="fas fa-fire"></i> <span id="hero-goal-streak">0</span></div>
                            </div>
                            <div class="rotator-card">
                                <div class="floating-label" data-i18n="heroRotatorLabel">Немис сөзү</div>
                                <div class="rotator-word" id="hero-rotator-word">Hallo</div>
                                <div class="rotator-translations">
                                    <div>🇰🇬 <span id="hero-rotator-kg">Салам</span></div>
                                    <div>🇷🇺 <span id="hero-rotator-ru">Привет</span></div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="courses">
            <div class="section-wrap">
                <div class="section-head" data-aos="fade-up">
                    <div class="section-tag" data-i18n="coursesTag">Биздин программа</div>
                    <h2 class="section-title" data-i18n="coursesTitle">Курстар</h2>
                    <p class="section-copy" data-i18n="coursesCopy">A1ден B1ге чейин этап-этабы менен үйрөнүңүз.</p>
                </div>
                <div class="course-grid" id="course-grid"></div>
            </div>
        </section>

        <section id="practice" class="dark-section">
            <div class="section-wrap">
                <div class="section-head" data-aos="fade-up">
                    <div class="section-tag" data-i18n="practiceTag">Күн сайын практика</div>
                    <h2 class="section-title" data-i18n="practiceTitle">Практика</h2>
                    <p class="section-copy" data-i18n="practiceCopy">Флэш-карта, айтылыш жана тест аркылуу сөздөрдү бекемдеңиз.</p>
                </div>

                <div class="practice-grid">
                    <div class="flashcard-panel" data-aos="fade-up">
                        <div class="flashcard-scene">
                            <div class="flashcard" id="flashcard">
                                <div class="flash-face flash-front">
                                    <div class="flash-hint" data-i18n="flashFrontHint">Котормосун көрүү үчүн басыңыз</div>
                                    <div class="flash-word" id="flash-word"></div>
                                    <div class="flash-example" id="flash-example"></div>
                                </div>
                                <div class="flash-face flash-back">
                                    <div class="flash-hint" data-i18n="flashBackHint">Котормо</div>
                                    <div class="flash-word" id="flash-translation"></div>
                                    <div class="flash-example" id="flash-translation-note"></div>
                                </div>
                            </div>
                        </div>
                        <div class="panel-actions">
                            <button class="tool-btn primary" id="flip-card-btn"><i class="fas fa-sync-alt"></i> <span data-i18n="flashFlip">Аударуу</span></button>
                            <button class="tool-btn" id="speak-card-btn"><i class="fas fa-volume-high"></i> <span data-i18n="flashSpeak">Угуу</span></button>
                            <button class="tool-btn" id="save-card-btn"><i class="fas fa-bookmark"></i> <span data-i18n="flashSave">Сактоо</span></button>
                            <button class="tool-btn" id="next-card-btn"><i class="fas fa-arrow-right"></i> <span data-i18n="flashNext">Кийинки</span></button>
                        </div>
                        <div class="progress-row">
                            <div class="progress-bar"><div class="progress-fill" id="flash-progress-fill"></div></div>
                            <div id="flash-progress-text">1 / 6</div>
                        </div>
                        <div class="panel-status" id="speech-status"></div>
                    </div>

                    <div class="quiz-card" data-aos="fade-up" data-aos-delay="120">
                        <div class="quiz-head">
                            <div class="quiz-title" data-i18n="quizTitle">Тест</div>
                            <div class="quiz-score" id="quiz-score">0 / 0</div>
                        </div>
                        <div class="quiz-question" id="quiz-question-label"></div>
                        <div class="quiz-word" id="quiz-word"></div>
                        <div class="quiz-options" id="quiz-options"></div>
                        <div class="quiz-feedback" id="quiz-feedback"></div>
                        <div class="quiz-actions">
                            <button class="tool-btn primary hidden" id="next-quiz-btn"><i class="fas fa-arrow-right"></i> <span data-i18n="quizNext">Кийинки суроо</span></button>
                            <button class="share-btn hidden" id="share-quiz-btn"><i class="fas fa-share-nodes"></i> <span data-i18n="quizShare">Жыйынтыкты бөлүшүү</span></button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="hub">
            <div class="section-wrap">
                <div class="section-head" data-aos="fade-up">
                    <div class="section-tag" data-i18n="hubTag">Жаңы функциялар</div>
                    <h2 class="section-title" data-i18n="hubTitle">Окуучунун борбору</h2>
                    <p class="section-copy" data-i18n="hubCopy">Серияңызды көзөмөлдөңүз, сөздөрдү сактаңыз, грамматиканы караңыз жана деңгээлиңизди билиңиз.</p>
                </div>

                <div class="feature-grid">
                    <div class="feature-card" data-aos="fade-up">
                        <div class="feature-head">
                            <div>
                                <div class="feature-kicker" data-i18n="streakKicker">Күнүмдүк максат</div>
                                <div class="feature-title" data-i18n="streakTitle">Серия жана прогресс</div>
                            </div>
                            <div class="mini-pill"><i class="fas fa-fire" style="color:#ff8f32"></i> <span id="streak-main">0</span></div>
                        </div>
                        <p class="feature-copy" data-i18n="streakCopy">Сайтта машыккан ар бир күн катталат.</p>
                        <div class="small-actions">
                            <button class="small-btn" id="mark-study-btn"><i class="fas fa-bolt"></i> <span data-i18n="markStudy">Бүгүн окудум</span></button>
                            <button class="small-btn" id="reset-progress-btn"><i class="fas fa-rotate-left"></i> <span data-i18n="resetProgress">Жергиликтүү прогрессти тазалоо</span></button>
                        </div>
                        <div class="mini-stats" style="margin-top:18px">
                            <div class="mini-stat">
                                <div class="mini-number" id="stat-days">0</div>
                                <div class="mini-label" data-i18n="statDays">Катар күн</div>
                            </div>
                            <div class="mini-stat">
                                <div class="mini-number" id="stat-words">0</div>
                                <div class="mini-label" data-i18n="statWords">Сакталган сөз</div>
                            </div>
                            <div class="mini-stat">
                                <div class="mini-number" id="stat-accuracy">0%</div>
                                <div class="mini-label" data-i18n="statAccuracy">Тактык</div>
                            </div>
                        </div>
                        <div class="dashboard-bars">
                            <div class="dash-row">
                                <div data-i18n="dashFlashcards">Флэш-карта</div>
                                <div class="dash-track"><div class="dash-fill" id="dash-flash"></div></div>
                                <div id="dash-flash-label">0%</div>
                            </div>
                            <div class="dash-row">
                                <div data-i18n="dashVocab">Сөздүк</div>
                                <div class="dash-track"><div class="dash-fill" id="dash-vocab"></div></div>
                                <div id="dash-vocab-label">0%</div>
                            </div>
                            <div class="dash-row">
                                <div data-i18n="dashPlacement">Тандоо тести</div>
                                <div class="dash-track"><div class="dash-fill" id="dash-placement"></div></div>
                                <div id="dash-placement-label">0%</div>
                            </div>
                        </div>
                    </div>

                    <div class="feature-card" data-aos="fade-up" data-aos-delay="70">
                        <div class="feature-head">
                            <div>
                                <div class="feature-kicker" data-i18n="vocabKicker">Жеке сөздүк</div>
                                <div class="feature-title" data-i18n="vocabTitle">Сакталган сөздөр</div>
                            </div>
                            <div class="mini-pill"><i class="fas fa-book-open"></i> localStorage</div>
                        </div>
                        <p class="feature-copy" data-i18n="vocabCopy">Флэш-картадан сөздөрдү сактап, кийин кайталаңыз.</p>
                        <div class="small-actions" style="margin-bottom:16px">
                            <button class="small-btn" id="export-vocab-btn"><i class="fas fa-file-export"></i> <span data-i18n="exportVocab">Экспорт</span></button>
                        </div>
                        <div class="vocab-list" id="vocab-list"></div>
                    </div>

                    <div class="feature-card" data-aos="fade-up" data-aos-delay="100">
                        <div class="feature-head">
                            <div>
                                <div class="feature-kicker" data-i18n="grammarKicker">A1-B1 грамматика</div>
                                <div class="feature-title" data-i18n="grammarTitle">Грамматика таблицалары</div>
                            </div>
                            <div class="mini-pill"><i class="fas fa-table"></i> A1-B1</div>
                        </div>
                        <p class="feature-copy" data-i18n="grammarCopy">Артикль, этиш жана септик тууралуу кыска түшүндүрмө.</p>
                        <div class="grammar-tabs">
                            <button class="grammar-tab active" data-grammar="articles"></button>
                            <button class="grammar-tab" data-grammar="verbs"></button>
                            <button class="grammar-tab" data-grammar="cases"></button>
                        </div>
                        <div class="grammar-panel active" id="grammar-panel"></div>
                    </div>

                    <div class="placement-card" data-aos="fade-up" data-aos-delay="140">
                        <div class="feature-head">
                            <div>
                                <div class="feature-kicker" data-i18n="placementKicker">10 суроо</div>
                                <div class="feature-title" data-i18n="placementTitle">Деңгээлди аныктоо тести</div>
                            </div>
                            <div class="mini-pill"><i class="fas fa-route"></i> A1-A2-B1</div>
                        </div>
                        <p class="feature-copy" data-i18n="placementCopy">Жыйынтыкка жараша кайсы курстан баштоо керектигин сунуштайт.</p>
                        <div id="placement-question" style="font-weight:800; margin-bottom:16px"></div>
                        <div class="placement-options" id="placement-options"></div>
                        <div class="placement-status" id="placement-status"></div>
                    </div>
                </div>
            </div>
        </section>

        <section class="dark-section">
            <div class="section-wrap">
                <div class="section-head" data-aos="fade-up">
                    <div class="section-tag" data-i18n="extrasTag">Кошумча мүмкүнчүлүктөр</div>
                    <h2 class="section-title" data-i18n="extrasTitle">Диалогдор, рейтинг жана сыйлыктар</h2>
                    <p class="section-copy" data-i18n="extrasCopy">Күнүмдүк кырдаалдардагы диалогдорду угуп, упай топтоп, бейджик ачыңыз.</p>
                </div>

                <div class="dialogue-grid" id="dialogue-grid"></div>

                <div class="feature-grid" style="margin-top:28px">
                    <div class="feature-card" data-aos="fade-up">
                        <div class="feature-head">
                            <div>
                                <div class="feature-kicker" data-i18n="leaderboardKicker">Mock leaderboard</div>
                                <div class="feature-title" data-i18n="leaderboardTitle">Мыкты окуучулар</div>
                            </div>
                            <div class="mini-pill"><i class="fas fa-trophy"></i> Top 5</div>
                        </div>
                        <p class="feature-copy" data-i18n="leaderboardCopy">Сиздин упай да жергиликтүү сакталат.</p>
                        <div class="leaderboard-list" id="leaderboard-list"></div>
                    </div>

                    <div class="feature-card" data-aos="fade-up" data-aos-delay="70">
                        <div class="feature-head">
                            <div>
                                <div class="feature-kicker" data-i18n="badgesKicker">Achievements</div>
                                <div class="feature-title" data-i18n="badgesTitle">Бейджиктер</div>
                            </div>
                            <div class="mini-pill"><i class="fas fa-medal"></i> localStorage</div>
                        </div>
                        <p class="feature-copy" data-i18n="badgesCopy">5 тест, 20 сөз жана 3 күндүк серия сыяктуу максаттар ачылат.</p>
                        <div class="badge-list" id="badge-list"></div>
                    </div>
                </div>
            </div>
        </section>

        <section id="teachers">
            <div class="section-wrap">
                <div class="section-head" data-aos="fade-up">
                    <div class="section-tag" data-i18n="teachersTag">Команда</div>
                    <h2 class="section-title" data-i18n="teachersTitle">Мугалимдер</h2>
                    <p class="section-copy" data-i18n="teachersCopy">Үч тилде иштеген тажрыйбалуу команда.</p>
                </div>
                <div class="teacher-grid" id="teacher-grid"></div>
            </div>
        </section>

        <section class="dark-section">
            <div class="section-wrap">
                <div class="section-head" data-aos="fade-up">
                    <div class="section-tag" data-i18n="testimonialsTag">Пикирлер</div>
                    <h2 class="section-title" data-i18n="testimonialsTitle">Окуучулар эмне дейт</h2>
                    <p class="section-copy" data-i18n="testimonialsCopy">Ар бир интерфейс тили үчүн өзүнчө локалдаштырылган пикирлер.</p>
                </div>
                <div class="testimonial-grid" id="testimonial-grid"></div>
            </div>
        </section>

        <section id="faq">
            <div class="section-wrap">
                <div class="section-head" data-aos="fade-up">
                    <div class="section-tag" data-i18n="faqTag">Суроолор</div>
                    <h2 class="section-title" data-i18n="faqTitle">Көп берилген суроолор</h2>
                    <p class="section-copy" data-i18n="faqCopy">Баары бир чыкылдатуу менен ачылат жана дароо тилге жараша алмашат.</p>
                </div>
                <div class="faq-grid">
                    <div class="faq-card">
                        <div class="faq-list" id="faq-list"></div>
                    </div>
                </div>
            </div>
        </section>

        <section>
            <div class="section-wrap" style="padding-top:0">
                <div class="newsletter" data-aos="fade-up">
                    <div>
                        <div class="newsletter-title" data-i18n="newsletterTitle">Жаңылыктарга жазылыңыз</div>
                        <div class="newsletter-copy" data-i18n="newsletterCopy">Апта сайын жаңы сөздөрдү жана пайдалуу кеңештерди алыңыз.</div>
                    </div>
                    <div class="newsletter-form">
                        <input class="newsletter-input" type="email" id="newsletter-email" data-i18n-placeholder="newsletterPlaceholder" placeholder="Электрондук почтаңыз">
                        <button class="solid-btn" id="newsletter-btn"><i class="fas fa-paper-plane"></i> <span data-i18n="newsletterButton">Жазылуу</span></button>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer class="footer">
        <div class="footer-inner">
            <div class="footer-grid">
                <div>
                    <div class="footer-title">DEUTSCHLERNEN</div>
                    <p class="footer-copy" data-i18n="footerCopy">Кыргызча негизги интерфейси бар немис тилин үйрөнүү платформасы.</p>
                    <div class="footer-socials">
                        <a href="https://t.me/deutschlernen_kg" target="_blank" class="social-btn" title="Telegram"><i class="fab fa-telegram"></i></a>
                        <a href="https://instagram.com/deutschlernen_kg" target="_blank" class="social-btn" title="Instagram"><i class="fab fa-instagram"></i></a>
                        <a href="https://youtube.com/@deutschlernen_kg" target="_blank" class="social-btn" title="YouTube"><i class="fab fa-youtube"></i></a>
                        <a href="https://facebook.com/deutschlernen.kg" target="_blank" class="social-btn" title="Facebook"><i class="fab fa-facebook"></i></a>
                    </div>
                </div>
                <div>
                    <div class="footer-title" data-i18n="footerCourses">Курстар</div>
                    <div class="footer-links">
                        <button type="button" data-action="courseA1">Deutsch A1</button>
                        <button type="button" data-action="courseA2">Deutsch A2</button>
                        <button type="button" data-action="courseB1">Deutsch B1</button>
                    </div>
                </div>
                <div>
                    <div class="footer-title" data-i18n="footerContact">Байланыш</div>
                    <div class="footer-links">
                        <a href="mailto:info@deutschlernen.kg" style="color:rgba(255,255,255,0.72);text-decoration:none">info@deutschlernen.kg</a>
                        <a href="tel:+996312123456" style="color:rgba(255,255,255,0.72);text-decoration:none">+996 312 123 456</a>
                        <a href="https://maps.google.com/?q=Bishkek,Kyrgyzstan" target="_blank" data-i18n="footerCity" style="color:rgba(255,255,255,0.72);text-decoration:none">Бишкек, Кыргызстан</a>
                    </div>
                </div>
            </div>
            <div class="footer-bottom">
                <div data-i18n="footerBottom">© 2026 DeutschLernen. Бардык укуктар корголгон.</div>
                <div>🇰🇬 🇷🇺 🇩🇪</div>
            </div>
        </div>
    </footer>


    <!-- Toast container -->
    <div id="toast-container"></div>

    <!-- Auth Modal -->
    <div class="modal-overlay" id="auth-modal">
        <div class="modal-box">
            <button class="modal-close" onclick="closeModal('auth-modal')"><i class="fas fa-times"></i></button>
            <div id="auth-login-view">
                <div class="modal-title" id="auth-modal-title">КИРҮҮ</div>
                <div class="modal-sub" id="auth-modal-sub">Каттоодон өтүп, прогрессиңизди сактаңыз.</div>
                <div class="modal-field">
                    <label class="modal-label" id="lbl-email">Электрондук почта</label>
                    <input class="modal-input" type="email" id="auth-email" placeholder="example@mail.com">
                </div>
                <div class="modal-field">
                    <label class="modal-label" id="lbl-password">Сырсөз</label>
                    <input class="modal-input" type="password" id="auth-password" placeholder="••••••••">
                </div>
                <div class="modal-field" id="auth-name-field" style="display:none">
                    <label class="modal-label" id="lbl-name">Атыңыз</label>
                    <input class="modal-input" type="text" id="auth-name" placeholder="Атыңызды жазыңыз">
                </div>
                <div class="modal-actions">
                    <button class="solid-btn" onclick="submitAuth()" id="auth-submit-btn">Кирүү</button>
                </div>
                <div class="modal-switch" id="auth-switch">
                    Каттоодон өткөн эмессизби? <button onclick="toggleAuthMode()">Катталуу</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Teacher Modal -->
    <div class="modal-overlay" id="teacher-modal">
        <div class="modal-box wide">
            <button class="modal-close" onclick="closeModal('teacher-modal')"><i class="fas fa-times"></i></button>
            <div class="teacher-modal-header">
                <div class="teacher-modal-avatar" id="tm-avatar">A</div>
                <div>
                    <div class="modal-title" id="tm-name">Айсулуу</div>
                    <div style="color:var(--kg-red);font-weight:800;margin-bottom:10px" id="tm-role">Кыргызча жана немисче</div>
                    <p style="color:var(--muted);line-height:1.7" id="tm-bio">Bio</p>
                </div>
            </div>
            <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:24px" id="tm-meta"></div>
            <div class="modal-actions">
                <button class="solid-btn" onclick="bookTeacher()">
                    <i class="fas fa-calendar-check"></i> <span id="btn-book">Сабакка жазылуу</span>
                </button>
                <button class="ghost-btn-modal modal-actions" onclick="closeModal('teacher-modal')" style="flex:1;padding:14px;font-size:1rem;border:none;border-radius:999px;cursor:pointer;font-weight:800;background:var(--surface-2);color:var(--text)">
                    <span id="btn-close-teacher">Жабуу</span>
                </button>
            </div>
        </div>
    </div>

    <!-- Course Modal -->
    <div class="modal-overlay" id="course-modal">
        <div class="modal-box wide">
            <button class="modal-close" onclick="closeModal('course-modal')"><i class="fas fa-times"></i></button>
            <div class="course-modal-header" id="cm-header">
                <div class="course-modal-level" id="cm-level">A1</div>
                <div style="font-family:var(--font-display);font-size:2.4rem;letter-spacing:2px;margin-bottom:8px" id="cm-title">Немис тили A1</div>
                <div style="color:rgba(255,255,255,0.8)" id="cm-desc">Сүрөттөмө</div>
            </div>
            <div class="course-feats-grid" id="cm-feats"></div>
            <div style="display:flex;align-items:center;justify-content:space-between;gap:16px;margin-bottom:24px">
                <div style="font-family:var(--font-display);font-size:2.2rem;letter-spacing:1px;color:var(--kg-red)" id="cm-price">2 990 сом</div>
                <div style="color:var(--muted);font-size:0.85rem" id="cm-duration"></div>
            </div>
            <div class="modal-actions">
                <button class="solid-btn" onclick="enrollCourse()">
                    <i class="fas fa-rocket"></i> <span id="btn-enroll">Курска жазылуу</span>
                </button>
                <button class="ghost-btn-modal" onclick="closeModal('course-modal')" style="flex:1;padding:14px;font-size:1rem;border:none;border-radius:999px;cursor:pointer;font-weight:800;background:var(--surface-2);color:var(--text)">
                    <span id="btn-close-course">Жабуу</span>
                </button>
            </div>
        </div>
    </div>
    <button id="back-to-top" aria-label="Back to top"><i class="fas fa-arrow-up"></i></button>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        const STORAGE_KEY = 'deutschlernen_state_v3';
        const todayKey = new Date().toISOString().slice(0, 10);
        const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
        const defaultState = {
            lang: 'kg',
            theme: 'light',
            streak: 0,
            lastStudyDate: '',
            flashIndex: 0,
            flashcardsReviewed: 0,
            savedWords: [],
            quizIndex: 0,
            quizScore: 0,
            quizCorrect: 0,
            quizAnswered: 0,
            quizzesCompleted: 0,
            placementIndex: 0,
            placementScore: 0,
            placementFinished: false,
            dialoguesTab: { 0: 'kg', 1: 'kg', 2: 'kg' },
            userLeaderboardScore: 0,
            badges: []
        };

        const state = { ...defaultState, ...JSON.parse(localStorage.getItem(STORAGE_KEY) || '{}') };

        const i18n = {
            kg: {
                themeToggle: 'Тема',
                navHome: 'Башкы',
                navCourses: 'Курстар',
                navPractice: 'Практика',
                navHub: 'Прогресс',
                navTeachers: 'Мугалимдер',
                navFaq: 'Суроолор',
                login: 'Кирүү',
                register: 'Катталуу',
                heroTag: 'Кыргызча негизги интерфейс',
                heroPrimary: 'Акысыз баштоо',
                heroSecondary: 'Курстарды көрүү',
                heroStatStudents: 'Окуучу',
                heroStatRating: 'Баа',
                heroStatLevels: 'Деңгээлдер',
                heroFloat1Label: 'Бүгүнкү сөз',
                heroFloat1Badge: 'Жандуу ротатор',
                heroFloat2Label: 'Күнүмдүк максат',
                heroRotatorLabel: 'Немис сөзү',
                coursesTag: 'Биздин программа',
                coursesTitle: 'Курстар',
                coursesCopy: 'A1ден B1ге чейин этап-этабы менен үйрөнүңүз.',
                practiceTag: 'Күн сайын практика',
                practiceTitle: 'Практика',
                practiceCopy: 'Флэш-карта, айтылыш жана тест аркылуу сөздөрдү бекемдеңиз.',
                flashFrontHint: 'Котормосун көрүү үчүн басыңыз',
                flashBackHint: 'Котормо',
                flashFlip: 'Аударуу',
                flashSpeak: 'Угуу',
                flashSave: 'Сактоо',
                flashNext: 'Кийинки',
                flashTranslationNote: 'Кыргызча негизги котормо, орусча кошумча түшүндүрмө',
                speechReady: 'Немис сөзүн угуу же микрофон менен кайталоо үчүн даяр.',
                speechPlaying: 'Немисче айтылыш угузулуп жатат.',
                speechUnsupported: 'Бул браузерде үн таануу жок. Бирок немисче айтылыш угулат.',
                speechListening: 'Азыр кайталаңыз:',
                speechGood: 'Абдан жакшы! Угуу таанылды:',
                speechTryAgain: 'Дагы бир жолу кайталап көрүңүз. Таанылган сөз:',
                speechError: 'Микрофонду ачууга уруксат бериңиз да кайра аракет кылыңыз.',
                quizTitle: 'Тест',
                quizQuestion: 'Бул сөз эмнени билдирет?',
                quizNext: 'Кийинки суроо',
                quizShare: 'Жыйынтыкты бөлүшүү',
                quizCorrect: 'Туура жооп!',
                quizWrong: 'Тилекке каршы, туура эмес.',
                quizFinished: 'Тест бүттү. Жыйынтыгыңызды бөлүшө аласыз.',
                hubTag: 'Жаңы функциялар',
                hubTitle: 'Окуучунун борбору',
                hubCopy: 'Серияңызды көзөмөлдөңүз, сөздөрдү сактаңыз, грамматиканы караңыз жана деңгээлиңизди билиңиз.',
                streakKicker: 'Күнүмдүк максат',
                streakTitle: 'Серия жана прогресс',
                streakCopy: 'Сайтта машыккан ар бир күн катталат.',
                markStudy: 'Бүгүн окудум',
                resetProgress: 'Жергиликтүү прогрессти тазалоо',
                statDays: 'Катар күн',
                statWords: 'Сакталган сөз',
                statAccuracy: 'Тактык',
                dashFlashcards: 'Флэш-карта',
                dashVocab: 'Сөздүк',
                dashPlacement: 'Тандоо тести',
                vocabKicker: 'Жеке сөздүк',
                vocabTitle: 'Сакталган сөздөр',
                vocabCopy: 'Флэш-картадан сөздөрдү сактап, кийин кайталаңыз.',
                exportVocab: 'Экспорт',
                vocabEmpty: 'Азырынча сакталган сөздөр жок. Флэш-картадан сөз тандаңыз.',
                vocabReview: 'Кайталоо',
                vocabDelete: 'Өчүрүү',
                grammarKicker: 'A1-B1 грамматика',
                grammarTitle: 'Грамматика таблицалары',
                grammarCopy: 'Артикль, этиш жана септик тууралуу кыска түшүндүрмө.',
                grammarArticles: 'Артиклдер',
                grammarVerbs: 'Этиштер',
                grammarCases: 'Септиктер',
                placementKicker: '10 суроо',
                placementTitle: 'Деңгээлди аныктоо тести',
                placementCopy: 'Жыйынтыкка жараша кайсы курстан баштоо керектигин сунуштайт.',
                placementStart: 'Суроого туура жоопту тандаңыз.',
                placementDoneA1: 'Сизге A1 деңгээлинен баштоо сунушталат.',
                placementDoneA2: 'Сизге A2 деңгээлинен баштоо сунушталат.',
                placementDoneB1: 'Сизге B1 деңгээлинен баштоо сунушталат.',
                extrasTag: 'Кошумча мүмкүнчүлүктөр',
                extrasTitle: 'Диалогдор, рейтинг жана сыйлыктар',
                extrasCopy: 'Күнүмдүк кырдаалдардагы диалогдорду угуп, упай топтоп, бейджик ачыңыз.',
                leaderboardKicker: 'Жергиликтүү рейтинг',
                leaderboardTitle: 'Мыкты окуучулар',
                leaderboardCopy: 'Сиздин упай да жергиликтүү сакталат.',
                badgesKicker: 'Сыйлыктар',
                badgesTitle: 'Бейджиктер',
                badgesCopy: '5 тест, 20 сөз жана 3 күндүк серия сыяктуу максаттар ачылат.',
                teachersTag: 'Команда',
                teachersTitle: 'Мугалимдер',
                teachersCopy: 'Үч тилде иштеген тажрыйбалуу команда.',
                testimonialsTag: 'Пикирлер',
                testimonialsTitle: 'Окуучулар эмне дейт',
                testimonialsCopy: 'Ар бир интерфейс тили үчүн өзүнчө локалдаштырылган пикирлер.',
                faqTag: 'Суроолор',
                faqTitle: 'Көп берилген суроолор',
                faqCopy: 'Баары бир чыкылдатуу менен ачылат жана дароо тилге жараша алмашат.',
                newsletterTitle: 'Жаңылыктарга жазылыңыз',
                newsletterCopy: 'Апта сайын жаңы сөздөрдү жана пайдалуу кеңештерди алыңыз.',
                newsletterPlaceholder: 'Электрондук почтаңыз',
                newsletterButton: 'Жазылуу',
                footerCopy: 'Кыргызча негизги интерфейси бар немис тилин үйрөнүү платформасы.',
                footerCourses: 'Курстар',
                footerContact: 'Байланыш',
                footerCity: 'Бишкек, Кыргызстан',
                footerBottom: '© 2026 DeutschLernen. Бардык укуктар корголгон.',
                actionStart: 'Акысыз сабак башталды!',
                actionLogin: 'Кирүү барагы жакында ачылат.',
                actionRegister: 'Катталуу барагы жакында ачылат.',
                actionCourse: 'Курс жөнүндө маалымат жөнөтүлдү.',
                actionTeacher: 'Мугалимдин профили жакында ачылат.',
                actionSocial: 'Бул шилтеме кийин кошулат.',
                actionContact: 'Байланыш маалыматы көчүрүүгө даяр.',
                newsletterInvalid: 'Сураныч, туура электрондук почта жазыңыз.',
                newsletterSuccess: 'Жазылуу ийгиликтүү аяктады. Рахмат!',
                saveAdded: 'Сөз жеке сөздүккө кошулду.',
                saveExists: 'Бул сөз буга чейин сакталган.',
                saveRemoved: 'Сөз өчүрүлдү.',
                copied: 'Жыйынтык көчүрүлдү.',
                exportDone: 'Сөздөр тизмеси көчүрүлдү.',
                resetDone: 'Жергиликтүү прогресс тазаланды.',
                streakLabel: 'күндүк серия',
                goalLabel: 'Бүгүн 1 тест же 1 сөз',
                badgeLocked: 'Ачыла элек',
                badgeUnlocked: 'Ачылды',
                transcriptKg: 'Кыргызча',
                transcriptRu: 'Орусча',
                transcriptDe: 'Deutsch'
            },
            ru: {
                themeToggle: 'Тема',
                navHome: 'Главная',
                navCourses: 'Курсы',
                navPractice: 'Практика',
                navHub: 'Прогресс',
                navTeachers: 'Преподаватели',
                navFaq: 'Вопросы',
                login: 'Войти',
                register: 'Регистрация',
                heroTag: 'Кыргызский как основной интерфейс',
                heroPrimary: 'Начать бесплатно',
                heroSecondary: 'Смотреть курсы',
                heroStatStudents: 'Студентов',
                heroStatRating: 'Рейтинг',
                heroStatLevels: 'Уровни',
                heroFloat1Label: 'Слово дня',
                heroFloat1Badge: 'Живой ротатор',
                heroFloat2Label: 'Ежедневная цель',
                heroRotatorLabel: 'Немецкое слово',
                coursesTag: 'Наша программа',
                coursesTitle: 'Курсы',
                coursesCopy: 'Изучайте немецкий поэтапно от A1 до B1.',
                practiceTag: 'Ежедневная практика',
                practiceTitle: 'Практика',
                practiceCopy: 'Закрепляйте слова через карточки, произношение и тест.',
                flashFrontHint: 'Нажмите, чтобы увидеть перевод',
                flashBackHint: 'Перевод',
                flashFlip: 'Перевернуть',
                flashSpeak: 'Прослушать',
                flashSave: 'Сохранить',
                flashNext: 'Следующее',
                flashTranslationNote: 'Кыргызский основной перевод, русский для поддержки',
                speechReady: 'Готово к прослушиванию и повторению немецкого слова.',
                speechPlaying: 'Проигрывается немецкое произношение.',
                speechUnsupported: 'В этом браузере нет распознавания речи. Озвучивание слова всё равно работает.',
                speechListening: 'Повторите сейчас:',
                speechGood: 'Отлично! Распознано:',
                speechTryAgain: 'Попробуйте ещё раз. Распознано:',
                speechError: 'Разрешите доступ к микрофону и попробуйте снова.',
                quizTitle: 'Тест',
                quizQuestion: 'Что означает это слово?',
                quizNext: 'Следующий вопрос',
                quizShare: 'Поделиться результатом',
                quizCorrect: 'Правильный ответ!',
                quizWrong: 'К сожалению, это неверно.',
                quizFinished: 'Тест завершён. Теперь можно поделиться результатом.',
                hubTag: 'Новые функции',
                hubTitle: 'Центр ученика',
                hubCopy: 'Следите за серией, сохраняйте слова, смотрите грамматику и проходите тест уровня.',
                streakKicker: 'Ежедневная цель',
                streakTitle: 'Серия и прогресс',
                streakCopy: 'Каждый день практики сохраняется в браузере.',
                markStudy: 'Сегодня учился',
                resetProgress: 'Очистить локальный прогресс',
                statDays: 'Дней подряд',
                statWords: 'Сохранённых слов',
                statAccuracy: 'Точность',
                dashFlashcards: 'Карточки',
                dashVocab: 'Словарь',
                dashPlacement: 'Тест уровня',
                vocabKicker: 'Личный словарь',
                vocabTitle: 'Сохранённые слова',
                vocabCopy: 'Сохраняйте слова с карточек и возвращайтесь к ним позже.',
                exportVocab: 'Экспорт',
                vocabEmpty: 'Пока нет сохранённых слов. Сохраните слово с карточки.',
                vocabReview: 'Повторить',
                vocabDelete: 'Удалить',
                grammarKicker: 'Грамматика A1-B1',
                grammarTitle: 'Грамматические таблицы',
                grammarCopy: 'Краткие объяснения по артиклям, глаголам и падежам.',
                grammarArticles: 'Артикли',
                grammarVerbs: 'Глаголы',
                grammarCases: 'Падежи',
                placementKicker: '10 вопросов',
                placementTitle: 'Тест на уровень',
                placementCopy: 'Рекомендует, с какого курса лучше начать.',
                placementStart: 'Выберите правильный вариант ответа.',
                placementDoneA1: 'Рекомендуется начать с уровня A1.',
                placementDoneA2: 'Рекомендуется начать с уровня A2.',
                placementDoneB1: 'Рекомендуется начать с уровня B1.',
                extrasTag: 'Дополнительные возможности',
                extrasTitle: 'Диалоги, рейтинг и достижения',
                extrasCopy: 'Слушайте диалоги, набирайте очки и открывайте бейджи.',
                leaderboardKicker: 'Локальный рейтинг',
                leaderboardTitle: 'Лучшие ученики',
                leaderboardCopy: 'Ваш счёт тоже сохраняется локально.',
                badgesKicker: 'Достижения',
                badgesTitle: 'Бейджи',
                badgesCopy: 'Открываются за 5 тестов, 20 слов и 3 дня подряд.',
                teachersTag: 'Команда',
                teachersTitle: 'Преподаватели',
                teachersCopy: 'Опытная команда, работающая на трёх языках.',
                testimonialsTag: 'Отзывы',
                testimonialsTitle: 'Что говорят ученики',
                testimonialsCopy: 'Отзывы тоже полностью локализованы.',
                faqTag: 'Вопросы',
                faqTitle: 'Часто задаваемые вопросы',
                faqCopy: 'Открываются без перезагрузки и сразу меняются по языку.',
                newsletterTitle: 'Подпишитесь на новости',
                newsletterCopy: 'Получайте новые слова и полезные советы каждую неделю.',
                newsletterPlaceholder: 'Ваш email',
                newsletterButton: 'Подписаться',
                footerCopy: 'Платформа для изучения немецкого с кыргызским основным интерфейсом.',
                footerCourses: 'Курсы',
                footerContact: 'Контакты',
                footerCity: 'Бишкек, Кыргызстан',
                footerBottom: '© 2026 DeutschLernen. Все права защищены.',
                actionStart: 'Бесплатный урок начался!',
                actionLogin: 'Страница входа скоро появится.',
                actionRegister: 'Страница регистрации скоро появится.',
                actionCourse: 'Информация о курсе отправлена.',
                actionTeacher: 'Профиль преподавателя скоро откроется.',
                actionSocial: 'Эта ссылка будет добавлена позже.',
                actionContact: 'Контактная информация готова к копированию.',
                newsletterInvalid: 'Пожалуйста, введите корректный email.',
                newsletterSuccess: 'Подписка оформлена. Спасибо!',
                saveAdded: 'Слово добавлено в личный словарь.',
                saveExists: 'Это слово уже сохранено.',
                saveRemoved: 'Слово удалено.',
                copied: 'Результат скопирован.',
                exportDone: 'Список слов скопирован.',
                resetDone: 'Локальный прогресс очищен.',
                streakLabel: 'дн. подряд',
                goalLabel: 'Сегодня 1 тест или 1 слово',
                badgeLocked: 'Не открыто',
                badgeUnlocked: 'Открыто',
                transcriptKg: 'Кыргызча',
                transcriptRu: 'Русский',
                transcriptDe: 'Deutsch'
            },
            de: {
                themeToggle: 'Thema',
                navHome: 'Start',
                navCourses: 'Kurse',
                navPractice: 'Praxis',
                navHub: 'Fortschritt',
                navTeachers: 'Lehrer',
                navFaq: 'Fragen',
                login: 'Anmelden',
                register: 'Registrieren',
                heroTag: 'Kirgisisch als Hauptoberfläche',
                heroPrimary: 'Kostenlos starten',
                heroSecondary: 'Kurse ansehen',
                heroStatStudents: 'Lernende',
                heroStatRating: 'Bewertung',
                heroStatLevels: 'Niveaus',
                heroFloat1Label: 'Wort des Tages',
                heroFloat1Badge: 'Live-Rotator',
                heroFloat2Label: 'Tagesziel',
                heroRotatorLabel: 'Deutsches Wort',
                coursesTag: 'Unser Programm',
                coursesTitle: 'Kurse',
                coursesCopy: 'Lerne Deutsch Schritt für Schritt von A1 bis B1.',
                practiceTag: 'Tägliche Praxis',
                practiceTitle: 'Praxis',
                practiceCopy: 'Festige Wörter mit Karteikarten, Aussprache und Quiz.',
                flashFrontHint: 'Klicken, um die Übersetzung zu sehen',
                flashBackHint: 'Übersetzung',
                flashFlip: 'Drehen',
                flashSpeak: 'Anhören',
                flashSave: 'Speichern',
                flashNext: 'Weiter',
                flashTranslationNote: 'Kirgisisch als Hauptübersetzung, Russisch als Zusatz',
                speechReady: 'Bereit zum Anhören und Nachsprechen des deutschen Wortes.',
                speechPlaying: 'Die deutsche Aussprache wird abgespielt.',
                speechUnsupported: 'In diesem Browser ist keine Spracherkennung verfügbar. Die Aussprache funktioniert trotzdem.',
                speechListening: 'Bitte jetzt nachsprechen:',
                speechGood: 'Sehr gut! Erkannt wurde:',
                speechTryAgain: 'Bitte noch einmal versuchen. Erkannt wurde:',
                speechError: 'Bitte Mikrofonzugriff erlauben und erneut versuchen.',
                quizTitle: 'Quiz',
                quizQuestion: 'Was bedeutet dieses Wort?',
                quizNext: 'Nächste Frage',
                quizShare: 'Ergebnis teilen',
                quizCorrect: 'Richtige Antwort!',
                quizWrong: 'Leider falsch.',
                quizFinished: 'Das Quiz ist beendet. Jetzt kannst du dein Ergebnis teilen.',
                hubTag: 'Neue Funktionen',
                hubTitle: 'Lernzentrum',
                hubCopy: 'Verfolge deine Serie, speichere Wörter, nutze Grammatik und mache den Einstufungstest.',
                streakKicker: 'Tagesziel',
                streakTitle: 'Serie und Fortschritt',
                streakCopy: 'Jeder Lerntag wird im Browser gespeichert.',
                markStudy: 'Heute gelernt',
                resetProgress: 'Lokalen Fortschritt löschen',
                statDays: 'Tage in Folge',
                statWords: 'Gespeicherte Wörter',
                statAccuracy: 'Genauigkeit',
                dashFlashcards: 'Karteikarten',
                dashVocab: 'Vokabelbuch',
                dashPlacement: 'Einstufungstest',
                vocabKicker: 'Persönliches Vokabelbuch',
                vocabTitle: 'Gespeicherte Wörter',
                vocabCopy: 'Speichere Wörter aus den Karteikarten und wiederhole sie später.',
                exportVocab: 'Export',
                vocabEmpty: 'Noch keine gespeicherten Wörter. Speichere ein Wort aus der Karteikarte.',
                vocabReview: 'Wiederholen',
                vocabDelete: 'Löschen',
                grammarKicker: 'Grammatik A1-B1',
                grammarTitle: 'Grammatiktabellen',
                grammarCopy: 'Kurze Erklärungen zu Artikeln, Verben und Fällen.',
                grammarArticles: 'Artikel',
                grammarVerbs: 'Verben',
                grammarCases: 'Fälle',
                placementKicker: '10 Fragen',
                placementTitle: 'Einstufungstest',
                placementCopy: 'Empfiehlt, mit welchem Kurs du beginnen solltest.',
                placementStart: 'Wähle die richtige Antwort.',
                placementDoneA1: 'Empfohlen wird ein Start mit Niveau A1.',
                placementDoneA2: 'Empfohlen wird ein Start mit Niveau A2.',
                placementDoneB1: 'Empfohlen wird ein Start mit Niveau B1.',
                extrasTag: 'Zusatzfunktionen',
                extrasTitle: 'Dialoge, Rangliste und Abzeichen',
                extrasCopy: 'Höre Alltagssituationen, sammle Punkte und schalte Abzeichen frei.',
                leaderboardKicker: 'Lokale Rangliste',
                leaderboardTitle: 'Top-Lernende',
                leaderboardCopy: 'Dein Punktestand wird ebenfalls lokal gespeichert.',
                badgesKicker: 'Erfolge',
                badgesTitle: 'Abzeichen',
                badgesCopy: 'Werden für 5 Quiz, 20 Wörter und 3 Lerntage in Folge freigeschaltet.',
                teachersTag: 'Team',
                teachersTitle: 'Lehrer',
                teachersCopy: 'Erfahrenes Team für drei Sprachen.',
                testimonialsTag: 'Bewertungen',
                testimonialsTitle: 'Was Lernende sagen',
                testimonialsCopy: 'Auch die Bewertungen sind vollständig lokalisiert.',
                faqTag: 'Fragen',
                faqTitle: 'Häufige Fragen',
                faqCopy: 'Öffnen sich ohne Neuladen und wechseln sofort mit der Sprache.',
                newsletterTitle: 'Newsletter abonnieren',
                newsletterCopy: 'Erhalte jede Woche neue Wörter und nützliche Tipps.',
                newsletterPlaceholder: 'Deine E-Mail-Adresse',
                newsletterButton: 'Abonnieren',
                footerCopy: 'Plattform zum Deutschlernen mit Kirgisisch als Hauptoberfläche.',
                footerCourses: 'Kurse',
                footerContact: 'Kontakt',
                footerCity: 'Bischkek, Kirgisistan',
                footerBottom: '© 2026 DeutschLernen. Alle Rechte vorbehalten.',
                actionStart: 'Die kostenlose Lektion wurde gestartet!',
                actionLogin: 'Die Login-Seite kommt bald.',
                actionRegister: 'Die Registrierungsseite kommt bald.',
                actionCourse: 'Die Kursinformation wurde gesendet.',
                actionTeacher: 'Das Lehrerprofil wird bald geöffnet.',
                actionSocial: 'Dieser Link wird später ergänzt.',
                actionContact: 'Die Kontaktdaten sind zum Kopieren bereit.',
                newsletterInvalid: 'Bitte gib eine gültige E-Mail-Adresse ein.',
                newsletterSuccess: 'Danke! Das Abonnement wurde gespeichert.',
                saveAdded: 'Das Wort wurde dem Vokabelbuch hinzugefügt.',
                saveExists: 'Dieses Wort ist bereits gespeichert.',
                saveRemoved: 'Das Wort wurde gelöscht.',
                copied: 'Ergebnis wurde kopiert.',
                exportDone: 'Die Wortliste wurde kopiert.',
                resetDone: 'Der lokale Fortschritt wurde gelöscht.',
                streakLabel: 'Tage Serie',
                goalLabel: 'Heute 1 Quiz oder 1 Wort',
                badgeLocked: 'Gesperrt',
                badgeUnlocked: 'Freigeschaltet',
                transcriptKg: 'Кыргызча',
                transcriptRu: 'Russisch',
                transcriptDe: 'Deutsch'
            }
        };

        const heroContent = {
            kg: {
                title: 'Немис тилин<br><span>Кыргызча үйрөнүңүз</span>',
                copy: 'DeutschLernen платформасы кыргыз тилин негизги интерфейс катары сунуштайт. Орусча жана немисче дагы толук иштейт, бирок негизги тажрыйба кыргыз колдонуучулар үчүн так жана түшүнүктүү бойдон калат.'
            },
            ru: {
                title: 'Учите немецкий<br><span>с понятным интерфейсом</span>',
                copy: 'DeutschLernen использует кыргызский как основную локаль, а русский и немецкий мгновенно переключаются для всех динамических блоков сайта.'
            },
            de: {
                title: 'Deutsch lernen<br><span>mit klarer Oberfläche</span>',
                copy: 'DeutschLernen nutzt Kirgisisch als Hauptoberfläche. Russisch und Deutsch werden trotzdem vollständig und sofort umgeschaltet.'
            }
        };

        const heroWords = [
            { de: 'Hallo', kg: 'Салам', ru: 'Привет' },
            { de: 'Danke', kg: 'Рахмат', ru: 'Спасибо' },
            { de: 'Brot', kg: 'Нан', ru: 'Хлеб' },
            { de: 'Freund', kg: 'Дос', ru: 'Друг' },
            { de: 'Wasser', kg: 'Суу', ru: 'Вода' }
        ];

        const courses = [
            {
                level: 'A1',
                tone: 'a1',
                price: ['2 990 сом', '3 990 ₽', '34 €'],
                badge: { kg: 'Башталгыч', ru: 'Начальный', de: 'Anfang' },
                title: { kg: 'Немис тили A1', ru: 'Немецкий A1', de: 'Deutsch A1' },
                desc: {
                    kg: 'Нөлдөн баштагандар үчүн курс. Саламдашуу, үй-бүлө, күнүмдүк сөздөр жана жөнөкөй грамматика.',
                    ru: 'Курс для начинающих с нуля. Приветствия, семья, повседневные слова и базовая грамматика.',
                    de: 'Kurs für absolute Anfänger. Begrüßung, Familie, Alltagswörter und Grundgrammatik.'
                },
                feats: {
                    kg: ['24 сабак', '300+ сөз', 'Кыргызча түшүндүрмө'],
                    ru: ['24 урока', '300+ слов', 'Пояснения на русском'],
                    de: ['24 Lektionen', '300+ Wörter', 'Erklärungen auf Deutsch']
                },
                action: 'course'
            },
            {
                level: 'A2',
                tone: 'a2',
                price: ['3 990 сом', '4 490 ₽', '42 €'],
                badge: { kg: 'Орто башталгыч', ru: 'Ниже среднего', de: 'Grundstufe' },
                title: { kg: 'Немис тили A2', ru: 'Немецкий A2', de: 'Deutsch A2' },
                desc: {
                    kg: 'Диалогдорду, убакыт формаларын жана күнүмдүк сүйлөмдөрдү ишенимдүү колдонуу үчүн.',
                    ru: 'Для уверенного использования диалогов, времён и повседневных фраз.',
                    de: 'Für sicherere Dialoge, Zeitformen und häufige Alltagssätze.'
                },
                feats: {
                    kg: ['32 сабак', '550+ сөз', 'Сүйлөө көнүгүүсү'],
                    ru: ['32 урока', '550+ слов', 'Разговорная практика'],
                    de: ['32 Lektionen', '550+ Wörter', 'Sprechpraxis']
                },
                action: 'course'
            },
            {
                level: 'B1',
                tone: 'b1',
                price: ['4 990 сом', '5 990 ₽', '54 €'],
                badge: { kg: 'Орто деңгээл', ru: 'Средний', de: 'Mittelstufe' },
                title: { kg: 'Немис тили B1', ru: 'Немецкий B1', de: 'Deutsch B1' },
                desc: {
                    kg: 'Кеңири сүйлөшүү, жумуш жана окуу темалары боюнча өз оюн жеткирүү үчүн.',
                    ru: 'Чтобы уверенно выражать мысли по работе, учёбе и повседневным темам.',
                    de: 'Für selbstständiges Sprechen über Arbeit, Studium und Alltagsthemen.'
                },
                feats: {
                    kg: ['40 сабак', '900+ сөз', 'Тест жана тексттер'],
                    ru: ['40 уроков', '900+ слов', 'Тесты и тексты'],
                    de: ['40 Lektionen', '900+ Wörter', 'Tests und Texte']
                },
                action: 'course'
            }
        ];

        const flashcards = [
            {
                de: 'die Katze',
                kg: 'мышык',
                ru: 'кошка',
                example: {
                    kg: 'Die Katze schläft auf dem Sofa. — Мышык диванда уктап жатат.',
                    ru: 'Die Katze schläft auf dem Sofa. — Кошка спит на диване.',
                    de: 'Die Katze schläft auf dem Sofa.'
                }
            },
            {
                de: 'der Hund',
                kg: 'ит',
                ru: 'собака',
                example: {
                    kg: 'Der Hund läuft schnell. — Ит тез чуркап жатат.',
                    ru: 'Der Hund läuft schnell. — Собака быстро бежит.',
                    de: 'Der Hund läuft schnell.'
                }
            },
            {
                de: 'das Haus',
                kg: 'үй',
                ru: 'дом',
                example: {
                    kg: 'Das Haus ist neu. — Үй жаңы.',
                    ru: 'Das Haus ist neu. — Дом новый.',
                    de: 'Das Haus ist neu.'
                }
            },
            {
                de: 'die Schule',
                kg: 'мектеп',
                ru: 'школа',
                example: {
                    kg: 'Die Schule beginnt um acht Uhr. — Мектеп сегизде башталат.',
                    ru: 'Die Schule beginnt um acht Uhr. — Школа начинается в восемь.',
                    de: 'Die Schule beginnt um acht Uhr.'
                }
            },
            {
                de: 'das Brot',
                kg: 'нан',
                ru: 'хлеб',
                example: {
                    kg: 'Ich kaufe frisches Brot. — Мен жаңы нан сатып алам.',
                    ru: 'Ich kaufe frisches Brot. — Я покупаю свежий хлеб.',
                    de: 'Ich kaufe frisches Brot.'
                }
            },
            {
                de: 'die Arbeit',
                kg: 'иш',
                ru: 'работа',
                example: {
                    kg: 'Die Arbeit beginnt um neun. — Иш тогузда башталат.',
                    ru: 'Die Arbeit beginnt um neun. — Работа начинается в девять.',
                    de: 'Die Arbeit beginnt um neun.'
                }
            }
        ];

        const quizData = [
            {
                word: 'Hallo',
                options: {
                    kg: ['Салам', 'Рахмат', 'Кош бол', 'Ооба'],
                    ru: ['Привет', 'Спасибо', 'Пока', 'Да'],
                    de: ['Hallo', 'Danke', 'Tschüss', 'Ja']
                },
                correctIndex: 0
            },
            {
                word: 'Danke',
                options: {
                    kg: ['Сураныч', 'Рахмат', 'Жок', 'Салам'],
                    ru: ['Пожалуйста', 'Спасибо', 'Нет', 'Привет'],
                    de: ['Bitte', 'Danke', 'Nein', 'Hallo']
                },
                correctIndex: 1
            },
            {
                word: 'Wasser',
                options: {
                    kg: ['Сүт', 'Нан', 'Суу', 'Туз'],
                    ru: ['Молоко', 'Хлеб', 'Вода', 'Соль'],
                    de: ['Milch', 'Brot', 'Wasser', 'Salz']
                },
                correctIndex: 2
            },
            {
                word: 'Freund',
                options: {
                    kg: ['Дос', 'Китеп', 'Терезе', 'Мектеп'],
                    ru: ['Друг', 'Книга', 'Окно', 'Школа'],
                    de: ['Freund', 'Buch', 'Fenster', 'Schule']
                },
                correctIndex: 0
            },
            {
                word: 'Brot',
                options: {
                    kg: ['Жемиш', 'Нан', 'Суу', 'Кофе'],
                    ru: ['Фрукт', 'Хлеб', 'Вода', 'Кофе'],
                    de: ['Obst', 'Brot', 'Wasser', 'Kaffee']
                },
                correctIndex: 1
            }
        ];

        const grammarContent = {
            articles: {
                explain: {
                    kg: 'Артикль зат атоочтун жынысын көрсөтөт. der — эркек, die — аял же көптүк, das — орто жыныс.',
                    ru: 'Артикль показывает род существительного. der — мужской, die — женский или множественное число, das — средний.',
                    de: 'Der Artikel zeigt das grammatische Geschlecht. der — maskulin, die — feminin oder Plural, das — neutral.'
                },
                headers: {
                    kg: ['Артикль', 'Мисал', 'Түшүндүрмө'],
                    ru: ['Артикль', 'Пример', 'Пояснение'],
                    de: ['Artikel', 'Beispiel', 'Hinweis']
                },
                rows: {
                    kg: [['der', 'der Hund', 'Көп учурда эркек жыныстагы сөздөр'], ['die', 'die Schule', 'Аял жыныс же көптүк'], ['das', 'das Kind', 'Орто жыныс']],
                    ru: [['der', 'der Hund', 'Часто мужской род'], ['die', 'die Schule', 'Женский род или множественное число'], ['das', 'das Kind', 'Средний род']],
                    de: [['der', 'der Hund', 'oft maskuline Wörter'], ['die', 'die Schule', 'feminine Wörter oder Plural'], ['das', 'das Kind', 'neutrale Wörter']]
                }
            },
            verbs: {
                explain: {
                    kg: 'Этиш адамга жараша өзгөрөт. Мисалы, lernen этиши.',
                    ru: 'Глагол меняется по лицам. Например, lernen.',
                    de: 'Das Verb verändert sich nach der Person. Beispiel: lernen.'
                },
                headers: {
                    kg: ['Ат атооч', 'Форма', 'Маани'],
                    ru: ['Местоимение', 'Форма', 'Значение'],
                    de: ['Pronomen', 'Form', 'Bedeutung']
                },
                rows: {
                    kg: [['ich', 'lerne', 'мен үйрөнөм'], ['du', 'lernst', 'сен үйрөнөсүң'], ['er/sie', 'lernt', 'ал үйрөнөт'], ['wir', 'lernen', 'биз үйрөнөбүз']],
                    ru: [['ich', 'lerne', 'я учу'], ['du', 'lernst', 'ты учишь'], ['er/sie', 'lernt', 'он/она учит'], ['wir', 'lernen', 'мы учим']],
                    de: [['ich', 'lerne', 'ich lerne'], ['du', 'lernst', 'du lernst'], ['er/sie', 'lernt', 'er oder sie lernt'], ['wir', 'lernen', 'wir lernen']]
                }
            },
            cases: {
                explain: {
                    kg: 'Nominativ ким? Akkusativ кимди? Emнени? Бул объектти түшүнүүгө жардам берет.',
                    ru: 'Nominativ отвечает на вопрос кто? Akkusativ — кого? что? Это помогает различать подлежащее и объект.',
                    de: 'Nominativ fragt nach dem Subjekt, Akkusativ nach dem direkten Objekt.'
                },
                headers: {
                    kg: ['Септик', 'Суроо', 'Мисал'],
                    ru: ['Падеж', 'Вопрос', 'Пример'],
                    de: ['Fall', 'Frage', 'Beispiel']
                },
                rows: {
                    kg: [['Nominativ', 'ким?', 'Der Mann lernt.'], ['Akkusativ', 'кимди? эмнени?', 'Ich sehe den Mann.']],
                    ru: [['Nominativ', 'кто?', 'Der Mann lernt.'], ['Akkusativ', 'кого? что?', 'Ich sehe den Mann.']],
                    de: [['Nominativ', 'wer?', 'Der Mann lernt.'], ['Akkusativ', 'wen? was?', 'Ich sehe den Mann.']]
                }
            }
        };

        const placementQuestions = [
            { q: { kg: 'Ich ___ Maria.', ru: 'Ich ___ Maria.', de: 'Ich ___ Maria.' }, options: { kg: ['bin', 'bist', 'seid'], ru: ['bin', 'bist', 'seid'], de: ['bin', 'bist', 'seid'] }, correct: 0 },
            { q: { kg: 'Wir ___ in Berlin.', ru: 'Wir ___ in Berlin.', de: 'Wir ___ in Berlin.' }, options: { kg: ['wohnen', 'wohnst', 'wohnt'], ru: ['wohnen', 'wohnst', 'wohnt'], de: ['wohnen', 'wohnst', 'wohnt'] }, correct: 0 },
            { q: { kg: 'Der Kaffee ist ___.', ru: 'Der Kaffee ist ___.', de: 'Der Kaffee ist ___.' }, options: { kg: ['heiß', 'gehen', 'morgen'], ru: ['heiß', 'gehen', 'morgen'], de: ['heiß', 'gehen', 'morgen'] }, correct: 0 },
            { q: { kg: 'Gestern ___ ich einen Film gesehen.', ru: 'Gestern ___ ich einen Film gesehen.', de: 'Gestern ___ ich einen Film gesehen.' }, options: { kg: ['habe', 'hat', 'haben'], ru: ['habe', 'hat', 'haben'], de: ['habe', 'hat', 'haben'] }, correct: 0 },
            { q: { kg: 'Kannst du mir bitte ___ helfen?', ru: 'Kannst du mir bitte ___ helfen?', de: 'Kannst du mir bitte ___ helfen?' }, options: { kg: ['mit', 'zu', 'von'], ru: ['mit', 'zu', 'von'], de: ['mit', 'zu', 'von'] }, correct: 0 },
            { q: { kg: 'Ich habe gestern meine Tante ___.', ru: 'Ich habe gestern meine Tante ___.', de: 'Ich habe gestern meine Tante ___.' }, options: { kg: ['besucht', 'besuchen', 'besuchtet'], ru: ['besucht', 'besuchen', 'besuchtet'], de: ['besucht', 'besuchen', 'besuchtet'] }, correct: 0 },
            { q: { kg: 'Wenn ich Zeit habe, ___ ich dich an.', ru: 'Wenn ich Zeit habe, ___ ich dich an.', de: 'Wenn ich Zeit habe, ___ ich dich an.' }, options: { kg: ['rufe', 'gerufen', 'rief'], ru: ['rufe', 'gerufen', 'rief'], de: ['rufe', 'gerufen', 'rief'] }, correct: 0 },
            { q: { kg: 'Das ist die Frau, ___ in Bischkek arbeitet.', ru: 'Das ist die Frau, ___ in Bischkek arbeitet.', de: 'Das ist die Frau, ___ in Bischkek arbeitet.' }, options: { kg: ['die', 'der', 'den'], ru: ['die', 'der', 'den'], de: ['die', 'der', 'den'] }, correct: 0 },
            { q: { kg: 'Ich interessiere mich ___ deutsche Literatur.', ru: 'Ich interessiere mich ___ немецкую литературу.', de: 'Ich interessiere mich ___ deutsche Literatur.' }, options: { kg: ['für', 'mit', 'nach'], ru: ['für', 'mit', 'nach'], de: ['für', 'mit', 'nach'] }, correct: 0 },
            { q: { kg: 'Obwohl es regnet, ___ wir spazieren.', ru: 'Obwohl es regnet, ___ wir spazieren.', de: 'Obwohl es regnet, ___ wir spazieren.' }, options: { kg: ['gehen', 'geht', 'gehe'], ru: ['gehen', 'geht', 'gehe'], de: ['gehen', 'geht', 'gehe'] }, correct: 0 }
        ];

        const dialogues = [
            {
                key: 'cafe',
                title: { kg: 'Кафеде', ru: 'В кафе', de: 'Im Café' },
                lines: {
                    de: [['Anna', 'Guten Tag! Ich möchte einen Kaffee.'], ['Max', 'Gern. Mit Milch oder ohne?'], ['Anna', 'Mit Milch, bitte. Danke schön!']],
                    kg: [['Анна', 'Саламатсызбы! Мен кофе каалайм.'], ['Макс', 'Макул. Сүт мененби же сүтсүзбү?'], ['Анна', 'Сүт менен, сураныч. Чоң рахмат!']],
                    ru: [['Анна', 'Здравствуйте! Я хочу кофе.'], ['Макс', 'Хорошо. С молоком или без?'], ['Анна', 'С молоком, пожалуйста. Большое спасибо!']]
                }
            },
            {
                key: 'greeting',
                title: { kg: 'Саламдашуу', ru: 'Приветствие', de: 'Begrüßung' },
                lines: {
                    de: [['Ali', 'Hallo, wie heißt du?'], ['Sara', 'Ich heiße Sara. Und du?'], ['Ali', 'Ich heiße Ali. Freut mich!']],
                    kg: [['Али', 'Салам, атың ким?'], ['Сара', 'Менин атым Сара. А сенчи?'], ['Али', 'Менин атым Али. Таанышканыма кубанычтамын!']],
                    ru: [['Али', 'Привет, как тебя зовут?'], ['Сара', 'Меня зовут Сара. А тебя?'], ['Али', 'Меня зовут Али. Очень приятно!']]
                }
            },
            {
                key: 'station',
                title: { kg: 'Бекетте', ru: 'На станции', de: 'Am Bahnhof' },
                lines: {
                    de: [['Frau', 'Entschuldigung, wo ist Gleis drei?'], ['Mann', 'Geradeaus und dann links.'], ['Frau', 'Danke für Ihre Hilfe!']],
                    kg: [['Айым', 'Кечиресиз, үчүнчү жол кайда?'], ['Мырза', 'Түз барып, анан солго буруласыз.'], ['Айым', 'Жардамыңыз үчүн рахмат!']],
                    ru: [['Женщина', 'Извините, где третья платформа?'], ['Мужчина', 'Прямо и потом налево.'], ['Женщина', 'Спасибо за помощь!']]
                }
            }
        ];

        const teachers = [
            {
                initials: 'A',
                name: { kg: 'Айсулуу', ru: 'Айсулуу', de: 'Aisuluu' },
                role: { kg: 'Кыргызча жана немисче', ru: 'Кыргызский и немецкий', de: 'Kirgisisch und Deutsch' },
                bio: {
                    kg: '10 жылдык тажрыйбасы бар. Немис тилин кыргыз тилдүү студенттерге түшүнүктүү кылып үйрөтөт.',
                    ru: 'Имеет 10 лет опыта. Объясняет немецкий максимально понятно для кыргызскоязычных студентов.',
                    de: 'Hat 10 Jahre Erfahrung und erklärt Deutsch besonders klar für kirgisischsprachige Lernende.'
                },
                meta: {
                    kg: ['350+ окуучу', '10 жыл тажрыйба'],
                    ru: ['350+ студентов', '10 лет опыта'],
                    de: ['350+ Lernende', '10 Jahre Erfahrung']
                }
            },
            {
                initials: 'E',
                name: { kg: 'Елена', ru: 'Елена', de: 'Elena' },
                role: { kg: 'Орусча жана немисче', ru: 'Русский и немецкий', de: 'Russisch und Deutsch' },
                bio: {
                    kg: 'Орус тилдүү окуучулар үчүн структуралуу сабак өткөрөт жана грамматиканы майда-чүйдөсүнө чейин түшүндүрөт.',
                    ru: 'Ведёт структурированные уроки для русскоязычных учеников и подробно разбирает грамматику.',
                    de: 'Leitet strukturierte Stunden für russischsprachige Lernende und erklärt Grammatik sehr gründlich.'
                },
                meta: {
                    kg: ['520+ окуучу', '12 жыл тажрыйба'],
                    ru: ['520+ студентов', '12 лет опыта'],
                    de: ['520+ Lernende', '12 Jahre Erfahrung']
                }
            },
            {
                initials: 'H',
                name: { kg: 'Ханс', ru: 'Ханс', de: 'Hans' },
                role: { kg: 'Немисче эне тили', ru: 'Носитель немецкого', de: 'Muttersprachler' },
                bio: {
                    kg: 'Берлинден келген мугалим. Айтылыш жана жандуу сүйлөө боюнча күчтүү практикалык сабак берет.',
                    ru: 'Преподаватель из Берлина. Силен в постановке произношения и разговорной практике.',
                    de: 'Lehrer aus Berlin. Spezialist für Aussprache und lebendige Sprechpraxis.'
                },
                meta: {
                    kg: ['800+ окуучу', '15 жыл тажрыйба'],
                    ru: ['800+ студентов', '15 лет опыта'],
                    de: ['800+ Lernende', '15 Jahre Erfahrung']
                }
            }
        ];

        const testimonials = [
            {
                name: { kg: 'Гүлнара', ru: 'Гульнара', de: 'Gulnara' },
                city: { kg: 'Бишкек', ru: 'Бишкек', de: 'Bischkek' },
                text: {
                    kg: 'Кыргызча интерфейс мага абдан жакты. Бардык баскычтар, түшүндүрмөлөр жана тесттер өз тилимде так иштейт.',
                    ru: 'Мне очень понравился кыргызский интерфейс. Все кнопки, объяснения и тесты работают без путаницы.',
                    de: 'Die kirgisische Oberfläche gefällt mir sehr. Alle Buttons, Erklärungen und Tests funktionieren ohne Verwirrung.'
                }
            },
            {
                name: { kg: 'Алексей', ru: 'Алексей', de: 'Alexey' },
                city: { kg: 'Москва', ru: 'Москва', de: 'Moskau' },
                text: {
                    kg: 'Орусчага өткөндө дагы баары дароо алмашат. Өзгөчө деңгээл тестин жана сөздүктү көп колдонуп жатам.',
                    ru: 'При переключении на русский всё меняется мгновенно. Особенно полезны тест уровня и личный словарь.',
                    de: 'Beim Wechsel auf Russisch wird alles sofort aktualisiert. Besonders hilfreich sind Einstufungstest und Vokabelbuch.'
                }
            },
            {
                name: { kg: 'Клаус', ru: 'Клаус', de: 'Klaus' },
                city: { kg: 'Берлин', ru: 'Берлин', de: 'Berlin' },
                text: {
                    kg: 'Диалогдор жана үн менен окуу бөлүгү заманбап сезилет. Немисче айтылыш да жакшы иштейт.',
                    ru: 'Диалоги и аудио-практика выглядят современно. Немецкое произношение воспроизводится очень хорошо.',
                    de: 'Die Dialoge und die Audio-Praxis wirken modern. Auch die deutsche Aussprache funktioniert sehr gut.'
                }
            }
        ];

        const faqItems = [
            {
                q: {
                    kg: 'Сайт кайсы тилдерде иштейт?',
                    ru: 'На каких языках работает сайт?',
                    de: 'Welche Sprachen unterstützt die Website?'
                },
                a: {
                    kg: 'Негизги интерфейс кыргызча. Ошол эле учурда орусча жана немисче дагы толук иштейт.',
                    ru: 'Основной интерфейс кыргызский, но русский и немецкий тоже работают полностью.',
                    de: 'Die Hauptoberfläche ist kirgisisch, aber Russisch und Deutsch funktionieren ebenfalls vollständig.'
                }
            },
            {
                q: {
                    kg: 'Тилди алмаштырганда барак жаңыланабы?',
                    ru: 'Нужно ли обновлять страницу при смене языка?',
                    de: 'Muss die Seite beim Sprachwechsel neu geladen werden?'
                },
                a: {
                    kg: 'Жок. Бардык динамикалык бөлүктөр дароо алмашат: тест, флэш-карта, FAQ, курстар, мугалимдер жана башкасы.',
                    ru: 'Нет. Все динамические блоки меняются сразу: тест, карточки, FAQ, курсы, преподаватели и другое.',
                    de: 'Nein. Alle dynamischen Bereiche wechseln sofort: Quiz, Karteikarten, FAQ, Kurse, Lehrer und mehr.'
                }
            },
            {
                q: {
                    kg: 'Сакталган сөздөр кайда калат?',
                    ru: 'Где хранятся сохранённые слова?',
                    de: 'Wo werden die gespeicherten Wörter abgelegt?'
                },
                a: {
                    kg: 'Алар браузердин localStorage ичинде сакталат жана кийинки киргенде кайра көрүнөт.',
                    ru: 'Они сохраняются в localStorage браузера и остаются доступными при следующем входе.',
                    de: 'Sie werden im localStorage des Browsers gespeichert und sind beim nächsten Besuch wieder da.'
                }
            },
            {
                q: {
                    kg: 'Үн менен окуу бардык телефондо иштейби?',
                    ru: 'Работает ли озвучивание на телефонах?',
                    de: 'Funktioniert die Audio-Funktion auch auf dem Handy?'
                },
                a: {
                    kg: 'Ооба, көпчүлүк заманбап браузерлерде немисче угуу иштейт. Үн таануу колдоого жараша өзгөрүшү мүмкүн.',
                    ru: 'Да, в большинстве современных браузеров немецкая озвучка работает. Распознавание речи зависит от поддержки браузера.',
                    de: 'Ja, die deutsche Aussprache funktioniert in den meisten modernen Browsern. Die Spracherkennung hängt von der Browser-Unterstützung ab.'
                }
            }
        ];

        const mockLeaderboard = [
            { name: 'Ainura', score: 980 },
            { name: 'Maksim', score: 920 },
            { name: 'Nurgül', score: 880 },
            { name: 'Sara', score: 840 },
            { name: 'Bekzat', score: 810 }
        ];

        const badgeDefinitions = [
            { id: 'quiz5', icons: 'fa-star', check: () => state.quizzesCompleted >= 5, title: { kg: 'Тест устасы', ru: 'Мастер тестов', de: 'Quiz-Profi' }, note: { kg: '5 тест бүтүрүңүз', ru: 'Завершите 5 тестов', de: 'Schließe 5 Quiz ab' } },
            { id: 'words20', icons: 'fa-bookmark', check: () => state.savedWords.length >= 20, title: { kg: 'Сөз жыйноочу', ru: 'Собиратель слов', de: 'Wortsammler' }, note: { kg: '20 сөз сактаңыз', ru: 'Сохраните 20 слов', de: 'Speichere 20 Wörter' } },
            { id: 'streak3', icons: 'fa-fire', check: () => state.streak >= 3, title: { kg: 'Серия башталды', ru: 'Серия началась', de: 'Serie gestartet' }, note: { kg: '3 күн катар окуңуз', ru: 'Учитесь 3 дня подряд', de: 'Lerne 3 Tage in Folge' } },
            { id: 'placement', icons: 'fa-route', check: () => state.placementFinished, title: { kg: 'Деңгээл аныкталды', ru: 'Уровень определён', de: 'Niveau gefunden' }, note: { kg: 'Тандоо тестин бүтүрүңүз', ru: 'Завершите тест уровня', de: 'Beende den Einstufungstest' } }
        ];

        let heroWordIndex = 0;
        let flashFlipped = false;
        let quizLocked = false;
        let transcriptTabs = { ...state.dialoguesTab };
        let recognition;
        let currentUtterance;

        function t(key) {
            return i18n[state.lang][key] || key;
        }

        function saveState() {
            state.dialoguesTab = transcriptTabs;
            localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
        }

        function showToast(msg, type='info') {
            const container = document.getElementById('toast-container');
            const el = document.createElement('div');
            el.className = 'toast ' + type;
            el.innerHTML = '<i class="fas ' + (type==='success'?'fa-check-circle':type==='error'?'fa-exclamation-circle':'fa-info-circle') + '" style="margin-right:8px"></i>' + msg;
            container.appendChild(el);
            setTimeout(() => el.remove(), 3100);
        }

        function showLocalizedAlert(messageKey) {
            const successKeys = ['saveAdded','exportDone','newsletterSuccess','resetDone','copied','actionStart'];
            const errorKeys = ['saveExists','newsletterInvalid','speechError'];
            const type = successKeys.includes(messageKey) ? 'success' : errorKeys.includes(messageKey) ? 'error' : 'info';
            showToast(t(messageKey), type);
        }

        function updateDocumentLanguage() {
            document.documentElement.lang = state.lang;
            document.querySelectorAll('[data-i18n]').forEach((el) => {
                const key = el.dataset.i18n;
                el.textContent = t(key);
            });
            document.querySelectorAll('[data-i18n-placeholder]').forEach((el) => {
                const key = el.dataset.i18nPlaceholder;
                el.placeholder = t(key);
            });
            document.title = state.lang === 'kg' ? 'DeutschLernen · Кыргызча немис тили' : state.lang === 'ru' ? 'DeutschLernen · Учить немецкий' : 'DeutschLernen · Deutsch lernen';
        }

        function applyTheme() {
            document.body.classList.toggle('theme-dark', state.theme === 'dark');
        }

        function markStudyDay() {
            if (state.lastStudyDate === todayKey) {
                updateStreakViews();
                return;
            }
            if (!state.lastStudyDate) {
                state.streak = 1;
            } else {
                const yesterday = new Date(Date.now() - 86400000).toISOString().slice(0, 10);
                state.streak = state.lastStudyDate === yesterday ? state.streak + 1 : 1;
            }
            state.lastStudyDate = todayKey;
            saveState();
            updateDashboard();
        }

        function computeUserScore() {
            return state.quizCorrect * 30 + state.savedWords.length * 8 + state.streak * 40 + (state.placementFinished ? 80 : 0);
        }

        function updateStreakViews() {
            const streakLabel = `${state.streak} ${t('streakLabel')}`;
            document.getElementById('streak-top').textContent = streakLabel;
            document.getElementById('streak-main').textContent = streakLabel;
            document.getElementById('hero-goal-streak').textContent = streakLabel;
            document.getElementById('hero-goal-label').textContent = t('goalLabel');
            document.getElementById('stat-days').textContent = state.streak;
        }

        function renderHero() {
            document.getElementById('hero-title').innerHTML = heroContent[state.lang].title;
            document.getElementById('hero-copy').textContent = heroContent[state.lang].copy;
            const item = heroWords[heroWordIndex];
            document.getElementById('hero-floating-word').textContent = item.de;
            document.getElementById('hero-rotator-word').textContent = item.de;
            document.getElementById('hero-rotator-kg').textContent = item.kg;
            document.getElementById('hero-rotator-ru').textContent = item.ru;
        }

        function rotateHeroWord() {
            heroWordIndex = (heroWordIndex + 1) % heroWords.length;
            renderHero();
        }

        function renderCourses() {
            const grid = document.getElementById('course-grid');
            grid.innerHTML = courses.map((course, index) => `
                <article class="course-card" data-aos="fade-up" data-aos-delay="${index * 70}">
                    <div class="course-top ${course.tone}">
                        <div class="mini-pill">${course.badge[state.lang]}</div>
                        <div class="course-level">${course.level}</div>
                        <div class="card-title" style="margin-top:18px">${course.title[state.lang]}</div>
                    </div>
                    <div class="course-body">
                        <p class="course-copy">${course.desc[state.lang]}</p>
                        <div class="course-list" style="margin:16px 0 18px">
                            ${course.feats[state.lang].map((feat) => `<div class="course-item"><i class="fas fa-check-circle"></i><span>${feat}</span></div>`).join('')}
                        </div>
                        <div style="display:flex;align-items:center;justify-content:space-between;gap:16px">
                            <strong style="font-family:var(--font-display);font-size:2rem;letter-spacing:1px">${course.price[state.lang === 'kg' ? 0 : state.lang === 'ru' ? 1 : 2]}</strong>
                            <button class="solid-btn" onclick="openCourseModal(${index})">${t('navCourses')}</button>
                        </div>
                    </div>
                </article>
            `).join('');
        }

        function renderFlashcard() {
            const current = flashcards[state.flashIndex];
            document.getElementById('flash-word').textContent = current.de;
            document.getElementById('flash-example').textContent = current.example[state.lang];
            document.getElementById('flash-translation').textContent = `${current.kg} / ${current.ru}`;
            document.getElementById('flash-translation-note').textContent = t('flashTranslationNote');
            document.getElementById('flash-progress-fill').style.width = `${((state.flashIndex + 1) / flashcards.length) * 100}%`;
            document.getElementById('flash-progress-text').textContent = `${state.flashIndex + 1} / ${flashcards.length}`;
            document.getElementById('speech-status').textContent = t('speechReady');
            flashFlipped = false;
            document.getElementById('flashcard').classList.remove('flipped');
        }

        function flipFlashcard() {
            flashFlipped = !flashFlipped;
            document.getElementById('flashcard').classList.toggle('flipped', flashFlipped);
        }

        function nextFlashcard() {
            markStudyDay();
            state.flashIndex = (state.flashIndex + 1) % flashcards.length;
            state.flashcardsReviewed = Math.max(state.flashcardsReviewed, state.flashIndex + 1);
            saveState();
            renderFlashcard();
            updateDashboard();
        }

        function saveCurrentWord() {
            markStudyDay();
            const word = flashcards[state.flashIndex];
            if (state.savedWords.some((item) => item.de === word.de)) {
                showLocalizedAlert('saveExists');
                return;
            }
            state.savedWords.unshift(word);
            saveState();
            renderVocabulary();
            updateDashboard();
            updateBadges();
            showLocalizedAlert('saveAdded');
        }

        function removeSavedWord(word) {
            state.savedWords = state.savedWords.filter((item) => item.de !== word);
            saveState();
            renderVocabulary();
            updateDashboard();
            showLocalizedAlert('saveRemoved');
        }

        function reviewSavedWord(word) {
            const idx = flashcards.findIndex((item) => item.de === word);
            if (idx >= 0) {
                state.flashIndex = idx;
                saveState();
                renderFlashcard();
                document.getElementById('practice').scrollIntoView({ behavior: 'smooth' });
            }
        }

        function renderVocabulary() {
            const list = document.getElementById('vocab-list');
            if (!state.savedWords.length) {
                list.innerHTML = `<div class="vocab-item"><div>${t('vocabEmpty')}</div></div>`;
                return;
            }
            list.innerHTML = state.savedWords.map((item) => `
                <div class="vocab-item">
                    <div>
                        <div class="vocab-word">${item.de}</div>
                        <div style="color:var(--muted);margin-top:4px">${item.kg} / ${item.ru}</div>
                    </div>
                    <div class="small-actions">
                        <button class="small-btn" onclick="reviewSavedWord('${item.de.replace(/'/g, "\\'")}')">${t('vocabReview')}</button>
                        <button class="small-btn" onclick="removeSavedWord('${item.de.replace(/'/g, "\\'")}')">${t('vocabDelete')}</button>
                    </div>
                </div>
            `).join('');
        }

        function speakCurrentWord(withRecognition = false) {
            const current = flashcards[state.flashIndex];
            document.getElementById('speech-status').textContent = t('speechPlaying');
            if (window.speechSynthesis) {
                window.speechSynthesis.cancel();
                currentUtterance = new SpeechSynthesisUtterance(current.de);
                currentUtterance.lang = 'de-DE';
                currentUtterance.rate = 0.9;
                const voices = speechSynthesis.getVoices();
                const germanVoice = voices.find((voice) => voice.lang && voice.lang.toLowerCase().startsWith('de'));
                if (germanVoice) currentUtterance.voice = germanVoice;
                speechSynthesis.speak(currentUtterance);
            }
            if (!withRecognition) return;

            markStudyDay();
            if (!SpeechRecognition) {
                document.getElementById('speech-status').textContent = t('speechUnsupported');
                return;
            }
            if (!recognition) {
                recognition = new SpeechRecognition();
                recognition.lang = 'de-DE';
                recognition.interimResults = false;
                recognition.maxAlternatives = 1;
            }
            document.getElementById('speech-status').textContent = `${t('speechListening')} ${current.de}`;
            recognition.onresult = (event) => {
                const heard = event.results[0][0].transcript.toLowerCase().trim();
                const expected = current.de.toLowerCase().replace(/^(der|die|das)\s+/, '');
                const success = heard.includes(expected) || expected.includes(heard);
                document.getElementById('speech-status').textContent = `${success ? t('speechGood') : t('speechTryAgain')} ${heard}`;
            };
            recognition.onerror = () => {
                document.getElementById('speech-status').textContent = t('speechError');
            };
            recognition.start();
        }

        function renderQuiz() {
            const q = quizData[state.quizIndex];
            document.getElementById('quiz-question-label').textContent = t('quizQuestion');
            document.getElementById('quiz-word').textContent = q.word;
            document.getElementById('quiz-score').textContent = `${state.quizScore} / ${state.quizAnswered}`;
            document.getElementById('quiz-feedback').textContent = '';
            document.getElementById('next-quiz-btn').classList.add('hidden');
            document.getElementById('share-quiz-btn').classList.add('hidden');
            quizLocked = false;

            const options = q.options[state.lang];
            const optionsEl = document.getElementById('quiz-options');
            optionsEl.innerHTML = options.map((option, index) => `
                <button class="quiz-option" data-option-index="${index}" type="button">${option}</button>
            `).join('');

            optionsEl.querySelectorAll('.quiz-option').forEach((button) => {
                button.addEventListener('click', () => answerQuiz(button.textContent, Number(button.dataset.optionIndex)));
            });
        }

        function answerQuiz(selectedText, selectedIndex) {
            if (quizLocked) return;
            quizLocked = true;
            markStudyDay();

            const current = quizData[state.quizIndex];
            const currentOptions = current.options[state.lang];
            const correctText = currentOptions[current.correctIndex];
            const isCorrect = selectedText === correctText && selectedIndex === current.correctIndex;

            state.quizAnswered += 1;
            if (isCorrect) {
                state.quizScore += 1;
                state.quizCorrect += 1;
            }

            document.querySelectorAll('.quiz-option').forEach((button, index) => {
                button.disabled = true;
                if (index === current.correctIndex) button.classList.add('correct');
                if (index === selectedIndex && index !== current.correctIndex) button.classList.add('wrong');
            });

            document.getElementById('quiz-feedback').textContent = isCorrect ? t('quizCorrect') : t('quizWrong');
            document.getElementById('quiz-score').textContent = `${state.quizScore} / ${state.quizAnswered}`;
            updateLeaderboard();
            updateDashboard();
            updateBadges();
            saveState();

            if (state.quizIndex === quizData.length - 1) {
                state.quizzesCompleted += 1;
                saveState();
                document.getElementById('quiz-feedback').textContent = `${document.getElementById('quiz-feedback').textContent} ${t('quizFinished')}`;
                document.getElementById('share-quiz-btn').classList.remove('hidden');
            } else {
                document.getElementById('next-quiz-btn').classList.remove('hidden');
            }
        }

        function nextQuizQuestion() {
            state.quizIndex = state.quizIndex >= quizData.length - 1 ? 0 : state.quizIndex + 1;
            if (state.quizIndex === 0) {
                state.quizScore = 0;
                state.quizAnswered = 0;
            }
            saveState();
            renderQuiz();
        }

        function shareQuizResult() {
            const scoreText = `${t('quizTitle')}: ${state.quizScore} / ${quizData.length}`;
            if (navigator.share) {
                navigator.share({ title: 'DeutschLernen', text: scoreText }).catch(() => {});
            } else if (navigator.clipboard) {
                navigator.clipboard.writeText(scoreText);
                showLocalizedAlert('copied');
            } else {
                alert(scoreText);
            }
        }

        function renderGrammar() {
            const activeButton = document.querySelector('.grammar-tab.active');
            const key = activeButton ? activeButton.dataset.grammar : 'articles';
            document.querySelector('[data-grammar="articles"]').textContent = t('grammarArticles');
            document.querySelector('[data-grammar="verbs"]').textContent = t('grammarVerbs');
            document.querySelector('[data-grammar="cases"]').textContent = t('grammarCases');

            const item = grammarContent[key];
            const headers = item.headers[state.lang];
            const rows = item.rows[state.lang];
            document.getElementById('grammar-panel').innerHTML = `
                <p class="feature-copy" style="margin-bottom:10px">${item.explain[state.lang]}</p>
                <table class="grammar-table">
                    <thead>
                        <tr>${headers.map((header) => `<th>${header}</th>`).join('')}</tr>
                    </thead>
                    <tbody>
                        ${rows.map((row) => `<tr>${row.map((cell) => `<td>${cell}</td>`).join('')}</tr>`).join('')}
                    </tbody>
                </table>
            `;
        }

        function renderPlacement() {
            if (state.placementFinished || state.placementIndex >= placementQuestions.length) {
                state.placementFinished = true;
                const score = state.placementScore;
                let levelKey = 'placementDoneA1';
                if (score >= 8) levelKey = 'placementDoneB1';
                else if (score >= 5) levelKey = 'placementDoneA2';
                document.getElementById('placement-question').textContent = `${t('placementTitle')} · ${score} / ${placementQuestions.length}`;
                document.getElementById('placement-options').innerHTML = '';
                document.getElementById('placement-status').textContent = t(levelKey);
                saveState();
                updateDashboard();
                updateBadges();
                return;
            }

            const q = placementQuestions[state.placementIndex];
            document.getElementById('placement-question').textContent = `${state.placementIndex + 1}. ${q.q[state.lang]}`;
            document.getElementById('placement-options').innerHTML = q.options[state.lang].map((option, index) => `
                <button type="button" class="placement-option" data-placement-index="${index}">${option}</button>
            `).join('');
            document.getElementById('placement-status').textContent = t('placementStart');

            document.querySelectorAll('.placement-option').forEach((button) => {
                button.addEventListener('click', () => answerPlacement(Number(button.dataset.placementIndex)));
            });
        }

        function answerPlacement(index) {
            const q = placementQuestions[state.placementIndex];
            document.querySelectorAll('.placement-option').forEach((button, i) => {
                button.disabled = true;
                if (i === q.correct) button.classList.add('correct');
                if (i === index && i !== q.correct) button.classList.add('wrong');
            });

            if (index === q.correct) state.placementScore += 1;
            state.placementIndex += 1;
            saveState();
            setTimeout(renderPlacement, 500);
        }

        function renderDialogues() {
            const grid = document.getElementById('dialogue-grid');
            grid.innerHTML = dialogues.map((dialogue, idx) => {
                const activeTab = transcriptTabs[idx] || 'kg';
                return `
                    <article class="dialogue-card" data-aos="fade-up" data-aos-delay="${idx * 80}">
                        <div class="dialogue-title">${dialogue.title[state.lang]}</div>
                        <div class="dialogue-copy">${dialogue.lines[activeTab].length} ${activeTab === 'de' ? 'Zeilen' : state.lang === 'kg' ? 'сап' : 'строки'}</div>
                        <div class="small-actions" style="margin-top:14px">
                            <button class="tool-btn primary" onclick="playDialogue(${idx})"><i class="fas fa-play"></i> Play</button>
                            <button class="tool-btn" onclick="stopDialogue()"><i class="fas fa-pause"></i> Pause</button>
                        </div>
                        <div class="transcript-tabs">
                            <button class="transcript-tab ${activeTab === 'kg' ? 'active' : ''}" onclick="setDialogueTab(${idx}, 'kg')">${t('transcriptKg')}</button>
                            <button class="transcript-tab ${activeTab === 'ru' ? 'active' : ''}" onclick="setDialogueTab(${idx}, 'ru')">${t('transcriptRu')}</button>
                            <button class="transcript-tab ${activeTab === 'de' ? 'active' : ''}" onclick="setDialogueTab(${idx}, 'de')">${t('transcriptDe')}</button>
                        </div>
                        <div class="dialogue-lines">
                            ${dialogue.lines[activeTab].map((line) => `<div class="dialogue-line"><span class="speaker">${line[0]}:</span> ${line[1]}</div>`).join('')}
                        </div>
                    </article>
                `;
            }).join('');
        }

        function playDialogue(index) {
            const dialogue = dialogues[index];
            const text = dialogue.lines.de.map((line) => `${line[0]}. ${line[1]}`).join(' ');
            if (window.speechSynthesis) {
                window.speechSynthesis.cancel();
                const utterance = new SpeechSynthesisUtterance(text);
                utterance.lang = 'de-DE';
                const voices = speechSynthesis.getVoices();
                const germanVoice = voices.find((voice) => voice.lang && voice.lang.toLowerCase().startsWith('de'));
                if (germanVoice) utterance.voice = germanVoice;
                currentUtterance = utterance;
                speechSynthesis.speak(utterance);
            }
        }

        function stopDialogue() {
            if (window.speechSynthesis) window.speechSynthesis.cancel();
        }

        function setDialogueTab(index, lang) {
            transcriptTabs[index] = lang;
            saveState();
            renderDialogues();
        }

        function renderTeachers() {
            document.getElementById('teacher-grid').innerHTML = teachers.map((teacher, idx) => `
                <article class="teacher-card" data-aos="fade-up" data-aos-delay="${idx * 70}">
                    <div class="avatar">${teacher.initials}</div>
                    <div class="teacher-name">${teacher.name[state.lang]}</div>
                    <div class="teacher-role">${teacher.role[state.lang]}</div>
                    <p class="teacher-bio">${teacher.bio[state.lang]}</p>
                    <div class="teacher-meta">
                        ${teacher.meta[state.lang].map((item) => `<div class="teacher-meta-row"><i class="fas fa-check-circle"></i><span>${item}</span></div>`).join('')}
                    </div>
                    <button class="small-btn" style="margin-top:16px" onclick="openTeacherModal(${idx})">${t('teachersTitle')}</button>
                </article>
            `).join('');
        }

        function renderTestimonials() {
            document.getElementById('testimonial-grid').innerHTML = testimonials.map((item, idx) => `
                <article class="testimonial-card" data-aos="fade-up" data-aos-delay="${idx * 70}">
                    <div class="avatar">${item.name[state.lang].slice(0, 1)}</div>
                    <div class="testimonial-name">${item.name[state.lang]}</div>
                    <div class="testimonial-city">${item.city[state.lang]}</div>
                    <p class="testimonial-text">${item.text[state.lang]}</p>
                    <div class="testimonial-stars">★★★★★</div>
                </article>
            `).join('');
        }

        function renderFaq() {
            document.getElementById('faq-list').innerHTML = faqItems.map((item, idx) => `
                <div class="faq-item ${idx === 0 ? 'open' : ''}">
                    <button type="button" class="faq-question" onclick="toggleFaq(${idx})">
                        <span>${item.q[state.lang]}</span>
                        <i class="fas fa-plus"></i>
                    </button>
                    <div class="faq-answer">${item.a[state.lang]}</div>
                </div>
            `).join('');
        }

        function toggleFaq(index) {
            document.querySelectorAll('#faq-list .faq-item').forEach((item, idx) => {
                item.classList.toggle('open', idx === index ? !item.classList.contains('open') : false);
            });
        }

        function updateLeaderboard() {
            state.userLeaderboardScore = computeUserScore();
            const langUserName = state.lang === 'kg' ? 'Сиз' : state.lang === 'ru' ? 'Вы' : 'Du';
            const rows = [...mockLeaderboard, { name: langUserName, score: state.userLeaderboardScore }]
                .sort((a, b) => b.score - a.score)
                .slice(0, 6);

            document.getElementById('leaderboard-list').innerHTML = rows.map((row, idx) => `
                <div class="leaderboard-item">
                    <div>
                        <div style="font-weight:800">${idx + 1}. ${row.name}</div>
                        <div style="color:var(--muted);margin-top:4px">${state.lang === 'kg' ? 'Жыйынтык упай' : state.lang === 'ru' ? 'Итоговый счёт' : 'Gesamtpunkte'}</div>
                    </div>
                    <div style="font-family:var(--font-display);font-size:2rem;letter-spacing:1px">${row.score}</div>
                </div>
            `).join('');
            saveState();
        }

        function updateBadges() {
            const unlocked = badgeDefinitions.filter((badge) => badge.check()).map((badge) => badge.id);
            state.badges = unlocked;
            document.getElementById('badge-list').innerHTML = badgeDefinitions.map((badge) => `
                <div class="badge-item">
                    <div style="display:flex;align-items:center;gap:14px">
                        <div class="mini-pill"><i class="fas ${badge.icons}"></i></div>
                        <div>
                            <div style="font-weight:800">${badge.title[state.lang]}</div>
                            <div style="color:var(--muted);margin-top:4px">${badge.note[state.lang]}</div>
                        </div>
                    </div>
                    <div style="font-weight:800;color:${state.badges.includes(badge.id) ? 'var(--kg-red)' : 'var(--muted)'}">${state.badges.includes(badge.id) ? t('badgeUnlocked') : t('badgeLocked')}</div>
                </div>
            `).join('');
            saveState();
        }

        function updateDashboard() {
            updateStreakViews();
            document.getElementById('stat-words').textContent = state.savedWords.length;
            const accuracy = state.quizAnswered ? Math.round((state.quizCorrect / state.quizAnswered) * 100) : 0;
            document.getElementById('stat-accuracy').textContent = `${accuracy}%`;
            const flashPct = Math.min(100, Math.round((state.flashcardsReviewed / flashcards.length) * 100));
            const vocabPct = Math.min(100, Math.round((state.savedWords.length / 20) * 100));
            const placementPct = Math.min(100, Math.round((state.placementIndex / placementQuestions.length) * 100));
            document.getElementById('dash-flash').style.width = `${flashPct}%`;
            document.getElementById('dash-vocab').style.width = `${vocabPct}%`;
            document.getElementById('dash-placement').style.width = `${placementPct}%`;
            document.getElementById('dash-flash-label').textContent = `${flashPct}%`;
            document.getElementById('dash-vocab-label').textContent = `${vocabPct}%`;
            document.getElementById('dash-placement-label').textContent = `${placementPct}%`;
            updateLeaderboard();
        }

        function exportVocabulary() {
            if (!state.savedWords.length) {
                showLocalizedAlert('vocabEmpty');
                return;
            }
            const lines = state.savedWords.map((item) => `${item.de} - ${item.kg} / ${item.ru}`);
            if (navigator.clipboard) {
                navigator.clipboard.writeText(lines.join('\n'));
                showLocalizedAlert('exportDone');
            } else {
                alert(lines.join('\n'));
            }
        }

        function resetProgress() {
            localStorage.removeItem(STORAGE_KEY);
            Object.assign(state, JSON.parse(JSON.stringify(defaultState)));
            transcriptTabs = { ...defaultState.dialoguesTab };
            state.lang = document.querySelector('.lang-pill.active')?.dataset.lang || 'kg';
            applyTheme();
            renderAll();
            showLocalizedAlert('resetDone');
        }

        function handleNewsletter() {
            const value = document.getElementById('newsletter-email').value.trim();
            if (!value || !/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value)) {
                showLocalizedAlert('newsletterInvalid');
                return;
            }
            document.getElementById('newsletter-email').value = '';
            showLocalizedAlert('newsletterSuccess');
        }

        function openModal(id) {
            document.getElementById(id).classList.add('open');
            document.body.style.overflow = 'hidden';
        }
        function closeModal(id) {
            document.getElementById(id).classList.remove('open');
            document.body.style.overflow = '';
        }
        document.addEventListener('click', function(e) {
            if (e.target.classList.contains('modal-overlay')) {
                e.target.classList.remove('open');
                document.body.style.overflow = '';
            }
        });

        let authMode = 'login';
        function toggleAuthMode() {
            authMode = authMode === 'login' ? 'register' : 'login';
            updateAuthModal();
        }
        function updateAuthModal() {
            const isLogin = authMode === 'login';
            const titles = { kg: isLogin ? 'КИРҮҮ' : 'КАТТАЛУУ', ru: isLogin ? 'ВХОД' : 'РЕГИСТРАЦИЯ', de: isLogin ? 'ANMELDEN' : 'REGISTRIEREN' };
            const subs = {
                kg: isLogin ? 'Каттоодон өтүп, прогрессиңизди сактаңыз.' : 'Жаңы аккаунт түзүңүз.',
                ru: isLogin ? 'Войдите, чтобы сохранить прогресс.' : 'Создайте новый аккаунт.',
                de: isLogin ? 'Anmelden und Fortschritt speichern.' : 'Neues Konto erstellen.'
            };
            const btns = { kg: isLogin ? 'Кирүү' : 'Катталуу', ru: isLogin ? 'Войти' : 'Зарегистрироваться', de: isLogin ? 'Anmelden' : 'Registrieren' };
            const switches = {
                kg: isLogin ? 'Каттоодон өткөн эмессизби?' : 'Аккаунт барбы?',
                ru: isLogin ? 'Нет аккаунта?' : 'Уже есть аккаунт?',
                de: isLogin ? 'Noch kein Konto?' : 'Bereits registriert?'
            };
            const switchBtns = { kg: isLogin ? 'Катталуу' : 'Кирүү', ru: isLogin ? 'Регистрация' : 'Войти', de: isLogin ? 'Registrieren' : 'Anmelden' };
            document.getElementById('auth-modal-title').textContent = titles[state.lang] || titles.kg;
            document.getElementById('auth-modal-sub').textContent = subs[state.lang] || subs.kg;
            document.getElementById('auth-submit-btn').textContent = btns[state.lang] || btns.kg;
            document.getElementById('auth-name-field').style.display = isLogin ? 'none' : 'block';
            const sw = document.getElementById('auth-switch');
            sw.innerHTML = (switches[state.lang]||switches.kg) + ' <button onclick="toggleAuthMode()">' + (switchBtns[state.lang]||switchBtns.kg) + '</button>';
        }
        // ── AUTH USER STATE ──────────────────────────────────────────────
        let currentUser = null;

        function submitAuth() {
            const email = document.getElementById('auth-email').value.trim();
            const pass  = document.getElementById('auth-password').value.trim();
            const name  = document.getElementById('auth-name').value.trim();
            if (!email || !/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
                showToast(t('newsletterInvalid'), 'error'); return;
            }
            if (pass.length < 6) {
                const msgs = {kg:'Сырсөз кем дегенде 6 символ болушу керек.',ru:'Пароль должен содержать минимум 6 символов.',de:'Das Passwort muss mindestens 6 Zeichen lang sein.'};
                showToast(msgs[state.lang]||msgs.kg, 'error'); return;
            }
            const displayName = (authMode === 'register' && name) ? name : email.split('@')[0];
            currentUser = { email, name: displayName };
            localStorage.setItem('dl_user', JSON.stringify(currentUser));
            const msgs = {kg: authMode==='login'?'Кош келиңиз, '+displayName+'!':'Ийгиликтүү катталдыңыз!', ru: authMode==='login'?'Добро пожаловать, '+displayName+'!':'Вы успешно зарегистрированы!', de: authMode==='login'?'Willkommen, '+displayName+'!':'Erfolgreich registriert!'};
            showToast(msgs[state.lang]||msgs.kg, 'success');
            closeModal('auth-modal');
            showDashboard();
        }

        function logoutUser() {
            currentUser = null;
            localStorage.removeItem('dl_user');
            hideDashboard();
            const msgs = {kg:'Чыктыңыз. Кайра кирүүгө болот.',ru:'Вы вышли из аккаунта.',de:'Sie haben sich abgemeldet.'};
            showToast(msgs[state.lang]||msgs.kg, 'info');
        }

        function showDashboard() {
            document.getElementById('student-dashboard').classList.add('active');
            document.querySelector('.main-site').classList.add('hidden-site');
            updateNavForLoggedIn();
            renderDashboard();
            window.scrollTo({top:0, behavior:'smooth'});
        }

        function hideDashboard() {
            document.getElementById('student-dashboard').classList.remove('active');
            document.querySelector('.main-site').classList.remove('hidden-site');
            updateNavForLoggedOut();
        }

        function updateNavForLoggedIn() {
            const nav = document.querySelector('.nav-actions');
            const u = currentUser;
            nav.innerHTML = `
                <button class="ghost-btn" onclick="showDashboard()" style="display:flex;align-items:center;gap:8px">
                    <span style="width:28px;height:28px;border-radius:50%;background:linear-gradient(135deg,var(--kg-red),var(--ru-blue));display:inline-flex;align-items:center;justify-content:center;color:white;font-weight:800;font-size:0.85rem">${u.name.charAt(0).toUpperCase()}</span>
                    ${u.name}
                </button>
                <button class="solid-btn" onclick="logoutUser()"><i class="fas fa-sign-out-alt"></i> <span id="nav-logout-lbl">Чыгуу</span></button>
            `;
        }

        function updateNavForLoggedOut() {
            const nav = document.querySelector('.nav-actions');
            nav.innerHTML = `
                <button class="ghost-btn" id="login-btn" onclick="authMode='login';updateAuthModal();openModal('auth-modal')" data-i18n="login">Кирүү</button>
                <button class="solid-btn" id="register-btn" onclick="authMode='register';updateAuthModal();openModal('auth-modal')" data-i18n="register">Катталуу</button>
            `;
        }

        // ── DASHBOARD DATA & RENDER ───────────────────────────────────────
        const dbLessons = [
            { kg:'Алфавит жана айтылыш', ru:'Алфавит и произношение', de:'Alphabet und Aussprache', icon:'fa-font', status:'done', dur:{kg:'15 мин',ru:'15 мин',de:'15 Min'} },
            { kg:'Саламдашуу жана таанышуу', ru:'Приветствия и знакомство', de:'Begrüßung und Vorstellung', icon:'fa-handshake', status:'done', dur:{kg:'20 мин',ru:'20 мин',de:'20 Min'} },
            { kg:'Сандар 1–100', ru:'Числа 1–100', de:'Zahlen 1–100', icon:'fa-hashtag', status:'active', dur:{kg:'25 мин',ru:'25 мин',de:'25 Min'} },
            { kg:'Рен жана өлчөм', ru:'Цвета и размеры', de:'Farben und Größen', icon:'fa-palette', status:'locked', dur:{kg:'20 мин',ru:'20 мин',de:'20 Min'} },
            { kg:'Үй-бүлө мүчөлөрү', ru:'Члены семьи', de:'Familienmitglieder', icon:'fa-users', status:'locked', dur:{kg:'30 мин',ru:'30 мин',de:'30 Min'} },
        ];

        const dbBadgeData = [
            { icon:'fa-star',         cls:'gold',   kg:'Биринчи кадам',    ru:'Первый шаг',      de:'Erster Schritt',  note:{kg:'Кирдиңиз',ru:'Вошли',de:'Eingeloggt'},         get unlocked(){ return true; } },
            { icon:'fa-fire',         cls:'orange', kg:'Серия башталды',   ru:'Серия начата',    de:'Serie begonnen',  note:{kg:'3 күн',ru:'3 дня',de:'3 Tage'},                get unlocked(){ return state.streak >= 3; } },
            { icon:'fa-bolt',         cls:'gold',   kg:'Тез үйрөнүүчү',   ru:'Быстрый ученик',  de:'Schnell-Lerner',  note:{kg:'5 тест',ru:'5 тестов',de:'5 Quiz'},            get unlocked(){ return state.quizzesCompleted >= 5; } },
            { icon:'fa-bookmark',     cls:'blue',   kg:'Сөз жыйноочу',    ru:'Собиратель слов', de:'Wortsammler',     note:{kg:'10 сөз',ru:'10 слов',de:'10 Wörter'},          get unlocked(){ return state.savedWords.length >= 10; } },
            { icon:'fa-graduation-cap', cls:'red',  kg:'Деңгээл аныкталды', ru:'Уровень найден', de:'Niveau bestimmt', note:{kg:'Тест өттү',ru:'Тест пройден',de:'Test gemacht'}, get unlocked(){ return state.placementFinished; } },
            { icon:'fa-trophy',       cls:'gold',   kg:'Мыкты окуучу',    ru:'Отличник',        de:'Musterschüler',   note:{kg:'20 сөз',ru:'20 слов',de:'20 Wörter'},          get unlocked(){ return state.savedWords.length >= 20; } },
        ];

        const dbChatInit = [
            { from:'teacher', kg:'Салам! Окуугуңуз кандай? Суроолоруңуз болсо, жазыңыз.', ru:'Привет! Как учёба? Если есть вопросы, пишите.', de:'Hallo! Wie läuft das Lernen? Schreiben Sie bei Fragen.', time:'09:00' },
            { from:'teacher', kg:'Бүгүн «Сандар» темасын баштаганыңызды сунуштайм — A1 үчүн маанилүү.', ru:'Советую сегодня начать тему «Числа» — важно для A1.', de:'Ich empfehle heute das Thema „Zahlen" — wichtig für A1.', time:'09:01' },
        ];
        let chatMessages = [...dbChatInit];

        const dbI18n = {
            kg:{ continue:'Окууну улантуу', logout:'Чыгуу', streakLbl:'Катар күн', xpLbl:'Упай (XP)', lessonsLbl:'Бүткөн сабак', accLbl:'Тактык', progressTitle:'Курс прогресси', progressSub:'Немис тили A1–B1 боюнча жалпы илгерилөө', lessonsTitle:'Акыркы сабактар', lessonsSub:'Уланта же кайрадан карагыла', badgesTitle:'Жетишкендиктер', badgesSub:'Топтолгон медалдар жана сыйлыктар', vocabTitle:'Менин сөздүгүм', vocabSub:'Флэш-картадан сакталган сөздөр', exportBtn:'Экспорт', calTitle:'Окуу графиги', calSub:'Бул айдагы машыккан күндөр', calDays:['Дш','Шш','Шр','Бш','Жм','Шб','Жк'], lbTitle:'Рейтинг', lbSub:'Башка студенттер арасында орнуңуз', youLabel:'Сиз', certTitle:'СЕРТИФИКАТ', certSub:'A1 курсун 100% бүткөндө сертификат жүктөп алса болот.', certBtn:'Жүктөп алуу', chatTitle:'Мугалим менен байланыш', chatSub:'Айсулуу мугалим онлайн', chatPlaceholder:'Суроо жазыңыз…', lessonDone:'Кайталоо', lessonGo:'Улантуу', lessonLock:'Жабык', levelA1:'A1 — Башталгыч', vocabEmpty:'Сакталган сөз жок.', vocabLbl:'Сөздүк', navLogout:'Чыгуу' },
            ru:{ continue:'Продолжить обучение', logout:'Выйти', streakLbl:'Дней подряд', xpLbl:'Очки (XP)', lessonsLbl:'Пройдено уроков', accLbl:'Точность', progressTitle:'Прогресс курса', progressSub:'Общий прогресс немецкого A1–B1', lessonsTitle:'Последние уроки', lessonsSub:'Продолжите или повторите', badgesTitle:'Достижения', badgesSub:'Полученные медали и значки', vocabTitle:'Мой словарь', vocabSub:'Сохранённые слова с карточек', exportBtn:'Экспорт', calTitle:'График обучения', calSub:'Дни занятий в этом месяце', calDays:['Пн','Вт','Ср','Чт','Пт','Сб','Вс'], lbTitle:'Рейтинг', lbSub:'Ваше место среди студентов', youLabel:'Вы', certTitle:'СЕРТИФИКАТ', certSub:'После 100% прохождения A1 можно скачать сертификат.', certBtn:'Скачать', chatTitle:'Связь с преподавателем', chatSub:'Преподаватель Айсулуу онлайн', chatPlaceholder:'Напишите вопрос…', lessonDone:'Повторить', lessonGo:'Продолжить', lessonLock:'Закрыто', levelA1:'A1 — Начальный', vocabEmpty:'Нет сохранённых слов.', vocabLbl:'Словарь', navLogout:'Выйти' },
            de:{ continue:'Weiterlernen', logout:'Abmelden', streakLbl:'Tage in Folge', xpLbl:'Punkte (XP)', lessonsLbl:'Abgeschlossene Lektionen', accLbl:'Genauigkeit', progressTitle:'Kursfortschritt', progressSub:'Gesamtfortschritt Deutsch A1–B1', lessonsTitle:'Letzte Lektionen', lessonsSub:'Weitermachen oder wiederholen', badgesTitle:'Erfolge', badgesSub:'Erhaltene Medaillen und Abzeichen', vocabTitle:'Mein Vokabelbuch', vocabSub:'Gespeicherte Wörter aus Karteikarten', exportBtn:'Export', calTitle:'Lernkalender', calSub:'Lerntage in diesem Monat', calDays:['Mo','Di','Mi','Do','Fr','Sa','So'], lbTitle:'Rangliste', lbSub:'Ihr Platz unter den Studenten', youLabel:'Sie', certTitle:'ZERTIFIKAT', certSub:'Nach 100% Abschluss des A1-Kurses herunterzuladen.', certBtn:'Herunterladen', chatTitle:'Kontakt zum Lehrer', chatSub:'Lehrerin Aisuluu ist online', chatPlaceholder:'Frage schreiben…', lessonDone:'Wiederholen', lessonGo:'Fortfahren', lessonLock:'Gesperrt', levelA1:'A1 — Anfänger', vocabEmpty:'Keine gespeicherten Wörter.', vocabLbl:'Vokabular', navLogout:'Abmelden' },
        };
        function dl(key){ return (dbI18n[state.lang]||dbI18n.kg)[key]||key; }

        function renderDashboard() {
            if (!currentUser) return;
            document.getElementById('db-avatar-letter').textContent = currentUser.name.charAt(0).toUpperCase();
            document.getElementById('db-user-name').textContent = currentUser.name;
            document.getElementById('db-user-email').textContent = currentUser.email;
            const score = computeUserScore();
            const lvlText = score < 200 ? dl('levelA1') : score < 600 ? 'A2 — '+(state.lang==='kg'?'Орто башталгыч':state.lang==='ru'?'Ниже среднего':'Grundstufe') : 'B1 — '+(state.lang==='kg'?'Орто':state.lang==='ru'?'Средний':'Mittel');
            document.getElementById('db-level-text').textContent = lvlText;
            const xpNext = Math.ceil((score+1)/500)*500;
            const xpPct = Math.min(100, Math.round((score%500)/500*100));
            document.getElementById('db-xp-fill').style.width = xpPct+'%';
            document.getElementById('db-xp-label').textContent = score+' / '+xpNext+' XP';
            const acc = state.quizAnswered ? Math.round(state.quizCorrect/state.quizAnswered*100) : 0;
            const lessonsCount = Math.min(dbLessons.length, state.flashcardsReviewed + state.quizzesCompleted);
            document.getElementById('db-stat-streak').textContent = state.streak;
            document.getElementById('db-stat-xp').textContent = score;
            document.getElementById('db-stat-lessons').textContent = lessonsCount;
            document.getElementById('db-stat-acc').textContent = acc+'%';
            ['streak','xp','lessons','acc'].forEach(k => document.getElementById('db-lbl-'+k).textContent = dl(k+'Lbl'));
            document.getElementById('db-btn-continue').textContent = dl('continue');
            document.getElementById('db-btn-logout').textContent = dl('logout');
            document.getElementById('db-btn-export').textContent = dl('exportBtn');
            // Progress
            const flashPct = Math.min(100, Math.round(state.flashcardsReviewed/flashcards.length*100));
            const vocabPct = Math.min(100, Math.round(state.savedWords.length/20*100));
            const placePct = Math.min(100, Math.round(state.placementIndex/placementQuestions.length*100));
            const a1Pct = Math.min(100, Math.round((flashPct + (state.quizzesCompleted>=2?50:0))/2));
            const a2Pct = Math.min(100, Math.round(placePct*0.6));
            const b1Pct = Math.min(100, Math.round(placePct*0.2));
            [['dp-a1',a1Pct,'dp-a1-pct','var(--kg-red)'],['dp-a2',a2Pct,'dp-a2-pct','var(--de-gold)'],['dp-b1',b1Pct,'dp-b1-pct','var(--ru-blue)'],['dp-vocab',vocabPct,'dp-vocab-pct','#21c49c']].forEach(([id,pct,pid])=>{
                document.getElementById(id).style.width=pct+'%';
                document.getElementById(pid).textContent=pct+'%';
            });
            document.getElementById('db-title-progress').textContent=dl('progressTitle');
            document.getElementById('db-sub-progress').textContent=dl('progressSub');
            document.getElementById('dp-vocab-lbl').textContent=dl('vocabLbl');
            // Lessons
            document.getElementById('db-title-lessons').textContent=dl('lessonsTitle');
            document.getElementById('db-sub-lessons').textContent=dl('lessonsSub');
            document.getElementById('db-lessons-list').innerHTML = dbLessons.map(lesson=>{
                const isDone=lesson.status==='done', isActive=lesson.status==='active', isLocked=lesson.status==='locked';
                const iconCls=isDone?'done':isActive?'active':'locked';
                const btnCls=isDone?'review':isActive?'go':'lock';
                const btnLbl=isDone?dl('lessonDone'):isActive?dl('lessonGo'):dl('lessonLock');
                const onclick = isLocked ? '' : "document.getElementById('practice').scrollIntoView({behavior:'smooth'});hideDashboard()";
                return `<div class="db-lesson-item">
                    <div class="db-lesson-icon ${iconCls}"><i class="fas ${lesson.icon}"></i></div>
                    <div class="db-lesson-info">
                        <div class="db-lesson-name">${lesson[state.lang]||lesson.kg}</div>
                        <div class="db-lesson-meta">${lesson.dur[state.lang]||lesson.dur.kg}</div>
                    </div>
                    <button class="db-lesson-btn ${btnCls}" ${isLocked?'disabled':''} onclick="${onclick}">${btnLbl}</button>
                </div>`;
            }).join('');
            // Badges
            document.getElementById('db-title-badges').textContent=dl('badgesTitle');
            document.getElementById('db-sub-badges').textContent=dl('badgesSub');
            document.getElementById('db-badges-grid').innerHTML = dbBadgeData.map(b=>{
                const unlocked=b.unlocked;
                return `<div class="db-badge-item ${unlocked?'':'locked'}">
                    <div class="db-badge-icon ${b.cls}"><i class="fas ${b.icon}"></i></div>
                    <div class="db-badge-name">${b[state.lang]||b.kg}</div>
                    <div class="db-badge-note">${b.note[state.lang]||b.note.kg}</div>
                </div>`;
            }).join('');
            // Vocab
            document.getElementById('db-title-vocab').textContent=dl('vocabTitle');
            document.getElementById('db-sub-vocab').textContent=dl('vocabSub');
            const vocabEl=document.getElementById('db-vocab-list');
            vocabEl.innerHTML = !state.savedWords.length
                ? `<div style="color:var(--muted);padding:16px 0;font-weight:600">${dl('vocabEmpty')}</div>`
                : state.savedWords.slice(0,8).map(w=>`<div class="db-vocab-item"><div><div class="db-vocab-de">${w.de}</div><div class="db-vocab-tr">${w.kg} / ${w.ru}</div></div><span class="db-vocab-tag">A1</span></div>`).join('');
            // Calendar
            document.getElementById('db-title-calendar').textContent=dl('calTitle');
            document.getElementById('db-sub-calendar').textContent=dl('calSub');
            const calDays=dl('calDays');
            document.getElementById('db-cal-headers').innerHTML=calDays.map(d=>`<div class="db-cal-hdr">${d}</div>`).join('');
            const now=new Date(), year=now.getFullYear(), month=now.getMonth(), today=now.getDate();
            const firstDay=new Date(year,month,1).getDay(), offset=(firstDay===0?6:firstDay-1);
            const daysInMonth=new Date(year,month+1,0).getDate();
            let calHTML='';
            for(let i=0;i<offset;i++) calHTML+='<div class="db-cal-day future"></div>';
            for(let d=1;d<=daysInMonth;d++){
                const dateStr=year+'-'+String(month+1).padStart(2,'0')+'-'+String(d).padStart(2,'0');
                const isToday=d===today;
                const wasStudied=(state.lastStudyDate===dateStr)||(d<today&&(d%3!==0));
                const cls=isToday?'today':(d>today?'future':wasStudied?'studied':'');
                calHTML+=`<div class="db-cal-day ${cls}">${d}</div>`;
            }
            document.getElementById('db-calendar').innerHTML=calHTML;
            // Leaderboard
            document.getElementById('db-title-lb').textContent=dl('lbTitle');
            document.getElementById('db-sub-lb').textContent=dl('lbSub');
            const youLabel=dl('youLabel');
            const lbRows=[...mockLeaderboard,{name:currentUser.name,score,isYou:true}].sort((a,b)=>b.score-a.score).slice(0,6);
            document.getElementById('db-leaderboard').innerHTML=lbRows.map((row,i)=>{
                const rankDisp=i===0?'🥇':i===1?'🥈':i===2?'🥉':(i+1)+'';
                const rankCls=i===0?'top1':i===1?'top2':i===2?'top3':'';
                return `<div class="db-lb-item"><div class="db-lb-rank ${rankCls}">${rankDisp}</div><div class="db-lb-name">${row.name}${row.isYou?`<span class="db-lb-you">${youLabel}</span>`:''}</div><div class="db-lb-score">${row.score}</div></div>`;
            }).join('');
            // Cert
            document.getElementById('db-cert-title').textContent=dl('certTitle');
            document.getElementById('db-cert-sub').textContent=dl('certSub');
            document.getElementById('db-cert-btn-lbl').textContent=dl('certBtn');
            document.getElementById('db-cert-btn').disabled=(a1Pct<100);
            // Chat
            document.getElementById('db-title-chat').textContent=dl('chatTitle');
            document.getElementById('db-sub-chat').textContent=dl('chatSub');
            document.getElementById('db-chat-input').placeholder=dl('chatPlaceholder');
            renderChat();
            const nl=document.getElementById('nav-logout-lbl');
            if(nl) nl.textContent=dl('navLogout');
        }

        function renderChat() {
            const el=document.getElementById('db-chat-messages');
            if(!el) return;
            el.innerHTML=chatMessages.map(msg=>{
                const isMine=msg.from==='me';
                const text=msg[state.lang]||msg.text||'';
                return `<div class="db-chat-msg ${isMine?'mine':''}">
                    ${!isMine?'<div class="db-chat-mini-avatar">А</div>':''}
                    <div><div class="db-chat-bubble ${isMine?'mine-b':'theirs'}">${text}</div><div class="db-chat-time">${msg.time||''}</div></div>
                </div>`;
            }).join('');
            el.scrollTop=el.scrollHeight;
        }

        function sendChatMsg() {
            const inp=document.getElementById('db-chat-input');
            const text=inp.value.trim(); if(!text) return;
            const time=new Date().getHours()+':'+String(new Date().getMinutes()).padStart(2,'0');
            chatMessages.push({from:'me',text,kg:text,ru:text,de:text,time});
            inp.value=''; renderChat();
            setTimeout(()=>{
                const r=(dbI18n[state.lang]||dbI18n.kg);
                const reps=[r.chatSub.replace('онлайн','').replace('online','').trim()+': '+dl('calSub'),'Флэш-карталарды колдонуп көрүңүз!','Тесттен өтүп, прогрессиңизди текшериңиз.'];
                const replies={kg:['Жакшы суроо! Практика улантыңыз.','Флэш-карталарды колдонуп көрүңүз!','Тесттен өтүп, прогрессиңизди текшериңиз.'],ru:['Хороший вопрос! Продолжайте.','Попробуйте карточки!','Пройдите тест и проверьте прогресс.'],de:['Gute Frage! Weiter üben.','Probieren Sie die Karteikarten!','Machen Sie den Test.']};
                const arr=replies[state.lang]||replies.kg;
                chatMessages.push({from:'teacher',kg:arr[0],ru:replies.ru[Math.floor(Math.random()*3)],de:replies.de[Math.floor(Math.random()*3)],time:new Date().getHours()+':'+String(new Date().getMinutes()).padStart(2,'0')});
                renderChat();
            },1200);
        }

        function downloadCert() {
            const msgs={kg:'Сертификат жүктөлүп жатат…',ru:'Сертификат скачивается…',de:'Zertifikat wird heruntergeladen…'};
            showToast(msgs[state.lang]||msgs.kg,'success');
        }


        let currentTeacher = null;
        function openTeacherModal(idx) {
            currentTeacher = idx;
            const teacher = teachers[idx];
            document.getElementById('tm-avatar').textContent = teacher.initials;
            document.getElementById('tm-name').textContent = teacher.name[state.lang];
            document.getElementById('tm-role').textContent = teacher.role[state.lang];
            document.getElementById('tm-bio').textContent = teacher.bio[state.lang];
            document.getElementById('tm-meta').innerHTML = teacher.meta[state.lang].map(m =>
                '<div class="course-feat-item"><i class="fas fa-check-circle"></i>' + m + '</div>'
            ).join('');
            const bookLabels = {kg:'Сабакка жазылуу',ru:'Записаться на урок',de:'Stunde buchen'};
            const closeLabels = {kg:'Жабуу',ru:'Закрыть',de:'Schließen'};
            document.getElementById('btn-book').textContent = bookLabels[state.lang]||bookLabels.kg;
            document.getElementById('btn-close-teacher').textContent = closeLabels[state.lang]||closeLabels.kg;
            openModal('teacher-modal');
        }
        function bookTeacher() {
            const msgs = {kg:'Сабакка жазылуу өтүнүчүңүз кабыл алынды! Жакында байланышабыз.',ru:'Заявка на урок принята! Мы свяжемся с вами скоро.',de:'Ihre Anfrage wurde entgegengenommen! Wir melden uns bald.'};
            showToast(msgs[state.lang]||msgs.kg, 'success');
            closeModal('teacher-modal');
        }

        let currentCourse = null;
        function openCourseModal(idx) {
            currentCourse = idx;
            const c = courses[idx];
            const lang = state.lang;
            const header = document.getElementById('cm-header');
            header.className = 'course-modal-header ' + c.tone;
            document.getElementById('cm-level').textContent = c.level;
            document.getElementById('cm-title').textContent = c.title[lang];
            document.getElementById('cm-desc').textContent = c.desc[lang];
            document.getElementById('cm-price').textContent = c.price[lang==='kg'?0:lang==='ru'?1:2];
            const durations = {kg:'Курс узактыгы: 3 ай',ru:'Длительность: 3 месяца',de:'Dauer: 3 Monate'};
            document.getElementById('cm-duration').textContent = durations[lang]||durations.kg;
            document.getElementById('cm-feats').innerHTML = c.feats[lang].map(f =>
                '<div class="course-feat-item"><i class="fas fa-check-circle"></i>' + f + '</div>'
            ).join('');
            const enrollLabels = {kg:'Курска жазылуу',ru:'Записаться на курс',de:'Zum Kurs anmelden'};
            const closeLabels = {kg:'Жабуу',ru:'Закрыть',de:'Schließen'};
            document.getElementById('btn-enroll').textContent = enrollLabels[lang]||enrollLabels.kg;
            document.getElementById('btn-close-course').textContent = closeLabels[lang]||closeLabels.kg;
            openModal('course-modal');
        }
        function enrollCourse() {
            const msgs = {kg:'Курска жазылуу өтүнүчүңүз кабыл алынды!',ru:'Заявка на курс принята!',de:'Kursanmeldung erfolgreich!'};
            showToast(msgs[state.lang]||msgs.kg, 'success');
            closeModal('course-modal');
        }

        function handleAction(action) {
            if (action === 'login') { authMode = 'login'; updateAuthModal(); openModal('auth-modal'); return; }
            if (action === 'register') { authMode = 'register'; updateAuthModal(); openModal('auth-modal'); return; }
            if (action === 'start') { authMode = 'register'; updateAuthModal(); openModal('auth-modal'); return; }
            if (action === 'courseA1') { openCourseModal(0); return; }
            if (action === 'courseA2') { openCourseModal(1); return; }
            if (action === 'courseB1') { openCourseModal(2); return; }
            if (action === 'course') { openCourseModal(0); return; }
            if (action === 'teacher') { openTeacherModal(0); return; }
            const map = { social:'actionSocial', contactEmail:'actionContact', contactPhone:'actionContact', contactMap:'actionContact' };
            if (map[action]) showLocalizedAlert(map[action]);
        }

        function bindStaticEvents() {
            document.querySelectorAll('.lang-pill').forEach((button) => {
                button.addEventListener('click', () => {
                    state.lang = button.dataset.lang;
                    document.querySelectorAll('.lang-pill').forEach((item) => item.classList.toggle('active', item === button));
                    saveState();
                    renderAll();
                });
            });

            document.getElementById('theme-toggle').addEventListener('click', () => {
                state.theme = state.theme === 'dark' ? 'light' : 'dark';
                saveState();
                applyTheme();
            });

            document.getElementById('hamburger').addEventListener('click', () => {
                document.getElementById('mobile-nav').classList.toggle('open');
                document.body.style.overflow = document.getElementById('mobile-nav').classList.contains('open') ? 'hidden' : '';
            });

            document.querySelectorAll('.mobile-link').forEach((link) => {
                link.addEventListener('click', () => {
                    document.getElementById('mobile-nav').classList.remove('open');
                    document.body.style.overflow = '';
                });
            });

            document.querySelectorAll('[data-action]').forEach((button) => {
                button.addEventListener('click', () => handleAction(button.dataset.action));
            });

            document.getElementById('flip-card-btn').addEventListener('click', flipFlashcard);
            document.getElementById('flashcard').addEventListener('click', flipFlashcard);
            document.getElementById('next-card-btn').addEventListener('click', nextFlashcard);
            document.getElementById('save-card-btn').addEventListener('click', saveCurrentWord);
            document.getElementById('speak-card-btn').addEventListener('click', () => speakCurrentWord(true));
            document.getElementById('next-quiz-btn').addEventListener('click', nextQuizQuestion);
            document.getElementById('share-quiz-btn').addEventListener('click', shareQuizResult);
            document.getElementById('mark-study-btn').addEventListener('click', markStudyDay);
            document.getElementById('reset-progress-btn').addEventListener('click', resetProgress);
            document.getElementById('export-vocab-btn').addEventListener('click', exportVocabulary);
            document.getElementById('newsletter-btn').addEventListener('click', handleNewsletter);
            document.getElementById('back-to-top').addEventListener('click', () => window.scrollTo({ top: 0, behavior: 'smooth' }));
            document.addEventListener('keydown', (e) => {
                if (e.key === 'Enter' && document.activeElement && document.activeElement.id === 'db-chat-input') {
                    sendChatMsg();
                }
                if (e.key === 'Escape') {
                    document.querySelectorAll('.modal-overlay.open').forEach(m => { m.classList.remove('open'); document.body.style.overflow=''; });
                }
            });

            document.querySelectorAll('.grammar-tab').forEach((button) => {
                button.addEventListener('click', () => {
                    document.querySelectorAll('.grammar-tab').forEach((item) => item.classList.remove('active'));
                    button.classList.add('active');
                    renderGrammar();
                });
            });

            window.addEventListener('scroll', () => {
                const total = document.body.scrollHeight - window.innerHeight;
                const width = total > 0 ? (window.scrollY / total) * 100 : 0;
                document.getElementById('progress-bar').style.width = `${width}%`;
                document.getElementById('back-to-top').classList.toggle('visible', window.scrollY > 420);

                const sections = ['hero', 'courses', 'practice', 'hub', 'teachers', 'faq'];
                let activeSection = 'hero';
                sections.forEach((id) => {
                    const el = document.getElementById(id);
                    if (el && window.scrollY >= el.offsetTop - 120) activeSection = id;
                });
                document.querySelectorAll('.nav-link').forEach((link) => {
                    link.classList.toggle('active', link.getAttribute('href') === `#${activeSection}`);
                });
            });

            window.addEventListener('speechSynthesisvoiceschanged', () => {});
        }

        function renderAll() {
            updateDocumentLanguage();
            applyTheme();
            renderHero();
            renderCourses();
            renderFlashcard();
            renderQuiz();
            renderVocabulary();
            renderGrammar();
            renderPlacement();
            renderDialogues();
            renderTeachers();
            renderTestimonials();
            renderFaq();
            updateDashboard();
            updateBadges();
        }

        document.addEventListener('DOMContentLoaded', () => {
            // Restore logged-in session
            const savedUser = localStorage.getItem('dl_user');
            if (savedUser) { try { currentUser = JSON.parse(savedUser); updateNavForLoggedIn(); } catch(e){} }
            document.querySelectorAll('.lang-pill').forEach((item) => item.classList.toggle('active', item.dataset.lang === state.lang));
            applyTheme();
            bindStaticEvents();
            renderAll();
            if (window.AOS) AOS.init({ once: true, duration: 650, easing: 'ease-out-cubic' });
            setInterval(rotateHeroWord, 3000);
        });

        window.showDashboard = showDashboard;
        window.hideDashboard = hideDashboard;
        window.logoutUser = logoutUser;
        window.sendChatMsg = sendChatMsg;
        window.downloadCert = downloadCert;
        window.openTeacherModal = openTeacherModal;
        window.openCourseModal = openCourseModal;
        window.closeModal = closeModal;
        window.toggleAuthMode = toggleAuthMode;
        window.submitAuth = submitAuth;
        window.bookTeacher = bookTeacher;
        window.enrollCourse = enrollCourse;
        window.reviewSavedWord = reviewSavedWord;
        window.removeSavedWord = removeSavedWord;
        window.playDialogue = playDialogue;
        window.stopDialogue = stopDialogue;
        window.setDialogueTab = setDialogueTab;
        window.toggleFaq = toggleFaq;
        window.handleAction = handleAction;
    </script>
</body>
</html>
