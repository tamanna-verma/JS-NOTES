Lazy Loading is a technique that allows you to load components or other assets asynchronously, on-demand, instead of loading everything upfront. This can help improve the initial load time of your application by splitting it into smaller, manageable chunks.

      import React, { lazy, Suspense } from 'react';


Define the component to be lazily loaded: 

      const MyComponent = lazy(() => import('./MyComponent'));


Note that the argument to React.lazy is a function that returns a dynamic import statement. This allows Webpack (or other bundlers) to create a separate chunk for the lazily loaded component.

Place the lazily loaded component inside a Suspense component:

      function App() {
        return (
          <div>
            <Suspense fallback={<div>Loading...</div>}>
              <MyComponent />
            </Suspense>
          </div>
        );
      }

The Suspense component is used to specify a fallback content while the lazily loaded component is being loaded.

By using lazy loading, you can defer the loading of those components until they are actually required, reducing the initial bundle size and improving the application's performance.
