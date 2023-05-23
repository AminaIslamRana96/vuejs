<template>
  

    <div class="vid">
    
    <video ref="videoElement" width="40" height="30"></video>
    
    <button @click="startRecording" :disabled="recording || recordingStarted">Start Recording</button>
    
    <button @click="stopRecording" :disabled="!recording || !recordingStarted">Stop Recording</button>
    
    <button @click="submitRecording" :disabled="!recordingStarted">Submit</button>
    
    </div>
    
    </template>
    
    <script>
    
    export default {
    
    data() {
    
    return {
    
    recording: true,
    
    recordingStarted: true,
    
    stream: null,
    
    mediaRecorder: null,
    
    recordedChunks: []
    
    };
    
    },
    
    mounted() {
    
    navigator.mediaDevices.getUserMedia({ video: true, audio: true })
    
    .then(stream => {
    
    this.$refs.videoElement.srcObject = stream;
    
    this.stream = stream;
    
    })
    
    .catch(error => {
    
    console.error('Error accessing media devices: ', error);
    
    });
    
    },
    
    methods: {
    
    startRecording() {
    
    this.recordedChunks = [];
    
    this.mediaRecorder = new MediaRecorder(this.stream, { mimeType: 'video/webm' });
    
    this.mediaRecorder.ondataavailable = event => {
    
    if (event.data && event.data.size > 0) {
    
    this.recordedChunks.push(event.data);
    
    }
    
    };
    
    this.mediaRecorder.start();
    
    this.recording = true;
    
    this.recordingStarted = true;
    
    },
    
    stopRecording() {
    
    this.mediaRecorder.stop();
    
    this.recording = false;
    
    },
    submitRecording() {

const blob = new Blob(this.recordedChunks, { type: 'video/webm' });
const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            document.body.appendChild(a);
            a.style = 'display: none';
            a.href = url;
            a.download = 'Recording.webm';
            a.click();
           
        }
       
}

}



</script>
   
  
  <style scoped>
  video {
    width: 30%;
    height: auto;
    border-block-color: chocolate;
  }
  button {
    display: block;
    margin-top: 10px;
    padding: 8px 16px;
    background-color: rgb(128, 51, 0);
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 4px;
  }
  .vid { 
    height: 200;
    width: 200;
  }
  </style>
  