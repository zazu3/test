<?php
// Handle file upload if POST request
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['imageData'])) {
    header('Content-Type: application/json');
    
    // Create uploads directory if needed
    if (!file_exists('uploads')) {
        mkdir('uploads', 0755, true);
    }
    
    // Process image data
    $imageData = $_POST['imageData'];
    $base64 = str_replace('data:image/jpeg;base64,', '', $imageData);
    $imageBinary = base64_decode($base64);
    
    // Save file
    $filename = 'capture_' . date('Y-m-d_His') . '.jpg';
    $filepath = 'uploads/' . $filename;
    
    if (file_put_contents($filepath, $imageBinary)) {
        echo json_encode(['status' => 'success', 'filename' => $filename]);
    } else {
        echo json_encode(['status' => 'error', 'message' => 'Save failed']);
    }
    exit;
}
?>
<!DOCTYPE html>
<html>
<head>
    <title>Auto-Capture Camera System</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin-top: 20px; }
        #cameraFeed { width: 640px; border: 3px solid #333; margin: 10px auto; }
        #status { color: green; margin: 15px; font-weight: bold; }
    </style>
</head>
<body>
    <h1>Automatic Door Entry Camera</h1>
    <div id="status">Initializing camera...</div>
    <video id="cameraFeed" autoplay playsinline></video>

    <script>
        let cameraInterval;
        let stream;

        // Start camera and auto-capture
        const startMonitoring = async () => {
            try {
                stream = await navigator.mediaDevices.getUserMedia({ 
                    video: { width: 1280, height: 720 } 
                });
                const video = document.getElementById('cameraFeed');
                video.srcObject = stream;
                document.getElementById('status').textContent = "Monitoring - Auto-capture every 30s";

                // Capture every 30 seconds
                cameraInterval = setInterval(() => capturePhoto(video), 1000);

            } catch (error) {
                document.getElementById('status').textContent = "Error: " + error.message;
            }
        };

        // Capture and upload photo
        const capturePhoto = (videoElement) => {
            const canvas = document.createElement('canvas');
            canvas.width = videoElement.videoWidth;
            canvas.height = videoElement.videoHeight;
            canvas.getContext('2d').drawImage(videoElement, 0, 0);

            // Convert to Base64 and upload
            const imageData = canvas.toDataURL('image/jpeg', 0.9);
            
            fetch(window.location.href, {
                method: 'POST',
                headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
                body: 'imageData=' + encodeURIComponent(imageData)
            })
            .then(response => response.json())
            .then(data => console.log("Saved:", data.filename))
            .catch(err => console.error("Upload error:", err));
        };

        // Start when page loads
        window.addEventListener('load', startMonitoring);
    </script>
</body>
</html>
