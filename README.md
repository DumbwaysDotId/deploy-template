# Cloudinary

`Cloudinary` is a cloud-based image and video management services. It enables users to upload, store, manage, manipulate, and deliver images and video for websites and apps.

### Prepare

- Login to [cloudinary](https://cloudinary.com/)

* Click `Media Library`

* Create a folder that will be used to store files

* Go to `Settings` → `Upload`

* Scroll down to `Upload presets`, Click `Add upload preset` → fill in the form and click `save`

### Server side (backend)

- Install cloudinary

  ```
  npm i cloudinary
  ```

* On `server/src/`

* Create `utils` folder and inside it create `cloudinary.js` file

* Add code below

  ```javascript
  const cloudinary = require('cloudinary').v2;
  cloudinary.config({
    cloud_name: process.env.CLOUDINARY_NAME,
    api_key: process.env.CLOUDINARY_API_KEY,
    api_secret: process.env.CLOUDINARY_API_SECRET,
  });

  module.exports = cloudinary;
  ```

  Get Cloudinary name, api key, and api secret from dashboard on web

* On File : `server/src/controllers/product.js`

* Get `cloudinary` from `utils`

  ```javascript
  ...
  const cloudinary = require('../utils/cloudinary');
  ...
  ```

* On `addProduct`, add code for handle uploader to cloudinary

  ```javascript
  ...
  const result = await cloudinary.uploader.upload(req.file.path, {
    folder: 'dumbmerch_file',
    use_filename: true,
    unique_filename: false,
  });
  ...
  ```

* Modify image attribute in data variable, like code below

  ```javascript
  ...
  const data = {
      name: req.body.name,
      desc: req.body.desc,
      price: req.body.price,
      image: result.public_id,
      qty: req.body.qty,
      idUser: req.user.id,
      };
  ...
  ```
