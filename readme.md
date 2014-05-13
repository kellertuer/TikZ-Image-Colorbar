# TikZ Image Colorbar

This small snippet adds the functionality to place a colorbar besides a 
TikZ node and hence an image.

## Commands

### `\NodeColorbar`
`\NodeColorbar` adds a colorbar to the node specifyed by the key `node`. This
node should be set `anchor=south west` (up to now). The Colorbar is then placed
besides (left) to the node adopting its height.

#### Further Keys available
* `node` name of the node, the colorbar is placed relative to; this argument
	is mandatory
* `position` (0.05) position with respect to the right side of the node given
	in percent of the nodes width,
		i.e. the standard value leaves 5% between the nodes border and the center
		of the colorbar
* `width` (0.025) complete width of the colorbar, i.e. width/2 to the left and
	right of the position determines the width (hence position-width/2 should be
	greater than 0)
* `colorbar` provide your own colorbar manually (you also can add this to the
	`colors` key, see next), by specifying each color fading yourself with four
	values: startvalue/startcolor/endvalue/endcolor, where start and endvalue are
	in [0,1] and the colors are xcolors
* `colors` sets the `colorbar` key directly with predefined styles, which are up
	to now
	* `gray` black (0) to white (1) colorbar
	* `hsv` the colormap `hsv` as provided by MatLab, i.e. the hue range of the
		HSV color space
	* `jet` the `colormap jet` provided by MatLab
	* `rwb` from red (0) to white (0.5) to blue (1)
* `y range` specify the range of the values the colorsbar indicates, given in
	the form `min to max`. Specifying this value activates the short form (see
	`y ticks` below)
* `y tick at border` (false) put ticks at the borders (0,1) of the colorbar.
	This value only has effect if the short form is activated (see `y ticks`). If
	it is `false` these is half a tick space left at each border
* `y ticks` There are two possibilities to specify ticks
	1. short form. By specifying `y range`, this value should be an integer
		specifying the number of ticks to be used. Together with `y tick at border`
		this determines the positions and values of the ticks. Each tick is
		printed using `\pgfmathprintnumber`, see their documentation to change the
		appearance of numbers.
	2. each tick is given as a tuple position/label, where position is relative,
		i.e. a value in [0,1] and label is a text or math to be displayed at the
		ticks end

### `\includegraphicsWithColorbar`
Combines the `\NodeColorbar` and provides an interface to directly specify the
image to be included. There are 3 Parameters, the first two are optional. The
parameters are

1. the keys given to `\NodeColorbar` (see last section).
2. the keys given to `\includegraphics` such as `width=` or `height=` and is 
	optional similar to the one of the command itself.
3. the path to the image, cf. the second parameter of `\includegraphics`

### Available Styling Arguments
* `ICBFrame` styling of the frame surrounding the colorbar
* `ICBImage` in the `\includegraphicsWithColorbar`, these keys are added to the
	node containing the image
* `ICBLabel` styling for the labels at each tick.
* `ICBTick` styling for the ticks

## Limitations & Possible Extensions
* works up to now only if the node is set `anchor=south west`
* in certain ranges (i.e. -0.5 to 0.5) there are rounding errors, when
	specifying an odd number of ticks for the value of 0.

## License
This small code snipped is published under the Beer/Coffee ware license as
proposed by Poul-Henning Kamp.

	% THE BEER-WARE LICENSE (Rev. 42):
	% Ronny Bergmann <mail@rbergmann.info> wrote this file. As long as
	% you retain this notice you can do whatever you want with this stuff. If we
	% meet some day, and you think this stuff is worth it, you can buy me a beer
	% or coffee in return.

