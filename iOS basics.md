# Project structure
## AppDelegate.swift
* Follows the delegation pattern, handles the events for an application
* With the `@UIApplicationMain` attribute, tells swift to call main Application code with this as its Delegate
* Given access to the window (similar to DOM), to set the root ViewController
  * Not necessary if using story boards
* The `#application` method is the entry point to the application

## ViewController.swift
* Really just the C in MVC, brokers updates between model and view

## Controller
* One controller per screen
* Handle API requests
* event handling
* navigation

## Models
* Pretty thin
* (De)Serialization
* Formatting of data to better formats (e.g absolute dates to relative dates, combining family and given names)

## Views
* Everything is usually absolutely positioned (O_o)
  * Autolayout is an alternative to this
* handle animations
* handle event detection (like touch, swipe, etc)

### Q: How to attach listeners to element events?
