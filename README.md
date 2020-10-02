# WallColle

Wallpaper collection management system.

WIP. Not ready for production.

## Introduction

This repo is designed to be the hub of managing community-contributed wallpapers.

It is tailored for [AOSC OS](https://aosc.io), but other communities may find this work helpful.

## Contribution Model

### Principles

- Wallpapers are contributed by community members.
- Each Wallpaper has 1 and only 1 Contributor.
- Each Contributor has an arbitrary number of Wallpapers.
- Each Pack contains multiple Wallpapers.
- For each release (e.g. OS Version), a set of Wallpapers may be bundled into it. Such a release is identified as a Pack.

## Wallpaper Quality Requirements

- Ratios: `1:1` or `16:10`.
- The format should be PNG, JPEG, or SVG.
- Minimal width: 2560px for `1:1`; 3200px for `16:10`.
- The colorspace should be sRGB.
- The color depth should be 8 bits.

## Contribute Wallpapers

### Copyright

- You should own the to-be-submitted image, or you can prove that any person can redistribute the image under a specific license.

### 1. Fork This Repo

Fork this repo to your own account and make changes there.

The following steps are supposed to be executed in your own repository.

### 2. Create Your Directory & Manifest

Suppose that your GitHub username is `myname`.

At `/contributors/myname/me.json`, you should write a JSON configuration which looks like this:

```json
{
    "uname": "myname",
    "name": "My Name",
    "uri": "mailto:myname@exmaple.com",
    "wallpapers": [
        {
            "i": 0,
            "f": "png",
            "t": "Image_Title",
            "l": "cc-by-nd-4.0",
            "tags": [ "Abstract", "Nature", "Forest" ]
        }
    ]
}
```

Field           | Description
--------------- | -----------
`uname`         | Your GitHub username.
`name`          | Your human-friendly name.
`uri`           | Your email address () or website.
`wallpapers`    | An array of your wallpapers.

For each entry in `wallpapers` field:

Field   | Description
------- | -----------
`i`     | The index of this image.
`f`     | The format of this image. Must be 3 lowercase characters. Can be `png`, `jpg`, or `svg`.
`t`     | The title of this image. Will be used for human-friendly display purposes. Can include letters, numbers, and hyphens. Must be unique across contributors. Use title capitalization.
`l`     | License identifier. You can find the list of acceptable licenses in another section later.
`tags`  | Optional field. An array of tags. Each tag can only contain lowercase letters. You can find the list of acceptable tags in another section later.

### 3. Put Your Image

Since this is your initial contribution, your directory should be empty.

Suppose that your contribution is a PNG file. You may put it in your directory and its path should be `/contributors/myname/0.png`.

The index should be autoincremental from 0. All formats share the same counter.

You may submit multiple images at once, surely.

### 4. Create Pull Request

Create a pull request, literally. We will review and merge, as long as the image qualifies.

## Packs

Each pack is represented by a file in `/packs`.

Each line consists of 3 parts:

- The `uname` of the contributor
- A colon character
- The index of the image

For example, `neruthes:0` refers to the sequence 0 image of contributor `neruthes`.

Empty lines are ignored. Comment lines start with `# `.

After configuring a pack definition at `/packs/packname`, run:

```
$ node make.js packname
```

Then the corresponding images will be copied to `/dist`, with a generated text description file `/dist/manifest.txt`, which includes some information of the pack and the included wallpapers (title, contributor, license).

Therefore you can "really" pack them with your favorite packing toolchain, zip or tar or whatever.

## Contribute Code

There is no limit!

## Prospective Works

- JSON format lint
- File existence check
- Preview candidates by tags

## Copyright

Copyright (c) 2020 Neruthes <i@neruthes.xyz> and 0 other contributors.

The Programs in this repository are released under GNU GPLv2.

The images may have their respective licenses, as defined in the corresponding configuration files.

## Contributors

- (Empty List)

## Appendix 1: Acceptable Tags

Major tags and minor tags coexist. Each minor tag must belong to 1 major tag.

When using any minor tag, its parent major tag must also be used.

The order of the tags in this depth-prioritizingly serialized tree is the order in which the tags of a wallpaper appear in the `tags` field array.

This is the tree of tags.

- Abstract
  - Geometry
  - Laser
- Civil
  - Countryside
  - Cyberpunk
  - Cyberpunk
  - Metropolis
- Fantasy
- Illustration
- Legacy
- Nature
  - Desert
  - Forest
  - Jungle
  - Mountain
  - Oasis
  - Plant
  - Water

## Appendix 2: Acceptable Licenses

- CC-BY-SA-4.0
- CC-BY-ND-4.0
- Public-Domain
