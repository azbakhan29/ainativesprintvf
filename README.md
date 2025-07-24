<!DOCTYPE html>
<html lang="en">
<head>
    <!-- Chosen Palette: Vibrant Professional (Light Cream, Deep Blue, Teal, Yellow, Coral) -->
    <!-- 
        Application Structure Plan: 
        The SPA is structured as a top-to-bottom narrative telling the story of the AI-Native Sprint.
        1.  Hero Section: A bold title and subtitle to introduce the topic and hook the user.
        2.  The Journey: A 3-step visual process flow (built with HTML/CSS) to explain the sprint's methodology (Discovery -> Theorizing -> The Pivot). This makes the process easy to follow.
        3.  The "AI Bell Curve": A dedicated section with a Chart.js line chart to visualize the key finding about AI productivity. This isolates the most important learning for maximum impact.
        4.  Key Reflections: A responsive grid of cards, each representing one of the five main learnings. This breaks down complex insights into digestible, visually separated chunks.
        5.  Situational Awareness Gap: A new section detailing AI's limitations in perception, comprehension, and projection, with interactive collapsible content for each level. This provides deeper insight into AI's cognitive shortcomings.
        6.  The Playbook: A tabbed interface presenting the actionable playbook for UXers, allowing users to switch between phases without extensive scrolling.
        This thematic, narrative structure was chosen over a direct report-to-page mapping because it guides the user through a story of discovery, challenge, and resolution, which is more engaging and improves comprehension and retention of the key takeaways.
    -->
    <!-- 
        Visualization & Content Choices:
        -   Sprint Journey: (Goal: Organize/Change) -> A styled HTML/CSS flexbox diagram was chosen to represent the process flow. This method is lightweight, fully responsive, and avoids the use of prohibited SVG or Mermaid JS, while clearly showing the progression of the sprint.
        -   AI Productivity: (Goal: Change) -> A Chart.js Line Chart is used to create the "AI Bell Curve." A line chart is the ideal visualization to show a trend or change over distinct phases, perfectly capturing the rise and fall of productivity described in the report. It is rendered on a Canvas, adhering to requirements.
        -   Situational Awareness Gap: (Goal: Inform/Organize) -> Structured HTML/CSS with Tailwind for a multi-level section. Each level (Perception, Comprehension, Projection) is presented as an. interactive, collapsible block (using JS for show/hide) to explain AI's capabilities at each cognitive level. This makes a nuanced concept explorable.
        -   Key Reflections: (Goal: Inform/Organize) -> A grid of cards with Unicode icons. This presentation method breaks down the five key learnings into manageable pieces. The card format gives each point its own space, and the icons add visual interest without using image files or SVG. Each reflection card also includes an "Explain More" button powered by the Gemini API to provide dynamic, detailed explanations.
        -   The Playbook: (Goal: Organize) -> A tabbed interface using HTML/CSS/JS. Each tab represents a phase, and its content uses concise bullet points. This significantly reduces vertical scroll and provides an intuitive navigation for the multi-phase playbook, avoiding the "long scroll" issue while retaining all content.
        All visualizations are accompanied by descriptive text to provide context and and explain the key message, ensuring the infographic is not just a collection of data points but a coherent story.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Learnings from an AI-Native Sprint | An Interactive Infographic</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;900&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F8F7F4;
            color: #1a202c;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            height: 350px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 400px;
            }
        }
        .flow-arrow {
            color: #D1D5DB;
            font-size: 2.5rem;
            line-height: 1;
        }
        .card-icon {
            font-size: 2.5rem;
            line-height: 1;
            width: 4rem;
            height: 4rem;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 0.5rem;
        }
        .collapsible-header {
            cursor: pointer;
            padding: 1rem;
            background-color: #E2E8F0;
            border-radius: 0.5rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: background-color 0.3s ease;
        }
        .collapsible-header:hover {
            background-color: #CBD5E0;
        }
        .collapsible-content {
            padding: 1rem;
            border-left: 2px solid #CBD5E0;
            margin-left: 0.5rem;
            margin-top: 0.5rem;
        }
        .collapsible-arrow {
            transition: transform 0.3s ease;
        }
        .collapsible-header[aria-expanded="true"] .collapsible-arrow {
            transform: rotate(90deg);
        }
        .tab-button.active {
            border-bottom: 3px solid #087E8B;
            color: #087E8B;
        }
    </style>
</head>
<body class="antialiased">

    <div class="container mx-auto p-4 md:p-8">

        <header class="text-center my-12 md:my-20">
            <h1 class="text-4xl md:text-6xl font-black text-gray-900 leading-tight">Learnings from an <span class="text-[#087E8B]">AI-Native Sprint</span></h1>
            <p class="mt-4 text-lg md:text-xl text-gray-600 max-w-3xl mx-auto">An interactive report on our experiment to challenge traditional problem-solving by building with AI at the core.</p>
        </header>

        <main>
            <section id="journey" class="mb-16 md:mb-24">
                <h2 class="text-3xl md:text-4xl font-bold text-center mb-4 text-gray-900">The Sprint Journey</h2>
                <p class="text-center text-gray-600 max-w-2xl mx-auto mb-12">Our two-week sprint followed a "try-fail-try-scale" framework, leading to a critical pivot in our approach.</p>
                <div class="flex flex-col md:flex-row justify-center items-center text-center gap-4 md:gap-8">

                    <div class="w-full md:w-1/3">
                        <div class="bg-white rounded-lg p-6 shadow-md h-full">
                            <div class="text-sm font-bold text-[#087E8B]">PHASE 1</div>
                            <h3 class="text-xl font-bold text-gray-900 mt-1">Deep Dive Discovery</h3>
                            <p class="mt-2 text-gray-600 text-sm">We began with extensive user shadowing and process overviews, using NotebookLM to capture and map our initial findings from AV technicians.</p>
                        </div>
                    </div>

                    <div class="flow-arrow my-4 md:my-0">&rarr;</div>

                    <div class="w-full md:w-1/3">
                        <div class="bg-white rounded-lg p-6 shadow-md h-full">
                            <div class="text-sm font-bold text-[#FF5A5F]">PHASE 2</div>
                            <h3 class="text-xl font-bold text-gray-900 mt-1">Preparing & Theorizing</h3>
                            <p class="mt-2 text-gray-600 text-sm">We applied JTBD & 5 Whys frameworks, using a custom "JTBD Expert" Gemini agent for AI-powered brainstorming and opportunity generation.</p>
                        </div>
                    </div>

                     <div class="flow-arrow my-4 md:my-0">&rarr;</div>
                    
                    <div class="w-full md:w-1/3">
                         <div class="bg-[#3C3C3C] text-white rounded-lg p-6 shadow-lg h-full">
                            <div class="text-sm font-bold text-[#F7B801]">THE PIVOT</div>
                            <h3 class="text-xl font-bold text-white mt-1">Human-Led Refinement</h3>
                            <p class="mt-2 text-gray-300 text-sm">AI's generic outputs led to a crucial shift: we reverted to human-led analysis with AI for recall, not primary generation.</p>
                        </div>
                    </div>
                </div>
            </section>
            
            <section id="bell-curve" class="mb-16 md:mb-24 bg-white rounded-lg p-6 md:p-8 shadow-md">
                <h2 class="text-3xl md:text-4xl font-bold text-center mb-4 text-gray-900">The "AI Bell Curve" of Productivity</h2>
                <p class="text-center text-gray-600 max-w-2xl mx-auto mb-8">A key learning was observing a distinct pattern in AI's utility. It provides incredible initial acceleration, but its effectiveness can peak and then decelerate without deep human collaboration to guide it.</p>
                <div class="chart-container">
                    <canvas id="bellCurveChart"></canvas>
                </div>
            </section>

            <section id="learnings" class="mb-16 md:mb-24">
                <h2 class="text-3xl md:text-4xl font-bold text-center mb-12 text-gray-900">Our Top 5 Reflections</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    
                    <div class="bg-white rounded-lg p-6 shadow-md flex flex-col items-start gap-4">
                        <div class="flex items-start gap-4 w-full">
                            <div class="card-icon bg-[#087E8B] bg-opacity-10 text-[#087E8B]">📈</div>
                            <div>
                                <h3 class="text-xl font-bold mb-2">The "AI Bell Curve" of Productivity</h3>
                                <p class="text-gray-600" id="reflection1-text">AI provides initial acceleration but then decelerates, with repetitive outputs requiring human effort. It excels at pattern recognition but struggles with deep context and novel insights.</p>
                            </div>
                        </div>
                        <button class="mt-4 px-4 py-2 bg-[#087E8B] text-white rounded-md hover:bg-[#065F6B] focus:outline-none focus:ring-2 focus:ring-[#087E8B] focus:ring-opacity-50 transition-colors duration-200 text-sm self-end" onclick="toggleExplanation(this, 'reflection1-text', 'explanation1-content')">✨ Explain More</button>
                        <div id="explanation1-content" class="mt-4 text-gray-700 hidden"></div>
                    </div>

                    <div class="bg-white rounded-lg p-6 shadow-md flex flex-col items-start gap-4">
                        <div class="flex items-start gap-4 w-full">
                            <div class="card-icon bg-[#087E8B] bg-opacity-10 text-[#087E8B]">🎭</div>
                            <div>
                                <h3 class="text-xl font-bold mb-2">The New Face of Bias</h3>
                                <p class="text-gray-600" id="reflection2-text">Human bias in input data translates into "Gem bias" in AI outputs. Curating diverse, contextualized input is crucial for objective results reflecting its training.</p>
                            </div>
                        </div>
                        <button class="mt-4 px-4 py-2 bg-[#087E8B] text-white rounded-md hover:bg-[#065F6B] focus:outline-none focus:ring-2 focus:ring-[#087E8B] focus:ring-opacity-50 transition-colors duration-200 text-sm self-end" onclick="toggleExplanation(this, 'reflection2-text', 'explanation2-content')">✨ Explain More</button>
                        <div id="explanation2-content" class="mt-4 text-gray-700 hidden"></div>
                    </div>

                    <div class="bg-white rounded-lg p-6 shadow-md flex flex-col items-start gap-4">
                        <div class="flex items-start gap-4 w-full">
                            <div class="card-icon bg-[#087E8B] bg-opacity-10 text-[#087E8B]">🔄</div>
                            <div>
                                <h3 class="text-xl font-bold mb-2">UX Redefined: Beyond Visuals and the Prompt Loop</h3>
                                <p class="text-gray-600" id="reflection3-text">The "prompt and answer loop" is a time sink. New UX paradigms are needed for human-AI collaboration that move beyond text queries to intuitive, visually rich engagement.</p>
                            </div>
                        </div>
                        <button class="mt-4 px-4 py-2 bg-[#087E8B] text-white rounded-md hover:bg-[#065F6B] focus:outline-none focus:ring-2 focus:ring-[#087E8B] focus:ring-opacity-50 transition-colors duration-200 text-sm self-end" onclick="toggleExplanation(this, 'reflection3-text', 'explanation3-content')">✨ Explain More</button>
                        <div id="explanation3-content" class="mt-4 text-gray-700 hidden"></div>
                    </div>
                    
                    <div class="bg-white rounded-lg p-6 shadow-md flex flex-col items-start gap-4">
                        <div class="flex items-start gap-4 w-full">
                            <div class="card-icon bg-[#087E8B] bg-opacity-10 text-[#087E8B]">🧠</div>
                            <div>
                                <h3 class="text-xl font-bold mb-2">The Indispensability of Human Intuition and Context</h3>
                                <p class="text-gray-600" id="reflection4-text">AI doesn't replace deep qualitative analysis and human intuition. Human-led exercises lead to grounded, actionable insights unparalleled by autonomous AI generation.</p>
                            </div>
                        </div>
                        <button class="mt-4 px-4 py-2 bg-[#087E8B] text-white rounded-md hover:bg-[#065F6B] focus:outline-none focus:ring-2 focus:ring-[#087E8B] focus:ring-opacity-50 transition-colors duration-200 text-sm self-end" onclick="toggleExplanation(this, 'reflection4-text', 'explanation4-content')">✨ Explain More</button>
                        <div id="explanation4-content" class="mt-4 text-gray-700 hidden"></div>
                    </div>
                    
                    <div class="bg-white rounded-lg p-6 shadow-md flex flex-col items-start gap-4 md:col-span-2">
                        <div class="flex items-start gap-4 w-full">
                            <div class="card-icon bg-[#FF5A5F] bg-opacity-10 text-[#FF5A5F]">🤝</div>
                            <div>
                                <h3 class="text-xl font-bold mb-2">Multidisciplinary Alignment is Key</h3>
                                <p class="text-gray-600" id="reflection5-text">Generic AI ideas can disengage teams. Human-led, collaborative ideation is vital for grounding ideas, achieving alignment, and identifying concrete, testable solutions across disciplines.</p>
                            </div>
                        </div>
                        <button class="mt-4 px-4 py-2 bg-[#087E8B] text-white rounded-md hover:bg-[#065F6B] focus:outline-none focus:ring-2 focus:ring-[#087E8B] focus:ring-opacity-50 transition-colors duration-200 text-sm self-end" onclick="toggleExplanation(this, 'reflection5-text', 'explanation5-content')">✨ Explain More</button>
                        <div id="explanation5-content" class="mt-4 text-gray-700 hidden"></div>
                    </div>

                </div>
            </section>

            <section id="situational-awareness" class="mb-16 md:mb-24 bg-white rounded-lg p-6 md:p-8 shadow-md">
                <h2 class="text-3xl md:text-4xl font-bold text-center mb-4 text-gray-900">A Key Limitation: AI's Situational Awareness Gap</h2>
                <p class="text-center text-gray-600 max-w-3xl mx-auto mb-8">A significant challenge identified was the AI's limited situational awareness. While AI excels at perception, it struggles with higher-order cognitive functions essential for true problem-solving. Interact with the levels below to learn more.</p>
                
                <div class="space-y-4 max-w-2xl mx-auto">
                    <!-- Level 1 Perception -->
                    <div class="border border-gray-200 rounded-lg">
                        <div class="collapsible-header font-bold text-gray-800" onclick="toggleCollapsible(this)" aria-expanded="false">
                            <span>Level 1: Perception - AI's Strength</span>
                            <span class="collapsible-arrow">&#9654;</span>
                        </div>
                        <div class="collapsible-content hidden">
                            <p class="text-gray-700">AI tools are excellent at taking raw inputs (transcripts, documents) and identifying discrete pieces of information. They "see" the data.</p>
                        </div>
                    </div>

                    <!-- Level 2 Comprehension -->
                    <div class="border border-gray-200 rounded-lg">
                        <div class="collapsible-header font-bold text-gray-800" onclick="toggleCollapsible(this)" aria-expanded="false">
                            <span>Level 2: Comprehension - Partial Strength</span>
                            <span class="collapsible-arrow">&#9654;</span>
                        </div>
                        <div class="collapsible-content hidden">
                            <p class="text-gray-700">AI can connect related pieces of information and summarize themes. However, it often missed implicit meaning, nuances, and the subtle "why" or "how" that human experience translates. It understands the "what," less of the "so what?"</p>
                        </div>
                    </div>

                    <!-- Level 3 Projection -->
                    <div class="border border-gray-200 rounded-lg">
                        <div class="collapsible-header font-bold text-gray-800" onclick="toggleCollapsible(this)" aria-expanded="false">
                            <span>Level 3: Projection - AI's Shortcoming</span>
                            <span class="collapsible-arrow">&#9654;</span>
                        </div>
                        <div class="collapsible-content hidden">
                            <p class="text-gray-700">This is where AI significantly lags. It struggles to anticipate future states, consequences, or potential issues based on incomplete knowledge. It lacks the ability to read between the lines, which is crucial for identifying truly transformative opportunities.</p>
                        </div>
                    </div>
                </div>
            </section>

            <section id="playbook" class="mb-16 md:mb-24 bg-white rounded-lg p-6 md:p-8 shadow-md">
                <h2 class="text-3xl md:text-4xl font-bold text-center mb-4 text-gray-900">The AI-Native Sprint Playbook for UXers</h2>
                <p class="text-center text-gray-600 max-w-3xl mx-auto mb-12">Based on my Sprint 0 experience, here's an actionable playbook for any UXer embarking on an AI-Native Sprint:</p>
                
                <div class="flex border-b border-gray-200 mb-4">
                    <button class="tab-button py-2 px-4 text-lg font-semibold text-gray-600 hover:text-[#087E8B] active" onclick="openTab(event, 'tab1')">Phase 1: Grounding the AI</button>
                    <button class="tab-button py-2 px-4 text-lg font-semibold text-gray-600 hover:text-[#FF5A5F]" onclick="openTab(event, 'tab2')">Phase 2: Ideation</button>
                    <button class="tab-button py-2 px-4 text-lg font-semibold text-gray-600 hover:text-[#F7B801]" onclick="openTab(event, 'tab3')">Phase 3: Actionable Outcomes</button>
                </div>

                <div id="tab1" class="tab-content active-tab">
                    <h3 class="text-xl font-bold text-[#087E8B] mb-4">Phase 1: Grounding the AI - Human-First Contextualization</h3>
                    <ul class="space-y-3 text-gray-600 list-disc pl-5">
                        <li>
                            <strong>Immerse, Observe, Document (The Human Way):</strong>
                            <ul class="list-disc pl-5 mt-2 space-y-1">
                                <li><strong>Direct Observation is Non-Negotiable:</strong> Prioritize shadowing and direct user observation over relying solely on interviews or secondary data. Capture raw, unstructured data (verbatim notes, photos, process flows) to build your <strong>implicit knowledge</strong> of the problem space.</li>
                                <li><strong>Structure Your Raw Data:</strong> Even before AI, apply basic thematic tagging or categorization to your raw notes. This helps organize your initial human understanding and prepares the data for AI ingestion.</li>
                            </ul>
                        </li>
                        <li class="mt-4">
                            <strong>Onboard AI with Contextual Depth:</strong>
                            <ul class="list-disc pl-5 mt-2 space-y-1">
                                <li><strong>Curate Input Data Thoughtfully:</strong> When feeding data to AI, selectively upload rich, diverse sources (direct quotes, detailed field notes, audio/video transcripts if privacy allows). The more nuanced the input, the better the output.</li>
                                <li><strong>Train AI with Frameworks:</strong> Use AI companions (expert Gems) to quickly internalize methodologies. Feed them foundational documents and instruct them to act as experts.</li>
                                <li><strong>Specify Output Depth:</strong> When prompting for analysis (pain points, opportunities), explicitly ask for <em>specific</em>, <em>detailed</em>, and <em>grounded</em> outputs. Avoid generic prompts.</li>
                            </ul>
                        </li>
                    </ul>
                </div>

                <div id="tab2" class="tab-content hidden">
                    <h3 class="text-xl font-bold text-[#FF5A5F] mb-4">Phase 2: Ideation - Human-AI Collaborative Native</h3>
                    <ul class="space-y-3 text-gray-600 list-disc pl-5">
                        <li>
                            <strong>Leverage AI for Recall and Expansion, Not Sole Generation:</strong>
                            <ul class="list-disc pl-5 mt-2 space-y-1">
                                <li><strong>AI as a Memory Aid:</strong> Use AI (NotebookLM) to quickly recall specific details, quotes, or process steps from your vast pool of discovery data.</li>
                                <li><strong>AI for Divergent Thinking:</strong> Once your human team defines core problems, use AI to brainstorm <em>variations</em> and <em>expansions</em> of ideas.</li>
                                <li><strong>Negative Prompting & Constraints:</strong> Guide AI creativity by explicitly stating what *not* to suggest, or by adding specific constraints.</li>
                            </ul>
                        </li>
                        <li class="mt-4">
                            <strong>Embrace Human-Led Synthesis & Prioritization:</strong>
                            <ul class="list-disc pl-5 mt-2 space-y-1">
                                <li><strong>Conduct Core Analysis as a Team:</strong> Facilitate frameworks like JTBD or 5 Whys with the entire multidisciplinary team using human whiteboard collaboration.</li>
                                <li><strong>Human Checkpoints:</strong> Schedule dedicated collaborative sessions to review AI-generated outputs, filter generics, apply human context, and refine insights.</li>
                                <li><strong>Feasibility-Driven Filtering:</strong> Actively involve engineers early to evaluate opportunities for feasibility and ROI, pruning futuristic or impractical AI suggestions.</li>
                            </ul>
                        </li>
                    </ul>
                </div>
                
                <div id="tab3" class="tab-content hidden">
                    <h3 class="text-xl font-bold text-[#F7B801] mb-4">Phase 3: Actionable Outcomes</h3>
                    <ul class="space-y-3 text-gray-600 list-disc pl-5">
                        <li>
                            <strong>Prioritize "Grounded" Opportunities:</strong>
                            <ul class="list-disc pl-5 mt-2 space-y-1">
                                <li><strong>Link to Measurable Outcomes:</strong> Ensure selected opportunities have a clear, measurable outcome (e.g., reduces time spent searching for tools by 20%).</li>
                                <li><strong>Prepare for MVT & Iteration:</strong> Develop Minimum Viable Tests (MVTs) that validate the AI's accuracy and impact (e.g., classifying tickets vs. technician responses).</li>
                            </ul>
                        </li>
                    </ul>
                </div>
            </section>
            
            <footer class="text-center my-16 md:my-24 border-t pt-8">
                <p class="text-lg text-gray-600 max-w-3xl mx-auto">The key takeaway is that the future is a <strong>symbiotic human-AI collaboration</strong>, using AI's strengths to augment our own intuition and problem-solving capabilities.</p>
                <p class="text-sm text-gray-500 mt-4">Learnings presented by azbak@. To <a href="https://docs.google.com/document/d/1HBflOJSRsXLVLurOQ4Ztabu_YkLaCK_coQBM8YaW3lc/edit?tab=t.0" target="_blank" class="text-[#087E8B] hover:underline font-semibold">click here to read a detailed document</a>.</p>
            </footer>

        </main>
    </div>

    <script>
        function wrapText(text, maxLength) {
            if (typeof text !== 'string' || text.length <= maxLength) {
                return text;
            }
            const words = text.split(' ');
            const lines = [];
            let currentLine = '';
            words.forEach(word => {
                if ((currentLine + ' ' + word).trim().length > maxLength && currentLine.length > 0) {
                    lines.push(currentLine.trim());
                    currentLine = word;
                } else {
                    currentLine += (currentLine ? ' ' : '') + word;
                }
            });
            if (currentLine) {
                lines.push(currentLine.trim());
            }
            return lines;
        }

        const bellCurveCtx = document.getElementById('bellCurveChart').getContext('2d');
        const bellCurveChart = new Chart(bellCurveCtx, {
            type: 'line',
            data: {
                labels: ['Initial Acceleration', 'Peak AI Utility', 'Deceleration & Repetition', 'Human-Led Refinement'],
                datasets: [{
                    label: 'Team Productivity & Momentum',
                    data: [20, 85, 50, 75], 
                    backgroundColor: 'rgba(8, 126, 139, 0.1)',
                    borderColor: '#087E8B',
                    tension: 0.4,
                    fill: true,
                    pointBackgroundColor: '#087E8B',
                    pointRadius: 5,
                    pointHoverRadius: 8
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    y: {
                        beginAtZero: true,
                        grid: {
                            color: 'rgba(0, 0, 0, 0.05)'
                        },
                        ticks: {
                            color: '#4A5568'
                        }
                    },
                    x: {
                        grid: {
                           display: false
                        },
                        ticks: {
                            color: '#4A5568',
                            callback: function(value, index, values) {
                                const label = this.getLabelForValue(value);
                                return wrapText(label, 16);
                            }
                        }
                    }
                },
                plugins: {
                    legend: {
                        display: false
                    },
                    tooltip: {
                        backgroundColor: '#ffffff',
                        titleColor: '#1a202c',
                        bodyColor: '#4A5568',
                        borderColor: '#E2E8F0',
                        borderWidth: 1,
                        callbacks: {
                            title: function(tooltipItems) {
                                const item = tooltipItems[0];
                                let label = item.chart.data.labels[item.dataIndex];
                                if (Array.isArray(label)) {
                                  return label.join(' ');
                                }
                                return label;
                            }
                        }
                    }
                }
            }
        });

        const API_KEY = ""; // Keep this empty, Canvas will provide it at runtime

        async function callGeminiAPI(prompt) {
            const model = 'gemini-2.5-flash-preview-05-20';
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/${model}:generateContent?key=${API_KEY}`;
            const chatHistory = [{ role: "user", parts: [{ text: prompt }] }];
            const payload = { contents: chatHistory };

            for (let i = 0; i < 3; i++) { // Retry up to 3 times
                try {
                    const response = await fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    const result = await response.json();
                    if (result.candidates && result.candidates.length > 0 &&
                        result.candidates[0].content && result.candidates[0].content.parts &&
                        result.candidates[0].content.parts.length > 0) {
                        return result.candidates[0].content.parts[0].text;
                    } else {
                        console.error("Unexpected API response structure:", result);
                        return "Error: Could not get a response from the AI.";
                    }
                } catch (error) {
                    console.error(`Attempt ${i + 1} failed:`, error);
                    if (i < 2) { // Not the last attempt, so wait and retry
                        await new Promise(res => setTimeout(res, Math.pow(2, i) * 1000)); // Exponential backoff
                    }
                }
            }
            return "Error: Failed to get a response after multiple attempts.";
        }

        async function toggleExplanation(button, textId, contentId) {
            const textElement = document.getElementById(textId);
            const contentElement = document.getElementById(contentId);

            if (contentElement.classList.contains('hidden')) {
                button.textContent = 'Generating...';
                button.disabled = true;
                const prompt = `Provide a short and concise explanation for: '${textElement.textContent.trim()}'.`;
                const explanation = await callGeminiAPI(prompt);
                contentElement.innerHTML = explanation;
                contentElement.classList.remove('hidden');
                button.textContent = 'Hide Explanation';
            } else {
                contentElement.classList.add('hidden');
                contentElement.innerHTML = ''; // Clear content when hidden
                button.textContent = '✨ Explain More';
            }
            button.disabled = false;
        }

        function toggleCollapsible(header) {
            const content = header.nextElementSibling;
            const isExpanded = header.getAttribute('aria-expanded') === 'true';

            if (isExpanded) {
                content.classList.add('hidden');
                header.setAttribute('aria-expanded', 'false');
            } else {
                content.classList.remove('hidden');
                header.setAttribute('aria-expanded', 'true');
            }
        }

        function openTab(event, tabId) {
            let i, tabContent, tabButtons;

            tabContent = document.getElementsByClassName("tab-content");
            for (i = 0; i < tabContent.length; i++) {
                tabContent[i].classList.add("hidden");
            }

            tabButtons = document.getElementsByClassName("tab-button");
            for (i = 0; i < tabButtons.length; i++) {
                tabButtons[i].classList.remove("active");
                tabButtons[i].classList.remove("border-b-3", "border-[#087E8B]", "text-[#087E8B]");
            }

            document.getElementById(tabId).classList.remove("hidden");
            event.currentTarget.classList.add("active", "border-b-3", "border-[#087E8B]", "text-[#087E8B]");
        }

        document.addEventListener('DOMContentLoaded', () => {
            // Set the first tab as active by default on load
            const firstTabButton = document.querySelector('.tab-button');
            if (firstTabButton) {
                firstTabButton.click();
            }
        });
    </script>
</body>
</html>
```
