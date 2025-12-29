# 🎸 TUNE UP

#### Video Demo:
https://youtu.be/RFVA44-iGLw

#### Description:

TuneUp! is a web-based guitar and ukulele tuner built using **HTML, CSS, and JavaScript**. The goal of this project was to create a functional, real-time musical instrument tuner that runs entirely in the browser, using the device’s microphone to capture sound and analyze pitch. This project combines concepts from audio signal processing, mathematics, and front-end web development, resulting in a practical and educational application.

The idea for TuneUp! came from my own experience as a beginner guitar player. While learning how to tune my instrument, I became curious about how tuners actually work. I wanted to understand how sound captured from a microphone could be transformed from an analog signal into digital data, how frequencies are detected, and how those frequencies are translated into musical notes. Instead of using an existing library or API, I decided to implement the core logic myself in JavaScript to better understand the underlying principles.

TuneUp! supports two instruments: **guitar** and **ukulele**, each with their standard tunings. The interface is minimal, intuitive, and responsive, providing immediate visual feedback through colors and a tuning ruler that indicates whether the note is flat, sharp, or in tune.

---

## 🗂 Project Structure

This project consists of two main files:

- `index.html`
- `styles.css`

All functionality and styling are contained within these two files, making the project lightweight and easy to run locally or deploy on any static hosting service.

---

## 🧠 HTML and JavaScript Logic (`index.html`)

The `index.html` file contains both the structure of the webpage and the JavaScript logic responsible for audio capture and pitch detection. The HTML defines the layout, including the title, instrument selection buttons, tuning information, frequency and note displays, and a visual tuning ruler.

The JavaScript section is where most of the project’s complexity lies. The tuner uses the **Web Audio API**, specifically `navigator.mediaDevices.getUserMedia`, to access the user’s microphone. Once permission is granted, an `AudioContext` and an `AnalyserNode` are created to process the incoming audio stream in real time.

To detect pitch, the project implements an **auto-correlation algorithm**. This method analyzes the waveform data from the microphone and estimates the fundamental frequency of the sound. Auto-correlation was chosen because it is reliable for monophonic signals such as a single guitar or ukulele string and does not require external dependencies.

After determining the frequency, the application converts it into a musical note using a mathematical relationship based on the **equal-tempered scale**, with **A4 = 440 Hz** as the reference. The frequency is mapped to a MIDI note number, which is then translated into a note name and octave (e.g., `E2`, `A4`, etc.).

The tuner also calculates the **cents difference**, which represents how far the detected frequency is from the exact pitch of the target note. This value is used to move the tuning needle left or right and to determine the color of the note display:

- **Green** when the note is in tune  
- **Yellow** when it is slightly off  
- **Red** when it is significantly out of tune  

A short *hold mechanism* was implemented to prevent the display from flickering when sound input briefly drops. This improves usability and creates a smoother user experience.

---

## 🎛 Instrument Selection and Design Choices

One important design decision was to include support for both guitar and ukulele. This is implemented through instrument selection buttons that dynamically update the displayed standard tuning. The tuning data is stored in a simple JavaScript object, making it easy to extend the project to additional instruments in the future.

Another deliberate choice was to keep all JavaScript inside the HTML file. While separating scripts into different files is often recommended for large applications, keeping everything in one file made this project easier to manage and review as a learning exercise.

The user interface was designed to be minimal and distraction-free. Since tuning requires focus and clarity, unnecessary elements were avoided. The visual ruler and needle were chosen instead of more complex graphics to clearly communicate pitch deviation in a familiar, tuner-like format.

---

## 🎨 CSS Styling (`styles.css`)

The `styles.css` file controls the visual appearance of the application. A dark theme was chosen to reduce eye strain and to resemble physical electronic tuners commonly used by musicians. High-contrast colors make the frequency and note information easy to read.

Color feedback plays a central role in usability. The CSS classes:

- `.in-tune`
- `.slightly-off`
- `.out-of-tune`

dynamically change the note color based on tuning accuracy. This allows users to understand their tuning status instantly, even without focusing on the numeric values.

Buttons and interactive elements include subtle hover effects and transitions to improve responsiveness and user experience. The tuning ruler and needle are styled using simple `div` elements and CSS positioning, demonstrating that effective visual feedback can be achieved without complex graphics or external libraries.

---

## ✅ Conclusion

TuneUp! is both a practical tool and a learning project. It demonstrates how modern web technologies can interact with hardware, process real-time audio, and apply mathematical concepts in a meaningful way. By building the tuner from scratch, I gained a deeper understanding of audio processing, frequency analysis, and browser-based APIs.
