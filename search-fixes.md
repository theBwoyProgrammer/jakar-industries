# Search Box Fixes Needed

## Issue 1: Search results are jammed together (no spacing between items)
In Header.astro, update the search results styling:

### Around line 335-360, update `.search-results`:
```css
.search-results {
  position: absolute;
  top: calc(100% + 0.5rem);
  left: 0;
  right: 0;
  background: rgba(0, 0, 0, 0.95);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 8px;
  overflow: hidden;
  max-height: 300px;
  overflow-y: auto;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
  display: flex;              /* ADD THIS */
  flex-direction: column;     /* ADD THIS */
  gap: 0;                     /* ADD THIS */
}
```

### Update `.search-result-item`:
```css
.search-result-item {
  display: block;
  padding: 0.85rem 1rem;      /* CHANGE from 0.75rem */
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  font-size: 0.85rem;
  transition: background 0.2s ease, color 0.2s ease;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  white-space: nowrap;        /* ADD THIS */
  overflow: hidden;           /* ADD THIS */
  text-overflow: ellipsis;    /* ADD THIS */
}
```

## Issue 2: Mobile search box shrinking

### Around line 376-397, update mobile search styles:
```css
@media (max-width: 767px) {
  .search-container--expanded {
    width: clamp(240px, 70vw, 320px);    /* CHANGE from 200px, 60vw, 280px */
    position: absolute;
    right: var(--space-md);
    top: 50%;
    transform: translateY(-50%);
    box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
    overflow: visible;
    max-width: calc(100vw - 2 * var(--space-md));
    min-width: 240px;                    /* ADD THIS */
  }
  
  .search-container {
    width: 40px;
    height: 40px;
  }
  
  .search-trigger {
    width: 40px;
    height: 40px;
  }
  
  .search-input {
    font-size: 0.9rem;
    min-width: 160px;                    /* ADD THIS */
  }

  .search-results {                      /* ADD THIS WHOLE BLOCK */
    width: 100%;
    max-width: none;
  }

  .search-result-item {                  /* ADD THIS WHOLE BLOCK */
    font-size: 0.8rem;
    padding: 0.75rem 0.85rem;
  }
}
```

These changes will:
1. Properly space out search results so they appear on separate lines
2. Prevent mobile search box from shrinking by setting minimum width
3. Improve readability on mobile devices
