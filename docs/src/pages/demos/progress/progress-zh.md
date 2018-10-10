---
title: Circular Progress, Linear Progress React component
components: CircularProgress, LinearProgress
---
# 进度

<p class="description">进度指示器用以表示一个不确定的等待时间或显示一个处理过程的时间长短。</p>

[进度指示器](https://material.io/design/components/progress-indicators.html) 通知用户当前处理过程的状态，例如加载一个应用，提交一个表单或保存一些更新。 它们与应用程序状态进行通信并指示可用的操作，例如用户是否可从当前页面离开。

**确定的** 指示器显示一个操作消耗多长时间。

**未确定**指示器可视化一个不确定的操作等待时间。

#### Progress as a group

When displaying progress for a sequence of processes, indicate overall progress rather than the progress of each activity.

## Circular

[Circular progress](https://material.io/design/components/progress-indicators.html#circular-progress-indicators) support both determinate and indeterminate processes.

- **Determinate** circular indicators fill the invisible, circular track with color, as the indicator moves from 0 to 360 degrees.
- **Indeterminate** circular indicators grow and shrink in size while moving along the invisible track.

### Circular Indeterminate

{{"demo": "pages/demos/progress/CircularIndeterminate.js"}}

### Interactive Integration

{{"demo": "pages/demos/progress/CircularIntegration.js"}}

### Circular Determinate

{{"demo": "pages/demos/progress/CircularDeterminate.js"}}

### Circular Static

{{"demo": "pages/demos/progress/CircularStatic.js"}}

## Linear

[Linear progress](https://material.io/design/components/progress-indicators.html#linear-progress-indicators) indicators.

### Linear Indeterminate

{{"demo": "pages/demos/progress/LinearIndeterminate.js"}}

### Linear Determinate

{{"demo": "pages/demos/progress/LinearDeterminate.js"}}

### Linear Buffer

{{"demo": "pages/demos/progress/LinearBuffer.js"}}

### Linear Query

{{"demo": "pages/demos/progress/LinearQuery.js"}}

## Non-standard ranges

The progress components accept a value in the range 0 - 100. This simplifies things for screen-reader users, where these are the default min / max values. Sometimes, however, you might be working with a data source where the values fall outside this range. Here's how you can easily transform a value in any range to a scale of 0 - 100:

```jsx
// MIN = Minimum expected value
// MAX = Maximium expected value

// Function to normalise the values (MIN / MAX could be integrated)
const normalise = value => (value - MIN) * 100 / (MAX - MIN);

// Example component that utilizes the `normalise` function at the point of render.
function Progress(props) {
  return (
    <React.Fragment>
      <CircularProgress variant="determinate" value={normalise(props.value)} />
      <LinearProgress variant="determinate" value={normalise(props.value)} />
    </React.Fragment>
  )
}
```

## Delaying appearance

There are [3 important limits](https://www.nngroup.com/articles/response-times-3-important-limits/) to know around response time. The ripple effect of the `ButtonBase` component ensures that the user feels that the system is reacting instantaneously. Normally, no special feedback is necessary during delays of more than 0.1 but less than 1.0 second. After 1.0 second, you can display a loader to keep user's flow of thought uninterrupted.

{{"demo": "pages/demos/progress/DelayingAppearance.js"}}

## Limitations

Under heavy load, you might lose the stroke dash animation or see random CircularProgress ring widths. You should run processor intensive operations in a web worker or by batch in order not to block the main rendering thread.

![heavy load](/static/images/progress/heavy-load.gif)

See https://github.com/mui-org/material-ui/issues/10327