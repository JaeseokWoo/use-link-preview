# use-link-preview

`use-link-preview` is a React custom hook that simply provides link-preview metadata by [link-preview-server](https://github.com/JaeseokWoo/link-preview-server).

## Document

- [Installation](#installation)
- [How to use](#how-to-use)
- [API options](#api-options)
- [Demo](#demo)

## Installation

```bash
npm install use-link-preview
```

## How to use

### Install the package.

```bash
npm install use-link-preview
```

### Import and Use use-link-preview for components that require link-preview metadata.

```jsx
import useLinkPreview from "use-link-preview";

function LinkPreview({ url }) {
  const { metadata, isLoading, isError } = useLinkPreview(url);

  // Usage example
  return (
    <>
      {isLoading && <LoadingComponent />}
      {isError && <ErrorComponent />}
      {metadata && (
        <>
          <h3>{metadata.title}</h3>
          <p>{metadata.description}</p>
          <p>{metadata.domain}</p>
          <img src={metadata.img} />
          <p>{metadata.requestUrl}</p>
        </>
      )}
    </>
  );
}
```

## API options

```js
const { metadata, isLoading, isError } = useLinkPreview(url);
```

### parameter

- `url`: url string to get link-preview metadata

### return value

- `metadata`: Received link-preview metadata (or null)
- `isLoading`: Check if metadata is being parsed. true or false
- `isError`: error thrown by parsing metadata (or null)

### types

- **metadata**

  - title: string | null;
  - description: string | null;
  - img: string | null;
  - domain: string;
  - requestUrl: string;

- **isLoading**: boolean

- **isError**: Error | null

## Demo

[link-preview-server](https://js-linkpreview.herokuapp.com/)
