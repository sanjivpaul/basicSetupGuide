# Installation Guide
### 1. Vite React
#### Installation
```
npm create vite@latest
```

```
npm i
```

#### Run
```
npm run dev
```

### 2. Use of Ternary Operator
```jsx
  const [error, setError] = useState(false)

  const removeValue = () => {
    if (counter > 0) {
      setCounter(counter - 1)
    }else{
      setError(true)
    }
  }

// we can use it by this way
 {error && (
        <span>Counter can't be negative</span>
    )}


```