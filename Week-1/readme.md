<h1>Workings of a Browser</h1>

<h3>When a user enters an URL in the browser, how does the browser fetch the desired result ? </h3>

Main functionality of a browser is to show the web resourse choosen by the user. Browser fetches the document from requested servers, renders and paints the document for the user to see and interact.
- **High level structure of a browser**

![image](https://user-images.githubusercontent.com/77035980/224569157-bec1484c-0fa8-487a-be60-15df2efded63.png)

  1. The user interface: this includes the address bar, back/forward button, bookmarking menu, etc. Every part of the browser display except the window where you see the     requested page.
  2. The browser engine: marshals actions between the UI and the rendering engine.
  3. The rendering engine: responsible for displaying requested content. For example if the requested content is HTML, the rendering engine parses HTML and CSS, and           displays the parsed content on the screen.
  4. Networking: for network calls such as HTTP requests, using different implementations for different platform behind a platform-independent interface.
  5. UI backend: used for drawing basic widgets like combo boxes and windows. This backend exposes a generic interface that is not platform specific. Underneath it uses       operating system user interface methods.
  6. JavaScript interpreter: Used to parse and execute JavaScript code.
  7. Data storage: This is a persistence layer. The browser may need to save all sorts of data locally, such as cookies. Browsers also support storage mechanisms such as     localStorage, IndexedDB, WebSQL and FileSystem.

- **Rendering Engine**

Rendering engine parses the html document and convert elements to DOM node in a tree called the "content tree". The engine will parse the style data, both in external CSS files and in style elements.
The render tree contains rectangles with visual attributes like color and dimensions. The rectangles are in the right order to be displayed on the screen.

After the construction of the render tree it goes through a "layout" process. This means giving each node the exact coordinates where it should appear on the screen. The next stage is painting - the render tree will be traversed and each node will be painted using the UI backend layer.

It's important to understand that this is a gradual process. For better user experience, the rendering engine will try to display contents on the screen as soon as possible. It will not wait until all HTML is parsed before starting to build and layout the render tree. Parts of the content will be parsed and displayed, while the process continues with the rest of the contents that keeps coming from the network

![image](https://user-images.githubusercontent.com/77035980/224570507-ffa98073-f737-4b7b-a4b4-1a9f5f752a0d.png)


There are multiple rendering engines such as Trident used by Internet Explorer, Firefox uses Gecko, Safari uses WebKit. Chrome and Opera use Blink, a fork of WebKit.
