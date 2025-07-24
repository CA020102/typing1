<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Luyện gõ 10 ngón - Tùy chọn văn bản</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            max-width: 1000px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f5f5f5;
            text-align: center;
        }
        h1 {
            color: #2c3e50;
            margin-bottom: 10px;
        }
        .subtitle {
            color: #7f8c8d;
            margin-bottom: 20px;
        }
        .container {
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }
        #text-display {
            font-size: 22px;
            margin: 20px 0;
            padding: 20px;
            background: #f9f9f9;
            border-radius: 5px;
            min-height: 150px;
            text-align: left;
            line-height: 1.6;
        }
        #input-field {
            width: 100%;
            padding: 15px;
            font-size: 18px;
            border: 2px solid #ddd;
            border-radius: 5px;
            margin-bottom: 20px;
        }
        #custom-text {
            width: 100%;
            padding: 15px;
            font-size: 16px;
            border: 2px solid #ddd;
            border-radius: 5px;
            margin-bottom: 15px;
            min-height: 100px;
            font-family: inherit;
        }
        .stats {
            display: flex;
            justify-content: space-around;
            margin-bottom: 25px;
            flex-wrap: wrap;
        }
        .stat-box {
            background: #3498db;
            color: white;
            padding: 12px 15px;
            border-radius: 5px;
            min-width: 120px;
            margin: 5px;
            flex-grow: 1;
        }
        .stat-box.score {
            background: #e74c3c;
            font-weight: bold;
        }
        .highlight {
            background-color: #fffde7;
            border-bottom: 2px solid #ffc107;
        }
        .correct {
            color: #27ae60;
        }
        .incorrect {
            color: #e74c3c;
            text-decoration: underline;
        }
        .buttons {
            margin: 20px 0;
        }
        button {
            background: #2ecc71;
            color: white;
            border: none;
            padding: 12px 25px;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
            margin: 8px;
            transition: all 0.3s;
        }
        button:hover {
            background: #27ae60;
            transform: translateY(-2px);
        }
        button:disabled {
            background: #95a5a6;
            cursor: not-allowed;
            transform: none;
        }
        .difficulty {
            margin: 15px 0;
        }
        .difficulty button {
            padding: 8px 15px;
            background: #3498db;
        }
        .difficulty button.active {
            background: #2980b9;
            font-weight: bold;
        }
        .tab-container {
            margin-bottom: 20px;
        }
        .tab-buttons {
            display: flex;
            justify-content: center;
            margin-bottom: 15px;
        }
        .tab-button {
            padding: 10px 20px;
            background: #ecf0f1;
            border: none;
            cursor: pointer;
            font-size: 16px;
            transition: all 0.3s;
        }
        .tab-button:first-child {
            border-radius: 5px 0 0 5px;
        }
        .tab-button:last-child {
            border-radius: 0 5px 5px 0;
        }
        .tab-button.active {
            background: #3498db;
            color: white;
        }
        .tab-content {
            display: none;
        }
        .tab-content.active {
            display: block;
        }
        .custom-text-container {
            text-align: left;
            margin-bottom: 20px;
        }
        .history-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        .history-title {
            color: #2c3e50;
            margin-top: 0;
            text-align: left;
            border-bottom: 2px solid #eee;
            padding-bottom: 10px;
        }
        .history-item {
            display: flex;
            justify-content: space-between;
            padding: 10px;
            border-bottom: 1px solid #eee;
            text-align: left;
        }
        .history-item:nth-child(even) {
            background-color: #f9f9f9;
        }
        .history-difficulty {
            display: inline-block;
            padding: 2px 8px;
            border-radius: 10px;
            font-size: 12px;
            color: white;
        }
        .easy-difficulty {
            background: #2ecc71;
        }
        .medium-difficulty {
            background: #f39c12;
        }
        .hard-difficulty {
            background: #e74c3c;
        }
        .custom-difficulty {
            background: #9b59b6;
        }
        .history-score {
            font-weight: bold;
            color: #e74c3c;
        }
        .clear-history {
            background: #e74c3c;
            margin-top: 15px;
        }
        .clear-history:hover {
            background: #c0392b;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>LUYỆN GÕ 10 NGÓN NÂNG CAO</h1>
        <div class="subtitle">Rèn luyện kỹ năng đánh máy nhanh và chính xác</div>
        
        <div class="tab-container">
            <div class="tab-buttons">
                <button class="tab-button active" id="sample-tab-btn">Văn bản mẫu</button>
                <button class="tab-button" id="custom-tab-btn">Văn bản tùy chỉnh</button>
            </div>
            
            <div class="tab-content active" id="sample-tab">
                <div class="difficulty">
                    <button id="easy-btn" class="active">Dễ</button>
                    <button id="medium-btn">Trung bình</button>
                    <button id="hard-btn">Khó</button>
                </div>
            </div>
            
            <div class="tab-content" id="custom-tab">
                <div class="custom-text-container">
                    <h3>Nhập văn bản của bạn:</h3>
                    <textarea id="custom-text" placeholder="Nhập hoặc dán văn bản bạn muốn luyện gõ vào đây..."></textarea>
                    <button id="use-custom-text-btn">Sử dụng văn bản này</button>
                </div>
            </div>
        </div>
        
        <div class="stats">
            <div class="stat-box">
                <div>Tốc độ</div>
                <div id="wpm">0 WPM</div>
            </div>
            <div class="stat-box">
                <div>Độ chính xác</div>
                <div id="accuracy">100%</div>
            </div>
            <div class="stat-box">
                <div>Thời gian</div>
                <div id="timer">00:00:00</div>
            </div>
            <div class="stat-box score">
                <div>Điểm số</div>
                <div id="score">0</div>
            </div>
        </div>
        
        <div id="text-display">Chọn văn bản và nhấn "Bắt đầu" để bắt đầu luyện tập!</div>
        <input type="text" id="input-field" placeholder="Gõ văn bản ở đây..." disabled>
        
        <div class="buttons">
            <button id="start-btn">Bắt đầu</button>
            <button id="new-text-btn" disabled>Đổi văn bản</button>
            <button id="reset-btn" disabled>Làm lại</button>
        </div>
    </div>

    <div class="history-container">
        <h2 class="history-title">Lịch sử luyện tập</h2>
        <div id="history-list"></div>
        <button id="clear-history-btn" class="clear-history">Xóa lịch sử</button>
    </div>

    <script>
        // Danh sách các đoạn văn bản mẫu theo độ khó
        const sampleTexts = {
            easy: [
                "Học gõ mười ngón là kỹ năng quan trọng trong thời đại công nghệ. Bắt đầu bằng cách đặt các ngón tay đúng vị trí trên bàn phím.",
                "Hà Nội là thủ đô của Việt Nam với bề dày lịch sử hơn nghìn năm. Nơi đây có nhiều di tích văn hóa nổi tiếng thu hút du khách.",
                "Tiếng Việt phong phú và đa dạng với sáu thanh điệu. Việc gõ đúng dấu trong văn bản rất quan trọng để truyền đạt ý nghĩa chính xác.",
                "Công nghệ thông tin đang thay đổi cách chúng ta làm việc và giao tiếp. Kỹ năng đánh máy tốt giúp tăng hiệu suất công việc đáng kể.",
                "Việt Nam có nhiều cảnh đẹp từ Bắc vào Nam. Mỗi vùng miền có nét đặc trưng riêng về văn hóa, ẩm thực và con người."
            ],
            medium: [
                "Luyện gõ mười ngón đòi hỏi sự kiên nhẫn và thực hành thường xuyên. Ban đầu bạn có thể chậm nhưng đừng nản chí, hãy tập trung vào độ chính xác trước khi nâng cao tốc độ. Thói quen đặt ngón tay đúng vị trí sẽ giúp bạn tiến bộ nhanh chóng.",
                "Bàn phím QWERTY được thiết kế từ thế kỷ 19 và vẫn là chuẩn phổ biến nhất hiện nay. Mặc dù có nhiều bố cục bàn phím thay thế được cho là hiệu quả hơn, nhưng QWERTY vẫn chiếm ưu thế nhờ tính phổ biến và thói quen người dùng.",
                "Khi luyện gõ, hãy cố gắng không nhìn vào bàn phím. Điều này giúp bạn phát triển trí nhớ cơ bắp. Nếu mắc lỗi, đừng dừng lại để sửa ngay mà hãy tiếp tục đến cuối đoạn văn, sau đó quay lại kiểm tra các lỗi. Cách này giúp duy trì nhịp độ gõ liên tục.",
                "Việc sử dụng đúng ngón tay cho từng phím giúp tăng hiệu suất gõ và giảm mệt mỏi. Các ngón trỏ nên phụ trách các phím ở hàng giữa, ngón cái cho phím cách, và các ngón khác chia đều cho các phím còn lại. Thực hành thường xuyên sẽ tạo thành phản xạ tự nhiên."
            ],
            hard: [
                "Trong thời đại kỹ thuật số hiện nay, kỹ năng đánh máy nhanh và chính xác trở thành yêu cầu cơ bản đối với hầu hết các công việc văn phòng. Theo nghiên cứu, một người đánh máy chuyên nghiệp có thể đạt tốc độ lên tới 80-100 từ mỗi phút (WPM) với độ chính xác trên 98%. Tuy nhiên, để đạt được mức này đòi hỏi quá trình luyện tập bài bản và kiên trì.",
                "Bàn phím cơ (mechanical keyboard) đang trở thành lựa chọn của nhiều người dùng chuyên nghiệp nhờ độ bền cao và cảm giác gõ tốt hơn so với bàn phím thông thường. Mỗi loại switch khác nhau (như Cherry MX Red, Blue hay Brown) mang lại trải nghiệm gõ đặc trưng, phù hợp với nhu cầu từ văn phòng đến gaming. Việc lựa chọn bàn phím phù hợp cũng góp phần cải thiện hiệu suất đánh máy.",
                "Phương pháp luyện gõ hiệu quả bao gồm: chia nhỏ bài tập thành các phần ngắn, tập trung vào các tổ hợp phím khó, sử dụng các phần mềm luyện gõ chuyên dụng, và quan trọng nhất là duy trì thói quen luyện tập đều đặn mỗi ngày. Ghi lại kết quả sau mỗi buổi tập giúp theo dõi sự tiến bộ và điều chỉnh phương pháp phù hợp. Đừng quên giữ tư thế ngồi đúng để tránh các vấn đề về xương khớp khi làm việc lâu với máy tính."
            ]
        };

        // Biến toàn cục
        let currentText = "";
        let timer;
        let seconds = 0;
        let isTyping = false;
        let correctChars = 0;
        let totalTyped = 0;
        let startTime;
        let score = 0;
        let currentDifficulty = "easy";
        let currentMode = "sample"; // 'sample' hoặc 'custom'
        let history = JSON.parse(localStorage.getItem('typingHistory')) || [];

        // DOM Elements
        const textDisplay = document.getElementById('text-display');
        const inputField = document.getElementById('input-field');
        const startBtn = document.getElementById('start-btn');
        const newTextBtn = document.getElementById('new-text-btn');
        const resetBtn = document.getElementById('reset-btn');
        const wpmDisplay = document.getElementById('wpm');
        const accuracyDisplay = document.getElementById('accuracy');
        const timerDisplay = document.getElementById('timer');
        const scoreDisplay = document.getElementById('score');
        const easyBtn = document.getElementById('easy-btn');
        const mediumBtn = document.getElementById('medium-btn');
        const hardBtn = document.getElementById('hard-btn');
        const customTextArea = document.getElementById('custom-text');
        const useCustomTextBtn = document.getElementById('use-custom-text-btn');
        const sampleTabBtn = document.getElementById('sample-tab-btn');
        const customTabBtn = document.getElementById('custom-tab-btn');
        const sampleTab = document.getElementById('sample-tab');
        const customTab = document.getElementById('custom-tab');
        const historyList = document.getElementById('history-list');
        const clearHistoryBtn = document.getElementById('clear-history-btn');

        // Hàm chuyển đổi tab
        function switchTab(tab) {
            if (tab === 'sample') {
                sampleTabBtn.classList.add('active');
                customTabBtn.classList.remove('active');
                sampleTab.classList.add('active');
                customTab.classList.remove('active');
                currentMode = "sample";
            } else {
                sampleTabBtn.classList.remove('active');
                customTabBtn.classList.add('active');
                sampleTab.classList.remove('active');
                customTab.classList.add('active');
                currentMode = "custom";
            }
        }

        // Hàm khởi tạo văn bản ngẫu nhiên theo độ khó
        function getRandomText(difficulty) {
            const texts = sampleTexts[difficulty];
            return texts[Math.floor(Math.random() * texts.length)];
        }

        // Hàm định dạng thời gian (hh:mm:ss)
        function formatTime(seconds) {
            const hrs = Math.floor(seconds / 3600);
            const mins = Math.floor((seconds % 3600) / 60);
            const secs = seconds % 60;
            
            return [
                hrs.toString().padStart(2, '0'),
                mins.toString().padStart(2, '0'),
                secs.toString().padStart(2, '0')
            ].join(':');
        }

        // Hàm hiển thị lịch sử
        function renderHistory() {
            historyList.innerHTML = '';
            
            if (history.length === 0) {
                historyList.innerHTML = '<p style="text-align: center; color: #7f8c8d;">Chưa có lịch sử luyện tập</p>';
                return;
            }
            
            // Sắp xếp lịch sử theo thời gian mới nhất
            const sortedHistory = [...history].sort((a, b) => new Date(b.timestamp) - new Date(a.timestamp));
            
            sortedHistory.forEach((item, index) => {
                const historyItem = document.createElement('div');
                historyItem.className = 'history-item';
                
                const difficultyClass = item.difficulty === 'custom' ? 'custom-difficulty' : `${item.difficulty}-difficulty`;
                
                historyItem.innerHTML = `
                    <div>
                        <strong>#${index + 1}</strong> - 
                        <span class="history-difficulty ${difficultyClass}">${getDifficultyName(item.difficulty)}</span>
                        <br>
                        <small>${new Date(item.timestamp).toLocaleString()}</small>
                    </div>
                    <div style="text-align: right;">
                        <div>${item.wpm} WPM</div>
                        <div>${item.accuracy}% chính xác</div>
                        <div class="history-score">${item.score} điểm</div>
                    </div>
                `;
                
                historyList.appendChild(historyItem);
            });
        }

        // Hàm chuyển đổi tên độ khó
        function getDifficultyName(difficulty) {
            switch(difficulty) {
                case 'easy': return 'Dễ';
                case 'medium': return 'Trung bình';
                case 'hard': return 'Khó';
                case 'custom': return 'Tùy chỉnh';
                default: return difficulty;
            }
        }

        // Hàm lưu kết quả vào lịch sử
        function saveToHistory() {
            const timeElapsed = (new Date().getTime() - startTime) / 60000;
            const wordsTyped = inputField.value.length / 5;
            const wpm = Math.round(wordsTyped / timeElapsed) || 0;
            const accuracy = totalTyped > 0 ? Math.round((correctChars / totalTyped) * 100) : 100;
            
            const historyItem = {
                timestamp: new Date().toISOString(),
                difficulty: currentMode === 'sample' ? currentDifficulty : 'custom',
                wpm: wpm,
                accuracy: accuracy,
                score: score,
                timeSpent: seconds
            };
            
            history.unshift(historyItem);
            
            // Giới hạn lịch sử 50 bản ghi
            if (history.length > 50) {
                history.pop();
            }
            
            // Lưu vào localStorage
            localStorage.setItem('typingHistory', JSON.stringify(history));
            
            // Cập nhật giao diện
            renderHistory();
        }

        // Hàm bắt đầu bài tập
        function startTest() {
            if (isTyping) return;
            
            if (currentMode === 'custom' && customTextArea.value.trim() === '') {
                alert('Vui lòng nhập văn bản tùy chỉnh trước khi bắt đầu!');
                return;
            }
            
            currentText = currentMode === 'sample' 
                ? getRandomText(currentDifficulty) 
                : customTextArea.value.trim();
            
            renderText();
            
            inputField.value = "";
            inputField.disabled = false;
            inputField.focus();
            
            isTyping = true;
            seconds = 0;
            correctChars = 0;
            totalTyped = 0;
            score = 0;
            
            startTime = new Date().getTime();
            
            // Bắt đầu đếm thời gian
            timer = setInterval(() => {
                seconds++;
                timerDisplay.textContent = formatTime(seconds);
                updateScore();
            }, 1000);
            
            // Cập nhật UI
            startBtn.disabled = true;
            newTextBtn.disabled = false;
            resetBtn.disabled = false;
            easyBtn.disabled = true;
            mediumBtn.disabled = true;
            hardBtn.disabled = true;
            customTextArea.disabled = true;
            useCustomTextBtn.disabled = true;
            
            // Cập nhật thống kê ban đầu
            updateStats();
        }

        // Hàm render văn bản với highlight
        function renderText() {
            const inputText = inputField.value;
            let html = "";
            
            // Reset counters
            correctChars = 0;
            totalTyped = inputText.length;
            
            for (let i = 0; i < currentText.length; i++) {
                const currentChar = currentText[i];
                
                if (i < inputText.length) {
                    if (currentChar === inputText[i]) {
                        html += `<span class="correct">${currentChar}</span>`;
                        correctChars++;
                    } else {
                        html += `<span class="incorrect">${currentChar}</span>`;
                    }
                } else if (i === inputText.length) {
                    html += `<span class="highlight">${currentChar}</span>`;
                } else {
                    html += currentChar;
                }
            }
            
            textDisplay.innerHTML = html;
            
            // Kiểm tra nếu đã gõ hết văn bản
            if (inputText.length === currentText.length) {
                completeText();
            }
            
            updateStats();
        }

        // Hàm cập nhật thống kê
        function updateStats() {
            // Tính WPM (Words Per Minute)
            const timeElapsed = (new Date().getTime() - startTime) / 60000;
            const wordsTyped = inputField.value.length / 5;
            const wpm = Math.round(wordsTyped / timeElapsed) || 0;
            
            // Tính độ chính xác
            const accuracy = totalTyped > 0 
                ? Math.round((correctChars / totalTyped) * 100) 
                : 100;
            
            wpmDisplay.textContent = `${wpm} WPM`;
            accuracyDisplay.textContent = `${accuracy}%`;
        }

        // Hàm tính điểm
        function updateScore() {
            const timeElapsed = (new Date().getTime() - startTime) / 60000;
            const wordsTyped = inputField.value.length / 5;
            const wpm = Math.round(wordsTyped / timeElapsed) || 0;
            const accuracy = totalTyped > 0 ? (correctChars / totalTyped) : 1;
            
            // Công thức tính điểm: WPM * độ chính xác * hệ số độ khó
            let difficultyMultiplier = 1;
            if (currentDifficulty === "medium") difficultyMultiplier = 1.5;
            if (currentDifficulty === "hard") difficultyMultiplier = 2;
            if (currentMode === "custom") difficultyMultiplier = 1.8; // Độ khó trung bình cho văn bản tùy chỉnh
            
            score = Math.round(wpm * accuracy * difficultyMultiplier * (1 + seconds/300));
            scoreDisplay.textContent = score;
        }

        // Hàm khi hoàn thành văn bản
        function completeText() {
            saveToHistory();
            updateScore();
            
            // Thêm văn bản mới tự động nếu độ chính xác > 80%
            const accuracy = totalTyped > 0 ? Math.round((correctChars / totalTyped) * 100) : 100;
            if (accuracy > 80 && currentMode === 'sample') {
                setTimeout(() => {
                    currentText = getRandomText(currentDifficulty);
                    inputField.value = "";
                    renderText();
                    inputField.focus();
                }, 500);
            }
        }

        // Hàm kết thúc bài tập
        function endTest() {
            clearInterval(timer);
            inputField.disabled = true;
            isTyping = false;
            
            // Kích hoạt lại các nút
            startBtn.disabled = false;
            easyBtn.disabled = false;
            mediumBtn.disabled = false;
            hardBtn.disabled = false;
            customTextArea.disabled = false;
            useCustomTextBtn.disabled = false;
        }

        // Hàm reset bài tập
        function resetTest() {
            clearInterval(timer);
            inputField.value = "";
            inputField.disabled = true;
            isTyping = false;
            seconds = 0;
            timerDisplay.textContent = "00:00:00";
            wpmDisplay.textContent = "0 WPM";
            accuracyDisplay.textContent = "100%";
            scoreDisplay.textContent = "0";
            textDisplay.textContent = currentMode === 'sample' 
                ? "Chọn mức độ và nhấn 'Bắt đầu' để bắt đầu luyện tập!" 
                : "Nhấn 'Bắt đầu' để bắt đầu luyện tập với văn bản của bạn!";
            
            // Kích hoạt lại các nút
            startBtn.disabled = false;
            newTextBtn.disabled = true;
            resetBtn.disabled = true;
            easyBtn.disabled = false;
            mediumBtn.disabled = false;
            hardBtn.disabled = false;
            customTextArea.disabled = false;
            useCustomTextBtn.disabled = false;
        }

        // Hàm thay đổi độ khó
        function setDifficulty(difficulty) {
            currentDifficulty = difficulty;
            
            // Cập nhật UI
            easyBtn.classList.remove('active');
            mediumBtn.classList.remove('active');
            hardBtn.classList.remove('active');
            
            if (difficulty === "easy") easyBtn.classList.add('active');
            if (difficulty === "medium") mediumBtn.classList.add('active');
            if (difficulty === "hard") hardBtn.classList.add('active');
            
            if (!isTyping && currentMode === 'sample') {
                currentText = getRandomText(difficulty);
                renderText();
            }
        }

        // Hàm sử dụng văn bản tùy chỉnh
        function useCustomText() {
            if (customTextArea.value.trim() === '') {
                alert('Vui lòng nhập văn bản trước khi sử dụng!');
                return;
            }
            
            currentText = customTextArea.value.trim();
            renderText();
        }

        // Hàm xóa lịch sử
        function clearHistory() {
            if (confirm('Bạn có chắc chắn muốn xóa toàn bộ lịch sử?')) {
                history = [];
                localStorage.removeItem('typingHistory');
                renderHistory();
            }
        }

        // Event Listeners
        startBtn.addEventListener('click', startTest);
        newTextBtn.addEventListener('click', () => {
            if (!isTyping) return;
            if (currentMode === 'sample') {
                currentText = getRandomText(currentDifficulty);
            } else {
                currentText = customTextArea.value.trim();
            }
            inputField.value = "";
            renderText();
            inputField.focus();
        });
        resetBtn.addEventListener('click', resetTest);
        
        easyBtn.addEventListener('click', () => setDifficulty("easy"));
        mediumBtn.addEventListener('click', () => setDifficulty("medium"));
        hardBtn.addEventListener('click', () => setDifficulty("hard"));
        
        sampleTabBtn.addEventListener('click', () => switchTab('sample'));
        customTabBtn.addEventListener('click', () => switchTab('custom'));
        
        useCustomTextBtn.addEventListener('click', useCustomText);
        inputField.addEventListener('input', renderText);
        clearHistoryBtn.addEventListener('click', clearHistory);
        
        // Khởi tạo ban đầu
        setDifficulty("easy");
        renderHistory();
    </script>
</body>
</html>
