<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SoloLaunch - iOS Apps Built by AI</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: #000;
            color: #fff;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(0, 0, 0, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            transition: all 0.3s ease;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            background: linear-gradient(45deg, #00f5ff, #0080ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            transition: all 0.3s ease;
            position: relative;
        }

        .nav-links a:hover {
            color: #00f5ff;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(45deg, #00f5ff, #0080ff);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            background: radial-gradient(ellipse at center, #001122 0%, #000 70%);
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grid" width="10" height="10" patternUnits="userSpaceOnUse"><path d="M 10 0 L 0 0 0 10" fill="none" stroke="%23ffffff" stroke-width="0.1" opacity="0.1"/></pattern></defs><rect width="100" height="100" fill="url(%23grid)"/></svg>');
            animation: float 20s ease-in-out infinite;
        }

        .floating-elements {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .floating-element {
            position: absolute;
            background: linear-gradient(45deg, #00f5ff, #0080ff);
            border-radius: 50%;
            opacity: 0.1;
            animation: floatUp 15s infinite linear;
        }

        .floating-element:nth-child(1) {
            left: 10%;
            width: 20px;
            height: 20px;
            animation-delay: -5s;
        }

        .floating-element:nth-child(2) {
            left: 20%;
            width: 30px;
            height: 30px;
            animation-delay: -2s;
        }

        .floating-element:nth-child(3) {
            left: 70%;
            width: 25px;
            height: 25px;
            animation-delay: -8s;
        }

        .floating-element:nth-child(4) {
            left: 80%;
            width: 15px;
            height: 15px;
            animation-delay: -3s;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.1;
            }
            90% {
                opacity: 0.1;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }

        .hero-content {
            max-width: 800px;
            z-index: 2;
            position: relative;
        }

        .hero h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, #00f5ff, #0080ff, #00ff80);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: fadeInUp 1s ease-out;
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            opacity: 0.9;
            animation: fadeInUp 1s ease-out 0.3s both;
        }

        .cta-button {
            display: inline-block;
            padding: 1rem 2rem;
            background: linear-gradient(45deg, #00f5ff, #0080ff);
            color: #000;
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: all 0.3s ease;
            animation: fadeInUp 1s ease-out 0.6s both;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(0, 245, 255, 0.3);
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Sections */
        section {
            padding: 5rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 2.5rem;
            margin-bottom: 3rem;
            text-align: center;
            background: linear-gradient(45deg, #00f5ff, #fff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        /* Architecture Diagram */
        .architecture-diagram {
            background: linear-gradient(135deg, #001122, #000);
            border-radius: 20px;
            padding: 4rem 2rem;
            margin: 3rem 0;
            border: 1px solid rgba(0, 245, 255, 0.3);
        }

        .architecture-flow {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 1rem;
            margin-top: 3rem;
            position: relative;
        }

        .arch-node {
            background: linear-gradient(135deg, rgba(0, 245, 255, 0.1), rgba(0, 128, 255, 0.1));
            border: 2px solid rgba(0, 245, 255, 0.3);
            border-radius: 15px;
            padding: 2rem 1rem;
            text-align: center;
            position: relative;
            transition: all 0.3s ease;
            height: 200px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .arch-node:hover {
            transform: translateY(-8px);
            border-color: #00f5ff;
            box-shadow: 0 15px 40px rgba(0, 245, 255, 0.3);
        }

        .arch-icon {
            width: 50px;
            height: 50px;
            background: linear-gradient(45deg, #00f5ff, #0080ff);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1rem;
            font-size: 1.2rem;
            color: #000;
            font-weight: bold;
            position: relative;
            overflow: hidden;
        }

        .arch-icon::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            transition: left 0.6s;
        }

        .arch-node:hover .arch-icon::before {
            left: 100%;
        }

        .arch-node h3 {
            font-size: 1rem;
            margin-bottom: 0.5rem;
            color: #00f5ff;
            line-height: 1.2;
        }

        .arch-node p {
            font-size: 0.85rem;
            opacity: 0.9;
            line-height: 1.3;
        }

        /* Professional connecting lines */
        .arch-node:not(:last-child)::after {
            content: '';
            position: absolute;
            top: 50%;
            right: -0.5rem;
            width: 1rem;
            height: 2px;
            background: #00f5ff;
            transform: translateY(-50%);
            opacity: 0.6;
        }

        /* Animated dots on the connecting line */
        .architecture-flow .flow-dot {
            position: absolute;
            top: 50%;
            left: 0;
            width: 8px;
            height: 8px;
            background: #00f5ff;
            border-radius: 50%;
            transform: translateY(-50%);
            animation: flowDot 4s infinite linear;
            box-shadow: 0 0 10px rgba(0, 245, 255, 0.8);
            z-index: 10;
        }

        @keyframes flowDot {
            0% { left: calc(10% + 25px); opacity: 1; }
            19% { left: calc(30% - 8px); opacity: 1; }
            20% { left: calc(30% + 8px); opacity: 0; }
            21% { left: calc(30% + 8px); opacity: 1; }
            39% { left: calc(50% - 8px); opacity: 1; }
            40% { left: calc(50% + 8px); opacity: 0; }
            41% { left: calc(50% + 8px); opacity: 1; }
            59% { left: calc(70% - 8px); opacity: 1; }
            60% { left: calc(70% + 8px); opacity: 0; }
            61% { left: calc(70% + 8px); opacity: 1; }
            79% { left: calc(90% - 25px); opacity: 1; }
            80% { left: calc(90% - 25px); opacity: 0; }
            100% { left: calc(90% - 25px); opacity: 0; }
        }

        .arch-node:last-child::after,
        .arch-node:last-child::before {
            display: none;
        }

        /* Stats Section */
        .stats {
            background: linear-gradient(135deg, #001122, #000);
            margin: 0;
            max-width: 100%;
            padding: 5rem 0;
        }

        .stats-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .stat-card {
            background: rgba(0, 245, 255, 0.1);
            padding: 2rem;
            border-radius: 10px;
            text-align: center;
            border: 1px solid rgba(0, 245, 255, 0.3);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 245, 255, 0.1), transparent);
            transition: left 0.8s;
        }

        .stat-card:hover::before {
            left: 100%;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 245, 255, 0.2);
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            color: #00f5ff;
            display: block;
        }

        .stat-label {
            margin-top: 0.5rem;
            opacity: 0.8;
        }

        /* Features Grid */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .feature-card {
            background: linear-gradient(135deg, #001122, #000);
            padding: 2rem;
            border-radius: 15px;
            border: 1px solid rgba(0, 245, 255, 0.3);
            transition: all 0.3s ease;
        }

        .feature-card:hover {
            transform: translateY(-5px);
            border-color: #00f5ff;
            box-shadow: 0 15px 40px rgba(0, 245, 255, 0.2);
        }

        .feature-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(45deg, #00f5ff, #0080ff);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1rem;
            font-size: 1.8rem;
            font-weight: bold;
            color: #000;
            position: relative;
            overflow: hidden;
        }

        .feature-icon::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
        }

        .feature-card:hover .feature-icon::before {
            left: 100%;
        }

        .feature-card h3 {
            font-size: 1.3rem;
            margin-bottom: 1rem;
            color: #00f5ff;
        }

        /* Process Flow Diagram */
        .process-flow-diagram {
            background: linear-gradient(135deg, #000511, #001122);
            padding: 3rem;
            border-radius: 20px;
            margin: 3rem 0;
            border: 1px solid rgba(0, 245, 255, 0.2);
        }

        .flow-container {
            display: flex;
            flex-direction: column;
            gap: 2rem;
            position: relative;
            max-width: 800px;
            margin: 0 auto;
        }

        .flow-step {
            display: flex;
            align-items: flex-start;
            gap: 2rem;
            padding: 2rem;
            background: rgba(0, 245, 255, 0.05);
            border-radius: 15px;
            border: 1px solid rgba(0, 245, 255, 0.2);
            transition: all 0.3s ease;
            position: relative;
            height: 160px;
        }

        .flow-step:hover {
            transform: translateX(10px);
            border-color: rgba(0, 245, 255, 0.4);
            box-shadow: 0 5px 20px rgba(0, 245, 255, 0.1);
        }

        .flow-step::after {
            content: '';
            position: absolute;
            bottom: -25px;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 0;
            border-top: 15px solid #00f5ff;
            border-left: 10px solid transparent;
            border-right: 10px solid transparent;
            opacity: 0.7;
        }

        .flow-step:last-child::after {
            display: none;
        }

        .flow-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(45deg, #00f5ff, #0080ff);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            color: #000;
            font-weight: bold;
            flex-shrink: 0;
            position: relative;
            overflow: hidden;
        }

        .flow-icon::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
        }

        .flow-step:hover .flow-icon::before {
            left: 100%;
        }

        .flow-content {
            flex: 1;
        }

        .flow-content h3 {
            color: #00f5ff;
            margin-bottom: 1rem;
            font-size: 1.3rem;
        }

        .flow-content p {
            opacity: 0.9;
            line-height: 1.6;
            font-size: 0.95rem;
            overflow: hidden;
            display: -webkit-box;
            -webkit-line-clamp: 4;
            -webkit-box-orient: vertical;
        }

        /* Process Section */
        .process-steps {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .process-step {
            text-align: center;
            position: relative;
        }

        .step-number {
            width: 80px;
            height: 80px;
            background: linear-gradient(45deg, #00f5ff, #0080ff);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: bold;
            color: #000;
            margin: 0 auto 1rem;
            position: relative;
            overflow: hidden;
        }

        .step-number::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
        }

        .process-step:hover .step-number::before {
            left: 100%;
        }

        .process-step h3 {
            margin-bottom: 1rem;
            color: #00f5ff;
        }

        /* About Section */
        .about {
            background: linear-gradient(135deg, #001122, #000);
            margin: 0;
            max-width: 100%;
            padding: 5rem 0;
        }

        .about-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .about-text {
            font-size: 1.1rem;
            line-height: 1.8;
        }

        .about-highlights {
            background: rgba(0, 245, 255, 0.1);
            padding: 2rem;
            border-radius: 15px;
            border: 1px solid rgba(0, 245, 255, 0.3);
        }

        .highlight-item {
            display: flex;
            align-items: center;
            margin-bottom: 1rem;
            gap: 1rem;
        }

        .highlight-icon {
            width: 30px;
            height: 30px;
            background: linear-gradient(45deg, #00f5ff, #00ff80);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
        }

        /* Interactive Timeline */
        .timeline-section {
            background: linear-gradient(135deg, #000, #001122);
            padding: 5rem 2rem;
            margin: 3rem 0;
            border-radius: 20px;
        }

        .timeline {
            position: relative;
            max-width: 800px;
            margin: 0 auto;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 50%;
            top: 0;
            bottom: 0;
            width: 2px;
            background: linear-gradient(to bottom, #00f5ff, #0080ff);
            transform: translateX(-50%);
        }

        .timeline-item {
            display: flex;
            justify-content: flex-end;
            padding-right: 30px;
            position: relative;
            margin: 2rem 0;
            width: 50%;
        }

        .timeline-item:nth-child(even) {
            align-self: flex-end;
            justify-content: flex-start;
            padding-left: 30px;
            padding-right: 0;
            margin-left: 50%;
        }

        .timeline-content {
            background: rgba(0, 245, 255, 0.1);
            padding: 1.5rem;
            border-radius: 10px;
            border: 1px solid rgba(0, 245, 255, 0.3);
            transition: all 0.3s ease;
            max-width: 300px;
        }

        .timeline-content:hover {
            transform: scale(1.05);
            border-color: #00f5ff;
        }

        .timeline-dot {
            position: absolute;
            right: -10px;
            top: 1.5rem;
            width: 20px;
            height: 20px;
            background: #00f5ff;
            border-radius: 50%;
            border: 4px solid #000;
        }

        .timeline-item:nth-child(even) .timeline-dot {
            left: -10px;
            right: auto;
        }

        /* Testimonial Section */
        .testimonials {
            background: linear-gradient(135deg, #000811, #001122);
            margin: 0;
            max-width: 100%;
            padding: 5rem 0;
        }

        .testimonials-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .testimonial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .testimonial-card {
            background: rgba(0, 245, 255, 0.05);
            padding: 2rem;
            border-radius: 15px;
            border: 1px solid rgba(0, 245, 255, 0.2);
            position: relative;
            transition: all 0.3s ease;
        }

        .testimonial-card:hover {
            transform: translateY(-5px);
            border-color: rgba(0, 245, 255, 0.4);
            box-shadow: 0 10px 30px rgba(0, 245, 255, 0.1);
        }

        .testimonial-text {
            font-style: italic;
            margin-bottom: 1rem;
            line-height: 1.6;
            color: #e0e0e0;
        }

        .testimonial-author {
            color: #00f5ff;
            font-weight: 600;
            font-size: 0.9rem;
        }

        .testimonial-role {
            color: #888;
            font-size: 0.8rem;
            margin-top: 0.2rem;
        }

        /* CTA Section */
        .cta-section {
            background: linear-gradient(45deg, #001122, #000511);
            padding: 5rem 0;
            text-align: center;
        }

        .cta-content {
            max-width: 800px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .cta-title {
            font-size: 2.8rem;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, #00f5ff, #00ff80);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .cta-subtitle {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            opacity: 0.9;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        .cta-primary {
            padding: 1rem 2rem;
            background: linear-gradient(45deg, #00f5ff, #0080ff);
            color: #000;
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        .cta-secondary {
            padding: 1rem 2rem;
            border: 2px solid #00f5ff;
            color: #00f5ff;
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        .cta-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(0, 245, 255, 0.3);
        }

        .cta-secondary:hover {
            background: rgba(0, 245, 255, 0.1);
            transform: translateY(-3px);
        }

        /* Contact Section */
        .contact-form {
            max-width: 600px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: #00f5ff;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 1rem;
            background: rgba(0, 245, 255, 0.1);
            border: 1px solid rgba(0, 245, 255, 0.3);
            border-radius: 5px;
            color: #fff;
            font-size: 1rem;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #00f5ff;
            box-shadow: 0 0 10px rgba(0, 245, 255, 0.3);
        }

        .submit-btn {
            width: 100%;
            padding: 1rem;
            background: linear-gradient(45deg, #00f5ff, #0080ff);
            color: #000;
            border: none;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 20px rgba(0, 245, 255, 0.3);
        }

        /* Footer */
        footer {
            background: #000;
            text-align: center;
            padding: 2rem;
            border-top: 1px solid rgba(0, 245, 255, 0.3);
        }

        /* Animations */
        .animate-on-scroll {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }

        .animate-on-scroll.animated {
            opacity: 1;
            transform: translateY(0);
        }

        /* Progress Indicator */
        .progress-indicator {
            position: fixed;
            top: 0;
            left: 0;
            width: 0%;
            height: 3px;
            background: linear-gradient(90deg, #00f5ff, #0080ff);
            z-index: 9999;
            transition: width 0.3s ease;
        }

        /* Pulse Animation for Important Elements */
        .pulse {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% {
                box-shadow: 0 0 0 0 rgba(0, 245, 255, 0.7);
            }
            70% {
                box-shadow: 0 0 0 10px rgba(0, 245, 255, 0);
            }
            100% {
                box-shadow: 0 0 0 0 rgba(0, 245, 255, 0);
            }
        }

        /* Custom Modal Styles */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(10px);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 10000;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
        }

        .modal-overlay.show {
            opacity: 1;
            visibility: visible;
        }

        .modal {
            background: linear-gradient(135deg, #001122, #000511);
            border: 2px solid #00f5ff;
            border-radius: 20px;
            padding: 2rem;
            max-width: 400px;
            width: 90%;
            text-align: center;
            transform: scale(0.7);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .modal-overlay.show .modal {
            transform: scale(1);
        }

        .modal::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 245, 255, 0.1), transparent);
            transition: left 0.6s;
        }

        .modal:hover::before {
            left: 100%;
        }

        .modal-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(45deg, #ff6b6b, #ff8e8e);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 1rem;
            font-size: 1.8rem;
            color: #fff;
            animation: pulse 2s infinite;
        }

        .modal-title {
            font-size: 1.5rem;
            color: #00f5ff;
            margin-bottom: 1rem;
            font-weight: bold;
        }

        .modal-message {
            color: #fff;
            margin-bottom: 2rem;
            line-height: 1.5;
            opacity: 0.9;
        }

        .modal-button {
            background: linear-gradient(45deg, #00f5ff, #0080ff);
            color: #000;
            border: none;
            padding: 0.8rem 2rem;
            border-radius: 50px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 1rem;
        }

        .modal-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(0, 245, 255, 0.3);
        }

        /* Success Modal Variant */
        .modal.success .modal-icon {
            background: linear-gradient(45deg, #00ff80, #00f5ff);
        }

        /* Animations */
        @keyframes modalSlideIn {
            from {
                transform: translateY(-50px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }

        .modal-overlay.show .modal {
            animation: modalSlideIn 0.4s ease-out;
        }
        @media (max-width: 768px) {
            .cta-title {
                font-size: 2.2rem;
            }
            
            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }

            .nav-links {
                display: none;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero p {
                font-size: 1.1rem;
            }

            .about-content {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .section-title {
                font-size: 2rem;
            }

            .architecture-flow {
                flex-wrap: nowrap;
                overflow-x: auto;
                gap: 1rem;
            }

            .arch-node {
                min-width: 120px;
                padding: 1rem;
            }

            .arch-node h3 {
                font-size: 0.9rem;
            }

            .arch-node p {
                font-size: 0.75rem;
            }

            .arch-icon {
                width: 40px;
                height: 40px;
                font-size: 1rem;
            }

            .arch-node::after {
                right: -30px;
                border-left: 15px solid #00f5ff;
                border-top: 8px solid transparent;
                border-bottom: 8px solid transparent;
            }

            .arch-node::before {
                right: -25px;
                width: 40px;
                height: 3px;
            }

            .timeline::before {
                left: 20px;
            }

            .timeline-item {
                width: 100%;
                padding-left: 50px;
                padding-right: 0;
                justify-content: flex-start;
                margin-left: 0;
            }

            .timeline-item:nth-child(even) {
                padding-left: 50px;
                padding-right: 0;
                justify-content: flex-start;
                margin-left: 0;
            }

            .timeline-dot {
                left: 10px;
                right: auto;
            }

            .timeline-item:nth-child(even) .timeline-dot {
                left: 10px;
                right: auto;
            }

            .flow-step {
                flex-direction: column;
                text-align: center;
            }

            .flow-step::after {
                bottom: -15px;
                left: 50%;
                transform: translateX(-50%);
            }
        }
    </style>
</head>
<body>
    <!-- Progress Indicator -->
    <div class="progress-indicator" id="progressBar"></div>

    <!-- Floating Elements -->
    <div class="floating-elements">
        <div class="floating-element"></div>
        <div class="floating-element"></div>
        <div class="floating-element"></div>
        <div class="floating-element"></div>
    </div>

    <!-- Navigation -->
    <nav>
        <div class="nav-container">
            <div class="logo">SoloLaunch</div>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#features">Features</a></li>
                <li><a href="#process">Process</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1>iOS Apps Built by AI</h1>
            <p>We build, publish, and market iOS apps for solopreneurs using cutting-edge AI agents. Focus on your idea while we handle everything else.</p>
            <a href="#contact" class="cta-button pulse">Start Your App Journey</a>
        </div>
    </section>

    <!-- Architecture Diagram Section -->
    <section class="architecture-diagram animate-on-scroll">
        <h2 class="section-title">How Our AI System Works</h2>
        <div class="architecture-flow">
            <div class="arch-node">
                <div class="arch-icon">1</div>
                <h3>Your Idea</h3>
                <p>Submit your app concept</p>
            </div>
            <div class="arch-node">
                <div class="arch-icon">2</div>
                <h3>AI Analysis</h3>
                <p>Our AI analyzes requirements</p>
            </div>
            <div class="arch-node">
                <div class="arch-icon">3</div>
                <h3>Design Generation</h3>
                <p>Automated Figma designs</p>
            </div>
            <div class="arch-node">
                <div class="arch-icon">4</div>
                <h3>Code Development</h3>
                <p>AI writes Swift/SwiftUI</p>
            </div>
            <div class="arch-node">
                <div class="arch-icon">5</div>
                <h3>App Store Ready</h3>
                <p>Published & marketed</p>
            </div>
        </div>
    </section>

    <!-- Stats Section -->
    <section class="stats">
        <div class="stats-container">
            <h2 class="section-title animate-on-scroll">Proven Results</h2>
            <div class="stats-grid">
                <div class="stat-card animate-on-scroll">
                    <span class="stat-number">60K+</span>
                    <div class="stat-label">Total Downloads</div>
                </div>
                <div class="stat-card animate-on-scroll">
                    <span class="stat-number">$30K</span>
                    <div class="stat-label">Annual Recurring Revenue</div>
                </div>
                <div class="stat-card animate-on-scroll">
                    <span class="stat-number">500K+</span>
                    <div class="stat-label">TikTok Views</div>
                </div>
                <div class="stat-card animate-on-scroll">
                    <span class="stat-number">1200+</span>
                    <div class="stat-label">Paying Customers</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section id="features">
        <h2 class="section-title animate-on-scroll">Why Choose SoloLaunch?</h2>
        <div class="features-grid">
            <div class="feature-card animate-on-scroll">
                <div class="feature-icon">AI</div>
                <h3>AI-Powered Development</h3>
                <p>Our in-house AI agents handle coding, design, and development, delivering apps 10x faster than traditional agencies.</p>
            </div>
            <div class="feature-card animate-on-scroll">
                <div class="feature-icon">01</div>
                <h3>Affordable Pricing</h3>
                <p>Pay just $500 instead of $10,000-$40,000 that traditional mobile app agencies charge. No hidden costs or maintenance fees.</p>
            </div>
            <div class="feature-card animate-on-scroll">
                <div class="feature-icon">02</div>
                <h3>Complete Solution</h3>
                <p>We handle everything: development, App Store publishing, payment infrastructure, marketing, and organic TikTok promotion.</p>
            </div>
            <div class="feature-card animate-on-scroll">
                <div class="feature-icon">03</div>
                <h3>Marketing Included</h3>
                <p>Our TikTok marketing expertise has generated over 500,000 views, driving organic growth for your app.</p>
            </div>
            <div class="feature-card animate-on-scroll">
                <div class="feature-icon">04</div>
                <h3>Fast Development</h3>
                <p>While agencies take months, our AI-powered process delivers your app in days, not weeks.</p>
            </div>
            <div class="feature-card animate-on-scroll">
                <div class="feature-icon">05</div>
                <h3>Built for Entrepreneurs</h3>
                <p>Designed specifically for solopreneurs and small businesses who need to move fast and bootstrap their way to success.</p>
            </div>
        </div>
    </section>

    <!-- Process Flow Diagram -->
    <section class="process-flow-diagram animate-on-scroll">
        <h2 class="section-title">Detailed Development Process</h2>
        <div class="flow-container">
            <div class="flow-step">
                <div class="flow-icon">01</div>
                <div class="flow-content">
                    <h3>Requirements Gathering</h3>
                    <p>Our AI conducts an intelligent analysis of your app idea, target audience, and feature requirements. We identify the core functionality and create a comprehensive development roadmap.</p>
                </div>
            </div>
            <div class="flow-step">
                <div class="flow-icon">02</div>
                <div class="flow-content">
                    <h3>AI-Generated Design</h3>
                    <p>Advanced design algorithms create professional Figma mockups with modern UI/UX patterns. Every screen is optimized for iOS guidelines and user engagement.</p>
                </div>
            </div>
            <div class="flow-step">
                <div class="flow-icon">03</div>
                <div class="flow-content">
                    <h3>Code Generation</h3>
                    <p>Our proprietary AI writes clean, optimized Swift and SwiftUI code. The app is built with scalability, performance, and App Store guidelines in mind.</p>
                </div>
            </div>
            <div class="flow-step">
                <div class="flow-icon">04</div>
                <div class="flow-content">
                    <h3>Integration & Testing</h3>
                    <p>Payment systems, analytics, and cloud services are automatically integrated. Comprehensive testing ensures bug-free performance across all iOS devices.</p>
                </div>
            </div>
            <div class="flow-step">
                <div class="flow-icon">05</div>
                <div class="flow-content">
                    <h3>App Store Deployment</h3>
                    <p>We handle the entire App Store submission process, from metadata optimization to review approval. Your app goes live with zero effort from you.</p>
                </div>
            </div>
            <div class="flow-step">
                <div class="flow-icon">06</div>
                <div class="flow-content">
                    <h3>Marketing Launch</h3>
                    <p>Organic TikTok marketing campaigns drive initial downloads. We create engaging content that showcases your app's unique value proposition.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Process Section -->
    <section id="process">
        <h2 class="section-title animate-on-scroll">Our Simple Process</h2>
        <div class="process-steps">
            <div class="process-step animate-on-scroll">
                <div class="step-number">1</div>
                <h3>Share Your Idea</h3>
                <p>Tell us about your app concept and target audience. Our AI analyzes your requirements instantly.</p>
            </div>
            <div class="process-step animate-on-scroll">
                <div class="step-number">2</div>
                <h3>AI Development</h3>
                <p>Our AI agents create Figma designs, write code, and build your iOS app using proven frameworks.</p>
            </div>
            <div class="process-step animate-on-scroll">
                <div class="step-number">3</div>
                <h3>App Store Launch</h3>
                <p>We handle App Store submission, payment integration, and ensure your app meets all Apple guidelines.</p>
            </div>
            <div class="process-step animate-on-scroll">
                <div class="step-number">4</div>
                <h3>Marketing & Growth</h3>
                <p>Launch with organic TikTok marketing and ongoing support to maximize your app's success.</p>
            </div>
        </div>
    </section>

    <!-- Timeline Section -->
    <section class="timeline-section">
        <div class="stats-container">
            <h2 class="section-title animate-on-scroll">Our Journey & Milestones</h2>
            <div class="timeline">
                <div class="timeline-item animate-on-scroll">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <h3>Founded SoloLaunch</h3>
                        <p>Started with a vision to democratize app development using AI technology.</p>
                    </div>
                </div>
                <div class="timeline-item animate-on-scroll">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <h3>First AI Agent Development</h3>
                        <p>Built our proprietary AI system capable of generating iOS apps from ideas.</p>
                    </div>
                </div>
                <div class="timeline-item animate-on-scroll">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <h3>5 Successful Apps Built</h3>
                        <p>Validated our approach by building and launching 5 profitable iOS apps.</p>
                    </div>
                </div>
                <div class="timeline-item animate-on-scroll">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <h3>$30K ARR Achieved</h3>
                        <p>Reached $30,000 in annual recurring revenue from our app portfolio.</p>
                    </div>
                </div>
                <div class="timeline-item animate-on-scroll">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <h3>500K+ TikTok Views</h3>
                        <p>Mastered TikTok marketing, generating massive organic reach for our apps.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials Section -->
    <section class="testimonials">
        <div class="testimonials-container">
            <h2 class="section-title animate-on-scroll">What Our Clients Say</h2>
            <div class="testimonial-grid">
                <div class="testimonial-card animate-on-scroll">
                    <div class="testimonial-text">
                        "SoloLaunch turned my idea into a real app in just 2 weeks. The AI development process was incredible to watch - way faster than any agency I've worked with before."
                    </div>
                    <div class="testimonial-author">Marcus Chen</div>
                    <div class="testimonial-role">Fitness Coach & App Entrepreneur</div>
                </div>
                <div class="testimonial-card animate-on-scroll">
                    <div class="testimonial-text">
                        "For $500, I got what would have cost me $20K elsewhere. The TikTok marketing they provided got my app featured and downloaded thousands of times."
                    </div>
                    <div class="testimonial-author">Sarah Williams</div>
                    <div class="testimonial-role">Digital Marketing Consultant</div>
                </div>
                <div class="testimonial-card animate-on-scroll">
                    <div class="testimonial-text">
                        "The entire process was seamless. They handled everything from design to App Store approval. Now I'm making passive income from my app idea."
                    </div>
                    <div class="testimonial-author">David Park</div>
                    <div class="testimonial-role">Productivity App Creator</div>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section">
        <div class="cta-content">
            <h2 class="cta-title animate-on-scroll">Ready to Launch Your App?</h2>
            <p class="cta-subtitle animate-on-scroll">Join the solopreneurs who've already turned their ideas into profitable iOS apps</p>
            <div class="cta-buttons animate-on-scroll">
                <a href="#contact" class="cta-primary">Start Building Now</a>
                <a href="#about" class="cta-secondary">Learn More</a>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="about">
        <div class="about-container">
            <h2 class="section-title animate-on-scroll">About SoloLaunch</h2>
            <div class="about-content">
                <div class="about-text animate-on-scroll">
                    <p>We're not just another app development agency. We're pioneers in AI-powered app creation, built by entrepreneurs who understand the hustle.</p>
                    
                    <p>After building 5 successful iOS apps ourselves and generating $30,000 in ARR with 60,000+ downloads, we realized we could democratize app development for other solopreneurs.</p>
                    
                    <p>Traditional agencies are slow, expensive, and out of reach for most entrepreneurs. We're changing that with our AI-first approach that makes professional iOS app development accessible to everyone.</p>
                    
                    <p>As AI transforms the job market and pushes more people toward entrepreneurship, we're building the platform that lets anyone turn their idea into a published iOS app instantly.</p>
                </div>
                
                <div class="about-highlights animate-on-scroll">
                    <div class="highlight-item">
                        <div class="highlight-icon">01</div>
                        <span>5 successful iOS apps built</span>
                    </div>
                    <div class="highlight-item">
                        <div class="highlight-icon">02</div>
                        <span>$1,500+ revenue from first 3 clients</span>
                    </div>
                    <div class="highlight-item">
                        <div class="highlight-icon">03</div>
                        <span>AI-powered development pipeline</span>
                    </div>
                    <div class="highlight-item">
                        <div class="highlight-icon">04</div>
                        <span>Complete marketing solution</span>
                    </div>
                    <div class="highlight-item">
                        <div class="highlight-icon">05</div>
                        <span>Proven TikTok marketing strategy</span>
                    </div>
                    <div class="highlight-item">
                        <div class="highlight-icon">06</div>
                        <span>End-to-end app logistics</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact">
        <h2 class="section-title animate-on-scroll">Ready to Launch?</h2>
        <div class="contact-form animate-on-scroll">
            <form>
                <div class="form-group">
                    <label for="name">Your Name</label>
                    <input type="text" id="name" name="name" required>
                </div>
                <div class="form-group">
                    <label for="email">Email Address</label>
                    <input type="email" id="email" name="email" required>
                </div>
                <div class="form-group">
                    <label for="app-idea">What's your app idea?</label>
                    <textarea id="app-idea" name="app-idea" rows="5" placeholder="Tell us what you want to build..." required></textarea>
                </div>
                <button type="submit" class="submit-btn">Let's Build It</button>
            </form>
        </div>
    </section>

    <!-- Custom Modal -->
    <div id="customModal" class="modal-overlay">
        <div class="modal" id="modalContent">
            <div class="modal-icon" id="modalIcon">!</div>
            <h3 class="modal-title" id="modalTitle">Oops!</h3>
            <p class="modal-message" id="modalMessage">Please fill in all required fields to continue.</p>
            <button class="modal-button" onclick="closeModal()">Got it!</button>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <p>&copy; 2025 SoloLaunch. Building the future of iOS app development with AI.</p>
    </footer>

    <script>
        // Progress bar
        window.addEventListener('scroll', () => {
            const winScroll = document.body.scrollTop || document.documentElement.scrollTop;
            const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrolled = (winScroll / height) * 100;
            document.getElementById('progressBar').style.width = scrolled + '%';
        });

        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Animate elements on scroll
        const animateOnScroll = () => {
            const elements = document.querySelectorAll('.animate-on-scroll');
            elements.forEach(element => {
                const elementTop = element.getBoundingClientRect().top;
                const elementVisible = 150;
                
                if (elementTop < window.innerHeight - elementVisible) {
                    element.classList.add('animated');
                }
            });
        };

        window.addEventListener('scroll', animateOnScroll);
        animateOnScroll(); // Run once on load

        // Custom Modal Functions
        function showModal(title, message, type = 'error') {
            const modal = document.getElementById('customModal');
            const modalContent = document.getElementById('modalContent');
            const modalIcon = document.getElementById('modalIcon');
            const modalTitle = document.getElementById('modalTitle');
            const modalMessage = document.getElementById('modalMessage');
            
            modalTitle.textContent = title;
            modalMessage.textContent = message;
            
            if (type === 'success') {
                modalContent.classList.add('success');
                modalIcon.textContent = '✓';
            } else {
                modalContent.classList.remove('success');
                modalIcon.textContent = '!';
            }
            
            modal.classList.add('show');
        }

        function closeModal() {
            const modal = document.getElementById('customModal');
            modal.classList.remove('show');
        }

        // Close modal when clicking outside
        document.getElementById('customModal').addEventListener('click', function(e) {
            if (e.target === this) {
                closeModal();
            }
        });

        // Form submission with custom modal
        document.querySelector('form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const name = document.getElementById('name').value.trim();
            const email = document.getElementById('email').value.trim();
            const appIdea = document.getElementById('app-idea').value.trim();
            
            if (!name || !email || !appIdea) {
                showModal(
                    'Missing Information', 
                    'Please fill in all fields before submitting your request. We need your name, email, and app idea to get started!',
                    'error'
                );
                return;
            }
            
            // Email validation
            const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailRegex.test(email)) {
                showModal(
                    'Invalid Email', 
                    'Please enter a valid email address so we can contact you about your app project.',
                    'error'
                );
                return;
            }
            
            // Success message
            showModal(
                'Request Submitted!', 
                'Thank you for your interest! We\'ll review your app idea and contact you within 24 hours to discuss the next steps.',
                'success'
            );
            
            // Reset form after successful submission
            setTimeout(() => {
                this.reset();
                closeModal();
            }, 3000);
        });

        // Enhanced hover effects
        document.querySelectorAll('.feature-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-10px) scale(1.02)';
            });
            
            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(-5px) scale(1)';
            });
        });

        // Interactive timeline dots
        document.querySelectorAll('.timeline-dot').forEach(dot => {
            dot.addEventListener('click', function() {
                this.style.transform = 'scale(1.5)';
                setTimeout(() => {
                    this.style.transform = 'scale(1)';
                }, 200);
            });
        });

        // Stats counter animation
        const animateStats = () => {
            const statNumbers = document.querySelectorAll('.stat-number');
            statNumbers.forEach(stat => {
                const target = parseInt(stat.textContent.replace(/\D/g, ''));
                const suffix = stat.textContent.replace(/[0-9]/g, '');
                let current = 0;
                const increment = target / 100;
                
                const updateCounter = () => {
                    if (current < target) {
                        current += increment;
                        stat.textContent = Math.floor(current) + suffix;
                        setTimeout(updateCounter, 20);
                    } else {
                        stat.textContent = target + suffix;
                    }
                };
                
                updateCounter();
            });
        };

        // Trigger stats animation when in view
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting && entry.target.classList.contains('stats-grid')) {
                    animateStats();
                    observer.unobserve(entry.target);
                }
            });
        });

        document.querySelectorAll('.stats-grid').forEach(grid => {
            observer.observe(grid);
        });
    </script>
</body>
</html>
