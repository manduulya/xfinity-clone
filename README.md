<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="style.css">
    <title>Drum kit</title>
</head>
<body>
    <div id="keys">
        <div data-key="65" class="key">
            <kbd>A</kbd>
            <span class="sound">Boom</span>
        </div>
        <div data-key="83" class="key">
            <kbd>S</kbd>
            <span class="sound">Clap</span>
        </div>
        <div data-key="68" class="key">
            <kbd>D</kbd>
            <span class="sound">Hihat</span>
        </div>
        <div data-key="70" class="key">
            <kbd>F</kbd>
            <span class="sound">kick</span>
        </div>
        <div data-key="71" class="key">
            <kbd>G</kbd>
            <span class="sound">Openhat</span>
        </div>
        <div data-key="72" class="key">
            <kbd>H</kbd>
            <span class="sound">Ride</span>
        </div>
        <div data-key="74" class="key">
            <kbd>J</kbd>
            <span class="sound">Snare</span>
        </div>
        <div data-key="75" class="key">
            <kbd>K</kbd>
            <span class="sound">Tink</span>
        </div>
        <div data-key="76" class="key">
            <kbd>L</kbd>
            <span class="sound">Tom</span>
        </div>
    </div>
    

    <audio data-key="65" src="boom.wav"></audio>
    <audio data-key="83" src="clap.wav"></audio>
    <audio data-key="68" src="hihat.wav"></audio>
    <audio data-key="70" src="kick.wav"></audio>
    <audio data-key="71" src="openhat.wav"></audio>
    <audio data-key="72" src="ride.wav"></audio>
    <audio data-key="74" src="snare.wav"></audio>
    <audio data-key="75" src="tink.wav"></audio>
    <audio data-key="76" src="tom.wav"></audio>


<script>
    function removeTransition(e) {
        if (e.propertyName !== 'transform') return;
        e.target.classList.remove('playing');
    }
    function playSound(e) {
        const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
        const key = document.querySelector(`div[data-key="${e.keyCode}"]`);
        if (!audio) return;
        key.classList.add('playing');
        audio.currentTime = 0;
        audio.play();
    }
    const keys = Array.from(document.querySelectorAll('.key'));
    keys.forEach(key => key.addEventListener('transitionend', removeTransition));
    window.addEventListener('keydown', playSound);
</script>    
<!-- <script>
    window.addEventListener("keydown", function(e){
        const audio = document.querySelector('audio[data-key="${e.keyCode}"]');
        if(!audio) return;
        audio.play();
        console.log(audio);
    });
</script> -->

</body>
</html>
