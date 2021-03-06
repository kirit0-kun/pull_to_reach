# Pull-To-Reach

Pull to reach is utilizing the pull gesture to overcome the problem of accessing the non-reachable controls of an app by highlighting them and triggering them once you release your thumb!

<br><br>
###### example
<img src="https://github.com/TiO-Design/pull_to_reach/blob/master/media/example.gif?raw=true" width="443">
<br><br>

## Install

Add the following snippet into your `pubspec.yaml`. A release on pub will follow soon!

```yaml
pull_to_reach:
    git:
      url: https://github.com/TiO-Design/pull_to_reach.git
```

## Usage

1. Wrap your Page in a `PullToReachContext`
2. Wrap your ListView (or any other Scrollable) in a `ScrollToIndexConverter`
3. Use  a`Reachble` and react to focus and select events!
 
```dart
  PullToReachContext(
      indexCount: 4,
      child: Scaffold(
      appBar: AppBar(
        actions: [
          ReachableIcon(
            icon: Icon(Icons.search),
            index: 1,
            onSelect: _showSearchBox,
          ),
          Reachable(
            index: 2,
            child: someChild,
            onFocusChanged: (isFocused) {
              // customize appearance if focus changes
            },
            onSelect: () {
              // do navigation or trigger action
            },
          ),
        ],
      ),
      body: ScrollToIndexConverter(
        child: _buildList(),
      ),
    ));
```



### Haptic Feedback

Feedback can be configured using `HapticReachableFeedback`

```dart
// Optionally, vibration can be triggerd for specific indices.
final ReachableFeedback feedback = HapticReachableFeedback(
      shouldVibrateOnFocus: (index) => index > 0,
      shouldVibrateOnSelect: (index) => index > 0);
      
      
      PullToReachContext(
        onFocusChanged: feedback.onFocus,
        onSelectChanged: feedback.onSelect,
        child: yourChild,
     );
```





