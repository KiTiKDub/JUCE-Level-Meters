# Level Meters for JUCE Plugins
![Level Meter Demo](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExNnBrZHdybnQwMGxqbDMwODQ4Z3kzenVpNHFvYmw1cHFuOHducjFuMCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/SuO2tDYOqs4zhAJQPo/giphy-downsized-large.gif)

This repo is starting point to create level meters within your JUCE plugin. The basic processing of getting rms values is found in the `LevelMeterData.h`. To store your RMS values for your plugin, simply declare a `LevelMeterData` Object and call the `process` method in your `processBlock`.

## Audio Processing
The `process` method takes three arguments, `bool inOrOut`, `int channel`, and your audio buffer from the `processBlock`.

Set `bool inOrOut` to true to store your pre processed audio rms level, set to false for the output. You will need to call this method twice, once before you process, and once after.
`int channel` is the channel of the audio. You can run this in a for loop, or call as many times as you need.
Finally, pass the audio buffer for the third argument.

## Paint to GUI
Declare your `Level Meter` objects (typically 4) in the header of your GUI file. Make visible and place in your resize area as you would any other component. A snipet of code is placed in the repo that can be used in the `timerCallback` method to repaint your meters with the RMS Value. Make sure your Editor Component is inheriting from juce::Timer, as well as making sure that the `startTimerHz` method is called in your constructor.