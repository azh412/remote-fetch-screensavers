# remote-fetch-screensavers: Rotating YouTube Livestream Screensaver

A simple, self-contained HTML file that turns a list of YouTube livestreams into a dynamic, rotating screensaver for macOS using the [WebViewScreenSaver](https://github.com/liquidx/webviewscreensaver) extension.

## What It Does

This project provides a single `index.html` file that, when hosted online (for free via GitHub Pages), serves as a "control panel" for your screensaver. It randomly selects a YouTube livestream from a predefined list and displays it. After a configurable amount of time, it automatically and seamlessly switches to another random livestream.

### Features

-   **Random on Start:** Never see the same screensaver twice in a row.
-   **Automatic Rotation:** Keeps the content fresh by switching streams at a set interval.
-   **Seamless Transitions:** Uses an `<iframe>` to change videos without a jarring full-page reload.
-   **Highly Configurable:** Easily change the rotation time and the list of videos by editing one file.
-   **Zero Cost:** Runs entirely on free GitHub Pages hosting.
-   **Clean View:** The YouTube embed URLs are configured to hide controls and autoplay silently.

## How to Use

#### Step 1: Install the Screensaver Extension

-   You must have [WebViewScreenSaver](https://github.com/liquidx/webviewscreensaver/releases) installed on your Mac. Download the `WebViewScreenSaver.saver.zip` file from the latest release, unzip it, right-click `WebViewScreenSaver.saver`, and choose **Open** to install it.

#### Step 2: Configure Your `index.html`

-   Edit the `index.html` file in this repository to customize the rotation interval and your list of desired YouTube livestreams. (See the "Customization" section below for details).
-   Commit and push your changes.

#### Step 3: Get Your Live URL

-   This repository is designed to be hosted on GitHub Pages.
-   Go to your repository's **Settings** > **Pages**.
-   Set the **Source** to **Deploy from a branch**, using the `main` branch and `/ (root)` folder.
-   After a minute, GitHub will provide you with a live URL, like: `https://your-username.github.io/your-repository-name/`

#### Step 4: Set Up macOS Screen Saver

1.  Open **System Settings** > **Screen Saver**.
2.  Select **WebViewScreenSaver** from the list.
3.  Click **Screen Saver Options...**.
4.  Remove any existing URLs and add **only one**: your live GitHub Pages URL from Step 3.
5.  Click **OK**.

Your screensaver will now load your custom rotating livestream display every time it activates.

## Customization

All configuration is done by editing the `<script>` section inside the `index.html` file.

### Changing the Rotation Time

Modify the `rotationIntervalInMinutes` constant. You can use decimals for periods shorter than a minute (e.g., `0.5` for 30 seconds).

```javascript
// 1. Set the rotation interval in minutes.
const rotationIntervalInMinutes = 5; // Changed to 5 minutes
```

### Changing the Video List

Add or remove YouTube URLs from the `screensavers` array.

**Important:** You must use the special `embed` URL format to ensure the videos autoplay correctly and are clean. The format is:
`https://www.youtube.com/embed/VIDEO_ID?autoplay=1&mute=1&controls=0`

```javascript
// 2. Add your list of YouTube livestream URLs here.
const screensavers = [
  // Live View of Earth from ISS (example)
  'https://www.youtube.com/embed/86YLFOog4GM?autoplay=1&mute=1&controls=0',
  // Add your new URL here, with a comma after the previous one.
  'https://www.youtube.com/embed/SOME_NEW_VIDEO_ID?autoplay=1&mute=1&controls=0'
];
```

## License

This project is open source and available under the [MIT License](LICENSE).

-azh
