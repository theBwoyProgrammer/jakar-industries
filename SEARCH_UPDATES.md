# Search Box Updates Needed

## In Header.astro:

### 1. Change search container border-radius (line ~277):
FROM: `border-radius: 100px;`
TO: `border-radius: 4px;`

### 2. Change search trigger border-radius (line ~300):
FROM: `border-radius: 50%;`
TO: `border-radius: 4px;`

### 3. Remove hover expand listeners (around line 52-54 in script):
REMOVE these lines:
```
    // Expand on trigger hover
    searchTrigger.addEventListener('mouseenter', expand);
    searchContainer.addEventListener('mouseenter', expand);
    searchContainer.addEventListener('mouseleave', collapse);
```

## In Hero.astro:

### Fix market-btn underline animation to only underline text (around line 230):
REPLACE:
```css
  .market-btn.hover-underline-animation::after {
    height: 1px;
    background-color: rgba(255, 255, 255, 0.8);
  }
```

WITH:
```css
  .market-btn.hover-underline-animation {
    position: relative;
  }

  .market-btn.hover-underline-animation::after {
    height: 1px;
    background-color: rgba(255, 255, 255, 0.8);
    bottom: 1rem;
    width: calc(100% - 1.5rem);
    left: 50%;
    transform: translateX(-50%) scaleX(0);
  }

  .market-btn.hover-underline-animation:hover::after {
    transform: translateX(-50%) scaleX(1);
  }
```
