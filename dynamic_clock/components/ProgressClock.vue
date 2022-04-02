<template>
  <div class="position-absolute container-fluid mt-2">
    <div id="clock" class="progress-clock mx-auto">
      <button class="progress-clock-time-date" data-group="d" type="button">
        <small data-unit="w">Sunday</small><br />
        <span data-unit="mo">January</span>
        <span data-unit="d">1</span>
      </button>
      <button
        class="progress-clock-time-digit"
        data-unit="h"
        data-group="h"
        type="button"
      >
        12</button
      ><span class="progress-clock-time-colon">:</span
      ><button
        class="progress-clock-time-digit"
        data-unit="m"
        data-group="m"
        type="button"
      >
        00</button
      ><span class="progress-clock-time-colon">:</span
      ><button
        class="progress-clock-time-digit"
        data-unit="s"
        data-group="s"
        type="button"
      >
        00
      </button>
      <span class="progress-clock-time-ampm" data-unit="ap">AM</span>
      <svg
        class="progress-clock-rings"
        width="256"
        height="256"
        viewBox="0 0 256 256"
      >
        <defs>
          <linearGradient id="pc-red" x1="1" y1="0.5" x2="0" y2="0.5">
            <stop offset="0%" stop-color="#f953c6" />
            <stop offset="100%" stop-color="#b91d73" />
          </linearGradient>
          <linearGradient id="pc-yellow" x1="1" y1="0.5" x2="0" y2="0.5">
            <stop offset="0%" stop-color="#00B4DB" />
            <stop offset="100%" stop-color="#0083B0" />
          </linearGradient>
          <linearGradient id="pc-blue" x1="1" y1="0.5" x2="0" y2="0.5">
            <stop offset="0%" stop-color="#8E2DE2" />
            <stop offset="100%" stop-color="#4A00E0" />
          </linearGradient>
          <linearGradient id="pc-purple" x1="1" y1="0.5" x2="0" y2="0.5">
            <stop offset="0%" stop-color="#FF416C" />
            <stop offset="100%" stop-color="#FF4B2B" />
          </linearGradient>
        </defs>
        <!-- Days of Month -->
        <g data-units="d">
          <circle
            class="progress-clock-ring"
            cx="128"
            cy="128"
            r="74"
            fill="none"
            opacity="0.1"
            stroke="url(#pc-red)"
            stroke-width="12"
          />
          <circle
            class="progress-clock-ring-fill"
            data-ring="mo"
            cx="128"
            cy="128"
            r="74"
            fill="none"
            stroke="url(#pc-red)"
            stroke-width="12"
            stroke-dasharray="465 465"
            stroke-dashoffset="465"
            stroke-linecap="round"
            transform="rotate(-90,128,128)"
          />
        </g>
        <!-- Hours of Day -->
        <g data-units="h">
          <circle
            class="progress-clock-ring"
            cx="128"
            cy="128"
            r="90"
            fill="none"
            opacity="0.1"
            stroke="url(#pc-yellow)"
            stroke-width="12"
          />
          <circle
            class="progress-clock-ring-fill"
            data-ring="d"
            cx="128"
            cy="128"
            r="90"
            fill="none"
            stroke="url(#pc-yellow)"
            stroke-width="12"
            stroke-dasharray="565.5 565.5"
            stroke-dashoffset="565.5"
            stroke-linecap="round"
            transform="rotate(-90,128,128)"
          />
        </g>
        <!-- Minutes of Hour -->
        <g data-units="m">
          <circle
            class="progress-clock-ring"
            cx="128"
            cy="128"
            r="106"
            fill="none"
            opacity="0.1"
            stroke="url(#pc-blue)"
            stroke-width="12"
          />
          <circle
            class="progress-clock-ring-fill"
            data-ring="h"
            cx="128"
            cy="128"
            r="106"
            fill="none"
            stroke="url(#pc-blue)"
            stroke-width="12"
            stroke-dasharray="666 666"
            stroke-dashoffset="666"
            stroke-linecap="round"
            transform="rotate(-90,128,128)"
          />
        </g>
        <!-- Seconds of Minute -->
        <g data-units="s">
          <circle
            class="progress-clock-ring"
            cx="128"
            cy="128"
            r="122"
            fill="none"
            opacity="0.1"
            stroke="url(#pc-purple)"
            stroke-width="12"
          />
          <circle
            class="progress-clock-ring-fill"
            data-ring="m"
            cx="128"
            cy="128"
            r="122"
            fill="none"
            stroke="url(#pc-purple)"
            stroke-width="12"
            stroke-dasharray="766.5 766.5"
            stroke-dashoffset="766.5"
            stroke-linecap="round"
            transform="rotate(-90,128,128)"
          />
        </g>
      </svg>
    </div>
  </div>
</template>

<style scoped>
* {
  text-align: center;
  border: 0;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

:root {
  --bg-color: #fff;
}

body,
button {
  color: #b91d73;
  font: 1em;
}

body {
  background-color: var(--bg-color);
  height: 100vh;
  display: grid;
  place-items: center;
}

.progress-clock {
  display: grid;
  justify-content: center;
  align-content: center;
  position: relative;
  text-align: center;
  width: 16em;
  height: 16em;
}

.progress-clock-time-date,
.progress-clock-time-digit,
.progress-clock-time-colon,
.progress-clock-time-ampm {
  transition: color 0.2s linear;

  /* -webkit-user-select: auto;
  -moz-user-select: none;
  user-select: none; */
}

.progress-clock-time-date,
.progress-clock-time-digit {
  background: transparent;
}

.progress-clock-time-date,
.progress-clock-time-ampm {
  grid-column: 1 / 6;
}

.progress-clock-time-date {
  font-size: 0.75em;
  line-height: 1.33;
}

.progress-clock-time-digit,
.progress-clock-time-colon {
  font-size: 2em;
  font-weight: 400;
  grid-row: 2;
}

.progress-clock-time-colon {
  line-height: 1.275;
}

.progress-clock-time-ampm {
  cursor: default;
  grid-row: 3;
}

.progress-clock-rings {
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
}

.progress-clock-ring {
  opacity: 0.1;
}

.progress-clock-ring-fill {
  transition: opacity 0s 0.3s linear, stroke-dashoffset 0.3s ease-in-out;
}

.progress-clock-ring-fill-360 {
  opacity: 0;
  stroke-dashoffset: 0;
  transition-duration: 0.3s;
}
</style>

<script>
</script>
