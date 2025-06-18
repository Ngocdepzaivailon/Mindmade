# Mindmade
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YouthMind - Hỗ Trợ Tâm Lý Cho Giới Trẻ</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #4e73df;
            --secondary: #1cc88a;
            --accent: #f6c23e;
            --light: #f8f9fc;
            --dark: #5a5c69;
            --danger: #e74a3b;
            --success: #1cc88a;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .app-container {
            width: 100%;
            max-width: 1000px;
            height: 90vh;
            background: white;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            display: flex;
            overflow: hidden;
        }
        
        .sidebar {
            width: 300px;
            background: var(--primary);
            color: white;
            padding: 25px 20px;
            display: flex;
            flex-direction: column;
        }
        
        .logo {
            display: flex;
            align-items: center;
            margin-bottom: 30px;
        }
        
        .logo i {
            font-size: 32px;
            margin-right: 10px;
        }
        
        .logo h1 {
            font-size: 24px;
            font-weight: 600;
        }
        
        .resources-section {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 20px;
            margin-top: 20px;
            flex-grow: 1;
        }
        
        .resources-section h2 {
            font-size: 18px;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
        }
        
        .resources-section h2 i {
            margin-right: 10px;
        }
        
        .resource-item {
            background: rgba(255, 255, 255, 0.15);
            border-radius: 10px;
            padding: 12px;
            margin-bottom: 10px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .resource-item:hover {
            background: rgba(255, 255, 255, 0.25);
            transform: translateX(5px);
        }
        
        .resource-item h3 {
            font-size: 14px;
            margin-bottom: 5px;
        }
        
        .resource-item p {
            font-size: 12px;
            opacity: 0.8;
        }
        
        .main-content {
            flex: 1;
            display: flex;
            flex-direction: column;
        }
        
        .chat-header {
            padding: 20px;
            border-bottom: 1px solid #eee;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .chat-header h2 {
            color: var(--primary);
            font-size: 22px;
        }
        
        .mood-indicator {
            display: flex;
            align-items: center;
            background: #f0f5ff;
            padding: 8px 15px;
            border-radius: 20px;
        }
        
        .mood-indicator span {
            margin-right: 10px;
            font-size: 14px;
            color: var(--dark);
        }
        
        .moods {
            display: flex;
        }
        
        .mood {
            width: 24px;
            height: 24px;
            border-radius: 50%;
            margin: 0 3px;
            cursor: pointer;
            opacity: 0.5;
            transition: all 0.3s;
        }
        
        .mood.active {
            opacity: 1;
            transform: scale(1.2);
        }
        
        .mood-1 { background: #ff6b6b; }
        .mood-2 { background: #ff9e6b; }
        .mood-3 { background: #ffd66b; }
        .mood-4 { background: #a8e6cf; }
        .mood-5 { background: #4ecdc4; }
        
        .chat-container {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            background: #fafbfd;
            display: flex;
            flex-direction: column;
        }
        
        .message {
            max-width: 70%;
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 18px;
            position: relative;
            animation: fadeIn 0.3s;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .bot-message {
            align-self: flex-start;
            background: white;
            border: 1px solid #e0e6ef;
            border-bottom-left-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
        }
        
        .user-message {
            align-self: flex-end;
            background: var(--primary);
            color: white;
            border-bottom-right-radius: 5px;
        }
        
        .message-time {
            font-size: 10px;
            opacity: 0.7;
            margin-top: 5px;
            text-align: right;
        }
        
        .chat-input-container {
            padding: 20px;
            border-top: 1px solid #eee;
            display: flex;
            align-items: center;
            background: white;
        }
        
        .chat-input {
            flex: 1;
            padding: 15px 20px;
            border: 1px solid #ddd;
            border-radius: 30px;
            font-size: 16px;
            outline: none;
            transition: all 0.3s;
        }
        
        .chat-input:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(78, 115, 223, 0.2);
        }
        
        .send-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: var(--primary);
            color: white;
            border: none;
            margin-left: 15px;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 18px;
            transition: all 0.3s;
        }
        
        .send-btn:hover {
            background: #2e59d9;
            transform: scale(1.05);
        }
        
        .quick-replies {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 10px;
            margin-bottom: 20px;
        }
        
        .quick-reply {
            background: #edf2ff;
            color: var(--primary);
            border: none;
            border-radius: 20px;
            padding: 8px 15px;
            font-size: 14px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .quick-reply:hover {
            background: #dbe4ff;
        }
        
        .emergency-section {
            background: #fff3f3;
            border: 1px solid #ffd1d1;
            border-radius: 15px;
            padding: 15px;
            margin-top: auto;
        }
        
        .emergency-section h3 {
            color: var(--danger);
            margin-bottom: 10px;
            display: flex;
            align-items: center;
        }
        
        .emergency-section h3 i {
            margin-right: 10px;
        }
        
        .emergency-contacts {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .emergency-contact {
            background: white;
            border: 1px solid #ffd1d1;
            border-radius: 10px;
            padding: 10px;
            flex: 1;
            min-width: 120px;
            text-align: center;
            font-size: 13px;
        }
        
        .emergency-contact strong {
            color: var(--danger);
        }
        
        .emergency-btn {
            background: var(--danger);
            color: white;
            border: none;
            border-radius: 30px;
            padding: 12px 20px;
            margin-top: 15px;
            width: 100%;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .emergency-btn:hover {
            background: #c53030;
        }
        
        .emergency-btn i {
            margin-right: 8px;
        }
        
        .typing-indicator {
            display: flex;
            align-items: center;
            padding: 10px 15px;
            background: white;
            border-radius: 18px;
            border: 1px solid #e0e6ef;
            width: fit-content;
            margin-bottom: 15px;
        }
        
        .typing-indicator span {
            height: 8px;
            width: 8px;
            background: var(--dark);
            border-radius: 50%;
            margin: 0 2px;
            opacity: 0.4;
            animation: bounce 1.5s infinite;
        }
        
        .typing-indicator span:nth-child(1) { animation-delay: 0.1s; }
        .typing-indicator span:nth-child(2) { animation-delay: 0.2s; }
        .typing-indicator span:nth-child(3) { animation-delay: 0.3s; }
        
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }
        
        .resource-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        
        .modal-content {
            background: white;
            width: 90%;
            max-width: 600px;
            border-radius: 20px;
            overflow: hidden;
        }
        
        .modal-header {
            background: var(--primary);
            color: white;
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .modal-body {
            padding: 25px;
            max-height: 60vh;
            overflow-y: auto;
        }
        
        .close-btn {
            background: none;
            border: none;
            color: white;
            font-size: 24px;
            cursor: pointer;
        }
        
        @media (max-width: 768px) {
            .app-container {
                flex-direction: column;
                height: auto;
            }
            
            .sidebar {
                width: 100%;
                height: auto;
            }
            
            .chat-container {
                min-height: 400px;
            }
        }
    </style>
</head>
<body>
    <div class="app-container">
        <div class="sidebar">
            <div class="logo">
                <i class="fas fa-brain"></i>
                <h1>YouthMind</h1>
            </div>
            
            <div class="mood-indicator">
                <span>Tâm trạng hôm nay:</span>
                <div class="moods">
                    <div class="mood mood-1" data-value="1"></div>
                    <div class="mood mood-2" data-value="2"></div>
                    <div class="mood mood-3 active" data-value="3"></div>
                    <div class="mood mood-4" data-value="4"></div>
                    <div class="mood mood-5" data-value="5"></div>
                </div>
            </div>
            
            <div class="resources-section">
                <h2><i class="fas fa-book-medical"></i> Tài nguyên hỗ trợ</h2>
                
                <div class="resource-item" data-resource="stress">
                    <h3>Quản lý căng thẳng</h3>
                    <p>Kỹ thuật thở, quản lý thời gian...</p>
                </div>
                
                <div class="resource-item" data-resource="anxiety">
                    <h3>Kiểm soát lo âu</h3>
                    <p>Bài tập thực hành, lời khuyên chuyên gia...</p>
                </div>
                
                <div class="resource-item" data-resource="depression">
                    <h3>Vượt qua trầm cảm</h3>
                    <p>Nhận biết dấu hiệu, cách tìm kiếm hỗ trợ...</p>
                </div>
                
                <div class="resource-item" data-resource="relationships">
                    <h3>Mối quan hệ lành mạnh</h3>
                    <p>Giao tiếp, ranh giới cá nhân...</p>
                </div>
            </div>
        </div>
        
        <div class="main-content">
            <div class="chat-header">
                <h2><i class="fas fa-head-side-virus"></i> Trợ lý Tâm lý</h2>
                <div class="mood-indicator">
                    <span>Tâm trạng của bạn:</span>
                    <div class="moods">
                        <div class="mood mood-1" data-value="1"></div>
                        <div class="mood mood-2" data-value="2"></div>
                        <div class="mood mood-3" data-value="3"></div>
                        <div class="mood mood-4" data-value="4"></div>
                        <div class="mood mood-5" data-value="5"></div>
                    </div>
                </div>
            </div>
            
            <div class="chat-container" id="chat-container">
                <div class="message bot-message">
                    Chào bạn! Mình là trợ lý tâm lý của YouthMind. 😊<br>
                    Hôm nay bạn cảm thấy thế nào? Mình có thể giúp gì cho bạn?
                    <div class="message-time">10:00 AM</div>
                </div>
                
                <div class="quick-replies">
                    <button class="quick-reply">Mình đang cảm thấy không ổn</button>
                    <button class="quick-reply">Cần lời khuyên về mối quan hệ</button>
                    <button class="quick-reply">Kỹ thuật giảm căng thẳng</button>
                    <button class="quick-reply">Mình muốn chia sẻ điều gì đó</button>
                </div>
                
                <div class="typing-indicator" id="typing-indicator" style="display: none;">
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
                
                <div class="emergency-section">
                    <h3><i class="fas fa-exclamation-triangle"></i> Hỗ trợ khẩn cấp</h3>
                    <p>Nếu bạn đang gặp tình huống nguy hiểm hoặc có ý định tự làm hại bản thân, hãy liên hệ ngay:</p>
                    
                    <div class="emergency-contacts">
                        <div class="emergency-contact">
                            <strong>Tổng đài 111</strong><br>
                            Bảo vệ Trẻ em
                        </div>
                        <div class="emergency-contact">
                            <strong>1900 633 069</strong><br>
                            Ngày mai tươi sáng
                        </div>
                        <div class="emergency-contact">
                            <strong>113</strong><br>
                            Công an
                        </div>
                    </div>
                    
                    <button class="emergency-btn">
                        <i class="fas fa-phone-alt"></i> Gọi hỗ trợ khẩn cấp
                    </button>
                </div>
            </div>
            
            <div class="chat-input-container">
                <input type="text" class="chat-input" id="user-input" placeholder="Viết tin nhắn của bạn...">
                <button class="send-btn" id="send-btn">
                    <i class="fas fa-paper-plane"></i>
                </button>
            </div>
        </div>
    </div>
    
    <div class="resource-modal" id="resource-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 id="modal-title">Quản lý căng thẳng</h2>
                <button class="close-btn" id="close-modal">&times;</button>
            </div>
            <div class="modal-body" id="modal-body">
                <!-- Nội dung tài nguyên sẽ được thêm ở đây -->
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const chatContainer = document.getElementById('chat-container');
            const userInput = document.getElementById('user-input');
            const sendBtn = document.getElementById('send-btn');
            const typingIndicator = document.getElementById('typing-indicator');
            const resourceItems = document.querySelectorAll('.resource-item');
            const resourceModal = document.getElementById('resource-modal');
            const modalTitle = document.getElementById('modal-title');
            const modalBody = document.getElementById('modal-body');
            const closeModal = document.getElementById('close-modal');
            const quickReplies = document.querySelectorAll('.quick-reply');
            const moods = document.querySelectorAll('.mood');
            
            // Cài đặt tâm trạng
            moods.forEach(mood => {
                mood.addEventListener('click', function() {
                    document.querySelectorAll('.mood').forEach(m => m.classList.remove('active'));
                    this.classList.add('active');
                });
            });
            
            // Gửi tin nhắn
            function sendMessage() {
                const message = userInput.value.trim();
                if (message) {
                    addMessage(message, 'user');
                    userInput.value = '';
                    
                    // Hiển thị trạng thái đang nhập
                    typingIndicator.style.display = 'flex';
                    
                    // Tạo phản hồi sau 1-2 giây
                    setTimeout(() => {
                        typingIndicator.style.display = 'none';
                        generateBotResponse(message);
                    }, 1500);
                }
            }
            
            // Thêm tin nhắn vào giao diện
            function addMessage(text, sender) {
                const messageDiv = document.createElement('div');
                messageDiv.classList.add('message');
                messageDiv.classList.add(sender + '-message');
                messageDiv.innerHTML = text + '<div class="message-time">' + getCurrentTime() + '</div>';
                chatContainer.insertBefore(messageDiv, typingIndicator);
                chatContainer.scrollTop = chatContainer.scrollHeight;
            }
            
            // Tạo phản hồi từ bot
            function generateBotResponse(userMessage) {
                let response = '';
                userMessage = userMessage.toLowerCase();
                
                if (userMessage.includes('buồn') || userMessage.includes('tồi tệ') || 
                    userMessage.includes('chán') || userMessage.includes('mệt mỏi')) {
                    response = "Mình rất tiếc khi biết bạn đang cảm thấy như vậy 😔. Bạn có thể chia sẻ thêm về cảm xúc của mình không? Đôi khi nói ra những điều trong lòng có thể giúp chúng ta cảm thấy nhẹ nhõm hơn.";
                } 
                else if (userMessage.includes('căng thẳng') || userMessage.includes('stress')) {
                    response = "Căng thẳng là phản ứng bình thường của cơ thể, nhưng nếu kéo dài có thể ảnh hưởng đến sức khỏe. Bạn thử áp dụng kỹ thuật thở 4-7-8 nhé: <br><br>1. Hít vào từ từ bằng mũi trong 4 giây<br>2. Giữ hơi thở trong 7 giây<br>3. Thở ra từ từ bằng miệng trong 8 giây<br><br>Lặp lại 4 lần. Bạn cảm thấy thế nào?";
                }
                else if (userMessage.includes('lo lắng') || userMessage.includes('bồn chồn')) {
                    response = "Khi cảm thấy lo lắng, bạn có thể thử phương pháp 'grounding' (kết nối với hiện tại):<br><br>1. <strong>Nhìn</strong>: Tìm 5 vật bạn có thể nhìn thấy<br>2. <strong>Chạm</strong>: Tìm 4 vật bạn có thể chạm vào<br>3. <strong>Nghe</strong>: Lắng nghe 3 âm thanh xung quanh<br>4. <strong>Ngửi</strong>: Nhận biết 2 mùi hương<br>5. <strong>Nếm</strong>: Cảm nhận 1 vị giác trong miệng<br><br>Kỹ thuật này giúp đưa tâm trí bạn trở lại hiện tại.";
                }
                else if (userMessage.includes('quan hệ') || userMessage.includes('bạn bè') || 
                         userMessage.includes('gia đình') || userMessage.includes('người yêu')) {
                    response = "Mối quan hệ lành mạnh cần sự tôn trọng, giao tiếp rõ ràng và ranh giới cá nhân. Bạn đang gặp khó khăn cụ thể nào trong mối quan hệ của mình? Hãy nhớ rằng:<br><br>- Thể hiện cảm xúc bằng 'Tôi cảm thấy...' thay vì đổ lỗi<br>- Lắng nghe để hiểu, không chỉ để trả lời<br>- Chấp nhận sự khác biệt của nhau";
                }
                else if (userMessage.includes('cảm ơn') || userMessage.includes('thanks')) {
                    response = "Không có gì đâu bạn ơi! 😊 Mình luôn ở đây để lắng nghe và hỗ trợ bạn. Bất cứ khi nào bạn cần chia sẻ, mình sẵn sàng.";
                }
                else {
                    const responses = [
                        "Mình hiểu bạn đang muốn chia sẻ điều gì đó quan trọng. Bạn có thể nói thêm cho mình biết chi tiết hơn không?",
                        "Cảm ơn bạn đã tin tưởng chia sẻ. Mình đang lắng nghe và muốn hiểu rõ hơn về tình huống của bạn.",
                        "Mỗi người trải qua những khó khăn khác nhau. Bạn đang cảm thấy thế nào về tình huống này?",
                        "Chia sẻ cảm xúc là bước đầu tiên quan trọng. Bạn có muốn nói thêm về những gì đang xảy ra không?"
                    ];
                    response = responses[Math.floor(Math.random() * responses.length)];
                }
                
                addMessage(response, 'bot');
                
                // Thêm các gợi ý trả lời nhanh nếu cần
                if (userMessage.includes('căng thẳng') || userMessage.includes('stress')) {
                    addQuickReplies(['Cách thực hành thở 4-7-8', 'Kỹ thuật thư giãn cơ bắp', 'Quản lý thời gian hiệu quả']);
                }
            }
            
            // Thêm gợi ý trả lời nhanh
            function addQuickReplies(replies) {
                const container = document.createElement('div');
                container.classList.add('quick-replies');
                
                replies.forEach(reply => {
                    const button = document.createElement('button');
                    button.classList.add('quick-reply');
                    button.textContent = reply;
                    button.addEventListener('click', () => {
                        addMessage(reply, 'user');
                        setTimeout(() => {
                            generateBotResponse(reply);
                        }, 1000);
                    });
                    container.appendChild(button);
                });
                
                chatContainer.insertBefore(container, typingIndicator);
                chatContainer.scrollTop = chatContainer.scrollHeight;
            }
            
            // Lấy thời gian hiện tại
            function getCurrentTime() {
                const now = new Date();
                return now.getHours().toString().padStart(2, '0') + ':' + 
                       now.getMinutes().toString().padStart(2, '0');
            }
            
            // Hiển thị tài nguyên
            resourceItems.forEach(item => {
                item.addEventListener('click', function() {
                    const resource = this.getAttribute('data-resource');
                    showResource(resource);
                });
            });
            
            // Hiển thị nội dung tài nguyên
            function showResource(resource) {
                let title = '';
                let content = '';
                
                switch(resource) {
                    case 'stress':
                        title = 'Quản lý căng thẳng';
                        content = `
                            <h3>Kỹ thuật quản lý căng thẳng</h3>
                            <p>Căng thẳng là phản ứng tự nhiên của cơ thể trước các thách thức. Dưới đây là một số phương pháp hiệu quả:</p>
                            
                            <h4>1. Thở sâu (4-7-8)</h4>
                            <ul>
                                <li>Hít vào bằng mũi trong 4 giây</li>
                                <li>Giữ hơi thở trong 7 giây</li>
                                <li>Thở ra bằng miệng trong 8 giây</li>
                                <li>Lặp lại 4 lần</li>
                            </ul>
                            
                            <h4>2. Quản lý thời gian</h4>
                            <ul>
                                <li>Sử dụng ma trận Eisenhower: phân loại công việc theo mức độ quan trọng và khẩn cấp</li>
                                <li>Phương pháp Pomodoro: làm việc 25 phút, nghỉ 5 phút</li>
                                <li>Ưu tiên 3 việc quan trọng mỗi ngày</li>
                            </ul>
                            
                            <h4>3. Hoạt động thể chất</h4>
                            <p>30 phút vận động mỗi ngày giúp giảm hormone căng thẳng và tăng endorphin.</p>
                        `;
                        break;
                    case 'anxiety':
                        title = 'Kiểm soát lo âu';
                        content = `
                            <h3>Chiến lược kiểm soát lo âu</h3>
                            <p>Lo âu trở thành vấn đề khi nó ảnh hưởng đến cuộc sống hàng ngày. Dưới đây là các kỹ thuật hiệu quả:</p>
                            
                            <h4>1. Kỹ thuật Grounding (5-4-3-2-1)</h4>
                            <ul>
                                <li>Nhận biết 5 vật bạn có thể nhìn thấy</li>
                                <li>4 vật bạn có thể chạm vào</li>
                                <li>3 âm thanh bạn có thể nghe thấy</li>
                                <li>2 mùi hương bạn có thể ngửi thấy</li>
                                <li>1 vị giác bạn có thể cảm nhận</li>
                            </ul>
                            
                            <h4>2. Thách thức suy nghĩ tiêu cực</h4>
                            <ul>
                                <li>Xác định suy nghĩ tự động: "Điều tồi tệ nhất có thể xảy ra là gì?"</li>
                                <li>Đánh giá khả năng xảy ra thực tế</li>
                                <li>Tìm bằng chứng phản bác suy nghĩ tiêu cực</li>
                                <li>Hình dung kết quả tích cực</li>
                            </ul>
                            
                            <h4>3. Chăm sóc bản thân</h4>
                            <ul>
                                <li>Ngủ đủ 7-9 tiếng mỗi đêm</li>
                                <li>Hạn chế caffeine và đường</li>
                                <li>Thực hành thiền định 10 phút mỗi ngày</li>
                                <li>Duy trì kết nối xã hội</li>
                            </ul>
                        `;
                        break;
                    case 'depression':
                        title = 'Vượt qua trầm cảm';
                        content = `
                            <h3>Nhận biết và đối phó với trầm cảm</h3>
                            <p>Trầm cảm không đơn thuần là cảm thấy buồn mà là một tình trạng y tế nghiêm trọng. Các dấu hiệu cần chú ý:</p>
                            
                            <h4>Triệu chứng chính:</h4>
                            <ul>
                                <li>Tâm trạng chán nản hầu hết thời gian trong ngày</li>
                                <li>Mất hứng thú với các hoạt động từng yêu thích</li>
                                <li>Thay đổi đáng kể về cân nặng và giấc ngủ</li>
                                <li>Cảm giác vô giá trị hoặc tội lỗi quá mức</li>
                                <li>Suy nghĩ về cái chết hoặc tự tử</li>
                            </ul>
                            
                            <h4>Các bước hỗ trợ:</h4>
                            <ol>
                                <li><strong>Tìm kiếm chuyên gia</strong>: Bác sĩ tâm thần, nhà tâm lý lâm sàng</li>
                                <li><strong>Liệu pháp tâm lý</strong>: CBT (Trị liệu nhận thức hành vi) đặc biệt hiệu quả</li>
                                <li><strong>Hoạt động nhỏ mỗi ngày</strong>: Đi bộ ngắn, viết nhật ký, gọi điện cho bạn bè</li>
                                <li><strong>Xây dựng thói quen</strong>: Ngủ, ăn uống đúng giờ</li>
                                <li><strong>Tránh cô lập</strong>: Duy trì kết nối dù nhỏ với người thân</li>
                            </ol>
                            
                            <h4>Tài nguyên hỗ trợ tại Việt Nam:</h4>
                            <ul>
                                <li>Tổng đài 111: Bảo vệ Trẻ em</li>
                                <li>Trung tâm Pháp y Tâm thần khu vực</li>
                                <li>Bệnh viện Tâm thần Trung ương</li>
                            </ul>
                        `;
                        break;
                    case 'relationships':
                        title = 'Mối quan hệ lành mạnh';
                        content = `
                            <h3>Xây dựng mối quan hệ lành mạnh</h3>
                            <p>Mối quan hệ lành mạnh dựa trên sự tôn trọng, tin tưởng và giao tiếp cởi mở. Dưới đây là các yếu tố quan trọng:</p>
                            
                            <h4>1. Giao tiếp hiệu quả</h4>
                            <ul>
                                <li>Sử dụng câu "Tôi cảm thấy..." thay vì đổ lỗi</li>
                                <li>Lắng nghe tích cực, không ngắt lời</li>
                                <li>Thể hiện sự đồng cảm: "Mình hiểu bạn cảm thấy..."</li>
                                <li>Giải quyết xung đột khi cả hai bình tĩnh</li>
                            </ul>
                            
                            <h4>2. Thiết lập ranh giới lành mạnh</h4>
                            <ul>
                                <li>Xác định nhu cầu cá nhân và truyền đạt rõ ràng</li>
                                <li>Tôn trọng không gian riêng của nhau</li>
                                <li>Học cách nói "không" mà không cảm thấy tội lỗi</li>
                                <li>Nhận biết các dấu hiệu kiểm soát hoặc thao túng</li>
                            </ul>
                            
                            <h4>3. Duy trì sự cân bằng</h4>
                            <ul>
                                <li>Dành thời gian cho bản thân và sở thích cá nhân</li>
                                <li>Có cuộc sống xã hội bên ngoài mối quan hệ</li>
                                <li>Hỗ trợ nhưng không hy sinh bản thân quá mức</li>
                                <li>Chia sẻ trách nhiệm và quyết định</li>
                            </ul>
                            
                            <h4>4. Nhận biết mối quan hệ độc hại</h4>
                            <p>Các dấu hiệu cảnh báo:</p>
                            <ul>
                                <li>Thường xuyên chỉ trích, làm nhục</li>
                                <li>Kiểm soát hành vi, bạn bè, mạng xã hội</li>
                                <li>Không tôn trọng ranh giới cá nhân</li>
                                <li>Bạo lực thể chất hoặc cảm xúc</li>
                                <li>Đổ lỗi cho bạn về hành vi của họ</li>
                            </ul>
                        `;
                        break;
                }
                
                modalTitle.textContent = title;
                modalBody.innerHTML = content;
                resourceModal.style.display = 'flex';
            }
            
            // Đóng modal
            closeModal.addEventListener('click', () => {
                resourceModal.style.display = 'none';
            });
            
            // Đóng modal khi nhấn bên ngoài
            window.addEventListener('click', (e) => {
                if (e.target === resourceModal) {
                    resourceModal.style.display = 'none';
                }
            });
            
            // Gửi tin nhắn khi nhấn nút
            sendBtn.addEventListener('click', sendMessage);
            
            // Gửi tin nhắn khi nhấn Enter
            userInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    sendMessage();
                }
            });
            
            // Gợi ý trả lời nhanh
            quickReplies.forEach(reply => {
                reply.addEventListener('click', function() {
                    const text = this.textContent;
                    addMessage(text, 'user');
                    
                    typingIndicator.style.display = 'flex';
                    
                    setTimeout(() => {
                        typingIndicator.style.display = 'none';
                        generateBotResponse(text);
                    }, 1500);
                });
            });
            
            // Tạo tin nhắn chào mừng
            setTimeout(() => {
                addMessage("Chào bạn! Mình có thể giúp gì cho bạn hôm nay? Bạn có muốn chia sẻ về tâm trạng hiện tại của mình không?", 'bot');
            }, 1000);
        });
    </script>
</body>
</html>
