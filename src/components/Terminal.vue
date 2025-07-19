<template>
    <div class="terminal">
        <pre class="ascii-name">
    ⢀⣀⣀⡀⠀⠀⠀⠀⠀⠀⠀⣠⠾⠛⠶⣄⢀⣠⣤⠴⢦⡀⠀⠀⠀⠀
⠀⠀⠀⢠⡿⠉⠉⠉⠛⠶⠶⠖⠒⠒⣾⠋⠀⢀⣀⣙⣯⡁⠀⠀⠀⣿⠀⠀⠀⠀
⠀⠀⠀⢸⡇⠀⠀⠀⠀⠀⠀⠀⠀⢸⡏⠀⠀⢯⣼⠋⠉⠙⢶⠞⠛⠻⣆⠀⠀⠀
⠀⠀⠀⢸⣧⠆⠀⠀⠀⠀⠀⠀⠀⠀⠻⣦⣤⡤⢿⡀⠀⢀⣼⣷⠀⠀⣽⠀⠀⠀
⠀⠀⠀⣼⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠙⢏⡉⠁⣠⡾⣇⠀⠀⠀
⠀⠀⢰⡏⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⠋⠉⠀⢻⡀⠀⠀
⣀⣠⣼⣧⣤⠀⠀⠀⣀⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⡀⠀⠀⠐⠖⢻⡟⠓⠒
⠀⠀⠈⣷⣀⡀⠀⠘⠿⠇⠀⠀⠀⢀⣀⣀⠀⠀⠀⠀⠿⠟⠀⠀⠀⠲⣾⠦⢤⠀
⠀⠀⠋⠙⣧⣀⡀⠀⠀⠀⠀⠀⠀⠘⠦⠼⠃⠀⠀⠀⠀⠀⠀⠀⢤⣼⣏⠀⠀⠀
⠀⠀⢀⠴⠚⠻⢧⣄⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⣤⠞⠉⠉⠓⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠈⠉⠛⠛⠶⠶⠶⣶⣤⣴⡶⠶⠶⠟⠛⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
        </pre>
        <span>
            Copyleft (ɔ) 2025 Esa Kian · <a href="https://www.gnu.org/licenses/gpl-3.0.html">GPL-3.0</a>
        </span>
        <pre class="bio-text">
            <span v-for="(line, index) in typedLines" :key="index" v-html="line"></span>
            <iframe v-if="showPlayer" style="border-radius:12px" src="https://open.spotify.com/embed/track/2kRFrWaLWiKq48YYVdGcm8?utm_source=generator&theme=0" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
        </pre>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const showPlayer = ref(false);

const bioLines = [
    "> whoami",
    "esa kian. spawned in iran",
    "currently executing from finland",
    "writes code with the calm precision of a hitman — silent, effective, and occasionally poetic",
    "> uptime",
    "8 years deep in the software trenches",
    "refactored legacy horrors",
    "turned business logic into something that almost resembles art",
    "doesn’t build software to impress recruiters",
    "builds it so it doesn’t fall apart at 3am",
    "> affiliations",
    "migrated haunted monoliths, reduced cloud costs because waste is sin",
    "commits clean",
    "thinks dirty",
    "automates everything",
    "> find / -name esa-kian",
    `<a href="https://github.com/esa-kian" target="_blank">github</a> · <a href="https://linkedin.com/in/esa-kian/" target="_blank">linkedin</a> · <a href="https://medium.com/@esa-kian" target="_blank">medium</a>`,
    "ping me via pull request or summon me in a failing production log",
    "> soundtrack",
    "listen to my favorite song while you pretend to read this:",
    "> exit"
]

const typedLines = ref([])
const typingSpeed = 30
const initialDelay = 300

onMounted(async () => {
    await new Promise(resolve => setTimeout(resolve, initialDelay))
    for (const line of bioLines) {
        let currentLine = ''
        for (const char of line) {
            currentLine += char
            typedLines.value = [...typedLines.value.slice(0, -1), currentLine]
            await new Promise(resolve => setTimeout(resolve, typingSpeed))
        }
        typedLines.value.push('')
    }
    showPlayer.value = true;

})
</script>

<style scoped>
.terminal {
    background-color: #000;
    color: #00ff00;
    font-family: 'Courier New', Courier, monospace;
    padding: 0.5rem;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: stretch;
    box-sizing: border-box;
    overflow: hidden;
}

.ascii-name {
    font-size: 0.7rem;
    margin-bottom: 1rem;
    white-space: pre;
    overflow-wrap: break-word;
    word-break: break-word;
    width: 100%;
}

.bio-text {
    font-size: 1rem;
    white-space: pre-wrap;
    word-wrap: break-word;
    overflow-wrap: break-word;
    width: 100%;
}

.bio-text span {
    font-family: 'Courier New', Courier, monospace;
    display: block;
    line-height: 1.6;
    margin-bottom: 0.2rem;
}

a {
    color: #00ff00;
    text-decoration: underline;
}

a:link {
    color: #00ff00;
    text-decoration: underline;
}

a:active {
    color: #00ff00;
    text-decoration: underline;
}

a:hover {
    color: #00ff00;
    text-decoration: underline;
}


@media (max-width: 600px) {
    .ascii-name {
        font-size: 0.5rem;
    }

    .bio-text {
        font-size: 0.9rem;
    }
}
</style>