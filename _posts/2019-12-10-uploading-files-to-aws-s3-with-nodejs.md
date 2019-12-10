---
title: Uploading Files to AWS S3 with Node.js
image: "/assets/default-social-image.png"
categories: Node.js
---

**Introduction**

Many of today's software and web applications require some sort of file for storage-images, invoices, audio files, etc. The conventional way of saving data is literally to save them on the HDD of the server or database. Saving data on the server's HDD, though, comes with drawbacks such as being unable to scale up, allocating storage before using, and much higher/non-flexible costs. Not to mention, it can really put a strain on the server to request a huge amount of (potentially large) images.

Developers began hosting files with the ability to store providers like [AWS S3](https://aws.amazon.com/s3/), [Google Cloud Storage](https://cloud.google.com/storage/), etc. to offload servers.

We'll show you how to write Node.js code for uploading files to S3 in this article.

**What is S3?**

S3, or Simple Storage Service, is an Amazon Web Services (AWS) cloud storage network. You could store any number of files using S3 while you are still billed for what you are actually using.

S3 also offers multi-regional hosting and storage of data by area of users, allowing them to access the required data very easily with minimal delay.

**Setting up the Environment**

**AWS Credentials**

To get started:

1. The AWS Security Key Access credentials need to be generated first. Login to your AWS Management Console to do this.
2. Click on your username
3. Then select Access Keys -> Create New Access Key
4. Next, you could either copy from the window, the Control Key ID and Hidden Access Key, or download it as a `.CSV` file

**Creating an S3 Bucket**

1. Now let's create a properly accessed AWS S3 Bucket. Use the AWS management console or use Node.js to do this.
2. To use the management console to build a S3 bucket, go to the S3 service by accessing it from the service menu
3. Choose "Create Bucket" and enter your bucket's name and the region you want your bucket to host. If you already know the majority of your users would come upon which area, it is prudent to pick a country/region as close as possible to their location. This will ensure that the server files are served in a better timeframe. The title you choose for your bucket ought to be a unique name to all AWS clients, so take a new one if there is no name accessible
4. Follow the wizard and configure permissions and other parameters according to your specifications.

We will first have to set up our development environment to build the bucket using Node.js.

**Development Environment**

Let's start now with our example by setting up a new project Node.js:

`$ npm init`

We need to install the AWS SDK (System Development Kit) to start using any AWS Cloud Services in Node.js.

Use your preferred package manager to install it, we will use `npm`:

`$ npm i --save aws-sdk`

**Implementation**

**Creating an S3 Bucket**

If you have already manually created a bucket, this part may be skipped. And if not, let's construct a file in your project directory, say, `create-bucket.js`.

To access your S3 bucket, import the `aws-sdk` library:

`const AWS = require('aws-sdk');`

Let's now identify three constants for ID, SECRET, and BUCKET_NAME to be stored. To identify and for accessing our bucket, these are used:

```
// Enter copied or downloaded access ID and secret key here
const ID = '';
const SECRET = '';

// The name of the bucket that you have created
const BUCKET_NAME = 'test-bucket';
```

Now, by passing our access keys, we need to configure the S3 interface:

```
const s3 = new AWS.S3({
    accessKeyId: ID,
    secretAccessKey: SECRET
});
```

Now with the effective initialization of the S3 interface, we can go forward and build the bucket:

```
const params = {
    Bucket: BUCKET_NAME,
    CreateBucketConfiguration: {
        // Set your region here
        LocationConstraint: "eu-west-1"
    }
};

s3.createBucket(params, function(err, data) {
    if (err) console.log(err, err.stack);
    else console.log('Bucket Created Successfully', data.Location);
});
```

At this point, if the bucket is created in the cloud, we can run the code and test it:

`$ node create-bucket.js`

Now, If the execution of software is successful, you can see the message of successful execution accompanied by the address of the bucket in the output:

`Bucket Created Successfully http://test-bucket-2415soig.s3.amazonaws.com/`

You should access the dashboard of your S3 to make sure the bucket is built

Please take a look at the [official documentation](https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html) for a complete list of regions and other parameters.

**Uploading Files**

Let's enforce the features of file upload at this level. Install the `aws-sdk` package to view your S3 bucket in a new file, for instance `upload.js`, and the `fs` module to read files from your computer:

```
const fs = require('fs');
const AWS = require('aws-sdk');
```

To store `ID`, `SECRET`, and `BUCKET_NAME`, we need to identify three constants and configure the S3 client as we have done before.

Let's construct a function that accepts a parameter of `fileName`, describing the file that we want to upload:

```
const uploadFile = (fileName) => {
    // Read content from the file
    const fileContent = fs.readFileSync(fileName);

    // Setting up S3 upload parameters
    const params = {
        Bucket: BUCKET_NAME,
        Key: 'cat.jpg', // File name you want to save as in S3
        Body: fileContent
    };

    // Uploading files to the bucket
    s3.upload(params, function(err, data) {
        if (err) {
            throw err;
        }
        console.log(`File uploaded successfully. ${data.Location}`);
    });
};
```

We have to interpret the contents as a buffer before we submit the file. After reading it, we may specify the parameters required for uploading the file, like `Bucket`, `Key` and `Body`.

There is a plethora of many other optional parameters in relation to such three parameters. Below are a few basic things to get an understanding of the stuff you should describe for a file when uploading:

* `StorageClass`: Defines the class you want the object to be stored. S3 was designed to easily serve files. But you can use a different storage class if files are not regularly accessed. When you have barely accessed files for instance, you can hold them in "S3 Glacier Storage" wherein the cost is very low in comparison to "S3 Standard Storage". However in case you need it, it will take longer time to view such documents and is bound by a different service level agreement policy.
* `ContentType`: Sets the MIME type of image. "Binary/octet-stream" will be the default form. A MIME type such as "image/jpeg" is added to help browsers and other HTTP clients identify the file type.
* `ContentLength`: Sets the body size in bytes, which is helpful if the body size can not be immediately calculated.
* `ContentLanguage`: Set this parameter to describe the content's language. This will also help identify or convert information from HTTP users.

We will use our bucket name for the `Bucket` parameter, while we will use the file name for that we want to save as with the `Key` parameter, and we will use `fileContent` for the `Body` parameter.

Through passing the filename to the function, we can upload any file.

`uploadFile('cat.jpg');`

While in the same directory as the code, you may overwrite "cat.jpg" with a file name, a relative or an absolute path to the file.

We can run the code at this moment in time and check whether it works:

`$ node upload.js`

If all is well, you need to see the output as seen below with a reference to your file that is stored in `data.Location`:

`File uploaded successfully. https://test-bucket-1242tsr.s3.ap-northeast-2.amazonaws.com/cat.jpg`

Any error should also be reflected on the console, if it occurs.

In addition, in the AWS Management Console, you may go to your bucket and ensure that the file is uploaded.

**Conclusion**

Hosting data through cloud services such as AWS S3, Google Cloud Cloud, etc. is one amongst popular choice for developers to access the application servers. A very basic Node.js app is built that uses the `aws-sdk` framework to manage file uploads to S3 through its interface.

You can also set up public access to your bucket or files using the console, depending on your specifications.

If nonetheless, you want to play around with the code, you can find it in [GitHub](https://gist.github.com/jkasun/b0e2b818e0271db9c1363f637dacf12e).