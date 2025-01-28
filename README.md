# Expo AsyncStorage TypeError: Converting circular structure to JSON
This repository demonstrates a common error encountered when using AsyncStorage in Expo applications: a TypeError related to converting circular structures to JSON.  The error arises when attempting to store data containing circular references in AsyncStorage, which only supports storing stringified JSON data.

## Problem
The issue lies in the incorrect usage of AsyncStorage's `setItem` method.  If you try to store an object with a circular reference (an object referencing itself directly or indirectly), JSON.stringify will throw an error. AsyncStorage uses JSON.stringify behind the scenes, causing the failure.

## Solution
The solution involves ensuring that only serializable data is passed to `setItem`.  This usually entails restructuring your data to remove circular references before storing it in AsyncStorage.