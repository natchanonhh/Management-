<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบหลังบ้าน - จัดการข้อมูลส่วนบุคคล</title>
    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #f0f2f5; margin: 0; padding: 20px; }
        .admin-box { max-width: 500px; background: white; margin: 40px auto; padding: 30px; border-radius: 16px; box-shadow: 0 8px 24px rgba(0,0,0,0.08); }
        h2 { margin-top: 0; color: #1a1a1a; text-align: center; font-weight: 600; }
        .form-group { margin-bottom: 18px; }
        label { display: block; margin-bottom: 6px; font-weight: 600; color: #444; font-size: 14px; }
        input[type="text"], input[type="email"], input[type="password"], textarea, input[type="file"] {
            width: 100%; padding: 12px; border: 1.5px solid #dce0e4; border-radius: 8px; box-sizing: border-box; font-size: 15px; transition: border-color 0.2s;
        }
        input:focus, textarea:focus { border-color: #0066ff; outline: none; }
        button { width: 100%; padding: 14px; background: #0066ff; color: white; border: none; border-radius: 8px; font-size: 16px; cursor: pointer; font-weight: bold; transition: background 0.2s; }
        button:hover { background: #0052cc; }
        #admin-panel { display: none; }
        .result-link { background: #e6f4ea; padding: 16px; border-radius: 8px; border: 1px solid #ceead6; word-break: break-all; margin-top: 20px; display: none; }
    </style>
</head>
<body>

    <div id="login-panel" class="admin-box">
        <h2>Admin Management</h2>
        <div class="form-group">
            <label>อีเมลผู้ดูแลระบบ</label>
            <input type="email" id="admin-email" placeholder="admin@example.com">
        </div>
        <div class="form-group">
            <label>รหัสผ่าน</label>
            <input type="password" id="admin-password" placeholder="******">
        </div>
        <button onclick="loginAdmin()">เข้าสู่ระบบ</button>
        <p id="login-error" style="color:#d93025; text-align:center; display:none; font-size: 14px; margin-top: 15px;">อีเมลหรือรหัสผ่านไม่ถูกต้อง</p>
    </div>

    <div id="admin-panel" class="admin-box">
        <h2>อัปโหลดและตั้งค่าสิทธิ์ไฟล์</h2>
        
        <div class="form-group">
            <label>1. ชื่อไฟล์ / หัวข้อข้อมูล</label>
            <input type="text" id="file-title" placeholder="เช่น วิดีโอแนะนำระบบ SCHOOL MONEY">
        </div>

        <div class="form-group">
            <label>2. เลือกไฟล์ (รองรับวิดีโอ 9:16, PDF, รูปภาพ)</label>
            <input type="file" id="file-input">
        </div>

        <div class="form-group">
            <label>3. คำสั่งให้หน้าบ้านกรอก (Smart Login Prompt)</label>
            <input type="text" id="login-prompt" placeholder="เช่น กรุณากรอกรหัสนักศึกษาเพื่อเข้าดูข้อมูลค่าใช้จ่าย">
        </div>

        <div class="form-group">
            <label>4. รายชื่อหรือรหัสที่อนุญาตให้เข้าดูได้ (คั่นด้วย ,)</label>
            <textarea id="allowed-credentials" rows="4" placeholder="เช่น 65010001, 65010002, สมชาย"></textarea>
            <small style="color:#666; font-size: 12px; display: block; margin-top: 4px;">* ใส่ข้อมูลทุกคนที่อนุญาตให้เข้าดูได้ คั่นด้วยเครื่องหมายจุลภาค (,)</small>
        </div>

        <button onclick="uploadDataAndSetRules()" style="background: #0d904f;">อัปโหลดและสร้างลิงก์</button>

        <div id="result-box" class="result-link">
            <strong style="color: #0d904f;">สร้างลิงก์สำเร็จ!</strong><br>
            <span style="font-size: 14px; color: #333;">ส่งลิงก์นี้ให้ผู้ใช้งานเปิดในระบบเพื่อดูไฟล์:</span><br><br>
            <a id="share-link" href="#" target="_blank" style="color: #0066ff; font-weight: 500;">กำลังสร้างลิงก์...</a>
        </div>
    </div>

    <script>
        const SUPABASE_URL = 'https://qspfyaqsnbtyzqcvfzsd.supabase.co';
        const SUPABASE_ANON_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InFzcGZ5YXFzbmJ0eXpxY3ZmenNkIiwicm9sZSI6ImFub24iLCJpYXQiOjE3ODIxMTgzOTMsImV4cCI6MjA5NzY5NDM5M30.je7dDqR3XnHP3SwNgUCM4Ae2DnajhLGAUh0wnSKCh2c';
        const supabase = window.supabase.createClient(SUPABASE_URL, SUPABASE_ANON_KEY);

        async function loginAdmin() {
            const email = document.getElementById('admin-email').value;
            const password = document.getElementById('admin-password').value;
            const { data, error } = await supabase.auth.signInWithPassword({ email, password });

            if (error) {
                document.getElementById('login-error').style.display = 'block';
            } else {
                document.getElementById('login-panel').style.display = 'none';
                document.getElementById('admin-panel').style.display = 'block';
            }
        }

        async function uploadDataAndSetRules() {
            const fileTitle = document.getElementById('file-title').value;
            const fileInput = document.getElementById('file-input').files[0];
            const loginPrompt = document.getElementById('login-prompt').value;
            const credentialsText = document.getElementById('allowed-credentials').value;

            if (!fileTitle || !fileInput || !loginPrompt || !credentialsText) {
                alert('กรุณากรอกข้อมูลให้ครบทุกช่อง');
                return;
            }

            const uploadBtn = document.querySelector('button[onclick="uploadDataAndSetRules()"]');
            uploadBtn.innerText = 'กำลังอัปโหลด...';
            uploadBtn.disabled = true;

            const allowedCredentialsArray = credentialsText.split(',').map(item => item.trim());
            const fileName = Date.now() + '_' + fileInput.name.replace(/[^a-zA-Z0-9.]/g, ''); 

            const { data: storageData, error: storageError } = await supabase.storage
                .from('secure_vault')
                .upload('uploads/' + fileName, fileInput);

            if (storageError) {
                alert('อัปโหลดไฟล์ไม่สำเร็จ: ' + storageError.message);
                uploadBtn.innerText = 'อัปโหลดและสร้างลิงก์';
                uploadBtn.disabled = false;
                return;
            }

            const { data: dbData, error: dbError } = await supabase
                .from('system_files')
                .insert([{ 
                    file_title: fileTitle, 
                    storage_path: storageData.path, 
                    login_prompt: loginPrompt, 
                    allowed_credentials: allowedCredentialsArray 
                }])
                .select();

            if (dbError) {
                alert('บันทึกเงื่อนไขฐานข้อมูลไม่สำเร็จ: ' + dbError.message);
                uploadBtn.innerText = 'อัปโหลดและสร้างลิงก์';
                uploadBtn.disabled = false;
                return;
            }

            const createdFileId = dbData[0].id;
            let currentOrigin = window.location.origin + window.location.pathname.replace('admin.html', 'index.html');
            if (currentOrigin.endsWith('/')) currentOrigin += 'index.html';
            const finalShareLink = `${currentOrigin}?id=${createdFileId}`;

            document.getElementById('share-link').href = finalShareLink;
            document.getElementById('share-link').innerText = finalShareLink;
            document.getElementById('result-box').style.display = 'block';
            
            uploadBtn.innerText = 'อัปโหลดสำเร็จ!';
            setTimeout(() => {
                uploadBtn.innerText = 'อัปโหลดและสร้างลิงก์ใหม่';
                uploadBtn.disabled = false;
            }, 3000);
        }
    </script>
</body>
</html>
