# Portable Weather Station
I chose the portable weather station because at first I thought it was a really asthetic looking machine and when I saw it I thought I could maybe take it further like adding a alarm clock or being able to add the radio on it or since it will be connected to the internet I can add wallpapers and maybe even bluetooth. I saw so many possibilitys within this project and knew I had to choose it.


<!--- This is an HTML comment in Markdown -->
<!--- You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML -->
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->


| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Srinivas KV | Moreau Catholic Highschool | CS | Incoming Sophmore

<!--- <!DOCTYPE html> -->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
</head>
<body>
    <img src="Srini (1).jpg" alt="Description of the image" style="width: 200px; height: 250px;">
</body>
</html>
<div class="sixteen-by-nine-container"></div>


  
# Final Milestone

 <!--- **Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.** -->

<iframe width="560" height="315" src="https://www.youtube.com/embed/Q4zouhd0b40?si=aiF6BbjEz-n0E7XG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

For my third and final milestone, I installed the case for the board. My biggest challenge was that I wanted to use a 3D-printed case, but the screw holes weren't all the same size, so I had to use the default one from the kit. Additionally, the stickers were very difficult to remove because I have no nails. My biggest triumph at BSE was actually creating a working machine, despite struggling and making many mistakes along the way. In the future, I hope to learn more about building intricate machines and explore more projects.


# Second Milestone

<!--- **Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.** -->

<iframe width="560" height="315" src="https://www.youtube.com/embed/uKa1C4XUtzY?si=sODOz5yk6ktykRSA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<!-- For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone -->

For my second milestone, I focused on running and testing the code. It failed a few times, but by carefully troubleshooting, I eventually got it to work. In my first milestone, I struggled with the code and where to place it, but after thoroughly following the instructions, I managed to get it running. For my final milestone, I need to install the case for the board.


# First Milestone

<!-- **Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.** -->

<iframe width="560" height="315" src="https://www.youtube.com/embed/xr4JSieIGDQ?si=Cr2bdL1JQDSTqnhS" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

In my first milestone, I focused on placing the code in the correct locations and organizing the files. I used Python as my programming language. My main challenge was not placing the code correctly and having too many code.py files, which caused confusion about where the main code should go. I had to restart six times, with the last attempt nearly complete, but I persevered and asked for help when needed. After successfully organizing the code, the next step was running it on the board.


# Starter Project


<iframe width="560" height="315" src="https://www.youtube.com/embed/_VXxgNMKxaE?si=erfkqwNb2pGp1LlU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>



# Description

For my starter project, I chose to build a calculator because I thought it would be a cool way to understand the basic mechanics of a device we use for simple math calculations every day. The process was quite challenging: I initially mixed up the steps, which took a while to correct, and my soldering iron was subpar, making it difficult to melt the solder wire properly. Additionally, assembling the plates was very frustrating due to the tiny and loose screws. Despite these obstacles, the experience was bittersweet. Completing the project and seeing the calculator work was incredibly satisfying, making all the effort and frustration worthwhile.


# Schematics 
 <img width="652" alt="Screenshot 2024-06-21 at 11 02 43 AM" src="https://github.com/SriniKV58804/Srini_BlueStamp_Portfolio/assets/172419240/aa0631a3-d5e2-43ae-887b-5a52f30b43e9">


# Code
<!-- Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. -->

Code.py:

```python
# SPDX-FileCopyrightText: 2019 Limor Fried for Adafruit Industries
#
# SPDX-License-Identifier: MIT

"""
This example queries the Open Weather Maps site API to find out the current
weather for your location... and display it on a screen!
if you can find something that spits out JSON data, we can display it
"""
import sys
import time
import board
from adafruit_pyportal import PyPortal
cwd = ("/"+__file__).rsplit('/', 1)[0] # the current working directory (where this file is)
sys.path.append(cwd)
import openweather_graphics  # pylint: disable=wrong-import-position

# Get wifi details and more from a secrets.py file
try:
    from secrets import secrets
except ImportError:
    print("WiFi secrets are kept in secrets.py, please add them there!")
    raise

# Use cityname, country code where countrycode is ISO3166 format.
# E.g. "New York, US" or "London, GB"
LOCATION = "Fremont , US"

# Set up where we'll be fetching data from
DATA_SOURCE = "http://api.openweathermap.org/data/2.5/weather?q="+LOCATION
DATA_SOURCE += "&appid="+secrets['openweather_token']
# You'll need to get a token from openweather.org, looks like 'b6907d289e10d714a6e88b30761fae22'
DATA_LOCATION = []


# Initialize the pyportal object and let us know what data to fetch and where
# to display it
pyportal = PyPortal(url=DATA_SOURCE,
                    json_path=DATA_LOCATION,
                    status_neopixel=board.NEOPIXEL,
                    default_bg=0x000000)

gfx = openweather_graphics.OpenWeather_Graphics(pyportal.splash, am_pm=True, celsius=False)

localtile_refresh = None
weather_refresh = None
while True:
    # only query the online time once per hour (and on first run)
    if (not localtile_refresh) or (time.monotonic() - localtile_refresh) > 3600:
        try:
            print("Getting time from internet!")
            pyportal.get_local_time()
            localtile_refresh = time.monotonic()
        except RuntimeError as e:
            print("Some error occured, retrying! -", e)
            continue

    # only query the weather every 10 minutes (and on first run)
    if (not weather_refresh) or (time.monotonic() - weather_refresh) > 600:
        try:
            value = pyportal.fetch()
            print("Response is", value)
            gfx.display_weather(value)
            weather_refresh = time.monotonic()
        except RuntimeError as e:
            print("Some error occured, retrying! -", e)
            continue

    gfx.update_time()
    time.sleep(30)  # wait 30 seconds before updating anything again

```
secret.py:

```python

# This file is where you keep secret settings, passwords, and tokens!
# If you put them in the code you risk committing that info or sharing it

  
```
openweather_graphics:

```python

# SPDX-FileCopyrightText: 2019 Limor Fried for Adafruit Industries
#
# SPDX-License-Identifier: MIT

import time
import json
import displayio
from adafruit_display_text.label import Label
from adafruit_bitmap_font import bitmap_font

cwd = ("/"+__file__).rsplit('/', 1)[0] # the current working directory (where this file is)

small_font = cwd+"/fonts/Arial-12.bdf"
medium_font = cwd+"/fonts/Arial-16.bdf"
large_font = cwd+"/fonts/Arial-Bold-24.bdf"

class OpenWeather_Graphics(displayio.Group):
    def __init__(self, root_group, *, am_pm=True, celsius=True):
        super().__init__()
        self.am_pm = am_pm
        self.celsius = celsius

        root_group.append(self)
        self._icon_group = displayio.Group()
        self.append(self._icon_group)
        self._text_group = displayio.Group()
        self.append(self._text_group)

        self._icon_sprite = None
        self._icon_file = None
        self.set_icon(cwd+"/weather_background.bmp")

        self.small_font = bitmap_font.load_font(small_font)
        self.medium_font = bitmap_font.load_font(medium_font)
        self.large_font = bitmap_font.load_font(large_font)
        glyphs = b'0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ-,.: '
        self.small_font.load_glyphs(glyphs)
        self.medium_font.load_glyphs(glyphs)
        self.large_font.load_glyphs(glyphs)
        self.large_font.load_glyphs(('°',))  # a non-ascii character we need for sure
        self.city_text = None

        self.time_text = Label(self.medium_font)
        self.time_text.x = 200
        self.time_text.y = 12
        self.time_text.color = 0xFFFFFF
        self._text_group.append(self.time_text)

        self.temp_text = Label(self.large_font)
        self.temp_text.x = 200
        self.temp_text.y = 195
        self.temp_text.color = 0xFFFFFF
        self._text_group.append(self.temp_text)

        self.main_text = Label(self.large_font)
        self.main_text.x = 10
        self.main_text.y = 195
        self.main_text.color = 0xFFFFFF
        self._text_group.append(self.main_text)

        self.description_text = Label(self.small_font)
        self.description_text.x = 10
        self.description_text.y = 225
        self.description_text.color = 0xFFFFFF
        self._text_group.append(self.description_text)

    def display_weather(self, weather):
        weather = json.loads(weather)

        # set the icon/background
        weather_icon = weather['weather'][0]['icon']
        self.set_icon(cwd+"/icons/"+weather_icon+".bmp")

        city_name =  weather['name'] + ", " + weather['sys']['country']
        print(city_name)
        if not self.city_text:
            self.city_text = Label(self.medium_font, text=city_name)
            self.city_text.x = 10
            self.city_text.y = 12
            self.city_text.color = 0xFFFFFF
            self._text_group.append(self.city_text)

        self.update_time()

        main_text = weather['weather'][0]['main']
        print(main_text)
        self.main_text.text = main_text

        temperature = weather['main']['temp'] - 273.15 # its...in kelvin
        print(temperature)
        if self.celsius:
            self.temp_text.text = "%d °C" % temperature
        else:
            self.temp_text.text = "%d °F" % ((temperature * 9 / 5) + 32)

        description = weather['weather'][0]['description']
        description = description[0].upper() + description[1:]
        print(description)
        self.description_text.text = description
        # "thunderstorm with heavy drizzle"

    def update_time(self):
        """Fetch the time.localtime(), parse it out and update the display text"""
        now = time.localtime()
        hour = now[3]
        minute = now[4]
        format_str = "%d:%02d"
        if self.am_pm:
            if hour >= 12:
                hour -= 12
                format_str = format_str+" PM"
            else:
                format_str = format_str+" AM"
            if hour == 0:
                hour = 12
        time_str = format_str % (hour, minute)
        print(time_str)
        self.time_text.text = time_str

    def set_icon(self, filename):
        """The background image to a bitmap file.

        :param filename: The filename of the chosen icon

        """
        print("Set icon to ", filename)
        if self._icon_group:
            self._icon_group.pop()

        if not filename:
            return  # we're done, no icon desired

        # CircuitPython 6 & 7 compatible
        if self._icon_file:
            self._icon_file.close()
        self._icon_file = open(filename, "rb")
        icon = displayio.OnDiskBitmap(self._icon_file)
        self._icon_sprite = displayio.TileGrid(
            icon, pixel_shader=getattr(icon, 'pixel_shader', displayio.ColorConverter()))

        # # CircuitPython 7+ compatible
        # icon = displayio.OnDiskBitmap(filename)
        # self._icon_sprite = displayio.TileGrid(icon, pixel_shader=background.pixel_shader)

        self._icon_group.append(self._icon_sprite)
```
settings.toml:

```python

#this file contains the wifi ssid and password and connects the board to the internet which is the first step in it accesing the weather data

```


# Bill of Materials
<!-- Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. --> 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Adafruit PyPortal - CircuitPython Powered Internet Display | this item is the main board which does everything which connects to the internet and displays the weather data | $54.95 | <a href="https://www.adafruit.com/product/4116/"> Link </a> |
| USB A/Micro Cable - 2m | This is used to connect the board to the computer or power on in general | $4.95| <a href="https://www.adafruit.com/product/2185/"> Link </a> |
| Black Nylon Machine Screw and Stand-off Set – M2.5 Thread | the screws are used to put the stand together | $16.95 | <a href="https://www.adafruit.com/product/3299/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here. 
