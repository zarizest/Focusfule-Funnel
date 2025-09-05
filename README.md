# Focusfule-Funnel
<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FocusFuel Interactive Funnel Explorer</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #FDFBF8; color: #3D3D3D; }
        .step-item.active { border-color: #F59E0B; color: #F59E0B; font-weight: 600; }
        .step-item.active .step-circle { background-color: #F59E0B; color: white; }
        .step-item .step-circle { background-color: #E5E7EB; color: #6B7280; }
        .chart-container { position: relative; width: 100%; max-width: 600px; margin: 0 auto; height: 300px; max-height: 400px; }
        .mockup-browser { border: 8px solid #E5E7EB; border-radius: 12px; box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1); overflow: hidden; transition: transform 0.3s ease; }
        .mockup-browser:hover { transform: scale(1.02); }
        .mockup-header { background-color: #E5E7EB; padding: 8px; display: flex; align-items: center; gap: 6px; }
        .mockup-dot { width: 12px; height: 12px; border-radius: 50%; }
        .gemini-loader { display: none; }
        .gemini-response { background-color: #fffbeb; border: 1px solid #fde68a; border-radius: 8px; padding: 1rem; margin-top: 1rem; }
    </style>
</head>
<body class="antialiased">
    <div class="container mx-auto p-4 md:p-8">
        <header class="text-center mb-8 md:mb-12">
            <h1 class="text-4xl md:text-5xl font-bold text-gray-800">FocusFuel</h1>
            <p class="text-lg text-gray-600 mt-2">Interactive Funnel Explorer ✨</p>
        </header>
        <nav id="step-navigation" class="mb-8 md:mb-12" aria-label="Funnel Stages">
            <div class="flex flex-col md:flex-row justify-center items-center space-y-4 md:space-y-0 md:space-x-4"></div>
        </nav>
        <main id="content-area" class="bg-white rounded-2xl shadow-lg p-6 md:p-10 min-h-[60vh]" role="main"></main>
    </div>

    <script>
    // --- Constants & State ---
    const funnelData = [ /* ... Funnel Steps: (unchanged for brevity, copy from your original) ... */ ];
    const navigationContainer = document.querySelector('#step-navigation > div');
    const contentArea = document.getElementById('content-area');
    let currentChart = null;

    // --- Navigation Render ---
    function renderNavigation() {
        navigationContainer.innerHTML = '';
        funnelData.forEach((step, index) => {
            const stepElement = document.createElement('button');
            stepElement.className = 'step-item flex items-center p-2 border-b-4 border-transparent transition-colors duration-300';
            stepElement.dataset.index = index;
            stepElement.setAttribute('aria-label', `Go to step ${index+1}: ${step.name}`);
            stepElement.innerHTML = `
                <span class="step-circle w-8 h-8 rounded-full flex items-center justify-center font-bold mr-3 transition-colors">${index + 1}</span>
                <span>${step.name}</span>
            `;
            navigationContainer.appendChild(stepElement);
        });
    }

    // --- Step Render ---
    function renderStep(index) {
        const stepData = funnelData[index];
        // Main Content
        contentArea.innerHTML = `
            <section class="text-center mb-8" aria-label="Stage Objective">
                <h2 class="text-3xl font-bold text-gray-800">${index+1}. ${stepData.name}</h2>
                <p class="text-gray-600 mt-2 max-w-3xl mx-auto">${stepData.objective}</p>
            </section>
            <div class="grid lg:grid-cols-3 gap-8 items-start">
                <section class="lg:col-span-2" aria-label="Stage Mockup">
                    ${stepData.mockupHtml}
                </section>
                <aside class="lg:col-span-1 bg-amber-50 rounded-xl p-6 border border-amber-200" aria-label="Strategy Breakdown">
                    <h3 class="font-bold text-xl mb-4 text-amber-800">${stepData.analysis.title}</h3>
                    <ul class="space-y-4">
                        ${stepData.analysis.points.map(point => `
                            <li class="border-l-4 border-amber-400 pl-4">
                                <h4 class="font-semibold text-gray-700">${point.heading}</h4>
                                <p class="text-sm text-gray-500 italic my-1">${point.copy}</p>
                                <p class="text-sm text-amber-700">${point.trigger}</p>
                            </li>
                        `).join('')}
                    </ul>
                    <div class="mt-6">
                        <button id="gemini-generate-btn" data-index="${index}" class="w-full bg-gradient-to-r from-purple-500 to-indigo-600 text-white font-semibold py-2 px-4 rounded-lg hover:shadow-lg transition-shadow" aria-label="Generate new ideas">
                            ✨ Naye Ideas Generate Karein
                        </button>
                        <div id="gemini-loader" class="gemini-loader text-center mt-4">
                            <p class="text-sm text-gray-600">Ideas generate ho rahe hain...</p>
                        </div>
                        <div id="gemini-response-container"></div>
                    </div>
                </aside>
            </div>
        `;
        // Chart
        if (currentChart) { currentChart.destroy(); currentChart = null; }
        if (stepData.name === "Offer Page") renderValueChart();
        if (stepData.name === "Follow-up Sequence") setupAccordion();
        // Navigation Active State
        document.querySelectorAll('.step-item').forEach((item, i) => {
            item.classList.toggle('active', i === index);
        });
        // Gemini Button
        document.getElementById('gemini-generate-btn').addEventListener('click', handleGenerateIdeas);
    }

    // --- Gemini API Integration ---
    async function handleGenerateIdeas(event) {
        const index = event.target.dataset.index;
        const prompt = funnelData[index].analysis.geminiPrompt;
        const loader = document.getElementById('gemini-loader');
        const responseContainer = document.getElementById('gemini-response-container');
        const button = event.target;
        loader.style.display = 'block';
        responseContainer.innerHTML = '';
        button.disabled = true;
        try {
            const generatedText = await callGeminiAPI(prompt);
            displayGeminiResponse(generatedText, responseContainer);
        } catch (error) {
            console.error("Gemini API call failed:", error);
            responseContainer.innerHTML = `<div class="gemini-response text-red-700"><p>Ek error aa gayi. Please thodi der baad try karein.</p></div>`;
        } finally {
            loader.style.display = 'none';
            button.disabled = false;
        }
    }
    async function callGeminiAPI(prompt, retries = 3, delay = 1000) {
        // NOTE: Insert your Gemini API key securely, never expose in frontend production!
        const apiKey = ""; // <-- Your Gemini API Key
        const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-05-20:generateContent?key=${apiKey}`;
        const payload = {
            contents: [{ parts: [{ text: prompt }] }],
            generationConfig: { temperature: 0.7, topP: 1, topK: 1, maxOutputTokens: 256 }
        };
        for (let i = 0; i < retries; i++) {
            try {
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });
                if (!response.ok) throw new Error(`HTTP error! status: ${response.status}`);
                const result = await response.json();
                const text = result?.candidates?.[0]?.content?.parts?.[0]?.text;
                if (text) return text;
                throw new Error("Invalid response structure from Gemini API");
            } catch (error) {
                if (i === retries - 1) throw error;
                await new Promise(res => setTimeout(res, delay * Math.pow(2, i)));
            }
        }
    }
    function displayGeminiResponse(text, container) {
        // Format markdown-like Gemini response
        const formattedText = text
            .replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>')
            .replace(/\* (.*?)(?=\n\* |\n\n|$)/g, '<li class="ml-4 mb-2 p-2 bg-white rounded shadow-sm">$1</li>')
            .replace(/\n/g, '<br>');
        container.innerHTML = `<div class="gemini-response"><ul>${formattedText}</ul></div>`;
    }

    // --- Chart.js Value Stack ---
    function renderValueChart() {
        const ctx = document.getElementById('valueChart').getContext('2d');
        currentChart = new Chart(ctx, {
            type: 'bar',
            data: {
                labels: ['Total Value', 'Your Price'],
                datasets: [{
                    label: 'Price in ₹',
                    data: [3096, 999],
                    backgroundColor: ['rgba(217, 119, 6, 0.2)', 'rgba(245, 158, 11, 0.8)'],
                    borderColor: ['rgba(217, 119, 6, 1)', 'rgba(245, 158, 11, 1)'],
                    borderWidth: 1
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: { y: { beginAtZero: true } },
                plugins: {
                    legend: { display: false },
                    tooltip: { callbacks: { label: context => `₹${context.raw}` } }
                }
            }
        });
    }

    // --- Accordion for Follow-up Sequence ---
    function setupAccordion() {
        const accordionItems = document.querySelectorAll('.accordion-item');
        accordionItems.forEach(item => {
            const header = item.querySelector('.accordion-header');
            const content = item.querySelector('.accordion-content');
            const icon = item.querySelector('.accordion-icon');
            header.addEventListener('click', () => {
                const isVisible = !content.classList.contains('hidden');
                document.querySelectorAll('.accordion-content').forEach(c => c.classList.add('hidden'));
                document.querySelectorAll('.accordion-icon').forEach(i => i.textContent = '+');
                if (!isVisible) { content.classList.remove('hidden'); icon.textContent = '-'; }
            });
        });
    }

    // --- Navigation Events ---
    navigationContainer.addEventListener('click', (e) => {
        const stepItem = e.target.closest('.step-item');
        if (stepItem) { const index = parseInt(stepItem.dataset.index, 10); renderStep(index); }
    });

    // --- Initial Render ---
    document.addEventListener('DOMContentLoaded', () => {
        renderNavigation();
        renderStep(0);
    });

    </script>
</body>
</html>
