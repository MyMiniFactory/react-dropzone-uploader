# React Dropzone Uploader


[![NPM](https://img.shields.io/npm/v/react-dropzone-uploader.svg)](https://www.npmjs.com/package/react-dropzone-uploader)
[![npm bundle size (minified + gzip)](https://img.shields.io/bundlephobia/minzip/react-dropzone-uploader.svg)](https://www.npmjs.com/package/react-dropzone-uploader)

React Dropzone Uploader is a customizable file dropzone and uploader for React.


## Features
- Detailed file metadata and previews, especially for image, video and audio files
- Upload status and progress, upload cancellation and restart
- Easily set auth headers and additional upload fields ([see S3 example](https://react-dropzone-uploader.js.org/docs/s3))
- Modular design; use as standalone dropzone, file input, file uploader
- Customize styles using CSS or JS
- Fully controllable via optional props, callbacks and component injection
- Lightweight and fast


## Documentation
<https://react-dropzone-uploader.js.org>


## Installation
`npm install --save react-dropzone-uploader`

Import default styles in your app.

~~~js
import 'react-dropzone-uploader/dist/styles.css'
~~~


## Quick Start
RDU handles common use cases with almost no config. The following code gives you a dropzone and clickable file input that accepts image, audio and video files. It uploads files to `https://httpbin.org/post`, and renders a button to submit files that are done uploading. [Check out a live demo](https://codepen.io/kylebebak/pen/wYRNzY/?editors=0010).

~~~js
import 'react-dropzone-uploader/dist/styles.css'
import Dropzone from 'react-dropzone-uploader'

const MyUploader = () => {
  // specify upload params and url for your files
  const getUploadParams = ({ meta }) => { return { url: 'https://httpbin.org/post' } }
  
  // called every time a file's `status` changes
  const handleChangeStatus = ({ meta, file }, status) => { console.log(status, meta, file) }
  
  // receives array of files that are done uploading when submit button is clicked
  const handleSubmit = (files) => { console.log(files.map(f => f.meta)) }

  return (
    <Dropzone
      getUploadParams={getUploadParams}
      onChangeStatus={handleChangeStatus}
      onSubmit={handleSubmit}
      accept="image/*,audio/*,video/*"
    />
  )
}
~~~


## UMD Build
This library is available as an ES Module at <https://unpkg.com/react-dropzone-uploader@2.2.0/dist/react-dropzone-uploader.umd.js>.

If you want to include it in your page, you need to include the dependencies and CSS as well.

~~~html
<script src="https://cdnjs.cloudflare.com/ajax/libs/react/16.4.2/umd/react.production.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react-dom/16.4.2/umd/react-dom.production.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/prop-types/15.6.2/prop-types.min.js"></script>

<script src="https://unpkg.com/react-dropzone-uploader@2.2.0/dist/react-dropzone-uploader.umd.js"></script>
<link rel"stylesheet" href="https://unpkg.com/react-dropzone-uploader@2.2.0/dist/styles.css"></script>
~~~


## Contributing
<https://github.com/fortana-co/react-dropzone-uploader/blob/master/contributing.md>


## Thanks
Thanks to `react-dropzone`, `react-fine-uploader`, `react-select`, and `redux-form` for inspiration.
