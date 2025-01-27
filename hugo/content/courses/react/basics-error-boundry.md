---
title: Error Boundries
description: How do Error Boundaries work in React?
weight: 11
lastmod: 2022-02-22T11:11:30-09:00
draft: false
vimeo: 683073619
emoji: 🚨
video_length: 1:15
---

{{< file "react" "App.js" >}}
```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    console.log('something went horribly wrong', error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Fallback UI</h1>;
    }

    return this.props.children;
  }
}

// Example Usage

function Main() {
  return (
    <Dashboard>
      <ErrorBoundary>
        <Orders />
      </ErrorBoundary>
    </Dashboard>
  );
}
```