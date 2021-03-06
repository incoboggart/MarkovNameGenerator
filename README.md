[![Markov Namegen logo](https://github.com/Tw1ddle/MarkovNameGenerator/blob/master/screenshots/markovnamegen_logo.png?raw=true "Markov Namegen Procedural Random Name Generator Project logo")](https://www.samcodes.co.uk/project/markov-namegen/)

[![Travis Build Status](https://img.shields.io/travis/Tw1ddle/MarkovNameGenerator.svg?style=flat-square)](https://travis-ci.org/Tw1ddle/MarkovNameGenerator)
[![License Badge](https://licensebuttons.net/l/by-nc/4.0/80x15.png)](https://github.com/Tw1ddle/MarkovNameGenerator/blob/master/LICENSE)

Markov Namegen is a Markov chain-based procedural name generator written in Haxe. Run it [in your browser](https://www.samcodes.co.uk/project/markov-namegen/).

Demonstrates the [markov-namegen haxelib](https://lib.haxe.org/p/markov-namegen). Read the docs [here](https://tw1ddle.github.io/MarkovNameGenerator/).

## Features
* Hundreds of editable training data presets.
* Configurable corpus, order and prior model parameter settings.
* Filter results by length, start, end, content and regex match.
* Sort by Damerau-Levenshtein distance to list results by similarity.
* Save and share custom data, settings and results with one click.

## Usage

Try the [demo](https://www.samcodes.co.uk/project/markov-namegen/) to generate your own words. For example:

```
Training Dataset: English Towns
Order: 5
Prior: 0.01
Words To Generate: 100
Max Processing Time: 500ms
Length: 8-12
Starts with: b
Ends with:
Include: ham
Exclude:
Similarity To: birmingham
Matches Regex:
```

A list of results will be displayed. Here are the first 10 results from this run:
```
Barkingham
Basingham
Birkenham
Bebingham
Bollingham
Bridlingham
Billenham
Berwickham
Botteringham
Bradnincham
```

Hit one of the sharing buttons to share results and settings via a generated URL. Note that large training data sets generate URLs too long for some browsers and servers - reduce the amount of training data to work around this.

## Screenshots
Here is the demo in action:

[![Screenshot](https://github.com/Tw1ddle/MarkovNameGenerator/blob/master/screenshots/screenshot1.png?raw=true "Markov Namegen Procedural Random Name Generator screenshot 1")](https://www.samcodes.co.uk/project/markov-namegen/)

[![Screenshot](https://github.com/Tw1ddle/MarkovNameGenerator/blob/master/screenshots/screenshot2.png?raw=true "Markov Namegen Procedural Random Name Generator screenshot 2")](https://www.samcodes.co.uk/project/markov-namegen/)

[![Screenshot](https://github.com/Tw1ddle/MarkovNameGenerator/blob/master/screenshots/screenshot3.png?raw=true "Markov Namegen Procedural Random Name Generator screenshot 3")](https://www.samcodes.co.uk/project/markov-namegen/)

## How It Works

The [markov-namegen haxelib](https://lib.haxe.org/p/markov-namegen) uses [Markov chains](https://en.wikipedia.org/wiki/Markov_chain) to procedurally generate original words.

Using a set of words as [training data](https://en.wikipedia.org/wiki/Machine_learning), the library calculates the conditional probability of a letter coming up after a sequence of letters chosen so far. It looks back up to "n" characters, where "n" is the order of the model.

The generator can use several orders of models, each with memory n. Starting with the highest order models (models with bigger memories), it tries to get a new character, falling back to lower order models if necessary - an approach known as [Katz's back-off model](https://en.wikipedia.org/wiki/Katz%27s_back-off_model).

A [Dirichlet prior](https://en.wikipedia.org/wiki/Dirichlet_distribution#Special_cases) is used to add a constant probability that any letter may be picked as the next letter. This acts as an additive smoothing factor and adds a bit more "randomness" to the generated output.

Countless words are generated, and are then filtered and sorted according to several tweakable criteria like length, start and end characters, [similarity to a target word](https://en.wikipedia.org/wiki/Levenshtein_distance), and so on.

## Library Install

Get the Markov Namegen library from [GitHub](https://github.com/Tw1ddle/MarkovNameGenerator/tree/master/lib) or through [haxelib](https://lib.haxe.org/p/markov-namegen/).

Include it in your ```.hxml```
```
-lib markov-namegen
```

Or add it to your ```Project.xml```:
```
<haxelib name="markov-namegen" />
```

## Notes
* Many of the concepts used for the generator were suggested in [this article](http://www.roguebasin.com/index.php?title=Names_from_a_high_order_Markov_Process_and_a_simplified_Katz_back-off_scheme) by Jeffrey Lund.
* If you have any questions or suggestions then [get in touch](https://twitter.com/Sam_Twidale) or open an issue.
* Remember to read the [documentation](https://tw1ddle.github.io/MarkovNameGenerator/).

## License
The website and demo code are licensed under CC BY-NC. The [haxelib library](https://lib.haxe.org/p/markov-namegen/) itself is MIT licensed. The noUiSlider settings sliders are WTFPL. Most of the training data was compiled from sites like Wikipedia and census data sources.
