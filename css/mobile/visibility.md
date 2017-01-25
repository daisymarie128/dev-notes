### Visibility on ios

The [visibility](https://developer.mozilla.org/en/docs/Web/CSS/visibility) property in css does not work well on IOS devices.

I havn't had time to investigate this issue much, but what I tested involved using 2 Vimeo containers on top of each other and this caused funny results.

**Issues:**
- Couldn't press play on one of the videos
- Toggling/switching between the two videos never showed the other one.

```
span {
		visibility: hidden;

		&.active {
			visibility: visible;
		}
	}
```

###### Fixed using this instead:

```
span {
		display: none;

		&.active {
			display: block;
		}
	}
```
