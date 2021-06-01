# Compendium Module

Followed the instructions on [Forge](https://forums.forge-vtt.com/t/how-to-create-and-distribute-a-compendium-module/13260#heading--content) to create a basic compendium module that didn't require a complicated hosting setup.

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

There is a Github workflow here (`.github/workflows/release.yml`) to automatically create a release which includes a zipped copy of the module and the `module.json` file as release artifacts.

Tag any commit with something starting with a v (v0.1, v1.2, etc.) and it'll get turned into a release once it's pushed to github.

Feel free to use the workflow, it should copy over as is. To then get your manifest information, you'll want to update the `download` and `manifest` values:

```json
{
  "name": "module-name",
  "download": "https://github.com/${{github.repository}}/releases/latest/download/module.zip"
  "manifest": "https://github.com/${{github.repository}}/releases/latest/download/module.json"
}
```

You can change the name of the zip file if you want, but `module.json` needs to retain its name.

### Git tags

If you haven't worked with git tags before, this is how.

Start with the commit that you want to tag checked out. For this example, I'm going to use the tag v1.2

```sh
git tag v1.2 # create the tag, which will be connected to the current checkout sha
git push origin v1.2 # push the tag to github (or wherever)
```

You can make more complex tags with comments, check help for that.
