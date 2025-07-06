# Doll-Clothing-Quiz
Quiz for customers
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fashion Doll Clothing Preference Quiz</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #ff6b9d 0%, #c44569 50%, #786fa6 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .quiz-container {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 30px;
            max-width: 650px;
            width: 100%;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .quiz-header {
            text-align: center;
            margin-bottom: 30px;
        }

        .quiz-title {
            color: #333;
            font-size: 2.5em;
            margin-bottom: 10px;
            font-weight: bold;
            background: linear-gradient(45deg, #ff6b9d, #c44569);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .quiz-subtitle {
            color: #666;
            font-size: 1.1em;
            margin-bottom: 20px;
            line-height: 1.4;
        }

        .question-container {
            margin-bottom: 25px;
        }

        .question {
            font-size: 1.2em;
            color: #333;
            margin-bottom: 15px;
            font-weight: 600;
        }

        .options {
            display: grid;
            gap: 12px;
        }

        .option {
            background: linear-gradient(135deg, #ffeef8 0%, #f8f4ff 100%);
            border: 2px solid #e9d5ff;
            border-radius: 15px;
            padding: 18px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
        }

        .option::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
            transition: left 0.5s ease;
        }

        .option:hover::before {
            left: 100%;
        }

        .option:hover {
            background: linear-gradient(135deg, #ff6b9d, #c44569);
            border-color: #ff6b9d;
            transform: translateY(-3px);
            color: white;
            box-shadow: 0 10px 25px rgba(255, 107, 157, 0.3);
        }

        .option input[type="radio"] {
            margin-right: 15px;
            transform: scale(1.3);
            accent-color: #ff6b9d;
        }

        .option.selected {
            background: linear-gradient(135deg, #ff6b9d, #c44569);
            border-color: #ff6b9d;
            color: white;
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(255, 107, 157, 0.4);
        }

        .submit-btn {
            background: linear-gradient(135deg, #ff6b9d 0%, #c44569 50%, #786fa6 100%);
            color: white;
            border: none;
            padding: 18px 45px;
            font-size: 1.2em;
            border-radius: 30px;
            cursor: pointer;
            width: 100%;
            margin-top: 25px;
            transition: all 0.3s ease;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .submit-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 30px rgba(255, 107, 157, 0.4);
        }

        .submit-btn:disabled {
            background: #ccc;
            cursor: not-allowed;
            transform: none;
        }

        .results {
            display: none;
            text-align: center;
            padding: 25px;
            background: linear-gradient(135deg, #ffeef8 0%, #f8f4ff 100%);
            border-radius: 20px;
            margin-top: 25px;
            border: 2px solid #e9d5ff;
        }

        .results h3 {
            color: #333;
            margin-bottom: 20px;
            font-size: 1.6em;
            background: linear-gradient(45deg, #ff6b9d, #c44569);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .result-item {
            background: white;
            padding: 15px;
            margin: 8px 0;
            border-radius: 12px;
            border-left: 5px solid #ff6b9d;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }

        .progress-bar {
            background: rgba(255, 255, 255, 0.3);
            height: 8px;
            border-radius: 4px;
            margin-bottom: 25px;
            overflow: hidden;
            backdrop-filter: blur(5px);
        }

        .progress-fill {
            background: linear-gradient(90deg, #ff6b9d, #c44569);
            height: 100%;
            width: 0%;
            transition: width 0.4s ease;
            border-radius: 4px;
        }

        .question-number {
            color: #ff6b9d;
            font-weight: bold;
            font-size: 0.9em;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
        }

        .question-number::before {
            content: '✨';
            margin-right: 8px;
        }

        .doll-emoji {
            font-size: 1.5em;
            margin: 0 8px;
        }

        @media (max-width: 600px) {
            .quiz-title {
                font-size: 2em;
            }
            
            .quiz-container {
                padding: 20px;
            }
            
            .option {
                padding: 15px;
            }
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <div class="quiz-header">
            <h1 class="quiz-title">Fashion Doll Style Quiz</h1>
            <p class="quiz-subtitle">Help us create the perfect OOAK outfits for your 16" fashion dolls! <span class="doll-emoji">👗</span> Tell us about your style preferences <span class="doll-emoji">💖</span></p>
        </div>

        <div class="progress-bar">
            <div class="progress-fill" id="progressFill"></div>
        </div>

        <form id="quizForm">
            <div class="question-container">
                <div class="question-number">Question 1 of 8</div>
                <div class="question">Which outfit category do you find most appealing for your fashion dolls?</div>
                <div class="options">
                    <label class="option">
                        <input type="radio" name="q1" value="lingerie">
                        💋 Lingerie - Delicate, intimate pieces with lace and silk details
                    </label>
                    <label class="option">
                        <input type="radio" name="q1" value="casual">
                        👕 Casual Modern - Contemporary everyday wear with trendy touches
                    </label>
                    <label class="option">
                        <input type="radio" name="q1" value="classic">
                        👗 Classic Dresses - Timeless, elegant pieces that never go out of style
                    </label>
                    <label class="option">
                        <input type="radio" name="q1" value="evening">
                        ✨ Evening Gowns - Glamorous, formal wear for special occasions
                    </label>
                    <label class="option">
                        <input type="radio" name="q1" value="romantic">
                        🌹 Romantic Outfits - Soft, feminine pieces with vintage charm
                    </label>
                </div>
            </div>

            <div class="question-container">
                <div class="question-number">Question 2 of 8</div>
                <div class="question">What's your preferred color palette for doll clothing?</div>
                <div class="options">
                    <label class="option">
                        <input type="radio" name="q2" value="pastels">
                        🌸 Soft pastels (blush pink, lavender, mint green)
                    </label>
                    <label class="option">
                        <input type="radio" name="q2" value="jewel">
                        💎 Rich jewel tones (emerald, sapphire, ruby)
                    </label>
                    <label class="option">
                        <input type="radio" name="q2" value="neutral">
                        🤍 Neutral elegance (cream, beige, champagne)
                    </label>
                    <label class="option">
                        <input type="radio" name="q2" value="bold">
                        🔥 Bold & vibrant (hot pink, electric blue, sunset orange)
                    </label>
                    <label class="option">
                        <input type="radio" name="q2" value="monochrome">
                        🖤 Classic monochrome (black, white, silver)
                    </label>
                </div>
            </div>

            <div class="question-container">
                <div class="question-number">Question 3 of 8</div>
                <div class="question">What level of detail do you prefer in doll outfits?</div>
                <div class="options">
                    <label class="option">
                        <input type="radio" name="q3" value="minimalist">
                        ✨ Clean & minimalist - Simple elegance with perfect fit
                    </label>
                    <label class="option">
                        <input type="radio" name="q3" value="moderate">
                        💫 Moderate detail - Some embellishments and interesting textures
                    </label>
                    <label class="option">
                        <input type="radio" name="q3" value="elaborate">
                        🎭 Highly detailed - Intricate beading, embroidery, and accessories
                    </label>
                    <label class="option">
                        <input type="radio" name="q3" value="mixed">
                        🌈 It depends on the outfit style and occasion
                    </label>
                </div>
            </div>

            <div class="question-container">
                <div class="question-number">Question 4 of 8</div>
                <div class="question">Which fabric types appeal to you most?</div>
                <div class="options">
                    <label class="option">
                        <input type="radio" name="q4" value="luxurious">
                        💎 Luxurious fabrics (silk, satin, velvet, brocade)
                    </label>
                    <label class="option">
                        <input type="radio" name="q4" value="delicate">
                        🌸 Delicate materials (lace, tulle, chiffon, organza)
                    </label>
                    <label class="option">
                        <input type="radio" name="q4" value="textured">
                        🎨 Textured fabrics (tweed, jacquard, embossed materials)
                    </label>
                    <label class="option">
                        <input type="radio" name="q4" value="contemporary">
                        ✨ Contemporary blends (high-quality synthetics, mixed materials)
                    </label>
                </div>
            </div>

            <div class="question-container">
                <div class="question-number">Question 5 of 8</div>
                <div class="question">How important are matching accessories?</div>
                <div class="options">
                    <label class="option">
                        <input type="radio" name="q5" value="essential">
                        💍 Essential - Complete sets with shoes, jewelry, and bags
                    </label>
                    <label class="option">
                        <input type="radio" name="q5" value="some">
                        👜 Some accessories - A few key pieces to complement the outfit
                    </label>
                    <label class="option">
                        <input type="radio" name="q5" value="minimal">
                        ✨ Minimal accessories - Let the clothing be the star
                    </label>
                    <label class="option">
                        <input type="radio" name="q5" value="flexible">
                        🌟 Flexible - Depends on the outfit and my mood
                    </label>
                </div>
            </div>

            <div class="question-container">
                <div class="question-number">Question 6 of 8</div>
                <div class="question">What's your preferred price range for OOAK doll outfits?</div>
                <div class="options">
                    <label class="option">
                        <input type="radio" name="q6" value="budget">
                        💝 Budget-friendly ($15-30)
                    </label>
                    <label class="option">
                        <input type="radio" name="q6" value="moderate">
                        💖 Moderate range ($30-60)
                    </label>
                    <label class="option">
                        <input type="radio" name="q6" value="premium">
                        💎 Premium quality ($60-100)
                    </label>
                    <label class="option">
                        <input type="radio" name="q6" value="collector">
                        👑 Collector's piece ($100+)
                    </label>
                </div>
            </div>

            <div class="question-container">
                <div class="question-number">Question 7 of 8</div>
                <div class="question">Which era or style inspiration appeals to you most?</div>
                <div class="options">
                    <label class="option">
                        <input type="radio" name="q7" value="vintage">
                        🌹 Vintage inspired (1920s-1960s glamour)
                    </label>
                    <label class="option">
                        <input type="radio" name="q7" value="modern">
                        🏙️ Contemporary modern (current fashion trends)
                    </label>
                    <label class="option">
                        <input type="radio" name="q7" value="fantasy">
                        🦄 Fantasy & fairytale (magical, whimsical designs)
                    </label>
                    <label class="option">
                        <input type="radio" name="q7" value="timeless">
                        ⚡ Timeless elegance (classic styles that transcend eras)
                    </label>
                </div>
            </div>

            <div class="question-container">
                <div class="question-number">Question 8 of 8</div>
                <div class="question">How often do you purchase outfits for your fashion dolls?</div>
                <div class="options">
                    <label class="option">
                        <input type="radio" name="q8" value="monthly">
                        📅 Monthly - I love updating their wardrobe regularly
                    </label>
                    <label class="option">
                        <input type="radio" name="q8" value="seasonal">
                        🌸 Seasonally - A few times a year for special occasions
                    </label>
                    <label class="option">
                        <input type="radio" name="q8" value="special">
                        ✨ For special pieces - When I find something truly unique
                    </label>
                    <label class="option">
                        <input type="radio" name="q8" value="collector">
                        💎 Collector mindset - Quality over quantity, rare purchases
                    </label>
                </div>
            </div>

            <button type="submit" class="submit-btn" id="submitBtn" disabled>✨ Complete Quiz ✨</button>
        </form>

        <div class="results" id="results">
            <h3>🎉 Thank you for sharing your style preferences!</h3>
            <p>Your responses help me create the perfect OOAK outfits for your fashion dolls. Here's your style profile:</p>
            <div id="resultsSummary"></div>
            <p style="margin-top: 20px; font-size: 0.9em; color: #666;">
                💝 Your preferences are noted and will inspire future creations! Keep an eye on my eBay listings for pieces that match your style. 👗✨
            </p>
        </div>
    </div>

    <script>
        // Store quiz responses
        let quizResponses = {};
        
        // Update progress bar
        function updateProgress() {
            const totalQuestions = 8;
            const answeredQuestions = Object.keys(quizResponses).length;
            const progress = (answeredQuestions / totalQuestions) * 100;
            document.getElementById('progressFill').style.width = progress + '%';
        }

        // Handle radio button changes
        document.querySelectorAll('input[type="radio"]').forEach(radio => {
            radio.addEventListener('change', function() {
                // Remove selected class from all options in this question
                const questionName = this.name;
                document.querySelectorAll(`input[name="${questionName}"]`).forEach(r => {
                    r.closest('.option').classList.remove('selected');
                });
                
                // Add selected class to chosen option
                this.closest('.option').classList.add('selected');
                
                // Store response
                quizResponses[questionName] = this.value;
                
                // Update progress
                updateProgress();
                
                // Enable submit button when all questions are answered
                if (Object.keys(quizResponses).length === 8) {
                    document.getElementById('submitBtn').disabled = false;
                }
            });
        });

        // Handle form submission
        document.getElementById('quizForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Create results summary
            const resultsSummary = document.getElementById('resultsSummary');
            resultsSummary.innerHTML = '';
            
            const labels = {
                q1: 'Preferred Category',
                q2: 'Color Palette',
                q3: 'Detail Level',
                q4: 'Fabric Preference',
                q5: 'Accessories',
                q6: 'Price Range',
                q7: 'Style Inspiration',
                q8: 'Purchase Frequency'
            };
            
            const valueLabels = {
                lingerie: 'Lingerie & Intimate Wear',
                casual: 'Casual Modern Outfits',
                classic: 'Classic Dresses',
                evening: 'Evening Gowns',
                romantic: 'Romantic Outfits',
                pastels: 'Soft Pastels',
                jewel: 'Rich Jewel Tones',
                neutral: 'Neutral Elegance',
                bold: 'Bold & Vibrant',
                monochrome: 'Classic Monochrome',
                minimalist: 'Clean & Minimalist',
                moderate: 'Moderate Detail',
                elaborate: 'Highly Detailed',
                mixed: 'Depends on Style',
                luxurious: 'Luxurious Fabrics',
                delicate: 'Delicate Materials',
                textured: 'Textured Fabrics',
                contemporary: 'Contemporary Blends',
                essential: 'Complete Sets Essential',
                some: 'Some Key Accessories',
                minimal: 'Minimal Accessories',
                flexible: 'Depends on Outfit',
                budget: 'Budget-Friendly ($15-30)',
                premium: 'Premium Quality ($60-100)',
                collector: 'Collector\'s Piece ($100+)',
                vintage: 'Vintage Inspired',
                modern: 'Contemporary Modern',
                fantasy: 'Fantasy & Fairytale',
                timeless: 'Timeless Elegance',
                monthly: 'Monthly Purchases',
                seasonal: 'Seasonal Purchases',
                special: 'Special Pieces Only',
            };
            
            for (const [question, answer] of Object.entries(quizResponses)) {
                const resultItem = document.createElement('div');
                resultItem.className = 'result-item';
                resultItem.innerHTML = `<strong>${labels[question]}:</strong> ${valueLabels[answer] || answer}`;
                resultsSummary.appendChild(resultItem);
            }
            
            // Show results
            document.getElementById('quizForm').style.display = 'none';
            document.getElementById('results').style.display = 'block';
            
            // Log results for the seller
            console.log('Fashion Doll Clothing Quiz Results:', quizResponses);
            
            // Create detailed summary for seller analysis
            const timestamp = new Date().toISOString();
            const detailedResults = {
                timestamp: timestamp,
                responses: quizResponses,
                summary: {
                    preferredCategory: valueLabels[quizResponses.q1],
                    colorPalette: valueLabels[quizResponses.q2],
                    detailLevel: valueLabels[quizResponses.q3],
                    fabricPreference: valueLabels[quizResponses.q4],
                    accessoryImportance: valueLabels[quizResponses.q5],
                    priceRange: valueLabels[quizResponses.q6],
                    styleInspiration: valueLabels[quizResponses.q7],
                    purchaseFrequency: valueLabels[quizResponses.q8]
                }
            };
            
            console.log('Detailed Analysis:', detailedResults);
            
            // Send results to Google Sheets
            sendToGoogleSheets(detailedResults);
            
            // Also store locally as backup
            const existingData = JSON.parse(localStorage.getItem('dollClothingQuizResults') || '[]');
            existingData.push(detailedResults);
            localStorage.setItem('dollClothingQuizResults', JSON.stringify(existingData));
        });

        // Function to send data to Google Sheets
        function sendToGoogleSheets(data) {
            // Replace with your Google Apps Script URL
            const GOOGLE_SCRIPT_URL = 'YOUR_GOOGLE_SCRIPT_URL_HERE';
            
            fetch(GOOGLE_SCRIPT_URL, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(data)
            })
            .then(response => response.json())
            .then(result => {
                console.log('Data sent to Google Sheets:', result);
            })
            .catch(error => {
                console.error('Error sending to Google Sheets:', error);
                // Fallback to local storage if Google Sheets fails
                console.log('Saved locally as backup');
            });
        }

        // Initialize
        updateProgress();
    </script>
</body>
</html>
