<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Get Key Script Success</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            /* Thay thế ảnh nền Itachi độ phân giải cao gần giống hình mẫu */
            background: url('https://images.alphacoders.com/134/1347318.png') no-repeat center center fixed;
            background-size: cover;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        /* Lớp phủ tối mờ toàn màn hình để làm nổi bật khung ở giữa */
        body::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background: rgba(0, 0, 0, 0.2);
            z-index: 1;
        }

        /* Khung kính mờ Glassmorphism giữa màn hình */
        .key-box-container {
            position: relative;
            z-index: 2;
            background: rgba(30, 30, 30, 0.65);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            border: 1.5px solid rgba(255, 74, 74, 0.25);
            width: 90%;
            max-width: 440px;
            padding: 30px 22px;
            border-radius: 12px;
            text-align: center;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.6);
        }

        /* Tiêu đề GET KEY SCRIPT màu đỏ rực */
        .title {
            color: #ff3333;
            font-size: 20px;
            font-weight: 800;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            margin-bottom: 15px;
            text-shadow: 0 0 10px rgba(255, 51, 51, 0.4);
        }

        /* Đoạn văn bản chúc mừng */
        .description {
            color: #dedede;
            font-size: 14px;
            line-height: 1.5;
            margin-bottom: 20px;
        }

        /* Ô hiển thị chuỗi mã Key */
        .key-display {
            background-color: #111116;
            color: #ffffff;
            font-size: 15px;
            font-weight: bold;
            padding: 14px;
            border-radius: 6px;
            margin-bottom: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            letter-spacing: 0.5px;
            user-select: all;
            word-break: break-all;
        }

        /* Nút Sao Chép Key màu đỏ chuyển sắc */
        .btn-copy {
            width: 100%;
            padding: 14px;
            background: linear-gradient(180deg, #dc143c, #990000);
            color: #ffffff;
            border: none;
            border-radius: 6px;
            font-size: 15px;
            font-weight: bold;
            text-transform: uppercase;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(153, 0, 0, 0.4);
            transition: transform 0.1s ease, filter 0.2s ease;
        }

        .btn-copy:hover {
            filter: brightness(1.2);
        }

        .btn-copy:active {
            transform: scale(0.98);
        }

        /* Thông báo nổi (Toast Notification) chúc chơi game vui vẻ */
        .toast-msg {
            visibility: hidden;
            min-width: 200px;
            background-color: rgba(17, 17, 17, 0.9);
            color: #ffffff;
            text-align: center;
            border-radius: 30px;
            padding: 10px 24px;
            position: fixed;
            z-index: 10;
            bottom: 45%; /* Vị trí căn ngay dưới khung như trong ảnh */
            font-size: 14px;
            border: 1px solid rgba(255, 255, 255, 0.15);
            box-shadow: 0 5px 15px rgba(0,0,0,0.5);
        }

        /* Hiệu ứng hiện thông báo */
        .toast-msg.show {
            visibility: visible;
            animation: fadeInOut 2.5s ease-in-out;
        }

        @keyframes fadeInOut {
            0% { opacity: 0; transform: scale(0.9); }
            15% { opacity: 1; transform: scale(1); }
            85% { opacity: 1; transform: scale(1); }
            100% { opacity: 0; transform: scale(0.9); }
        }
    </style>
</head>
<body>

<div class="key-box-container">
    <div class="title">GET KEY SCRIPT</div>
    <div class="description">
        Chúc mừng bạn đã vượt qua liên kết thành công!<br>Dưới đây là Key của bạn:
    </div>

    <div class="key-display" id="key-string">ItachiHubVIP_6Hrs_aBcD1E2fG3H</div>

    <button class="btn-copy" onclick="copyKey()">SAO CHÉP KEY</button>
</div>

<div class="toast-msg" id="toast">Chúc bạn chơi game vui vẻ!</div>

<script>
    // Hàm xử lý tạo key ngẫu nhiên mỗi lần load trang (nếu muốn) hoặc cố định dạng chuỗi
    function generateRandomKey() {
        const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
        let randomStr = '';
        for (let i = 0; i < 10; i++) {
            randomStr += characters.charAt(Math.floor(Math.random() * characters.length));
        }
        // Gán mã key động cho đẹp mắt
        document.getElementById('key-string').innerText = `KawJeiHub_6Hrs_${randomStr}`;
    }

    // Chạy tạo key ngẫu nhiên ngay khi load trang xong
    window.onload = generateRandomKey;

    function copyKey() {
        const keyText = document.getElementById('key-string').innerText;

        // Tiến hành copy chuỗi vào bộ nhớ máy
        navigator.clipboard.writeText(keyText).then(() => {
            const toast = document.getElementById('toast');
            
            // Kích hoạt class hiển thị thông báo "Chúc bạn chơi game vui vẻ!"
            toast.classList.add('show');
            
            // Tự động ẩn thông báo sau 2.5 giây
            setTimeout(() => {
                toast.classList.remove('show');
            }, 2500);
        }).catch(err => {
            alert('Không thể sao chép, hãy bôi đen đoạn mã để tự copy.');
        });
    }
</script>

</body>
</html>
