---
title: godot-tester
date: 2023-10-01 03:14:52 +00:00
tags:
  - croconut
  - GitHub Actions
draft: false
repo: croconut/godot-tester
marketplace: https://github.com/marketplace/actions/godot-tester
version: v5.1
dependentsNumber: "27"
---


Version updated for **croconut/godot-tester** to version **v5.1**.
- This publisher is shown as erified by GitHub.
- This action is used across all versions by **27** repositories.

Go to the [GitHub Marketplace](https://github.com/marketplace/actions/godot-tester) to find the latest changes.

## Release notes

# Godot Tester - Godot 4 & GUT 9 Support

## What's Changed
* chore: Use Node 20 and `checkout@v4` by @jeremyckahn in https://github.com/croconut/godot-tester/pull/40

## New Contributors
* @jeremyckahn made their first contribution in https://github.com/croconut/godot-tester/pull/40
* @baabcantcode made their first contribution in https://github.com/croconut/godot-tester/pull/30

**Full Changelog**: https://github.com/croconut/godot-tester/compare/v4...v5.1

## Additions from previous releases
* Rewrote the action to use Node JS.
* Added download support for Godot 4 & QA tested with GUT 9.
* Removed input: `ignore-errors`. 
  * Test result parsing is no longer done via STDOUT, it is done via the exported .XML file provided by GUT.
* Increased the default import timeout from 1 second to 15 seconds
* Updated `Dockerfile` to download .NET dependencies
* customizing the test directory path (e.g. tests instead of test)
* support for alternative release types, previously only stable was supported
* can set maximum failures with max-fails
* can check assert pass / fail counts instead of test pass / fail counts
* can specify a custom download URL for the godot binary
* GUT's XML test results are now being parsed
## Example Use:

```yaml
name: Godot testing

on: [ push ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - uses: croconut/godot-tester@v5.1
      with:
        # required
        version: "4.1"
        # the type of release of godot that the tests should be run with
        release_type: "rc2"
        is-mono: "true"
        # the folder with your project.godot file in it
        path: "tester"
        # how long to spend importing assets before tests are run
        import-time: "5"
        # how long tests can run in seconds
        test-timeout: "45"
        # the ratio of tests that must pass for this action to pass
        # e.g. 0.6 means 60% of your tests must pass
        minimum-pass: "0.6"
        # the directory containing Gut tests
        test-dir: "res://test"
        # instead of running GUT's command line tool, 
        # you can run a test scene if you have one
        # set up a scene like in this repo --> located at /tester_GUT_v9.0.1/test/alt_mode/tests.tscn
        # set up a script like in this repo --> located at /tester_GUT_v9.0.1/test/alt_mode/cli_test.gd
        # ensure that the script exits on test completion
        # uses relative path from your godot project directory
        direct-scene: "tester_GUT_v9.0.1/test/alt_mode/tests.tscn" 
        # default is false, set true to count asserts instead of tests
        assert-check: "true" 
        # not checked by default, set to a number to limit the 
        # maximum amount of failed tests for a passing test suite
        max-fails: 3  
        # default is GUTs default: 'res://.gutconfig.json'; set this to load a different config file
        config-file: "res://.myconfig.json" 
        # designate a custom url to download the godot binary from
        custom-godot-dl-url: ""
        # relative path to the xml file to read / write GUT's results from, recommended
        # for direct-scene users to check this file if you have issues
        result-output-file: "test_results.xml"

```
