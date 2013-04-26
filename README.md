ZXingSimple
===========

[ZXing](https://github.com/zxing/zxing) Simplified example for Android.

Using the latest source of 2013-04-25.

Capture
-------

```
Intent intent = new Intent(this, CaptureActivity.class);
intent.setAction(Intents.Scan.ACTION);
/*intent.putExtra(Intents.Scan.WIDTH, 400);
intent.putExtra(Intents.Scan.HEIGHT, 300);*/
startActivityForResult(intent, REQ_CAPTURE);
```

Generate
--------

```
Intent intent = new Intent(Intents.Encode.ACTION);
intent.putExtra(Intents.Encode.FORMAT, BarcodeFormat.QR_CODE);
/** Contents.Type comments for details */
intent.putExtra(Intents.Encode.TYPE, Contents.Type.TEXT);
intent.putExtra(Intents.Encode.DATA, text);
try {
    QRCodeEncoder qrCodeEncoder = new QRCodeEncoder(this, intent, dimension, false);
    Bitmap bitmap = qrCodeEncoder.encodeAsBitmap();
    if (bitmap == null) {
        Log.w(TAG, "Could not encode barcode");
        Toast.makeText(this, R.string.msg_encode_contents_failed, Toast.LENGTH_SHORT)
                .show();
    } else {
        String title = qrCodeEncoder.getTitle();
        String contents = qrCodeEncoder.getContents();
        // TODO
    }
} catch (WriterException e) {
    e.printStackTrace();
}
```

Portrait mode
-------------

`android:screenOrientation="portrait"`

Search file for key words `Modified for portrait`.
