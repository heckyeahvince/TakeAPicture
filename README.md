# Taking a Picture

This assignment illustrates the basic usage of built-in camera in Android.


## Problem:

Implement an Android activity for taking a picture and show it in an ImageView.   


## Keypoints:

Setting up a button onClickListener in Java:
```Java
        Button b = (Button) findViewById(R.id.picbutton);

        b.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent picIntent = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);
                startActivityForResult(picIntent, REQUEST_IMAGE_CAPTURE);
            }
        });
```

Showing the taken image in an ImageView:
```Java
   @Override
    protected void onActivityResult(int requestCode, int resultCode,
                                    Intent intent) {
        if (requestCode == REQUEST_IMAGE_CAPTURE
                && resultCode == RESULT_OK) {
            setContentView(R.layout.activity_pic);
            Bitmap bmp = (Bitmap) intent.getExtras().get("data");
            ImageView img = (ImageView) findViewById(R.id.pictureview);
            img.setImageBitmap(bmp);
        }
    }
```
