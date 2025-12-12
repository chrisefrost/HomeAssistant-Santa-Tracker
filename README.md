# 🎅 Santa Tracker for Home Assistant

A festive Home Assistant integration that tracks Santa's journey on Christmas Eve using the Google Santa Tracker API, complete with AI-generated CCTV footage from the North Pole!

![Santa Tracker Dashboard](images/santa-tracker-dashboard.gif)

## ✨ Features

- **Real-time Santa Tracking**: Live updates of Santa's current location using Google's Santa Tracker API
- **CCTV Footage**: Looping video player displaying AI-generated "security camera" footage from the North Pole
- **Journey Statistics**: Track key metrics including:
  - Countries visited
  - Next destinations
  - Presents delivered
  - Pies eaten
  - And more festive data!

## 📋 Prerequisites

- Home Assistant installation
- Access to your Home Assistant configuration files
- Video files for the CCTV loop (examples included, or create your own)

## 🚀 Installation

### 1. File Structure

Copy the following files to their respective directories in your Home Assistant configuration:

```
config/
├── automations/
│   └── cctv_loop_player.yaml
├── templates/
│   └── santa_tracker.yaml
├── configuration.yaml (merge the provided snippet)
└── www/
    └── media/
        ├── a1.mp4
        ├── a2.mp4
        ├── a3.mp4
        └── ... (additional videos)
```

### 2. Configuration Steps

1. **Copy the automation file**
   - Place `cctv_loop_player.yaml` in your `automations/` directory

2. **Copy the template file**
   - Place `santa_tracker.yaml` in your `templates/` directory

3. **Update your configuration.yaml**
   - Add the snippet from the provided `configuration.yaml` to your main configuration file

4. **Create the input_text helper** (REQUIRED)
   - Go to Settings → Devices & Services → Helpers
   - Click "Create Helper" → Text
   - Name it: `random_video_filename`
   - Leave the initial value blank (the automation will populate it)
   - This helper stores the current video filename for the CCTV loop

5. **Add media files**
   - Create a `media/` folder inside your `www/` directory
   - Copy the provided video files (or add your own) to `www/media/`
   - Name your videos sequentially: `a1.mp4`, `a2.mp4`, `a3.mp4`, etc.

6. **Restart Home Assistant**
   - Restart Home Assistant to load the new configuration

## 🎥 Adding More Videos

The CCTV loop player cycles through your video files randomly. To add more videos:

1. Name your new videos following the sequence: `a4.mp4`, `a5.mp4`, `a6.mp4`, etc.
2. Place them in the `www/media/` directory
3. Update the `cctv_loop_player.yaml` file:

Find this line:
```yaml
{% set max_val = 3 %}
```

Change it to match your highest video number. For example, if you have 34 videos:
```yaml
{% set max_val = 34 %}
```

## 🎬 Creating Your Own Videos

The included sample videos were created using GROK AI to generate CCTV-style footage mimicking security cameras at the North Pole. Feel free to:
- Use the provided examples
- Generate your own using AI tools
- Record your own festive footage
- Mix and match different sources

Just ensure they're in MP4 format and follow the naming convention (`a1.mp4`, `a2.mp4`, etc.).
I also reduce size and remove audio from the videos GROK creates using;
```yaml
ffmpeg -i input.mp4 -an -vf scale=iw/2:-1 output.mp4
```

## 📊 Data Tracked

The Santa Tracker displays various metrics from Google's Santa Tracker API:
- Current location
- Countries visited count
- Next destination(s)
- Total presents delivered
- Pies eaten by Santa
- Distance traveled
- Arrival times

## 🎄 Usage

Once installed and configured, the Santa Tracker will automatically become available in your Home Assistant dashboard. Add the entities to your Lovelace UI to display Santa's current status and the CCTV feed.

## 🤝 Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.
Also there is a post on Reddit https://www.reddit.com/r/homeassistant/comments/1pkq695/santa_tracker/

## 📝 License

This project is provided as-is for personal use. The Google Santa Tracker API is provided by Google.

## 🎅 Credits

- **Google Santa Tracker API**: For providing the real-time Santa tracking data
- **GROK AI**: Used to generate the sample CCTV footage
- **Community**: Thanks to the Home Assistant community for inspiration

---

**Merry Christmas and Happy Tracking! 🎄✨**
