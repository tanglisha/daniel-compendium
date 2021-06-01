# Compendium Module

Followed the instructions on [Forge](https://forums.forge-vtt.com/t/how-to-create-and-distribute-a-compendium-module/13260#heading--content) to create a very basic compendium module.

To use this module, you have to start from when you first open Foundry VTT. Go to the `Add-on Modules` tab. Click the button on the bottom left called `Install Module`. On the bottom of the resulting popup, you'll see a text box titled `Manifest URL`. Paste the following into that box:

```
https://github.com/tanglisha/daniel-compendium/releases/latest/download/module.json
```

Now click the `Install` button to the right of that text box.

You can now launch your world, the module should be available. Within your world, go to `Game Settings`. Click `Manage Modules`. There will be a module on the list titled `Daniel's Shiny New Compendium`. Make sure the box to the left is checked. If it isn't, check the box and click the `Save Module Settings` button at the bottom left of that popup.

You'll now see the module content in the `Compendium` tab under the `Default` folder, because I haven't figured out how to get things elsewhere yet. You can import individual items or entire directories, which will then show up in the `Items` tab.

# Developer Notes

I made this as a learning exercise. Feel free to take it and mess with it.

## Github Actions

There is a Github workflow here (`.github/workflows/release.yml`) to automatically create a release which includes a zipped copy of the module and the `module.json` file as release artifacts. Feel free to use the workflow, it should copy over as is. To then get your manifest information, you'll want to update the following values:

```
  "download": "https://github.com/<owner>/<project>/releases/latest/download/module.zip"
  "manifest": "https://github.com/<owner>/<project>/releases/latest/download/module.json"

```

You can change the name of the zip file if you want, but `module.json` needs to retain its name.
