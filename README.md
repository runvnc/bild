# Bild

Yet another build/task runner.  This one is based on YAML.  I like the declarative nature of grunt, but it seems a bit heavyweight to 
install, and the way things work is more complicated than I need.  This is simpler and needs less boilerplate.

## Installation

`npm install -g bild` (may require sudo).

## Usage

Include `bild` plus whatever plugins (for example `bild-coffee` and `bild-uglify`) in the package.json under `devDependencies`.
Run `npm install` (may require sudo).

Create a file called bild.yaml in the project directory formatted as a list like this:

```yaml
- coffee:
    files: src/*.coffee
    out: lib
- uglify: 
    files: public/js/*.js
    out: public/js/min.js
```

Run the command `bild` to compile some files to coffeescript and minify some other files.

## Plugins

Plugins are npm modules named `bild-whatever` where "whatever" is the word you use in the YAML file.  So when `bild` sees 'coffee' as an item 
in the list in the YAML, it will require `bild-coffee`.  

Each plugin exports a 'process' function.  See, for example, the `bild-coffee` code.

## Running individual tasks

You can give a specific plugin to run on the command line.  So with the above YAML, running `bild coffee` will only execute the coffee task.
