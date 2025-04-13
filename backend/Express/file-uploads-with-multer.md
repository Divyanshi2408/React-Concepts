# File Uploads with Multer

[Multer](https://www.npmjs.com/package/multer) is a Node.js middleware used to handle `multipart/form-data`, which is primarily used for uploading files.

---

## Install Multer

```bash
npm install multer
```
### Basic Setup
```
const express = require('express');
const multer = require('multer');
const app = express();

// Configure storage
const storage = multer.diskStorage({
  destination: (req, file, cb) => {
    cb(null, 'uploads/'); // Folder to save files
  },
  filename: (req, file, cb) => {
    cb(null, `${Date.now()}-${file.originalname}`);
  }
});

// Create upload instance
const upload = multer({ storage });

// Upload single file
app.post('/upload', upload.single('file'), (req, res) => {
  res.send('File uploaded successfully!');
});
```
Make sure to create an uploads folder in your root directory or handle it dynamically.

### Upload Multiple Files
```
app.post('/upload-multiple', upload.array('files', 5), (req, res) => {
  res.send('Multiple files uploaded!');
});
```
'files' must match the field name in the form. The number 5 limits uploads to 5 files.

### File Type Filtering
```
const fileFilter = (req, file, cb) => {
  if (file.mimetype.startsWith('image/')) {
    cb(null, true); // Accept file
  } else {
    cb(new Error('Only images are allowed!'), false); // Reject file
  }
};

const uploadWithFilter = multer({
  storage,
  fileFilter
});
```

### File Size Limit
```
const uploadWithLimit = multer({
  storage,
  limits: { fileSize: 1024 * 1024 * 5 } // 5MB
});
```

### Example HTML Form (for testing)
html
```
<form action="/upload" method="POST" enctype="multipart/form-data">
  <input type="file" name="file" />
  <button type="submit">Upload</button>
</form>
```

### Summary
| Feature |	Description |
| ------- | ------------- |
| upload.single('fieldname')	| Upload a single file |
| upload.array('fieldname', n)	| Upload multiple files |
| storage	| Define destination and filename format |
| fileFilter |	Restrict uploads to certain file types |
| limits |	Limit file size or number of files |
